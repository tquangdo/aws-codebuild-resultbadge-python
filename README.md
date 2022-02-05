# aws-codebuild-resultbadge-python 🐳

![Stars](https://img.shields.io/github/stars/tquangdo/aws-codebuild-resultbadge-python?color=f05340)
![Issues](https://img.shields.io/github/issues/tquangdo/aws-codebuild-resultbadge-python?color=f05340)
![Forks](https://img.shields.io/github/forks/tquangdo/aws-codebuild-resultbadge-python?color=f05340)
[![Report an issue](https://img.shields.io/badge/Support-Issues-green)](https://github.com/tquangdo/aws-codebuild-resultbadge-python/issues/new)

## Build status:
---
![AWS CodeBuild](https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoicFVrMUcvME5ueUhLbmNKZ0pzaTR1RGNxOEZIbFpES1NWZElDd1pGZWxRUGNLeHc3NTRQR052cnA4UCt1dUZ3ZnB0YWgvZnBybjJOSjhXRDQxYWtuZGpzPSIsIml2UGFyYW1ldGVyU3BlYyI6IkhCMExWMENWZDVqUlNVNGYiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)

![detail](screenshots/detail.png)
## reference
[haitrungblog](https://haitrung.net/ci-task-voi-github-va-aws-codebuild/)


## step by step
### 1) create a repo
+ run process in repo:
1. Mặc định cấu hình life-cycle build dựa vào file `buildspec.yml` đặt ở thư mục root của source code
> buildspec.yml là file config life-cycle khi build project (appspec.yml là file config life-cycle khi deploy project)
+ hoac cach khac la dung `Insert build commands`
![buildspec](screenshots/buildspec.png)
2. `buildspec.yml`
```yml
    build:
        commands:
            - echo "BUILD phase"
            - python test.py
```
3. `test.py`
```py
def test_codebuild():
    assert functions.test_module(2) == 5 // return FALSE
```
4. `functions/function.py`
```py
def test_module(n):
    return n*2; 
```

### 2) generate new token
https://github.com/settings/tokens 

### 3) create AWS CodeBuild build project `DoTQ_CodeBuildDemo_Master`
+ add source: choose 2) & 1)
+ webhook: check `Rebuild every time a code change is pushed to this repository`
> reponame in screenshoot is old: `test_aws_codebuild.git`
+ Build specifications: Chọn `Use a buildspec file` (l/q `buildspec.yml`)
![codebuild](screenshots/codebuild.png)

### 4) copy badge URL
paste to  aws-codebuild-resultbadge-python/README.md → auto build OK

### 5) edit src code in 1) to return NG result
+ → auto build NG
![codebuildng](screenshots/codebuildng.png)
+
![badgeng](screenshots/badgeng.png)
