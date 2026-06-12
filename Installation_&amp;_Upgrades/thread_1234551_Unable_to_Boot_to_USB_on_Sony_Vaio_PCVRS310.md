---
title: "Unable to Boot to USB on Sony Vaio PCVRS310"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by Loafers on 2009-08-08
[B]UPDATED:
Okay I tried booting to a Window$ cd, but it was still unable to detect.  Therefore I'm guessing there must be something wrong with the computer.  I have the boot order set up correct.  1. USB-FDD 2. CD-Rom 3. IDE and it STILL does not detect any media at ALL.  The closest I ever got was when my computer hanged like 3 seconds when I had my Window$ cd-rom in, but that's as far as I got to get my computer to detect anything...  Any solutions :/?
[/B]

OLD:
> I am unable to boot to my usb ubuntu livecd on my sister's sony vaio PCVRS310.  I tried chaning the boot order and the following were listed: 
IDE
USB-FDD
LSA?LSB?120

So i put USB as the first thing to boot to and restarted, but it still does not detect my usb.  

I know my usb is bootable because it works on my dell laptop and my dads ibm computer.  I'm guessing i'm supposed to boot to usb-zip therefore it isn't supported?

---

### Post by Herman on 2009-08-08
It won't be 'USB zip', or at least I don't think so. If I'm guessing correctly, that means an old kind of floppy drive called a zip drive, attached via a USB cable. There aren't too many zip drives around these days as far as I know. Some of my computers list that option in the BIOS boot order too. 

Another way that should work would be to boot your computer and watch carefully as the computer is booting up for instructions about how to get into the BIOS boot menu. Most PCs have a BIOS boot menu, and often the F12 key is the one to press in the early stages of booting for a BIOS boot menu. Hopefully, it will show the option to boot from USB, or maybe you need to select 'boot from Hdd', and then in another sub-menu you'll find your USB drive, listed as another hard drive. You might need to play around and reboot a few times before you get it right.
Another way to do it would be to try booting from some kind of boot loader in a CD or floppy disk. GRUB Boot Loader or GAG Boot Manager can both boot operating systems in other (non-first) disks.

Some computers don't support booting from USB.
I even have one that's fairly new that can't boot from USB, but my oldest one can do it.
I hope your sister's can.

---

### Post by Loafers on 2009-08-08
> **Herman said:**
> It won't be 'USB zip', or at least I don't think so. If I'm guessing correctly, that means an old kind of floppy drive called a zip drive, attached via a USB cable. There aren't too many zip drives around these days as far as I know. Some of my computers list that option in the BIOS boot order too. 

Another way that should work would be to boot your computer and watch carefully as the computer is booting up for instructions about how to get into the BIOS boot menu. Most PCs have a BIOS boot menu, and often the F12 key is the one to press in the early stages of booting for a BIOS boot menu. Hopefully, it will show the option to boot from USB, or maybe you need to select 'boot from Hdd', and then in another sub-menu you'll find your USB drive, listed as another hard drive. You might need to play around and reboot a few times before you get it right.
Another way to do it would be to try booting from some kind of boot loader in a CD or floppy disk. GRUB Boot Loader or GAG Boot Manager can both boot operating systems in other (non-first) disks.

Some computers don't support booting from USB.
I even have one that's fairly new that can't boot from USB, but my oldest one can do it.
I hope your sister's can.

Hi thanks for your reply.  I was able to access BIOS settings and change the boot order so it would boot to "USB-FDD", but it is still unable to boot.  I know my usb isn't the problem because it works on my other 2 computers, so I don't know why it doesn't work particularly on my sister's comp :/

---

### Post by Herman on 2009-08-08
Some computers just don't have the built-in ability in their motherboard. 

Try the F12 key trick I already mentioned and see if it does any good.

Here's a link about how I do it with one of my computers just for an example, [How I boot from my BIOS]("http://members.iinet.net.au/%7Eherman546/p1.html#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).
I know that almost all computers will be different, but I hope that will be enough to give you the idea.

---

### Post by DracoMoye on 2009-08-08
You can try to boot with PLoP Boot Manager ([http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)) it booted my usb device for me.

---

### Post by Loafers on 2009-08-08
Okay I tried booting to a Window$ cd, but it was still unable to detect.  Therefore I'm guessing there must be something wrong with the computer.  I have the boot order set up correct.  1. USB-FDD 2. CD-Rom 3. IDE and it STILL does not detect any media at ALL.  The closest I ever got was when my computer hanged like 3 seconds when I had my Window$ cd-rom in, but that's as far as I got to get my computer to detect anything...  Any solutions :/?

---

### Post by nbala.iyer on 2010-11-09
hi . were you able to have this resolved ???

---

### Post by Loafers on 2010-11-09
> **nbala.iyer said:**
> hi . were you able to have this resolved ???
No :(  I had to use a cd I think.

---

### Post by Rikki123s on 2011-07-22
I know this post is old, but i think this might help. unless someone has already posted it (I haven't read everything).

press F2 to boot into BIOS. in one of the menus there will be an option for Sony Vaios saying "External HDD Boot". By default this is disabled. press Enter on the option, scroll to "Enable". press enter again. Now your computer should boot into the USB interface.

I have a Vaio TX3XP, it worked for me

---

### Post by xryebreadx on 2012-04-15
> **Rikki123s said:**
> I know this post is old, but i think this might help. unless someone has already posted it (I haven't read everything).

press F2 to boot into BIOS. in one of the menus there will be an option for Sony Vaios saying "External HDD Boot". By default this is disabled. press Enter on the option, scroll to "Enable". press enter again. Now your computer should boot into the USB interface.

I have a Vaio TX3XP, it worked for me

I have been trying to insall a form of linux on my USB drive to have it  work.  I tried different software (Unetbootin and USB Installer  something) with different ISOs.  Nothing worked on my Sony VAIO  VGN-365E.  It would just go past the USB boot and boot to windows. But,  pressing Escape then F2 after that to go to BIOS and then Enabling  External HDD Boot worked.

---

### Post by oldos2er on 2012-04-15
Closed, necromancy.

---

