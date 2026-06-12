---
title: "how to update grub bootmanager?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by tonjaa on 2009-06-02
now i use ubuntu9.04 and new for Linux
i try to install systemrescuecd on hardisk.
i do by step from website
first step i copy file to directory /sysrcd/
second step they told update the grub or lilo
i use grub when boot to lock in but i not understand to correct way . they have Example 
[COLOR=DarkOrange]
Here is an example of Grub configuration (edit menu.lst or grub.conf in /boot/grub/) In this example, files are located in /dev/hda8. The grub device name is (hd0,7) (you must subtract 1 from the linux device name, then 8-1=7) [/COLOR]
[COLOR=Green]title    SystemRescueCd from hard-disk
root     (hd0,7)
kernel   /sysrcd/rescuecd subdir=sysrcd setkmap=us
initrd   /sysrcd/initram.igz
boot[/COLOR]

i want to know how to edit menu.lst ?
i must to type  new line like Example or delete of old type in menu.lst?
and at root what's the (hd0,..) 
when i boot it 's have a bloblem or not if i need to boot to ubuntu desktop
and how to change to boot from systemrescuecd ?
i scare if i do wrong way it's make grub bad and lose it.
if who know the correct way please tell me by step .

---

