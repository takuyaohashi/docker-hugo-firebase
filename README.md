# docker-hugo-firebase
A docker image with hugo and firebase-cli installed

# Using on Gitlab CI

Here the example of `.gitlab-ci.yml` for Hugo `0.49`:

```yaml
image: takuyaohashi/docker-hugo-firebase:0.49

before_script:
  - hugo version
  - firebase --version

hugo_firebase:
  stage: deploy
  only:
    - master
  except:
    - dev
  script:
  - rm -rf public
  - hugo --config config.production.toml
  - firebase deploy --token ${FIREBASE_TOKEN}
```
