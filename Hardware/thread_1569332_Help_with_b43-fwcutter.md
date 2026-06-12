---
title: "Help with b43-fwcutter"
date: 2010-09-06
forum: Hardware
---

### Post by JustinGordon on 2010-09-06
Trying to get wireless working on Acer Aspire 5610Z (girlfriend's old laptop, where I removed Windows Vista and told her Ubuntu would be great).

Card: BCM 4318
Ubuntu: Latest Lucid updates, upgraded from Karmic.

I tried following the instructions on: [http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian)
to install b43-fwcutter, but it seems to fail. No error message on the "no networking" install.

I think the problem is that in trying everything on the forums, I've messed up something.

I can start networking (cabled) by running
$ sudo modprobe b44  

I can then use the package manager to install (or re-install) the b43-fwcutter package.

But then I can't activate the driver, as I get a message that a different driver is in use (via the System-->Administration-->Hardware Drivers screen).

I try to activate the proprietary driver, and I get a message that this failed, and the only message in jockey.log is 
unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0

Do I need to disable b44 before this works? Any magic sequence of steps? I'm guessing that it's the problem of the "different driver" causing the conflict.

Is there any way that I can easily refresh my network settings to the defaults so that I can follow the instructions on b43-fwcutter?

Anything I can post on the forum to help diagnose this?

p.s., If I can't get this working soon, I'm throwing this laptop out my window and telling my girlfriend to buy a new Macbook!

Thanks in advance,

Justin

---

### Post by coffeecat on 2010-09-06
> **JustinGordon said:**
> 
I can start networking (cabled) by running
$ sudo modprobe b44  

... which sounds as though you have a Broadcom ethernet device as well. I have no direct experience of Broadcom, but I happened to come across a post by a member pointing out an issue when you use the proprietary driver for Broadcom wireless, and you also have a broadcom wired device that uses the b44 driver. Here's the post:

[http://ubuntuforums.org/showpost.php?p=8371562&postcount=3](http://ubuntuforums.org/showpost.php?p=8371562&postcount=3)

I hope that provides a solution for you.

Also, a bit late now, but a useful community documentation page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

**Edit:** a cheaper option than buying a new Macbook, (:wink:) would be to buy a replacement mini wireless card for the laptop. If you do, check whether that machine takes a mini-PCI or mini-PCIe. An Intel chipset would be what I would choose - most work out of the box - but search the forums first. I came across a thread today linking to a bug report concerning one of the newer Intel chipsets.

---

### Post by JustinGordon on 2010-09-06
> **coffeecat said:**
> ... which sounds as though you have a Broadcom ethernet device as well. I have no direct experience of Broadcom, but I happened to come across a post by a member pointing out an issue when you use the proprietary driver for Broadcom wireless, and you also have a broadcom wired device that uses the b44 driver. Here's the post:
[http://ubuntuforums.org/showpost.php?p=8371562&postcount=3](http://ubuntuforums.org/showpost.php?p=8371562&postcount=3)
I hope that provides a solution for you.
Also, a bit late now, but a useful community documentation page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Thanks, but my model 4318 does not seem officially supported, the BCM4318
"STA takes the BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225".

I think my problem is somehow related to the b44 driver not letting the b43 driver get installed.

Thanks in advance for any advice.

Justin

---

### Post by JustinGordon on 2010-09-06
After rebooting, if I run 
[B]sudo modprobe b43
[/B] 
then wireless starts up and seems to work...

**Now, how do I have this happen automatically if rebooted?**

Note, it seems unnecessary to load the proprietary driver. 

Thanks in advance.

Justin

---

### Post by coffeecat on 2010-09-07
> **JustinGordon said:**
> **Now, how do I have this happen automatically if rebooted?**

It used to be easy. Or, rather, it probably still is but I'm not sure how now that Ubuntu is transitioning from init to upstart and, frankly, I'm vague about the details.

A link which may or may not be useful:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

You need to put a custom script somewhere. Your script would be a simple "modprobe b43" with no sudo because during the boot sequence root has control. And it would need to be executed at the correct time, after the system has autodetected the Broadcom ethernet device and loaded b44. Or something. To be honest, I'm not sure because my first link seemed to be describing the clash between b43 and b44 that you're experiencing but you say that you have to modprobe b44 as well.

All very confusing, or perhaps you could include the whole modprobe sequence from that link and then add modprobe b43 to the end. Perhaps, then, both devices will work.

Or perhaps there is a much more elegant solution. When I get a chance I'll do a bit more searching and get back to you. Someone must have solved this. Broadcom wireless is always a hassle anyway because of the licensing issues around the wireless driver and firmware, but the combination of Broadcom wireless and ethernet must be fairly common.

---

### Post by coffeecat on 2010-09-07
> **coffeecat said:**
> Or perhaps there is a much more elegant solution. When I get a chance I'll do a bit more searching and get back to you.

Not as elegant as I'd hoped, but it least it identifies where the script might go - /etc/rc.local. A word of caution, however. The link refers to version 8.10 and the bootup sequence is being radically changed, but there is still an /etc/rc.local in Lucid. Worth a try. Link:

[http://tenthblog.com/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)

Whether or not it would be a good idea  to modprobe 43 as well after 44, I don't know.

---

### Post by aspiredfang on 2010-09-07
Hi there,

i had a very similar problem trying to get the Broadcom wireless driver working no my laptop. Neither B43-fwcutter or the proprietary drivers would work. In the end, I got so fed up I took the last option and compiled the set of drivers myself; since that day things have been working great.

I can't say exactly what was going wrong with these drivers but, if you are still having big issues and want to try something other than tearing your hair out, read on :) 

- First, I removed all traces of the proprietary and fwcutter. For me, this was quite simply going in to synaptic package manager and then a cleanup using ubuntu-tweak

- You can get the source code for compiling: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

- Extract the files to a directory of your choosing. For all self compiled programs, I use ~/programs/***

- Open up a terminal in the directory where you extracted the drivers to

- You will then need to compile the drivers as with any other program
"sudo ./configure"

- Once all the dependencies have been met
   "sudo make"

- Then the actual install
   "sudo make install"

After rebooting your computer, the driver will be active and for me, EVERYTHING wireless worked as you would expect it to. I hope this helps:KS

---

### Post by JustinGordon on 2010-09-09
So I thought that running 
> sudo modprobe b43 
would start up networking upon reboot! But no more. Now I can't get it (b43) to start again...Sigh. This is maddening!

So, any other options than recompile? Anybody else try that technique and get good results?

Thanks in advance,

Justin

---

### Post by Ayuthia on 2010-09-09
You might want to check and see what is currently loaded:
```

lsmod|grep -e b4 -e wl -e ndis -e ssb

```
Like you said, the Broadcom STA driver is not compatible with the 4318 card.  The command above is going to check and see if the wl (Broadcom STA driver), NDISwrapper, and the b43/b44/ssb drivers are loaded.

You can also try the following:
```
sudo modprobe -r b43 
sudo modprobe -r b44 
sudo modprobe -r ssb 
sudo modprobe -r wl 
sudo modprobe -r ndiswrapper
sudo modprobe b44
sudo modprobe b43
sudo iwlist scan

```
Some of the modprobe -r commands can come back with some error messages, but that is ok because some of those drivers might not be currently loaded.  They are just commands to unload the possible conflicting drivers.

If those commands do not get the wireless card started up again, check:
```

dmesg

```
and see if anything shows up at the bottom of the result to see if it says anything about the wireless driver.

---

