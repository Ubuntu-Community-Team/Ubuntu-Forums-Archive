---
title: "can't edit menu.lst, help!"
date: 2008-08-27
forum: General Help
---

### Post by geezas on 2008-08-27
I try to "sudo gedit /boot/grub/menu.lst" but I get "cannot open display:" error

Is there a way to edit menu.lst in GUI?  ...would be so much easier but it doesnt let me save the file.

i tried gksudo instead of sudo, same problem

---

### Post by VMC on 2008-08-27
That should work. Does it ask for your password? Also try Alt+F2 then "gksu nautilus /boot/grub" then just click on "menu.lst" from Nautilus and try that method.

---

### Post by tact on 2008-08-27
I would presume that you are on a non-GUI terminal login - correct?  Meaning you have used ctrl-alt-F1 (etc) to get to a fullscreen non-gui terminal or you are booting up in a recovery terminal etc... (this is the only way you would get the message "cannot open display")

gedit will not run in that kind of (non-GUI) terminal as it is a GUI editor.  

in a (non-gui) terminal you need to use a non-gui editor like nano or... 
- you need to start the x windows gui system and then open a terminal (xterminal) inside the gui if you want to use a gui editor

So ...  are you able to boot your system and log in to the (GUI) desktop as per usual?  If so then open a gui terminal (you don't give much info as to what you are doing or what flavour of ubuntu you are using - if gnome (ubuntu) then you find terminal in Applications>Accessories>Terminal)

Does that help?  If you are unable to boot to your normal desktop and need more assistance then drop a reply with a bit more detail on whats happened and what you need to do.

Cheers

---

### Post by mb_webguy on 2008-08-27
Also, you should really use gksu instead of sudo for GUI applications.

And you could use "sudo nano /boot/grub/menu.lst" to edit the file in the command line.

---

### Post by geezas on 2008-08-27
Thank You tact,
It worked when I used GUI terminal instead of the "CTRL+ALT+F1-F6" terminal.
I would have used it first but after a quick scan I didnt find the terminal.  I thought the terminal would be in a system tab, not applications/accessories tab ;]

---

### Post by tact on 2008-08-27
> **geezas said:**
> Thank You tact,
It worked when I used GUI terminal instead of the "CTRL+ALT+F1-F6" terminal.
I would have used it first but after a quick scan I didnt find the terminal.  I thought the terminal would be in a system tab, not applications/accessories tab ;]

Be careful editing menu.lst.  Mistakes could leave you with a non-bootable system.  Back up first.  (sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.20080828)

There are also parts of menu.lst that are generated automatically whenever the update-grub utility is run.  (update-grub can be run manually is ALSO run automatically whenever your update manager installs a new kernel for you).   

For example - never change the uuids for partitions by editing menu.lst manually.  Next time update-grub is run the OLD uuid's will be put back and your system will not boot.  (if you are editing menu.lst to change uuids for a partition reply here for the correct means).

Cheers

---

### Post by Tiler on 2008-10-01
I have many superfluous items in my menu.lst.  Should I comment out the items I don't want to appear or is it more complicated than that?  Here is the list:

[PHP]title		Ubuntu 8.04.1, kernel 2.6.26.5-ultimate
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26.5-ultimate root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.26.5-ultimate
quiet

title		Ubuntu 8.04.1, kernel 2.6.26.5-ultimate (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26.5-ultimate root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.26.5-ultimate

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-virtual
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-virtual
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-virtual (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-19-virtual

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-openvz
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-openvz root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-openvz
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-openvz (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-openvz root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-19-openvz

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/PHP]

---

### Post by Tiler on 2008-10-01
Found it:

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

---

