---
title: "frozen kernel, boot acpi=off works sometimes"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by pearlson on 2006-07-07
my notebook was stalling at the line, "unpacking linux. ok, loading kernel". 

i had trouble installing from the live CD until someone told me to enter "boot acpi=off" in the extra options. That worked got me past the freeze and i was able to install ubuntu from the icon on the desktop.

now when grub loads and i select ubuntu to run it freezes at the same point. i tried entering the acpi=off command again but it doesnt help. it makes a small difference if i run in recovery mode, but it just hangs up somewhere else after a lot of code flashes by the screen.

any ideas how to append the boot command from grub to make ubuntu load?

also, my sound card isn't picked up. im running an ASUS S1300N machne.

thanks! MP

---

### Post by pearlson on 2006-07-09
so i fixed the problem, finally! 

the acpi=off command needed to be added again to the boot command in grub. so for a while i would manually put the line in after each restart. then i found a website explaining how to edit the menu.lst  -- here is the fix.

(i used Vim, but any text editor will work as long as you are su -)
FIRST: copy the menu.lst file incase you make a mistake.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-original

SECOND: edit the menu.lst file. you'll need super user priv since its a read-only file by default.

sudo vim /boot/grub/menu.lst

the code is pretty simple for the file: # are comments and ignored by the booting shell, the rest is code that is either displayed or executed. scroll down to where there aren't any more commented sections and append the Ubuntu command as follows:

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash acpi=off
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot


you can add the acpi=off to the recoery mode also if you want. 


cheers,
MP

---

### Post by mpokrywka on 2006-07-09
Better option would be adding acpi=off as default kernel option for grub, because next time after kernel upgrade (ie security update) your change will be lost.
Find line with "# kopt=root=/dev/sdaxx ro" and make it "# kopt=root=/dev/sdaxx ro acpi=off". Line with "kopt" must start with #-sign.

But I have a question - try booting without "acpi=off" and without "quiet splash" parameters  - when grub menu shows you can edit parameters by pressing 'e'. When you remove "quiet splash" parameters there will be many debug messages while booting. I'm wondering if booting stops at:
```
SCSI device sda: drive cache: witeback
 sda:

```
If it stops there (partition detection), you can try turning off only libata acpi (I described it in [http://www.ubuntuforums.org/showthread.php?t=210153](http://www.ubuntuforums.org/showthread.php?t=210153) ), because working acpi is rather necessary for notebook.

---

### Post by krazyd on 2006-07-11
Hey, I'm having the same problem on a ASUS A6000KT notebook.
The problem with acpi=off is that none of the power features will work, which is quite a showstopper for a notebook.

I can't find a matching bug report on launchpad.net, and wondered if anyone had filed one. If not, I will. :)

---

