---
title: "Ubuntu 9.04 bricked my Acer Aspire One A150?"
date: 2009-10-02
forum: Hardware
---

### Post by joe213 on 2009-10-02
Hi,

i just installed Ubuntu 9.04 on my Acer Aspire One A150. First everything went ok, first restart no problem, i set my wlan password etc. and then restarted my ubuntu by shortcut ctrl-alt-del.

But then my netbook is not booting up any more - after powering on just the power led is on, the fan roars, but nothing happens. No blinking harddisk or keyboard led, no display output.

I just tried some different things, accu-pack in and out, with and without ac-adapter, plugging of the device from power souce for some minutes, but nothing helped.

Does anyone have an idea, what i could try to start it up?

Thanks,

NG
Joe

---

### Post by God of the Meeps on 2009-10-02
Have you tried just holding down the power button?

And did you install Ubuntu from a Live CD?

---

### Post by greenlake-walker on 2009-10-02
Jaunty and Mint 7 had a similar problem on an Acer Aspire X1300-U1801A.

Pressing ALT-F2 locked the computer.

I installed 810 Intrepid and beta 910 Karmic,
and there are no keyboard problems, 
in particlar, ALT-F2 works as expected.

Sidux gives the message, 
computer id's as Acer Aspire One, but can find no Acer Aspire One hardware.

Karmic gives the message,
Karmic doesn't recognize this bios.

---

### Post by joe213 on 2009-10-03
> **God of the Meeps said:**
> Have you tried just holding down the power button?

And did you install Ubuntu from a Live CD?

I installed it from Live-CD, which was on a usb stick. After installation i rebootet 1 time successfully and configured my wlan. After that i restarted it with ctrl-alt-del, ubuntu shutted down but than there is this black screen of death (power led is still on). Powering off and on just has the same effect - just this black screen and fan roaring, but no other activity, no beeping, nothing.

Holding down the power button just powers off the device after about 5 seconds. When i restart, the fan roars, but the screen does not display anything, just black. Also the led for harddisk activity ist not flickering, so i think the netbooks cannot startup bios anymore or so.

Never had any problems with ubuntu on other devices. Very strange problem ... maybe bios defect or overwritten by ubuntu problem?

---

### Post by joe213 on 2009-10-03
Seems to be a bios bug: (german blog)
[http://www.itgrl.de/2008/12/28/mund-zu-mund/](http://www.itgrl.de/2008/12/28/mund-zu-mund/)

After booting from USB devices (like after installation from LIVE-CD from USB-Stick), Acer Aspire One A110 and A150 often hangs and needs a bios update, to remove black screen of death.


Download actual bios from Acer website. Unzip it, copy the content of the dos-folder to the root of a FAT16 or FAT32 formatted usb-stick. Now you have a flashit.exe and a ****.fd. It's good to use a usb-stick with activity-le, to see, if somethings happens.
Make a copy of flashit.exe and name it flash.exe - one of them is called by the pre-bios-flasher later. Then you have to rename ****.fd to ZG5IA32.fd.
Power of the netbook, make shure you inserted battery pack and ac-plug - both is needed. Insert usb-stick in netbook.
Then hold FN and ESC-key simultaniously and power on - the power-button will now blink to show you, that the pre-bios-flasher is active. Release FN-ESC and press the power button again - now it will check your usb-stick and start updating the netbook. If that happens, the usb-stick will blink for some time. Don't do anything with your netbook at this time - wait for reboot, now bios should boot regulary.
If your netbook does not reboot after, let's say 5 minutes and usb-stick is not blinking any more, something went wrong with the bios update.

---

### Post by Ashler on 2009-10-10
> **joe213 said:**
> Seems to be a bios bug: (german blog)
[http://www.itgrl.de/2008/12/28/mund-zu-mund/](http://www.itgrl.de/2008/12/28/mund-zu-mund/)

After booting from USB devices (like after installation from LIVE-CD from USB-Stick), Acer Aspire One A110 and A150 often hangs and needs a bios update, to remove black screen of death.


Download actual bios from Acer website. Unzip it, copy the content of the dos-folder to the root of a FAT16 or FAT32 formatted usb-stick. Now you have a flashit.exe and a ****.fd. It's good to use a usb-stick with activity-le, to see, if somethings happens.
Make a copy of flashit.exe and name it flash.exe - one of them is called by the pre-bios-flasher later. Then you have to rename ****.fd to ZG5IA32.fd.
Power of the netbook, make shure you inserted battery pack and ac-plug - both is needed. Insert usb-stick in netbook.
Then hold FN and ESC-key simultaniously and power on - the power-button will now blink to show you, that the pre-bios-flasher is active. Release FN-ESC and press the power button again - now it will check your usb-stick and start updating the netbook. If that happens, the usb-stick will blink for some time. Don't do anything with your netbook at this time - wait for reboot, now bios should boot regulary.
If your netbook does not reboot after, let's say 5 minutes and usb-stick is not blinking any more, something went wrong with the bios update.


Any Idea what to do once you have had a Failed attempt and now Nothing happens? I went through the steps but never got any activity on the USB LED. The Only thing that is happening is the Power button flashes and the fan is on. :confused:

---

### Post by joe213 on 2009-10-12
When the power button flashes you have to press it, then it should read out your usb stick. Keep in mind that you need boot inserted battery and ac-power to make a bios update.

---

### Post by jalirious on 2010-03-20
F*ck Fu*k, I managed to flash boot my AAO fine a few times - but now no response. Kept trying to flash boot & upgrade the bios and I think I fried it. *******!

---

### Post by Xyphoid on 2010-03-24
Sorry to hear you bricked your AAO.

Bill Hicks rules!! :)

---

### Post by Espionage724 on 2010-03-24
That must suck dude...

Well i have one thing you might wanna attempt, it basically involves a Crysis Recovery Disk.

I made one by booting into ubuntu, doing some stuff to make a emulated floppy disc with bootable files, burtnt it to a cd, and then profit.

Heres the disc I made (although I would HIGHLY recommend not using it unless your sure it works on your hardware. My disc works on TM 2480, 3307, and 5750 for sure though.

---

