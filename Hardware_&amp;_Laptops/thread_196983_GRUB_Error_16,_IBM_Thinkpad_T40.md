---
title: "GRUB Error 16, IBM Thinkpad T40"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Sanjay Jadhav on 2006-06-15
I facing same problem about not able boot ubuntu or xp, I installed ubuntu on IBM ThinkPad T40.

Installation went smoothly, I got ubuntu desktop where I got one icon "Install" I proceed further with selecting local/time and followed all steps, incase of partition I selected 2nd option i.e. largest free space for swap. 
So I had 3 partitions 1. Linux Swap
                           2. Linux
                           3. Windows XP

After completing all that installation, I reboot the machine without Live CD, and I start getting following problem.

GRUB loading, please wait
Error 16.

I tried following:
1. In BIOS boot sequence I try to with hdd0, hdd1, hdd2 alternately, but got above error.
2. Rebooted system with Live CD, and able start ubuntu and again followed "Install" steup up to partition, where I seen Linux Swap is default for boot. Here I don’t know how to change that boot, so I will get option of selecting OS.

Right now I have Lice CD only, even not winXP boot CD.

Please give me solution step-by-step.

So how should I resolve this issue?

---

### Post by marcantonio on 2006-06-15
Can you post your /boot/grub/menu.lst?  To get at it, boot the live cd and mount your root partition.  Assuming it's /dev/hda2 type:
```
mount /dev/hda2 /media/hda2
```
You might have to create /media/hda2.

Then post the contents of /media/hda2/boot/grub/menu.lst.

You'll probably have to reinstall grub.

---

### Post by martz on 2006-06-17
i'm having the same problem on the same type of computer... and i've done what you said...

```
sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2

```
then i changed directories to /media/hda2/boot/grub
but in there there is no must.lst
there is a menu.lst which contains (i'm typing this from another computer so i'm gonna skip parts by saying (etc) where i know it's not important:
```
title  Ubuntu, kernel (etc)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root /dev/hda2 ro quiet
splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu (etc) (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.15-23-386

title Unbuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

and that's all

---

### Post by marcantonio on 2006-06-17
Sorry there is no must.lst, it's menu.lst as you found.  That was a typo...

You may want to post the output of:
```
# fdisk -l /dev/hda
```
before you do this, but we can make a few assumptions and give it a try.

Let's say the you have one disk, /dev/hda, and it's got three partitions on it:
[LIST]
[*]/dev/hda1 is an NTFS Windows partition
[*]/dev/hda2 is your ext3 Ubuntu root
[*]/dev/hda3 is your swap space
[/LIST]
Now, to reinstall grub in this situation you would do the following:

1.  Boot off the LiveCD and mount /dev/hda2 on /media/hda2 as above.

2.  chroot to that filesystem:
```
# chroot /media/hda2
```

3.  Install grub to /dev/hda's MBR.  If hda2 is your Linux partition then grub will see it as (hd0,1).

To install grub:

1.  Run:
```
# grub
```

2.  Specify your root partition:
```
grub> root (hd0,1)
```

3.  Install grub to /dev/hda's MBR:
```
grub> setup (hd0)
```

That should be it.  Pop out the CD and reboot.  For more info on installing grub install grub-doc and run:
```
# info grub
```
It'll give you lots of good stuff.

Let me know how you make out.

Marc

---

### Post by Sanjay Jadhav on 2006-06-18
Better everone should look here because here all issues are resloved.

Martz : see if following links help you are not, if those are not helping you then I think you need to format ur disk because you file system is destroied.

[GRUB HOWTO]("https://wiki.ubuntu.com/GrubHowto")
[GRUB HOWTO Floopy]("https://wiki.ubuntu.com/GrubHowto/BootFloppy")


Or Best is you will get all kind of help under [Ubuntu Wiki]("https://wiki.ubuntu.com/TitleIndex").

---

