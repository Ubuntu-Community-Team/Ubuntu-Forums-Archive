---
title: "ATI restricted drivers, bluetooth, only work after a Windows boot"
date: 2008-09-09
forum: Hardware
---

### Post by DinkyDogg on 2008-09-09
Hi. I'm on a new Thinkpad T400 laptop, with integrated Intel Bluetooth and an ATI Mobility Radeon 3470. I'm dual booting with Windows XP 64-bit.

Whenever I boot to Ubuntu immediately after having been in Windows, everything works great. But when I boot to Ubuntu again, without booting to Windows first, neither the ATI restricted drivers nor Bluetooth quite work. Bluetooth won't reconnect automatically to my device (a mouse). I have to manually disconnect the device and reconnect it. Also, after the initial splash screen as Ubuntu boots, I get a distorted screen of the Ubuntu desktop for a second or two before the screen goes black and I get an error saying that Ubuntu is in low-graphics mode.

It doesn't seem to matter whether the Windows boot was successful or not, or whether I have the Windows ATI drivers installed. It even works after booting to the setup screen on a Windows CD.

Anyone have an idea what the problem might be, or where I can look for a log that might shed some light on this problem? I'm willing to use the open source ATI drivers if I have to, but I do enjoy playing UT2004 under Linux and I'd prefer not to give that up, if I can avoid it.

Thanks in advance to anyone who can help.


Edit: Also, it seems that whenever I boot to Windows after an Ubuntu boot (where the ATI drivers initialized successfully), they fail in the Windows boot. I get a low resolution screen and it tells me that I don't have video drivers. Something in the ATI restricted drivers really screws up the device. Again, any advice appreciated. Do the drivers log somewhere?

---

### Post by mglukhovsky on 2008-09-16
As far as I can tell, this is because the T400 features switchable graphics, so that the laptop can alternate between integrated and discrete graphics modes to improve battery life when mobile.

In the BIOS, under Config->Display, by default the selection is Switchable, which will choose Discrete if the OS does not support switchable graphics (in the case of Ubuntu, given the poor quality  of the ATI drivers) or Switchable if it does.

However, if left at Switchable the results are poor. I got the same behavior you did. For now, I seem to have stable results (though I'm not sure quite yet as this is a new machine) if I leave the BIOS option set explicitly to be always Discrete.

Maybe in a year or two (given the slow work and shoddy condition of the ATI drivers currently) we will get solid switchable graphics in Linux. Until then...

---

### Post by DinkyDogg on 2008-09-18
Fantastic. That did the trick. Thanks very much.

However, I'm having a strange problem. Bluetooth only seems to work when I don't use the ATI restricted drivers. Does anyone know where the error messages are being logged to?

Thanks again.


Edit - Nevermind. It looks like the ATI drivers have nothing to do with it. But still, bluetooth only works some of the time. Where can I look for the error log when it does fail to start?

---

### Post by mglukhovsky on 2008-09-20
Sorry, can't help you there. Bluetooth is solid in my book.

A good tool provided in Ubuntu to read logs thrown in /var/log is the  System Log tool. You can access it by going to System->Administration->System Log in GNOME. You may be able to find more information there.

---

