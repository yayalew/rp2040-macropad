# Design Decisions

## RP2040

The RP2040 was selected because it provides:
- native USB support
- sufficient GPIO for the keyboard matrix and peripherals
- ADC channels for analog controls
- broad development ecosystem
- low component cost

## Keyboard Matrix

Nine switches are arranged as a 3×3 matrix, requiring six GPIOs rather
than nine.

Each switch includes a diode to prevent ghosting during simultaneous
keypresses.

## RGB Backlighting

Nine WS2812-compatible addressable LEDs provide independent per-key
lighting while requiring only one MCU GPIO.

A 74AHCT1G125 level translator converts the RP2040's 3.3 V data signal
to the 5 V logic domain used by the LEDs.

## Debugging

The board exposes the RP2040 SWD interface using the Raspberry Pi
3-pin debug connector standard:

- SWCLK
- GND
- SWDIO

This allows debugging with a Raspberry Pi Debug Probe or Pico configured
as a debug probe.

## USB

USB-C is used for power and USB 2.0 Full-Speed communication.

The design includes:
- 5.1 kΩ CC pull-down resistors
- ESD protection
- 27 Ω USB series termination resistors