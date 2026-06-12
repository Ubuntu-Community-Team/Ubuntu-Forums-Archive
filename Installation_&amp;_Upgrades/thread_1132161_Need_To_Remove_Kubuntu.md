---
title: "Need To Remove Kubuntu"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by markcynt on 2009-04-21
I have Vista, openSUSE, Ubuntu, and Kubuntu, installed in that order so right now the bootloader was installed by Kubuntu.

How do I get rid of Kubuntu without messing up Grub?

---

### Post by kiridude on 2009-04-21
You could boot with the Ubuntu cd, partition, and reinstall grub where you want it.

---

### Post by markcynt on 2009-04-21
I wasn't sure of what I was doing so I booted into Ubuntu and installed Grub to the MBR from there.

Now I can boot into Ubuntu and Vista but when I select openSUSE I get "Error 15, file not found."

So now I need to edit Grub but I'm not sure what to enter.

Tell what info you need and the command to get it. 

Thanks

Edit: Is this the info you need?
```

default 0
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=10c895b3-9c45-42aa-8606-3028615ca08a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=10c895b3-9c45-42aa-8606-3028615ca08a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=10c895b3-9c45-42aa-8606-3028615ca08a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=10c895b3-9c45-42aa-8606-3028615ca08a ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title openSUSE 11.1 - 2.6.27.7-9 (on dev/sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Hitachi_HDT725032VLA360_VFD201R80KUNZL-part6 resume=/dev/disk/by-id/ata-Hitachi_HDT725032VLA360_VFD201R80KUNZL-part5 splash=silent showopts vga=0x314
initrd /boot/initrd-2.6.27.7-9-pae
savedefault

title Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Hitachi_HDT725032VLA360_VFD201R80KUNZL-part6 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x314
initrd /boot/initrd-2.6.27.7-9-pae
savedefault
```

Mark

---

### Post by kiridude on 2009-04-22
Error 15 is usually due to incorrect installation. Check out this page to walk you through re-installation:

[http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

---

### Post by markcynt on 2009-04-22
I don't understand that information. Can anyone work with me on this to help me understand?

---

### Post by kiridude on 2009-04-22
Dude, my answer was very specific - you reinstalled grub wrong.

I also sent you a link to a very detailed, beginner oriented, guide to reinstalling grub correctly.  Did you expect me to fly over to your house and do it for you? Or did you expect a magic command to fix everything on the spot?

I guess I'm an idiot for taking time out of my day trying to help you.

Do you find it strange that nobody has responded to you...?

This is not customer service.

Nobody here is required to care about your problems, and nobody here owes you anything. People here help out of the kindness in their heart and the empathy they feel for the people now in difficult situations they, once upon a time, had to overcome. 

I suggest a new post with a different attitude, or hiring someone so you can scold them when you don't understand.

---

### Post by markcynt on 2009-04-22
Sorry about that kiridude.

---

### Post by shark1997 on 2009-04-22
He is right...

[B][SIZE="4"][SIZE="6"]THIS IS NOT CUSTOMER SERVICE.[/SIZE] WE DO WHAT WE WANT TO DO WHETHER YOU LIKE IT OR NOT.
SO INSTEAD OF CRITICIZING PEOPLE DO WHATEVER THEY TELL YOU TO DO. THEY DON'T HAVE TO DO THIS!!![/SIZE][/B]

---

### Post by markcynt on 2009-04-22
Alright guys, I'm sorry I responded the way I did. It's out of frustration from not understanding and no one being able to help me understand.

Having a bad day is all.

---

