---
title: "Ubuntu 9.04 (UNR), Option 431 3G problems (EeePC 1000)"
date: 2009-04-28
forum: Hardware
---

### Post by dave_chimaera on 2009-04-28
Hi there, 

I've just performed a clean build of Jaunty (from the UNR image) on my EeePC 1000. There is only one main issue with the install but its a doozy - I cannot get my 3G USB Modem working with it. 

Its a T-Mobile (UK) 3G stick, specifically an Option ICON 431 stick. 

Under Intrepid it was fairly straightforward - basically from pharscape.org I installed first Ozerocdoff to block the ZeroCD funcionality and then compiled the HSO driver against my kernel. 

I could then use NM-applet to fire up the connection and I was away. 

Under Jaunty however, it disconnects immediately with a 'GSM Disconnected' message.

I assume certain logs may come in handy - let me know and I'll pull them for you. 

Thanks in advance for any help you can offer

---

### Post by henrikmarcus on 2009-07-12
I have exactly the same problem! A clean install of Jaunty and then applied the same fix from pharscape to block ZeroCD.
[http://peck.org.uk/networkmanager-0.7.0-and-3g-wwan-modems.html](http://peck.org.uk/networkmanager-0.7.0-and-3g-wwan-modems.html)

The usb modem is recognized but it is impossible to connect. Have tried all different combinations of set/unset username, password & pin. As this seems to have solved the issue for others with the same problem, but with a slightly different usb modem.

excerpt from the log:
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Activation (ttyHS2) starting connection 'T-Mobile' 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): device state change: 3 -> 4 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) started... 
Jul  9 02:20:22 henrik-acer NetworkManager: <debug> [1247102422.041015] nm_serial_device_open(): (ttyHS2) opening device... 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) complete. 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): powering up... 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Registered on Home network 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Associated with network: +COPS: 0,0,"T-Mobile",2 
Jul  9 02:20:22 henrik-acer NetworkManager: <WARN>  dial_done(): Dialing timed out 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): device state change: 4 -> 9 
Jul  9 02:20:22 henrik-acer NetworkManager: <debug> [1247102422.563599] nm_serial_device_close(): Closing device 'ttyHS2' 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Marking connection 'T-Mobile' invalid. 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  Activation (ttyHS2) failed. 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): device state change: 9 -> 3 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): deactivating device (reason: 0). 
Jul  9 02:20:22 henrik-acer NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul  9 02:20:22 henrik-acer NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): now unmanaged 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): device state change: 3 -> 1 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): cleaning up... 
Jul  9 02:20:22 henrik-acer NetworkManager: <info>  (ttyHS2): taking down device. 


Any help is greatly appreciated!

---

### Post by mr_jrt on 2009-07-26
I'm trying to get one of these working for the desktop I've built my granddad.

I've got to the point where you are from a stock 9.04 install by installing "udev-extras" to get modem-modeswitch, then editing "/lib/udev/rules.d/61-option-modem-modeswitch.rules to use actual vendor and product IDs rather than params, as when running "udev --debug" I noticed udev was passing blank values to the program.

This getting me to the point where everything is in place, but dialling times out every time. I've tried increasing the "senddelay" value in the connection settings, but it doesn't seem to help.

```
Jul 26 17:11:21 spitfire NetworkManager: <info>  Activation (ttyHS2) starting connection 'T-Mobile' 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): device state change: 3 -> 4 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) started... 
Jul 26 17:11:21 spitfire NetworkManager: <debug> [1248624681.336207] nm_serial_device_open(): (ttyHS2) opening device... 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) complete. 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): powering up... 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Registered on Home network 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Associated with network: +COPS: 0,0,"T-Mobile",0 
Jul 26 17:11:21 spitfire NetworkManager: <WARN>  dial_done(): Dialing timed out 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): device state change: 4 -> 9 
Jul 26 17:11:21 spitfire NetworkManager: <debug> [1248624681.698321] nm_serial_device_close(): Closing device 'ttyHS2' 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Marking connection 'T-Mobile' invalid. 
Jul 26 17:11:21 spitfire NetworkManager: <info>  Activation (ttyHS2) failed. 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): device state change: 9 -> 3 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): deactivating device (reason: 0). 
Jul 26 17:11:21 spitfire kernel: [  886.024089] usb 1-1: USB disconnect, address 11
Jul 26 17:11:21 spitfire NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 26 17:11:21 spitfire NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): now unmanaged 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): device state change: 3 -> 1 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): cleaning up... 
Jul 26 17:11:21 spitfire NetworkManager: <info>  (ttyHS2): taking down device. 

```

It's all very frustrating.

---

