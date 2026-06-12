---
title: "trouble dual booting w/ two hdd"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by richpreville on 2006-02-01
I have two ide connected hdd's, one master and one slave. I'm trying to install Ubuntu on one (starting out slowly) and XP on the other. Problem is...when I install XP the setup process gets past the reformat (NTFS) but then boots right back into the setup afterwards (instead of booting from the hdd). This does not happen when I disconnect the slave hdd and then reboot the machine. Please, someone give me a bone here. A friend told me that it may be a mbr problem. I would appreciate anything....really,
Thanks

---

### Post by encompass on 2006-02-02
not quite sure what you mean... are you saying that windows setup crashes and reboots?  or are there some issues with the system loading linux after you install windows.
The easiest way to install ubuntu with windows is to ahve windows there first... then install ubunut on the free space you have given it.
Hope this helps.

---

### Post by richpreville on 2006-02-03
I'm not sure exactly what was going on but......when the first phase of the xp install completed, that is to say, when I usually do a complete install including formatting, after all the files from the cd load, the machine usually reboots asking me to "press any key to boot from cd," which I simply ignore and the machine boots from the hard drive on which the files have just been loaded. When I had my master and slave drive connected together, after I had run the first phase of the install, I didn't get the "press any key to boot from cd" prompt and the machine just automatically booted from the setup cd. 
Here's what I've done so far. 
Loaded each OS separately on the drives, alternately connecting and disconnecting them so that only one was connected at a time. Then, made the drive with Ubuntu the master and Windows the slave. Now I can boot from either, but I have to change the boot sequence in the BIOS. I would love to know how to get Ubuntu to "see" the XP install and get that in the GRUB. Maybe I could get the option to boot from either one instead of having to go into the BIOS to select. 

Let me know what you think.

---

### Post by Horndog on 2006-02-03
I could be wrong but Ubuntu and it's Grub does not read NTFS unless this option is compiled into the kernel. When I tried it I got that error.

---

### Post by aysiu on 2006-02-03
[QUOTE=Horndog]I could be wrong but Ubuntu and it's Grub does not read NTFS unless this option is compiled into the kernel. When I tried it I got that error.[/QUOTE] Grub read my NTFS Windows XP just fine, in Hoary and Breezy.

---

### Post by Horndog on 2006-02-03
[QUOTE=aysiu]Grub read my NTFS Windows XP just fine, in Hoary and Breezy.[/QUOTE]
Same hard drive, or two different hard drives? Would you be so kind as point my to the documentation the pertains to the Grub starting Windows XP with NTFS on a different hard drive.

That would be great thanks.

---

### Post by sniperweydz on 2006-02-03
i have a dual boot system (windows xp and ubuntu 5.10), but i was wondering what if my windows fail and i want to install it again, what will happen to my ubuntu partition? how will i be able to boot both again? need help

---

### Post by richpreville on 2006-02-04
Thanks for the help, encompass....I did end up reinstalling everything. For you guys out there, here's the advice I got: 

I haven't the foggiest why it doesn't try the CD... it could be that
when you don't have anything on the HD it then boots to the CD... mine
did that... so check your boot order and make sure that it is geting the
CDrom, then USB stick, then HD that way you can boot off of just aobut
anything.  The second thing... I would reinstall grub or the whole
ubuntu os to drive you want it too now with both cd's in... that should
set grub up correctly with out any issues.  Swapping the HD cables is
for the birds... and a pet peeve for me.  Yuck...  anyway... try to
respond just to the forum to help everyone out.

The original post was concerning two separte hard drives, both quantum fireballs, one 30 and one 6 gig. The 6 gig came from an old computer at school, the 30 came from a friend (so both have some mileage). Anyway, I bought a new Seagate 160 gig, reinstalled XP on that and Ubuntu on the old 30. It worked fine, boot sequence and all (grub, too!). I've always had the old 30 backed up on my hard drive (norton ghost), so reformatting the 30 is no prob (for those of you worried about data loss). End of it is....it could have been something about the old 6 gig (mbr, grub, who knows!) . If anyone runs into the same prob as in the original post, please post it!

---

### Post by Horndog on 2006-02-04
To close this thread and for clarity, OP never did get Grub to boot Windows XP NTFS from a different physical hard drive. Also no information-documentation was volunteered to assist in the problem. I personally don't think it's possible with out the Grub first mounting the second physical hard drive first.

Original problem unresolved.

---

### Post by confused57 on 2006-02-04
I don't know the thread, but do a search for poster "Iha".  He has a
method for dual booting 2 OS from separate hard drives.  I found it,
because I want to eventually set my system the same way.

---

### Post by Horndog on 2006-02-04
[QUOTE=confused57]I don't know the thread, but do a search for poster "Iha".  He has a
method for dual booting 2 OS from separate hard drives.  I found it,
because I want to eventually set my system the same way.[/QUOTE]

Thank you and Iha very much. That did the trick. I now have dual boot from two different physical hard drives First being ubuntu and the second being Windows XP NTFS. by adding this to themenu.lst
```

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

```
Add
```

title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

Case closed

---

