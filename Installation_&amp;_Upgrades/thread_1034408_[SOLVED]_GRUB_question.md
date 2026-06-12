---
title: "[SOLVED] GRUB question"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by beachdaze on 2009-01-08
Installed 8.10 but having issues with GRUB.

Hard drives are:
300GB sata on port 1 (boot drive w/XP Pro SP3) shows as sdc
300GB sata on port 2 (Ubuntu 8.10 amd 64) shows as sdd
1TB sata on port 3 (ntfs for storage only) shows as sdb
1TB sata USB (ntfs for backup) shows as sda

I'm confused as to why Ubuntu has a different "order" for the drives than BIOS.  So this leaves me questioning as to where to install GRUB.  Since sdc is the boot would that be (hd3,0)?  

I have installed Ubuntu, Debian, Mepis and other distros before I added the two TB drives without issue.  Guessing I should remove those two drives just to get it booting?  But then I'd have to mess around with fstab, which isn't all that bad, just a step I'd like to avoid.

Any advice is more than welcome.

Thanks - Bruce

---

### Post by ASchweitzer on 2009-01-08
If sdc is the drive you wish to use as boot, then the drive to specify to GRUB would be (hd2,0), from my experience.

As far as I understand it, the sda, sdb, etc labels are applied by the partitioning programs (having to do wih partition tables), and are dependent on when the partitions are made (or when they are 'added' to the system, in the case of the USB drives), and are independent of how the BIOS lists drives. (someone please correct me if I'm wrong)

As for GRUB drive mapping, the drive to specify to GRUB is always one lower than the sd*x* listing, IE:

*sda* maps to *(hd0,0)*
*sdb* maps to *(hd1,0)*
and so on

---

### Post by caljohnsmith on 2009-01-08
If Ubuntu is on sdd, I would recommend to install Grub to its MBR (Master Boot Record) and set your BIOS to boot that drive. Just keep in mind that Grub on start up sees the order of drives as the same as your BIOS boot order, so on start up (hd0) is the first boot drive, (hd1) is the second boot drive, etc. That means if you boot your Ubuntu sdd drive on start up, that would make it (hd0). Only when you are booted into Linux and Grub no longer has access to the BIOS to know the boot order does Grub see the order of drives as (hd0) being sda, (hd1) being sdb, (hd2) being sdc, etc. So the bottom line is, when you run Grub commands in Linux, then sda=(hd0), sdb=(hd1), etc, but on start up (hdX) is determined solely by the BIOS boot order. If you want some specific help installing Grub to the MBR of your Ubuntu drive and making sure the menu.lst will work for that situation, how about posting the output of the following:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup. We can work from there if you want.

---

### Post by Herman on 2009-01-08
Sorry, server error.

---

### Post by Herman on 2009-01-08
Sorry, server error.

---

### Post by Herman on 2009-01-08
Sorry for the multiple posts, the message I kept getting at my end was telling me my posts were not getting through because of a server error, so I kept trying again. Now I see that some did get through okay :oops:

---

### Post by Herman on 2009-01-08
> I'm confused as to why Ubuntu has a different "order" for the drives than BIOS. So this leaves me questioning as to where to install GRUB. Since sdc is the boot would that be (hd3,0)? Apparently, from what I have read, and even from my own experiments here at home with different computers, GRUB seems to have a hard time making sense out of the information it gets from some BIOSes. Some BIOSes might even register SATA drives in the chronological order in which the drives were added and the computer was rebooted, rather than according to the port numbers. Then when the BIOS is reset, they may revert to the port number order. So BIOSes can be fickle and finnicky.

Ubuntu has overcome that kind of problem with Intrepid Ibex because we use UUID numbers now, and not (hd0,0) and /dev/sda1 type numbering in our menu.lst and /etc/fstab files anymore, so you shouldn't need to go re-installing GRUB or editing any files at all, (unless you actually enjoy doing spending your time doing those kinds of things, or if you have more than one Linux currently installed).

The easiest way to fix your kind of problem is to just go into your BIOS and switch the hard drive order around in the BIOS the way you want the drives to be numbered, rather than just leaving it up to fate. 
Make the the one that GRUB was installed to will first, so GRUB will boot.
Then find the right order for the remainder of your drives so that Windows will boot if you have that. That way you won't need to go re-installing GRUB or editing menu.lst and /etc/fstab, at least not for Ubuntu, and your will also find that any Windows operating systems will boot okay too, once you find the right hard drive order.
If you currently have other Linux Systems you may still need to do some editing though, and if you have more than one other Linux then you may find it easier to to things the old fashioned way.

Regards, Herman :D

---

### Post by meierfra. on 2009-01-08
[QUOTE=beachdaze]I'm confused as to why Ubuntu has a different "order" for the drives than BIOS. [/QUOTE]

As far as I know, Ubuntu has no knowledge of the order of the drives in the bios, so it has to pick it's own order. 


[QUOTE=Herman]Ubuntu has overcome that kind of problem with Intrepid Ibex because we use UUID numbers now, and not (hd0,0) and /dev/sda1 type numbering in our menu.lst and /etc/fstab files anymore, so you shouldn't need to go re-installing GRUB or editing any files at all,
[/QUOTE]

Correct, there is no more need to edit fstab and menu.lst (unless UUIDs change). But grub still uses  "(hd0,0)" to find stage2 and menu.lst; and there are some rare cases where you might have to reinstall Grub, if Grub has used the wrong device map during installation . Also  if your bios  don't let you choose an arbitrary boot order (or you don't want to change the boot order), you might have to reinstall Grub.

---

### Post by beachdaze on 2009-01-08
Thank you all for the help.  I could make no sense of it so I went back to basics.  I removed the newer 1TB drive, and left only the two 300gb drives in place.  Re-ran the install and lo and behold, I can now dual boot into both the XP and Ubuntu!  So all is well.  

I have added back in the 1TB drive and the USB 1TB drive and all seem to be functioning.  I guess I'll  have to tinker with fstab so that the storage drive (1TB) is auto mounted, but that's another day.  On with security updates and "pretty" stuff for now.

Thanks again!

Bruce

---

