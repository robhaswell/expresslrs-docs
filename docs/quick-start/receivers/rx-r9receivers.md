---
template: main.html
---

![Setup-Banner](https://raw.githubusercontent.com/ExpressLRS/ExpressLRS-hardware/master/img/quick-start.png)

### FrSky RXes  
![FC Wiring](../../assets/images/FC-Wiring.jpg)

!!! attention ""
    Note: This will be the same wiring you'll use for flying and the subsequent firmware updates (via Passthrough). Forget the factory wiring guide!

#### Passthrough Flashing (works with Betaflight, iNav)

Valid Targets:

- `Frsky_RX_R9MM_R9MINI_via_BetaflightPassthrough`
- `Frsky_RX_R9MX_via_BetaflightPassthrough`
- `Frsky_RX_R9SLIM_via_BetaflightPassthrough`
- `Frsky_RX_R9SLIMPLUS_via_BetaflightPassthrough`
- `Frsky_RX_R9SLIMPLUS_OTA_via_BetaflightPassthrough`

Device Category: `Frsky R9`

Device:

- `Frsky RX R9MM R9MINI`
- `Frsky RX R9MX`
- `Frsky RX R9SLIM`
- `Frsky RX R9SLIMPLUS`
- `Frsky RX R9SLIMPLUS OTA`

![via Passthrough](../../assets/images/Method_RX_Passthrough-stm.png)

Make sure the correct [Bootloader](rx-bootloader.md) has been flashed to the receiver prior to wiring it up to your flight controller. Using the wiring guide above, find a free, uninverted UART in your FC. You can use your FC's wiring guide for a Crossfire or Ghost receiver.

Once wired to your FC, connect USB. Did your receiver powered up too (with both LEDs lit)? If so, disconnect USB, hold the bind button on your receiver, and reconnect to USB. The LED should start alternating between the Green and Red LEDs. Once it's alternating, you can then let go of the Bind Button.

If your receiver didn't get powered from USB, have a lipo ready and continue with the next steps. On the ExpressLRS Configurator, with your [Firmware Options] set, click on **Build & Flash**. Like on the TX module, it will take a while on the first time. Watch out for the `Passthrough Init` stage. This stage will check your FC Configuration for the Serial RX UART (Software Inversion via "set serialrx_inverted" and Half Duplex mode via "set serialrx_halfduplex" will be checked; both should be off.)

![Build & Flash](../../assets/images/BuildFlash.png)

Once `Retry... ` lines appear, connect a LiPo if your receiver isn't powered by the USB (i.e. power up your FC and receiver). On subsequent flash, you can have the LiPo plugged in and receiver powered up from the start prior to connecting the USB.

Wait for this process to finish. It's done once the "Success" prompt is shown.

#### Flashing via STLink (only recommended as last resort)

Valid Targets:

- `Frsky_RX_R9MM_R9MINI_via_STLINK`
- `Frsky_RX_R9MX_via_STLINK`
- `Frsky_RX_R9SLIM_via_STLINK`
- `Frsky_RX_R9SLIMPLUS_via_STLINK`
- `Frsky_RX_R9SLIMPLUS_OTA_via_STLINK`

Device Category: `Frsky R9`

Device:

- `Frsky RX R9MM R9MINI`
- `Frsky RX R9MX`
- `Frsky RX R9SLIM`
- `Frsky RX R9SLIMPLUS`
- `Frsky RX R9SLIMPLUS OTA`

![via STLink](../../assets/images/Method_RX_STLink-stm.png)

This method is irreversible. It will remove the ability to reflash back to Frsky firmware. You have been warned! Make sure your STLink dongle is properly recognized by your System as such (Drivers are installed, etc.).

Disable 'Readout Protection'. To do this download the [ST-LINK Utility](https://www.st.com/en/development-tools/stsw-link004.html) and follow this quick [how to video](https://youtu.be/SEYQ1HpRmk0). Or alternatively under linux you can use [OpenOCD](../../software/open-ocd.md). 

After doing so, Disconnect from STLink Utility.

Using the correct target specific for your receiver, set your [Firmware Options] and hit **Build & Flash** on the ExpressLRS Configurator.

![Build & Flash](../../assets/images/BuildFlash.png)

Once done, wire your receiver to your Flight Controller. Passthrough flashing can now be used for updating the receiver.

Here's the pinout for the R9 Slim:

![R9 Slim](../../assets/images/R9SlimConnection.jpg)

Wire the RX (CH5) to a TX pad in the FC and the TX (CH6) to an RX pad in the FC. And connect power as normal.

[Firmware Options]: ../firmware-options.md
