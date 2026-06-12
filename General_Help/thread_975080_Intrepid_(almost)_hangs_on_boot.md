---
title: "Intrepid (almost) hangs on boot"
date: 2008-11-08
forum: General Help
---

### Post by MiKom on 2008-11-08
I have recently upgraded my system to Intrepid and weird things started to happen. After first reboot the booting process stopped. The progress bar in splash image was standing still. However when I pressed some random keys it started moving a bit with each keystroke.
I tried booting without splash to look at kernel output but it showed no errors. It just stopped after one printk and stood still. When I pressed some key several new lines appeared. It was going the same until it loaded init and started loading services, so it's probably some kernel issue 
The same thing happens with Intrepid livecd, both 32 and 64 bit versions. It didn't happen before Hardy->Intrepid update, and it doesn't happen with Hardy livecds.

Very similar (or exactly the same) problem has been reported on forums a couple of times but was more or less ignored, or no working solution was found:


[http://ubuntuforums.org/showthread.php?t=953460](http://ubuntuforums.org/showthread.php?t=953460)
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6116441&postcount=266](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6116441&postcount=266)



There is also a bug, that I think is somehow connected with that issue (and also seems to be ignored):

[https://bugs.launchpad.net/ubuntu/+bug/290515](https://bugs.launchpad.net/ubuntu/+bug/290515)


I posted some outputs from my laptop in this bug that show the pause in boot process, you can see there after which printk it stopped that time, however I must note that at each boot it stops after some other printk.
My computer is HP Pavilion dv6510-ew. lspci and lspci -vvv output is attached.

---

### Post by sujithw on 2008-11-08
I have the same issue. I upgraded from 8.04 and now almost my system is not working. When starting, I have to keep pressing random keys to see the progress bar moving.

Hope someone will help me. I am a very basic ubuntu user and don't know much about getting some log files out to you. But if someone can instruct the steps to be taken, I may be able to get some log files.

---

### Post by flashbackk on 2008-11-08
Me too

---

### Post by Lesouteneur on 2008-11-08
Ive been trying to get over this problem since the release of intrepid, but still, no solutions have I found. In other posts I noticed most people having this problem seem to have Pavilions... I myself have a Compaq Presario F767NR laptop and am experiencing these same annoyances. I have been using Ubuntu on multiple computers since Dapper and have never experienced a problem like this (on this laptop only with Hardy).

---

### Post by gkrules on 2008-11-08
I have a Compaq F756NR experiencing this problem.
Maybe it has to do with HP products?

---

### Post by maxovride on 2008-11-08
i too am having this issue along with a few others.  i also believe it has to do with hp products.  i have using a hp dv6810us. 8.04 works great (well have i got the wireless to work) but nothing but problems with 8.10.  i have 8.10 running on a gateway laptop without issue, and a dell desktop even picked up my evdo usb modem with no issues.  i have to say thought that when it comes to hp products and linux i have had more issues then any other brand.  i dont think im gonna by an hp laptop again, they just arent linux freindly in my experiance.

here is a link to a thread that i started a few days ago about this issue and what i have tried
[http://ubuntuforums.org/showthread.php?t=974324](http://ubuntuforums.org/showthread.php?t=974324)

---

### Post by Lesouteneur on 2008-11-08
nvm

---

### Post by sujithw on 2008-11-10
I have followed one of the work arounds listed on the web to hold down the ctrl key when booting and it seems to work.

---

### Post by Lesouteneur on 2008-11-10
> **sujithw said:**
> I have followed one of the work arounds listed on the web to hold down the ctrl key when booting and it seems to work.

The problem is that it is not a permanent fix

---

### Post by MiKom on 2008-11-11
After upgrade to 2.6.27-8 kernel problem seems to be still present.

---

### Post by Lesouteneur on 2008-11-20
Josueped solved my problem for me you just have to add the boot option "acpi=noirq" (without quotes):

> **Josueped said:**
> here is the fix. from terminal

gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq 

and you are good to go.

---

