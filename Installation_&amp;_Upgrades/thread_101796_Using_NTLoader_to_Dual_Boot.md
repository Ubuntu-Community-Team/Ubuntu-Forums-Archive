---
title: "Using NTLoader to Dual Boot"
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by vodkamattvt on 2005-12-10
Is this possible with Ubuntu? I know that a lot of experienced Linux people will scoff at this, but for people that have used windows for so long it is nice to have something familiar, especially if there are lots of troubles with GRUB and Lilo.

Anyway, I found this article that I had bookmarked long long ago and wondered if it were possible? [http://www.users.bigpond.com/pclim/help-desk/dual-boot/dual-boot.html](http://www.users.bigpond.com/pclim/help-desk/dual-boot/dual-boot.html)

My hesitation comes from past experiences with Lilo and having to restore my MBR multiple times, inexperience with Linux in general, and difficulties Ive been reading about GRUB. I would rather just install linux without touching the MBR and then configure NTLoader in windows.

Thanks!

---

### Post by Herman on 2005-12-10
G'day, vodkamattvt, Herman here; currently the easiest and best way to install Ubuntu without touching your MBR, is to firstly make sure your computer's BIOS is set to boot from the floppy drive as well as the CD drive before the hard-disk. Then, make yourself a GAG boot floppy disk to boot from.
 Then, install Ubuntu and either create a seperate /boot partition and install GRUB to that,
 or, choose 'Go Back' when it asks you if you want to install GRUB ot MBR, go down one line in the 'Ubuntu installer Main Menu', and choose 'Install Lilo to a Hard disk', and then choose 'Install Lilo to your new Ubuntu partition'. You can also do that later even, after Ubuntu install is finished, even if GRUB is already installed as well, (I have them both! :D ) (Not necessary, just an experiment)
If you choose to use GAG from a boot floppy, you will need to have your GAG boot floppy all ready for when your computer spits the Ubuntu Install CD out near the end of the installation process and needs to re-boot to finish the installation. You will have to use the GAG floppy (or a GAG CD if you have no floppy drive), to re-boot from. You will need to have already practiced how to set up GAG as well, so you will know what to do, (how to configure GAG - it's easy, but it's best you already know before-hand). You can then use GAG off your GAG boot floppy to boot your computer whenever you want to try out Ubuntu. It will leave your MBR in it's 100% original condition. You can install it to MBR if you want though. It's best to choose 'install GAG to floppy disk' though, that's the whole point of it.
For instructions and links to GAG, find the GAG page in my signature link.

To answer your question; yes it is entirely possible to configure boot.ini in Windows to boot both OS's. Here is my collection of links for how to do that:
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)
[http://www.weblog.nohair.net/archives/000598.html](http://www.weblog.nohair.net/archives/000598.html)
[http://ubuntuforums.org/archive/index.php/t-80508.html](http://ubuntuforums.org/archive/index.php/t-80508.html)
[http://www.plugnpray.co.uk/linux/lilo-nt/1.html](http://www.plugnpray.co.uk/linux/lilo-nt/1.html)
[http://www.dewassoc.com/kbase/multiboot/boot_ini.htm](http://www.dewassoc.com/kbase/multiboot/boot_ini.htm)
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)
[http://hacks.oreilly.com/pub/h/2337](http://hacks.oreilly.com/pub/h/2337)
[http://www.linuxforums.org/tutorials/1/tutorial-3573.html](http://www.linuxforums.org/tutorials/1/tutorial-3573.html)
[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)
[http://www.computerhope.com/issues/ch000492.htm](http://www.computerhope.com/issues/ch000492.htm)
[http://www.prosig.com/protor/kbase/NT-Linux-boot.html](http://www.prosig.com/protor/kbase/NT-Linux-boot.html)

But the easiest and best way (in my opinion) is simply to install GRUB to MBR, that's what I do.
Have fun! :D , and good luck with it, Regards, (Herman)

---

### Post by vodkamattvt on 2005-12-10
Awesome, thanks for all those links. I think I have what Im looking for (Linux is on a different physical drive in my case).

---

### Post by onewisp on 2006-09-17
I have read most of the HowTos but I am still stuck. I edited my boot.ini to load the linux.bin file that I got from BootPart ([http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)). When NTLoader loaded it, it says HAL.dll is missing please copy it to <Windows>/System32/HAL.DLL.

I have installed uBuntu to partition 3 yesterday so I am sure uBuntu is there. How can I add lilo to uBuntu? Isn't it installed by default?

I am using uBuntu 6.06 64 bit edition.

---

