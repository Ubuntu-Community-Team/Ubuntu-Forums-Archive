---
title: "Dual Boot"
date: 2008-11-21
forum: General Help
---

### Post by FLCL on 2008-11-21
So i have windows installed on my slave, and linux on my master. Both drives are set to be able to boot in the bios, but whenever i turn on my computer i do not get a choice, it simply boots to linux. Why is that? Can someone help?

---

### Post by 73ckn797 on 2008-11-21
> **FLCL said:**
> So i have windows installed on my slave, and linux on my master. Both drives are set to be able to boot in the bios, but whenever i turn on my computer i do not get a choice, it simply boots to linux. Why is that? Can someone help?

Is grub set to offer a choice? Search the forums and you should find similar questions/answers.

---

### Post by FLCL on 2008-11-21
Nope, grub does give me any options D:

---

### Post by 73ckn797 on 2008-11-22
> **FLCL said:**
> Nope, grub does give me any options D:

Clarify. Does or does ***not*** give you any options?

What does grub list?

enter in terminal:
```
gksudo gedit /boot/grub/menu.lst
```

Post that info.

---

### Post by FLCL on 2008-11-22
My bad, it does **not** give me an option to boot to my windows drive in grub.
This is what i have:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=caacfef6-8628-4a86-8cd0-3811cd3d0f5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=caacfef6-8628-4a86-8cd0-3811cd3d0f5b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=caacfef6-8628-4a86-8cd0-3811cd3d0f5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=caacfef6-8628-4a86-8cd0-3811cd3d0f5b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
```

I was reading another thread somewhere on the forum..on my windows drive x.x, that you can edit the grub menu and add the Windows drive in there or something like that.  Not sure how to go about that though

---

### Post by 73ckn797 on 2008-11-22
I had to be reminded of how to do it the other day. 

Try adding this to the end of the grub/menu.lst. Save it and reboot. You will need to press escape when grub starts showing a count down to default to Ubuntu.

```
title Windows XP
root (hd0,0)
chainloader +1
```

See if that works. As long as Windows is the "(hd0,0)" it will work. Other wise you will have to try editing to suit the correct drive. 

I see that Ubuntu is on hd0,0. Is Windows on a separate drive? May need to change to hd1,0 or whatever will work.

---

### Post by confused57 on 2008-11-22
You might try the Window's grub entry in this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by FLCL on 2008-11-23
> **73ckn797 said:**
>  

I see that Ubuntu is on hd0,0. Is Windows on a separate drive? May need to change to hd1,0 or whatever will work.

Yeah, windows is on my other drive. Ubuntu is my master, and Windows is slave. I just edit it to hd1, and it should work?

> First, disconnect your Windows drive, then connect the drive you want to install Ubuntu on as the primary IDE master drive. After installing Ubuntu, allow the updater to install all the necessary updates, this may take awhile. Shutdown your computer and reconnect your Windows drive as slave, then restart, your computer will boot into Ubuntu.


Very thorough, but my question is, does it matter if i already have ubuntu installed on my master?(Both Windows and Ubuntu are fully set up and customized x.x)

---

### Post by TeXtonyx on 2008-11-23
No it doesn't matter. Either drive can be set to boot from Bios.
What does matter is where grub is installed, most likely it's
installed to your Master, in the MBR, which is Ubuntu. So the
menu.lst needs to have an entry for Windows. Mabye you will
need the more complex menu.lst entry which uses mapping. If you
read a tutorial they will probably show the more complex entry.
Now XP likely has its own bootloader installed in the MBR of the
second drive. So if you boot to the second drive (changed the bios
setting first) you will boot Windows. You can add Ubuntu to the
Windows bootloader, most likely boot.ini with free Bootpart.
So you can do it either way or both. 

Most likely you want to boot from your Ubuntu on the Master drive
and have the correct entry in /boot/grub/menu.lst to boot Windows.
gksudo gedit /boot/grub/menu.lst 
copy and paste your Windows entry under Other OS and save.
Windows will show up on your boot menu options next time you boot.
If you get a grub error it usually means you chose the wrong
entry to copy and paste (or type manually) into menu.lst
There shouldn't be an error report from Windows since you
said you can boot either OS from bios now.

---

### Post by confused57 on 2008-11-23
> **FLCL said:**
> Yeah, windows is on my other drive. Ubuntu is my master, and Windows is slave. I just edit it to hd1, and it should work?



Very thorough, but my question is, does it matter if i already have ubuntu installed on my master?(Both Windows and Ubuntu are fully set up and customized x.x)
Since you already have Ubuntu installed, the only info you need from the tutorial is instructions on adding a Window's entry to grub.  Was Windows installed to the slave drive, or installed to the master drive, then switched to slave position?

---

### Post by Bigneil on 2008-11-23
I'm not very computer savvy, but perhaps this helps. i too have too drives master and slave. When in Bios at the boot order screen there is an option to enable boot sprite! 

If it is enabled a screen pops during startup, and gives me a choice of which drive i want to boot from.

Good luck

---

