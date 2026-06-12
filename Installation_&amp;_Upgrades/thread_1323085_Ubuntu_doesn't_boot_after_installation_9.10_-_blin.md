---
title: "Ubuntu doesn't boot after installation 9.10 - blinking coursor"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by kausled on 2009-11-11
[FONT="Fixedsys"][SIZE="4"][COLOR="Blue"]Hallo![/COLOR]
I had installed Ubuntu 9.04 on my Acer Travelmate 4500 Laptop. It was fantastic. 


Than in October I changed the Size of my Partitions and Ubuntu didn't run anymore. So I deleted Ubuntu 9.04 and installed 9.10. The first problem was, that I had to switch ACPI=OFF in the menu of the Live-CD otherwise Ubuntu doesn't start.So the Live-System runs well and I installed Ubuntu without any errors. After the Installation I had to reboot the system. Grub2 started, I choosed Ubuntu 9.10 and than there's a black screen with a blinking cursor. (The same Problem is when I boot the Live-CD without ACPI=OFF. )

What shall I do? 
 [INDENT][/INDENT]        I can't disable ACPI in the BIOS and I don't know how to do it in GRUB and it's a Laptop, on which I need the Hibernate functions.

Will I have success,when I install 9.04 and upgrade to 9.10 ?
Or can I use an older Kernel?

Thank you for your answers! :D
[/SIZE][/FONT]

---

### Post by adrien214 on 2009-12-15
It's a late reply but I hope it might be of some help.
I have the same problem and so do many other people, it seems to be an issue with 9.10 and a supposedly unstable clock.

okay, all of what follows below can be achieved by selecting the image you wanna boot in the **grub2 boot menu** and then pressing the key "**e**" on the keyboard, there you can edit the boot options, sometimes, I wish I was reading more. This however needs to be done everytime you boot if you don't edit the /etc/default/grub file so read on...

The way to do disable the acpi in Grub2 is to edit the /etc/default/grub file

look on [this (hidden-ubuntu-forum-link) ]("http://ubuntuforums.org/showthread.php?t=1195275")page and search for 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

there you'll see what to do. hopefully it'll work for you, I'm gonna try it right away.

okay, for those who don't want to follow links,  locate the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
[I][SIZE="2"]
[INDENT]This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". **This line is where other instructions, such as "acpi=off" are placed**.[/INDENT][/SIZE][/I]

the other options that other people have found to work for the boot /freezing problem described above are :

[INDENT][I]clocksource = hpet
clock="notsc"
notsc=TRUE[/I][/INDENT]


[B]however, I havent tried these myself and thus don't blame me if it screws up everything (not that you'd be happy with your 9.10 so far ;D )

---

