# REST API

## [Release assets] download

```sh
curl -LJO \
    -u ${username}:${token} \
    -H "Accept: application/octet-stream" \
    https://api.github.com/repos/${username}/${repo}/releases/assets/${asset_id}
```

- Create a [token] on your GitHub account on
  `Settings > Developer settings > Personal access tokens`; use all `repo`
  authorizations to download release assets also from private repositories.
  On GitHub Actions the variable {% raw %}${{ secrets.GITHUB_TOKEN }}{% endraw %}
  can be used instead.
- To obtain the `asset_id`:

```sh
curl \
    -u ${username}:${token} \
    -H "Accept: application/vnd.github.v3+json" \
    https://api.github.com/repos/${username}/${repo}/releases/tags/${tag_name}
```

## Run Actions workflow

```sh
curl \
-u ${username}:${token} \
-X POST \
-H "Accept: application/vnd.github.v3+json" \
https://api.github.com/repos/${username}/${repo}/actions/workflows/${yml_filename}/dispatches \
-d '{"ref":"${branch}"}'
```


[token]:          https://github.com/settings/tokens
[Release assets]: https://docs.github.com/en/rest/reference/repos#get-a-release-asset
