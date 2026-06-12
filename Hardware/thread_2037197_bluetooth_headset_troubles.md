---
title: "bluetooth headset troubles"
date: 2012-08-03
forum: Hardware
---

### Post by fly2k on 2012-08-03
Hello!

Sorry for my english, I hope you will understand me correctly :)

I have a bluetooth headset nokia bt 55. Detecting and pairing done ok but the device do not work fine.

First, in A2DP mode the sound is almost ok, but with some pauses and delays. In the logs tons of messages like:
```

Aug  4 04:28:23 fly-ws pulseaudio[2413]: [bluetooth] module-bluetooth-device.c: Skipping 17175 us (= 3028 bytes) in audio stream

```

But it is not the main problem cos I need use the device exactly as headset while A2DP do not provide any input(microphone).

So, switching to HSP/HFP mode. There is no any "readable" sound at all. Only noises and crackles. Even 'test speakers' sounds like 'cat /dev/random > /dev/dsp'. In the logs tons of messages like:
```

Aug  4 04:35:18 fly-ws kernel: [ 3000.223665] Bluetooth: hci0 SCO packet for unknown connection handle 0

```

My system is latest Ubuntu 12.04 with gnome 3. The device connected via standard gnome interface, but I also tried the blueman manager, but its not help so I deleted it. PC is pretty modern, bluetooth adapter integrated at the motherboard(asus p8z68-v pro)

I installed bluez package, but not sure it is good idea cos at the official site I did read the bluez code must be in the kernel already. I did read some instructions about SCO module, but it seems to be deprecated cos I can't found any modules like btsco or so.. bluez-btsco is installed.

Help me plz! Thnx.

---

