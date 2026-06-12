---
title: "NC6400 Blutetooth problem"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by rsd.za on 2007-06-05
I'm a noob. I've been running ubuntu for 2 days and have zero previous experience with linux.

I've read on several sites that bluetooth works out of the box on Feisty with the Compaq NC6400 notebook. It doesn't appear to work on mine. I type hcitools dev and there are no devices listed.

I've checked the BIOS and the bluetooth device is enabled. I was running XP previously and I had the disabled bluetooth with the radio on/off button, which cycles through disabling/enabling wifi and bluetooth. Could this be a problem? Under ubuntu the button just turns wifi on / off.

I've looked in the device manager (thing) and searched for blue - nothing appeared.

I'm at a bit of a loss, since I know dangerously little about linux. Any advice / pointers / links will be greatly appreciated!

Thanks

Ross

---

### Post by IntuitiveNipple on 2007-06-05
It sounds to me as if you've put your finger on the problem. Under Windows there is a custom software switch to selectively enable/disable the bluetooth radio. The switch will be Compaq-specific.

What you need to find is a similar controller interface in Linux. Unfortunately I don't have any help for Compaq.

What I do know from using Sony Vaios is that the bluetooth radio can be enabled/disabled using a simple command from a terminal session or shell script to the sonypi controller. Maybe there is a similar controller utility for Compaq?

---

### Post by rsd.za on 2007-06-05
Interesting.

I might just install XP on a usb drive, boot up, press the button to turn the wifi on, boot in ubuntu and see what happens :)

bit of a mission though.

---

### Post by omarino on 2007-06-06
same problem on my nx7400. Did the solution work?

---

### Post by finni on 2007-06-08
Bluetooth works fine on my NX7400.

---

### Post by omarino on 2007-06-08
Man, i've read thousents of posts abount BT working out of the box on nx7400, but mine didn't.
Based on the posts of rsd and IntuitiveNipple i was able to pinpoint the problem. I had winXP instaled earlier and i disabled the BT module. Than I formated the disk and istaled UBUNTU and the BT was dead (apparently turned of by Win ACPI). I found no way to turn it back on in UBUNTU, so I solved the problem with a rather radical solution.
- i've taken out my laptop HDD and instaled XP on external USB HDD (see [http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)), enabled BT in XP boot and rebooted to ubuntu, viola, now BT works.

Seems to me, that would be the solution to rsd.da's problem. Just turning on the hardware switch woun't do it. You have to install drivers and HP Wireless manager to be able to switch BT back on.

---

### Post by rsd.za on 2007-06-08
Hey guys, thanks a lot for your input.

I haven't had a chance to do it myself, and getting bluetooth working isn't too urgent for me. I'm really glad to hear I can get it sorted when I have time though :)

---

