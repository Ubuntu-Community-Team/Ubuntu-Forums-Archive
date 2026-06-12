---
title: "MSI bluetooth dongle killed by plugging in USB stick?"
date: 2008-12-07
forum: Hardware
---

### Post by hansie99 on 2008-12-07
Hi,

This afternoon I inserted my usb stick in one of the two front usb ports of my computer. The other port is used by a MSI micro bluetooth dongle, which worked fine before under Ubuntu 8.10. 

When I plugged the usb stick in the usb port the led of the MSI went dead. The bluetooth icon in the notification area also disappeared. 

The usb stick works fine, but I am very annoyed that my bluetooth dongle died just by plugging a usb stick in. How can this be? 

lsusb doesn't report the bluetooth dongle any more. Tried it on other usb ports, but didn't matter. Rebooting (cold restart) didn't do the trick either. All usb ports are working fine, I checked that. 

I guess that it has something to do with the fact that both usb ports use the same bus. So the stick requested more current then the bluetooth dongle could handle? Any ideas? Am I correct? 

This means that you have to be careful which devices you plug in on the same bus? No safety measures for usb devices then? 

btw. this is the second usb-device that died. Two years ago somehow my webcam was killed in a similar way. On a different computer, using Ubuntu. 

More people encountered cases like this? Can't find anything on internet about it.

---

### Post by cariboo on 2008-12-07
I would suggset that you bluetooth device was defective. All electronic devices will fail over time, yours just failed sooner then others. I've been using MSI bluetooth dongles for several years, and the only problem I had is that my dog liked the dongle more then I did. :)

Jim

---

### Post by hansie99 on 2008-12-07
Thanks for your quick reply Jim! 

I am however quite certain that it has something to do with both usb ports being on the same bus. It is not just a defective device. The MSI bluetooth dongle was brand new. Also, it stopped working at exact the same moment I plugged in the usb stick. The led died and the bt icon disappeared on exactly thát moment. 

So the stick for example requested 1 watt and the MSI dongle is on the same usb bus, so if I am correct it must use the same 1 watt (or whatever it is). Then it seems the dongle can't handle 1 watt. That is what I think is the case, but I hope someone with more technical skills then I will give me an answer if I am correct or not. 

Maybe I am totally wrong here, but I think that if I buy the same bluetooth dongle and do this again, that dongle would also die. Since these dongles are cheap, I almost want to try that :)

---

