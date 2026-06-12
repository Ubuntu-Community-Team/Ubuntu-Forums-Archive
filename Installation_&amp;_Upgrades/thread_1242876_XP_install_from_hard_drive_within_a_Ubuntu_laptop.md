---
title: "XP install from hard drive within a Ubuntu laptop"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by Konero on 2009-08-17
**How can I get a "c:>" prompt at start up?**

For some reasons, my XP install Cd can't boot anymore. I'm thinking of processing an XP install from a hard drive by copying the I386 folder and running winnt.exe.

I just ran fresh Ubuntu install leaving an empty partition at the begging of my laptop drive.

Then I formated it using gparted as a ntfs partition.

and so far, it looks like like this :
```

/dev/sda1            3433        3554      979965   82  Linux swap / Solaris
/dev/sda2            3555        4538     7903980    5  Extended
/dev/sda3   *        2704        3432     5855692+  83  Linux
/dev/sda4               1        2703    21711816    7  HPFS/NTFS
/dev/sda5            3555        4538     7903948+  83  Linux
```I'd like to know how I could get the "C:>" prompt. 

I'm thinking of modifying menu.list but I don't know how to do it to it nor if it is possible.

---

### Post by oldfred on 2009-08-17
It is easier to install windows first then install ubuntu since windows will overwrite GRUB and you have to go back and reinstall it. I like to have several boot/repair CD's just in case. I have superGRUB, gparted, parted magic and Knopppix as well as my ubuntu install disk.

Years ago we used a dos disk to partition a drive, formated the drive,  a sys command to make the drive bootable , and copied all the windows install to c:\windows\install. Then when it wanted drivers it would default to that directory instead of asking for the install CD. Now adays with the Internet required for just about anything I do not know if you can do that.

Info on installing windows after ubuntu:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Konero on 2009-08-17
I ran "ubuntu only" comps for years, so I'm not at ease with multiboot issues, or even familiar with any kind of boot issues for whatever OS. 

For me olfred, in this case, this computer have no floppy disk drive (nor CD burning capabilies*)

I further investigated and I found out that I could maybe use the grub prompt and managing it with commands like : 
- rootnoverify, 
- makeactive, 
- boot 
and so on, I don't understand them yet.

I guess I need to put a command.com file on my future XP partition, right?
Anyone on this?

* well, capabilities I guess

---

### Post by oldfred on 2009-08-17
I cannot tell if your windows partition is primary or not, even though it is sda4. Windows is just about impossible  to boot windows from a extended partition (someone says they did, but most of us do not know how). Make sure Windows is one of the 3 primary partitions you have before you do anything. 

One site said these are the current XP files needed:
The normal boot files in XP will also be 
Autoexec.bat
Config.sys
IO.sys
Msdos.sys
NtDetect.com

If you have a bootable windows partition you add to your menu.lst
at the bottom(this was automatically created when I installed ubuntu and had windows installed:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1

The (hd0,0) entry varies depending on the drive and partition  you install windows on. sda4 will be (hd0,3)

---

### Post by oldfred on 2009-08-17
Some info on using USB to install:
[http://www.bootstrike.com/WindowsXP/dosinstalling.html](http://www.bootstrike.com/WindowsXP/dosinstalling.html)
[http://www.tech-recipes.com/rx/578/windows-xp-installing-from-harddrive/](http://www.tech-recipes.com/rx/578/windows-xp-installing-from-harddrive/)
[http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm](http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm)

---

### Post by Konero on 2009-08-17
Yep, thanks a bunch : I had the feeling I could get it working with USB, but it turned out that bios can't boot from a thumbdrive.

More research directed me toward the functioning of chainloader, and from what I got, it is NTLDR that grub try to chain load.

---

### Post by Konero on 2009-08-19
I managed to get a boot prompt on a usb device created with Unetbootin loaded with freedos and then on grub at start up with :
grub> root (hd1,0)
grub> chainloader +1
grub> boot
I finally get a "A:>" prompt! Which was nice after so many tries. 8-)
But I couldn't handle correctly Freedos.


Then I grabbed an iso of my XP CD install, burnt it in a cybercafé and checked that it was booting this time.

---

