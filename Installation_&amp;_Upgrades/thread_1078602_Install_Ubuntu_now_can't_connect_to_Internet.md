---
title: "Install Ubuntu now can't connect to Internet"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by waheedrafiq on 2009-02-23
Hi guys i am totally new to this OS

I am glad that I move away from Windows , Linux is a total new ball game. :) on this account my first hardware issue with Linux

When I install Unbuntu first time , I was able to access the internet via my LAN and i notice at the coner of the OS i needed to perform 266 updates so I did of course it downloaded all the updates from the internet and then install them after which my internet does not work

also how can i enable my buildin wireless connection ?

like wise my buildin cam

---

### Post by waheedrafiq on 2009-02-24
Hello anyone here , can anyone help me please !

---

### Post by lotu on 2009-02-24
You're going to need to give us some more information.  Like what version of ubuntu are you using and what is the make and model of your computer.  Also give as much detail as you can about the hardware your computer is running on.  If you can open a terminal window and run the command lspci then copy the output here that will tell us alot about your hardware.:p

---

### Post by waheedrafiq on 2009-03-14
I there thanks for getting back to me so soon. 

I am running ubuntu 8.10  on the top of my screen on the tool bar my network has got a explanation mark, when I double click on this it states that its connecting then it tells me that it has disconnected.

hence why I can't access the internet. can you please urgently help me as I need to be able to access the net in order to move on with my newly found life on Linux

---

### Post by ugm6hr on 2009-03-14
We can't help without details.

```
lshw -class network >>lshw.txt
lspci >>lspci.txt
ifconfig >>ifconfig.txt
cp /boot/grub/menu.lst menu.txt
```

These commands will create text files in your Home directory.  Copy and paste the contents back here (within [CODE] markers)

I suspect that a kernel update has a broken driver for your ethernet card.

You could try using an older kernel.  Press Escape to enter Grub menu, and select the lowest Ubuntu entry.

---

### Post by waheedrafiq on 2009-03-14
here is my output 

waheed@waheed-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff) 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22) 


you please help me , i am not going to go back to XP or Vista

---

### Post by ugm6hr on 2009-03-14
Read this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916)

You need to revert to the 2.6.27-7 kernel, as I thought.

For wifi: 
[http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141)

---

### Post by waheedrafiq on 2009-03-14
many thanks for  your prompt reply , but how do I go to the lowest Kernel , 

do I need to turn my PC off and then on upon that press Escape 

to scare to try again thing

---

### Post by waheedrafiq on 2009-03-14
Okay mate I just did the oppsite i just try it and said to myself what the hell.

That was pretty easy , now how can I fix the kernel issue ?

---

### Post by ugm6hr on 2009-03-14
Backup original menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst.bkp
```

Edit it:
```
gksudo gedit /boot/grub/menu.lst
```

Near bottom, find lines relating to new kernel, and place a **#** at the start of them (all of the relevant lines: **title, root, kernel, initrd** - but only those relating to 2.6.27-11 kernels)

---

### Post by waheedrafiq on 2009-03-15
Hi ugm6hr , first of all let me give you a big thanks for helping me out

not only did you fix the most import thing in the world thats the internet but you also fix the boot up issue too so it always boots up at the correct kernel which means I get internet.


many thanks for  your clear and simple instructions .

---

### Post by ugm6hr on 2009-03-15
No problem.

Hopefully, this will be fixed with the next kernel upgrade.

If not, the same might occur again - just do the same again (use 2.6.27-7).

I would suggest you get a launchpad account and subscribe to the bug report (and confirm you are affected): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916)

---

### Post by ugm6hr on 2009-03-15
PS: You might like to try the 2.6.27-9 kernel:
[linux-image-2.6.27-9-generic]("apt:linux-image-2.6.27-9-generic")

It is newer than the -7; I am uncertain whether it will work or not, but there are no bug reports related to it.  If it doesn't work, just boot back into -7 and # -9 entries again in menu.lst.

Also manual download from: [http://packages.ubuntu.com/intrepid-updates/i386/linux-image-2.6.27-9-generic/download](http://packages.ubuntu.com/intrepid-updates/i386/linux-image-2.6.27-9-generic/download)

---

### Post by .:Justus:. on 2009-03-15
> **ugm6hr said:**
> PS: You might like to try the 2.6.27-9 kernel:
[linux-image-2.6.27-9-generic]("apt:linux-image-2.6.27-9-generic")


I would like to thank you also ugm6hr, i made a thread about the same problem  a couple days ago but didn´t really get any helpful replies =[
It sounds like you have the solution for the problem so i´ll be trying it now.
Wifi and eth0 is working fine right now, i have 217 possible updates,
i should update now, restart, boot into the old -7 kernel, then edit the menu.lst? If this works I will be so thankful =]

---

### Post by ugm6hr on 2009-03-15
@Justus:
Install the -9 kernel (linked above) straight away with the update.

Then edit menu.lst to # the -11 entries.

**Then** reboot.

---

### Post by .:Justus:. on 2009-03-15
> **ugm6hr said:**
> @Justus:
Install the -9 kernel (linked above) straight away with the update.

Then edit menu.lst to # the -11 entries.

**Then** reboot.

oh ok gotcha
thanks a lot !

---

### Post by .:Justus:. on 2009-03-15
> **ugm6hr said:**
> @Justus:
Install the -9 kernel (linked above) straight away with the update.

Then edit menu.lst to # the -11 entries.

**Then** reboot.

hm it says that its updating to -13? maybe the bug was fixed in 13? should i still install -9?

---

### Post by ugm6hr on 2009-03-15
> **.:Justus:. said:**
> hm it says that its updating to -13? maybe the bug was fixed in 13? should i still install -9?

Really?

Worth giving -13 a go.  I can't find it on [http://packages.ubuntu.com/intrepid-updates/linux-image-generic](http://packages.ubuntu.com/intrepid-updates/linux-image-generic)

---

### Post by .:Justus:. on 2009-03-15
Sorry for triple posting, but this may be important for Threadstarter
After updating, i installed the -9 kernel
Experienced the same problems as earlier with -11,-13
Everything works fine though with -7 kernel!

to other people experiencing this problem:
**-7 kernel is your best bet, -9 does not fix this bug**
Thanks for all your help ugm6hr, finally fixed my problem ^^

> **ugm6hr said:**
> Really?

Worth giving -13 a go.  I can't find it on [http://packages.ubuntu.com/intrepid-updates/linux-image-generic](http://packages.ubuntu.com/intrepid-updates/linux-image-generic)
Yea, must be new dunno, it automatically installed with the updates.
New or not, it didn´t fix the bug, hope the new one does though...

---

### Post by ugm6hr on 2009-03-15
> **.:Justus:. said:**
> Yea, must be new dunno, it automatically installed with the updates.
New or not, it didn´t fix the bug, hope the new one does though...

Please update or re-report the bug for -13 kernel on launchpad if that is the case.

---

### Post by .:Justus:. on 2009-03-15
> **ugm6hr said:**
> Please update or re-report the bug for -13 kernel on launchpad if that is the case.

will do.

---

