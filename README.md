# nrf52-zmk-spike
Realtime OS Zephyr, Nordin nrf52x dongle board with custom shield using ZMK

# Build and flash

Run the following in the root of the repository.

## Setup

```
west init -l config
west update
west zypher-export
```

## Build

``` shell
west build -s zmk/app -b nrf52840dongle_nrf52840 -- -DSHIELD=esbmasap -DZMK_CONFIG="$(pwd)/config"
```

## Flash

```
nrfutil pkg generate --hw-version 52 --sd-req=0x00 --application build/zephyr/zmk.hex --application-version 1 zmk.zip
sudo nrfutil dfu usb-serial -pkg zmk.zip -p /dev/ttyACM0
```

## Log output

``` shell
sudo tio /dev/ttyACM0
```
