---
title: "Aspire 6930 Bluetooth and Mic Problems"
date: 2009-03-03
forum: Hardware
---

### Post by MobileDev on 2009-03-03
Hello everyone. I just got a new Acer Aspire 6930 and Ubuntu 8.10 works great, except for the following:

My integrated microphone refuses to work.

When I tap the Bluetooth button, the screen brightness increases and no Bluetooth. I noticed that with wireless adapter, the LED button must be tapped (turned on) in order for the laptop to connect to a wireless network. I assume that the same thing goes for the Bluetooth feature.

Using the Fn key works for everything except turning the brightness up. When I press Fn + Right Arrow, the brightness goes up, but "±" symbols keep popping up if I'm working with any app you type into (including this text field in Firefox). 

I have tried to find solutions to these problems, but google and several forum searches only yielded information about other Acer laptops and other versions of Ubuntu. Of course I still tried them, but the didn't work. 

Another thing that bothers me is that Acer doesn't seem to support Linux at all. 

Any help on these problems would be greatly appreciated (and should be archived for other Aspire 6930 owners).

---

### Post by K. Hendrik on 2009-03-03
Hi,
I've got a Acer Aspire 6935 i can't help you with the mic but i have the same Problem so please inform me if you solve this (via pm).

I also had a Problem with the keyboard i had to assign the keys... I made this [HowTo]("http://ubuntuforums.org/showthread.php?t=1084943") because your keyboard is different from mine you will need to write your own fdi-file but my file should show you the direction.
This [page]("https://help.ubuntu.com/community/MultimediaKeys") helped me alot.

---

### Post by MobileDev on 2009-03-04
Thanks for the links, but they didn't help me. Also, it turns out that, even though there is a bluetooth light, there is no bluetooth device installed in the laptop. I have to buy one seperately :) Anyway, I am still having mic issues. An external mic works fine, once I mess around with the settings, but the integrated mic won't work from Linux. Also, I am still getting those strange symbols popping up when I adjust my screen brightness.

---

### Post by K. Hendrik on 2009-03-04
hi,
the bluetooth button increasing the brightness means that the key is wrong assigned in the fdi-file the brightness button returning the "±" could be the same problem
. the blue icon normally only appears when a bluetooth device is recognized are u really sure you don't have bluetooth build in? please try
```
lsusb
```
to make sure if there's a bluetooth device it sould be listet (please post the result here)

---

### Post by MobileDev on 2009-03-13
Sorry I haven't been back here in a while. It's the End of the Quarter crunch at college right now, so I haven't been available. Anyway, here is the output of lsusb:
```
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 064e:a103 Suyin Corp. 
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Is the code tags the right way to enter this in the forum? Don't remember using them before. The Logitech is my mouse, I hate the touch pad. I also find it strange that my hard drive would be connected through a USB interface instead of SCSI, but this is the 32-bit version of Ubuntu and the laptop has a 64-bit processor. Two new questions: What is the Linux Foundation stuff, and what is Suyin Corp?

---

### Post by K. Hendrik on 2009-03-14
Ok, it seems  like you really don't have Bluetooth build in. The Suyin Corp. thing is your cardreader (just google 064e:a103). And using the code-tag for such results should be fine.

---

### Post by jijibabawu on 2009-03-17
Same Mic problem here. I just got a 6935G. Everything works fine except the integrated mic. It seems this mic problem has happened to some other Acer models as well. Tried the suggestion by Turon ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/147298](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/147298)), but still couldn't fix the problem.

---

### Post by MobileDev on 2009-03-18
I'm not a rocket scientist, but I think someone needs to come up with a special kernel module that properly handles the d##n USB mic on these f###in Acer laptops! :(  What's the point of having an working built-in camera and not a working built-in mic?! I have Vista on the other half of the drive and, surprise surprise, it doesn't have any trouble with the mic. What's really interesting is that the camera actually gives better quality under Linux. Is there a way I use the windows drivers under Linux in order to get the mic working?

---

### Post by executorvs on 2009-04-11
I don't think the mic is usb as it's not shown when I run lsusb in terminal.
however many usb audio devices are prevented from loading by default in /etc/modprobe.d/alsa-base.conf I found this in the french forums talking about the C-media card on my girlfriends desktop.

---

### Post by acridfusion on 2009-05-02
> **K. Hendrik said:**
> Hi,
I've got a Acer Aspire 6935 i can't help you with the mic but i have the same Problem so please inform me if you solve this (via pm).


Or you can post it here since i've got the identical issues/machine/os

---

### Post by speedtime on 2009-09-26
I have the same Mic Problem on my Aspire 6930 laptop
I tried [this topic]("https://help.ubuntu.com/community/HdaIntelSoundHowto") but it didn't work

any one have an idea plz!!!:confused:

---

### Post by Harix on 2010-07-11
I also tried to find solution, but my internal mic still does not work.
Acer 6930 model:zk2
9.10
Any new devellopments?
Thanks

---

