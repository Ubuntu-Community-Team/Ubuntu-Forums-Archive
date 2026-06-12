---
title: "multiple network cards"
date: 2010-10-02
forum: Hardware
---

### Post by Perica911 on 2010-10-02
Greetings,

I have toshiba portege and I want to use an external network card rtl8187 to pick up my wifi far from my office. In terminal I can check if there is an usb connection with >lsusb and system finds the card, ok. Than I check for network devices with >ifconfig I find both, my internal wifi device and my external one. But in the top right corner where I manage connections via desktop interface, system says I have both cards, but only finds networks for the first (internal one) but not for the other one. If I shut down wlan0(internal wifi card) with ifconfig wlan0 down, the desktop interface still sees all the networks and internet still works fine. I also have a mecanical switch on the laptop for wifi and if I turn it off desktop interface says both cards are disabled, but I can scan for networks in terminal with my external one. This is a bit strange to me since I usualy diagnose problems and see a logic in it, but I can not in this one. If anyone could help me, I would be very gratefull. If someone knows how to shut down internal wifi for certin (this >ifconfig wlan0 down is so so...) please tell me how:)

thank you for your help

Peter

---

### Post by juliobahar on 2010-11-12
> **Perica911 said:**
> Greetings,
If anyone could help me, I would be very gratefull. If someone knows how to shut down internal wifi for certin (this >ifconfig wlan0 down is so so...) please tell me how:)

thank you for your help

Peter

You can use two separate network managers - at least this is what I'm doing at the moment. One is the ubuntu native "networkManager" and "wicd" which can be downloaded from software centre. wicd is a little bulky, but more configurable.

To stop your Wifi card you can type this in command
```

# iwconfig <interface> txpower off

```

to turn it back on replace (off) with (on) or (auto)

---

