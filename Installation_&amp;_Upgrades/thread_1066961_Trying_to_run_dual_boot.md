---
title: "Trying to run dual boot"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by bigpayne69 on 2009-02-11
I need some help. I have a full Ubuntu laptop but I am tired of runing into drivers and programs that will only run in windows so I want to run a dual boot with xp. all the forums that I can find talk about installing ubuntu on a windows machine but nothing about instaling windows on an linux computer. does anyone know what would be the best way to do this?

---

### Post by zvacet on 2009-02-12
Download [Gparted live Cd]("http://gparted.sourceforge.net/") and shrink your Ubuntu partition with it.On that unallocated space install Windows.After that you will have to [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by bigpayne69 on 2009-02-13
I used Gparted live to reduce my ubuntu partition, then I formated the leftover space into a new partition and installed tiny xp on it. Once I had windows installed, It took over and I couldn't boot Ubuntu anymore. So I used an ubuntu boot disk and reinstalled grub into the mbr and now my computer boots in Ubuntu, not windows. I'm pretty new at this but I thought that it would give me the option to chose which OS I wanted to upon startup but it doesn't. Am I missing something here or am I just out of my mind.

---

### Post by Taemojitsu on 2009-02-13
you might not have installed Grub the right way. I never did get the method in that thread to work, it gave some weird error... in the end I ended up using grub-install with the --root-directory=XXX option.

But you probably just need to run update-grub, which will search for the Windows partition. (Maybe? might just search for new Linux kernels in /boot)

---

### Post by bigpayne69 on 2009-02-13
How do I do that?

OK I'm really new at this

---

### Post by logos34 on 2009-02-13
Manually add a windows boot entry to Grub [like this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu").

---

### Post by TombKing on 2009-02-13
If all else fails dual boot with windows works much better if you install windows first. So be prepared to backup data and start all over from scratch.

---

### Post by Taemojitsu on 2009-02-13
scary.

type 'update-grub' at the command line, inside of your working Ubuntu installation. If it says it's not there, then go to Synaptics and install it~

it will update the list of OS's that GRUB shows you at boot.

(note: it hasn't been mentioned in this thread, you can use [EBCD](http://neosmart.net/wiki/display/EBCD/) to boot Linux using the Vista bootloader)

---

### Post by bigpayne69 on 2009-02-14
ok this is my setup
/dev/sda1               1        8096    65031088+  83  Linux
/dev/sda2   *        8097        9327     9888007+   7  HPFS/NTFS
/dev/sda3            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

so if I'm trying to manually enter window into the grub menu, would my windows partition be (hd0,1) because I know that Ubuntu is (hd0,0) or how would I find out which one is which?

---

### Post by zvacet on 2009-02-14
Yes,your Windows partition will be (hd0,1).Follow** logos34**advice and you should be fine.

---

### Post by bigpayne69 on 2009-02-14
Id did like logo said and now my grub menu looks like this:
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.10, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=730fda3c-d1c0-4135-9d43-25c8e55306d0 ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

I'm not sure why there are so many options when booting Ubuntu but thats neither here nor there; the thing is, after I made the change, saved the file, and rebooted my computer. I hit ESC to enter the grub menu and the screen went black and the menu never showed up. I waited a minute for the menu to pop up but it never did. So, what did I do wrong?

---

### Post by bigpayne69 on 2009-02-14
good news, I just tried it again and the menu popped up the time. So far everything is working fine. Everyone, thanx for your help

---

### Post by logos34 on 2009-02-14
If that windows entry is inside the 'automagic' kernel section like it shows above, make sure to move it to the bottom of menu.lst, otherwise grub will delete it next time there's a kernel update.

You might want to adjust menu.lst so all those older kernels don't show:

> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# **howmany=[COLOR="Blue"]1[/COLOR]**

This will keep your current kernel plus next most recent (2.6.27-11 and -9). 

Then run 

sudo update-grub 

You can even uninstall the older ones in synaptic (search 'linux-image-2.6.24-' and 'linux-headers-2.6.24-').

hope that helps

enjoy

---

