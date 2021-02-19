
This repo is to check out how to refer to parent project version using properties.

This was created for making debug the question posted here: https://stackoverflow.com/q/66278445/622266

There are two maven projects, `top-level` and `auxiliary`. The are not expected to be in the same repository. `auxiliary` parents to `top-level`, when building `auxiliary`, the `top-level` artifacts are expected to be found in local or remote repository.

To look around:

```shell
git clone https://github.com/veselov/maven-parent-version-test.git
cd maven-parent-version-test/top-level
mvn install # this should go without a glitch
cd ../auxiliary

# try for hardcoded version values
mvn install # this works

# with parent referenced defined in child project's POM:
mvn -Pparent install # this doesn't work, but it's reasonable why

# with sub-module referencing grandparent
mvn -Pgrandparent install # this doesn't work, and I'm not sure why
                          # at least if you consider the comment to
                          # https://stackoverflow.com/a/6964151/622266
```
