---
title: "multiple grub confusion"
date: 2008-10-06
forum: General Help
---

### Post by fusionisthefuture on 2008-10-06
i know theres a lot of grub posts out there, and if this is repetitive i apologize, but i think its not.  

i have two hard drives.  according to the bios, the first boot device, and the first hard drive, is a 500gb sata drive.  the second is a 4gb compactflash card via sata connection.  i initially installed ubuntu (ibex alpha 6) on the 500gb drive, and i noticed, somewhat vexed, that when the install completes it just auto installs grub without asking me what i wanted to do, not freaking cool considering it was an alt install.  leave the guessing what i want for live cds, imo.  anyways, it didnt really matter because i only had the one operating system on there, and only using that one drive.  

then i went and installed mythbuntu on the 4gb flash drive (ibex beta alt).  this time it shows me that ive got ibex alpha installed already, and says that if all my operating systems are listed, i shouldnt worry, and just install grub on the mbr of the first hard drive (500gb), which i REALLY didnt want to do, but i did anyways.  so i reboot, and it boots to mythbuntu, and i know its on the flash drive cuz theres no noise when its loading.  i get into the operating system and check out /boot/grub/menu.lst and its... there, and it matches the screen grub just gave me.  it found my other kernels and everything, so i can still boot back, but why is it on my 4gb flash drive ?(second hard drive according to the bios; not the one that boots)

all this was not a problem till today, when i updated my alpha install (500gb drive) and it installed a new kernel.  when it got to updating grub, it asked me what to do with menu.lst, and i told it to keep the updaters version, which it did.  i went and checked menu.lst on my 500gb and noticed that it was updated with the new kernel, but had no listing of mythbuntu.  so my first hard drive, which is whats supposedly booting, has grub installed on it, but its not actually using that grub, its using a grub from my second hard drive, which is of course not updated with the new ubuntu kernel.  then i deleted the grub folder from the flash drive completely (being angry and knowing it wouldnt work after that) and it of course doesnt.  

recap: 
two hard drives
two grubs, one per drive
the grub from the wrong drive boots on startup

i think i know how to fix this, using a live cd and copying my grub folder from the 500 gb drive to the 4gb drive, but this is just a secondary computer, i want to know what the hell happened?

---

### Post by caljohnsmith on 2008-10-06
At least with the Ubuntu Live CD installer, when you get to the final stage of installation, you can click on the "advanced" button to tell the installer where to install Grub; there you could have specified /dev/sda to install Grub to the MBR (Master Boot Record) of the sda drive, which should be your 500 GB SATA.

Anyway, your situation right now is probably the Grub in the MBR of your SATA drive is pointing to your Mythbuntu install on your flash drive for its system files, including menu.lst. You can test whether that is true by disconnecting your flash drive on start up; if you get a Grub error before even seeing the Grub menu, then your Grub is definitely using your flash drive. 

Personally, I think the most ideal solution would be to make sure your BIOS is set to boot your SATA drive first, and then reinstall Grub to the MBR of your SATA drive, but have the MBR point to the Ubuntu on the SATA drive for all its system files. I would also install Grub to the MBR of your flash drive and point it to your Mythbuntu install on the flash drive for its files, that way both drives are completely independent of each other.

To do this, boot your Live CD and do the following:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
The commands above should return both of your Ubuntu/Mythbuntu partitions in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4). Use each one as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you can get that far and get a Grub menu on start up, let me know and we can go from there.

---

### Post by fusionisthefuture on 2008-10-06
thanks for the quick reply.

i assume this auto-grub thing is a relatively new development, it used to be the other way around, and was basically the primary reason i used the alt install cd.  its not like it gives you much in the way of configuration options (as far as i can tell).  anyways i liked it better before.  im going to wait till ibex is released to get on that live cd, but im sure what you wrote will work.  

one other thing.  how can i tell that my first hard drives grub was pointing to the files on the flash drive?  also, i checked after the upgrade of ubuntu, and both grubs had all of their configuration files in the /boot/grub/ folders.

edit:  i just ejected the flash card, and now i get error 21 instead of error 15 when booting.

---

### Post by caljohnsmith on 2008-10-06
Try running the following commands, which will tell us which of your drives have Grub in their MBR, and if Grub is in the MBR, which partition/drive does it use for its system files:
```
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sdb bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
The above commands assume your drives are sda and sdb, so if they have a different device name, be sure to use that. Please post the output. I'm leaving now but will probably be around tomorrow morning in case you've posted, just to let you know.

---

