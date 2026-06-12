---
title: "Laptop random shutdown (ACPI problem?)"
date: 2009-12-04
forum: Hardware
---

### Post by hejfelix on 2009-12-04
Hello guys,

I have a nice laptop which runs smoothly with ubuntu, however it shuts down randomly from time to time. I have a strong feeling that it is related to what other people call the "ACPI" bug. Misreading the temperature or whatever.

In ubuntu 9.04 I "fixed" it by disabling it with acpi=off in grub, this solved the problem but introduced the "laptop wont power off on its own" after pressing the shutdown software button. 
Now in 9.10 its on again, and I assume I will get the same problem when turning it off again. Is there a way to simply crank up the trip-point for soft-reset or disable that feature while still enabling the remaining features of ACPI?

I might retry the acpi=off option, but hopefully there are other options.

Thanks to anyone who helps me :)

---

### Post by Shawn K on 2010-02-09
I can't believe that no one had a response to this.  I'm having the same random shutdown problem myself - I'd like to fix it, too.

---

### Post by jdash1 on 2010-02-10
> **Shawn K said:**
> I can't believe that no one had a response to this.  I'm having the same random shutdown problem myself - I'd like to fix it, too.

we are on the same case bro, i couldn't leave my laptop running for hours.. everytime i comeback it automatically shuts down, i have set the power management of this but no luck.  :(


do you guys know where i could find log of time/reason when/why the computer crashes down ?

any help would be appreciated.

thanks

---

### Post by hejfelix on 2010-02-10
...
 Originally Posted by bunta123  View Post
On the terminal:

sudo gedit /etc/init.d/halt

Add the following line to the halt script:

rmmod snd-hda-intel

Proceed to a successful shutdown. 
...


This stuff worked for me, please spread it if it works for you too ;) The original post was here: [http://ubuntuforums.org/showthread.php?t=1306789&page=3]("http://ubuntuforums.org/showthread.php?t=1306789&page=3")

---

### Post by booteslebouvier on 2010-02-24
I had the same problem with Ubuntu running on a Acer Aspire 5720 dualcore T2330.

The problem was the main fan was not put on by a raise of temperature because the ACPI CPU temperature sensor was not considered. I think the module getting this done is "i8k". It did not get loaded on boot because apparently its compatible hardware list does not contain mine (and many others, as it seems). The most convincing source for me was:

[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)
under Sensors and fan control

so the solution is to use force=1 parameter to load i8k upon boot, i.e. add "i8k force=1" in  /etc/modules (or even better, to define "i8k force = 1" as the new "i8k" command).

I hope not to have frustrated some using sloppy beginners terminology...

---

