![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) 

# SKY130 Spiking Neuron

CMOS realization of an Izhikevich-style spiking neuron.

This is a Tiny Tapeout analog project in one `1x2` tile.
It uses SKY130 1.8 V devices.
The circuit is fully analog.
The digital pins and clock are not used.

![Layout](img/layout-6pins.png)

## Circuit

The circuit is inspired by the `V` and `U` dynamics of the Izhikevich neuron.
These act like membrane voltage and recovery behavior.

CMOS OTAs, current mirrors, resistors, and MIM capacitors create the analog dynamics.
The large repeated layout blocks include matched transistor arrays, resistor structures, and capacitors.
An output buffer drives the spike waveform at `VOUT`.

## Analog Pins

This version uses six analog pins.
Five pins are controls.
One pin is the output.

| Pin | Name | Use |
| --- | --- | --- |
| `ua[0]` | `VCORE` | Core control node |
| `ua[1]` | `IREFB` | Reference or bias input B |
| `ua[2]` | `VOUT` | Spike output voltage |
| `ua[3]` | `IREFA` | Reference or bias input A |
| `ua[4]` | `BIASC` | Control bias C |
| `ua[5]` | `BIASD` | Control bias D |

## How To Use

Power the chip from `VDPWR = 1.8 V`.
Apply quiet analog voltages to `VCORE`, `IREFB`, `IREFA`, `BIASC`, and `BIASD`.
Observe `VOUT` with an oscilloscope or DAQ.

Changing the control pins changes the spike shape, rate, and stability.
The circuit can show spike-like relaxation oscillation.
It is an analog CMOS neuron, not a digital simulator of the equation.

## Project Info

Top module: `tt_um_izh_neuron`

Authors: Abdulkarim Alorf, Tomohisa Kawakami
