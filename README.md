## Keymap and Firmware

This is for the Corne keyboard bought from the typeractive.xyz.

## Firmware files are built by GitHub Actions

Download it from the artifacts.

## Faster builds

Alternative to the GitHub actions, use Docker and VSCode on your local machine for faster builds.

Follow the [ZMK instruction](https://zmk.dev/docs/development/local-toolchain/setup/container).

Create Docker volume:

```sh
export ZMK_CONFIG_DIR={path_to_your_zmk-config_directory}
docker volume create --driver local -o o=bind -o type=none -o device="$ZMK_CONFIG_DIR" zmk-config
```

In the VSCode Docker dev container terminal, to build the zmk.uf2:

```sh
west build -d build/left -b nice_nano_v2 -- -DSHIELD=corne_left -DZMK_CONFIG=/workspaces/zmk-config/config && \
west build -d build/right -b nice_nano_v2 -- -DSHIELD=corne_right -DZMK_CONFIG=/workspaces/zmk-config/config
```
