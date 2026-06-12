---
title: "use ubuntu grub to boot Fedora Core 3"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by ckr on 2005-01-22
Hi all,

I'm setting up a multiboot enviroment.  At the moment I have ubuntu, winxp pro, and winxp64 installed and running great booting with grub.  I also installed Fedora Core 3 without a hitch, choosing to not install a bootloader thinking ubuntu's grub could do the trick.  So far, I can't quite get the "stanza" for Fedora working.  I get error messages that the partition cannot be mounted etc.  I can access the partition once in ubuntu just fine.  Although I've changed it several times, this is the current status of my Fedora section in menu.lst:

title Fedora Core 3
root  (hd0,3)
kernel   /vmlinuz-2.6.9-1.667 ro root=LABEL=/ rhgb quiet
initrd     /initrd-2.6.9-1.667.img
savedefault
boot

Like I said I've tried many different combos so far, this is just where I stand at the moment.

Is there anyone out there who successfully boots FC3 with the default grub that comes with Warty?  If so, could you please post how the menu.lst section is setup?

Thanks,

Brian.

---

### Post by xalphas on 2005-01-23
Hi

i haven't tried a dual boot with ubuntu and fedora. Only xp and ubuntu with succes. I am also using fedora 3 on my other box. Anyway just an idea below to add to grub of ubuntu. Again just thinking while writing. Haven't tested this before. 

title Fedora Core 
	root (hd0,3)
	kernel /vmlinuz-2.6.9-1.667 ro root=/dev/VolGroup00/LogVol00 vga=788 selinux=0
	initrd /initrd-2.6.9-1.667.img

hope it works.

---

### Post by piedamaro on 2005-01-23
I have fedora + ubuntu + xp ATM, this is my grub.conf (fedora root is on sda2 as well as grub):
> title Fedora Core (2.6.9-1.667.inotify.0.14smp)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.9-1.667.inotify.0.14smp ro root=/dev/sda2 rhgb exec-shield=0 quiet acpi=force
        initrd /boot/initrd-2.6.9-1.667.inotify.0.14smp.img 
You need to know the number of the partition where grub resides, where fedora resides, and you have to know exactly the name and the path of your kernel and initrd image.
:D

---

### Post by ckr on 2005-01-23
Hi,

Grub is in the mbr of hd0.  Fedora Core is installed on hd0,3.  I did not set up a separate partition for /boot.  I think my next attempt will be.

title     Fedora Core 3
root (hd0,3)
kernel    /boot/vmlinuz-2.6.9-1.667 ro root=/dev/hdc3  rhgb quiet
initrd      /boot/initrd-2.6.9-1.667.img


I'll go try it now.  Thanks for your advice.  =D> 

Brian

---

### Post by ckr on 2005-01-23
Nope, still doen't work.  :???: 
Gives me a "can't mount partition error 0x82" or something like that.  Anyone out there have any ideas?

Thanks.

Brian

---

### Post by akurashy on 2005-01-23
try

title		Fedora Core 3
root		(hd0,3)
kernel		kernel
initrd		int
savedefault
boot
chainloader	+1

dunno if it will work (just trying to help :D)

---

### Post by ckr on 2005-01-24
ok, I'm getting a bit closer now.   :confused: 

I'm now at 

root (hd0,2)
kernel   /boot/vmlinuz-2.6.9-1.667 ro root=/dev/hdc3 rhgb exed-shield=0 quiet
acpi=force
initrd     /boot/initrd-2.6.9-1.667.img


This boots up until checking the root filesystem where it errors out.  It says:

checking root filesystem
fsck.ext3:Unable to resolve 'LABEL=/1'
An error occured during the file system check
Dropping you to a shell; the sytem will reboot...

It then dropps to cli.  I've run fsck.ext3 on the partition and it checks out ok.  Running fsck by itself returns the same 'LABEL=/1' error.  Like I've mentioned before, I'm able to mount and view the file system from unbuntu just fine.  Any thoughts?

Brian.

---

### Post by piedamaro on 2005-01-24
You can omit exed-shield=0 acpi=force. That was _my_ configuration sorry :)
The best attemp was:
title Fedora Core 3
root (hd0,3)
kernel /boot/vmlinuz-2.6.9-1.667 ro root=/dev/hdc3 rhgb quiet
initrd /boot/initrd-2.6.9-1.667.img

Maybe your problem is that, since your root is on hdc3, in grub language it's tranlsated to (hd2,2). (grubs counts devices and partitions starting at zero)
You could try also grub command line completion: when in front of the grub prompt at startup, highlight the row where you specify your kernel, hit E, and then you are in edit mode. If you use <tab> you have command line completion! Maybe this way you can see exactlywhere  your kernel is.
Let me know how it went :)

---

### Post by ckr on 2005-01-25
Using tab for line completion did not work.

I believe that at one point I may have had a label of "1" on the fedora partition, hence it's mention of unable to resolve "LABEL=/1".  I've tried to put the label back in but it still doesn't boot.

I'm not sure why the linuxes are seeing the hard drive as hdc.  It is the primary channel of the primary ide controller, but that's how Ubuntu and Fedora's anaconda reported it.  So although one would think that hdc3 would be hd2,2, it's not on this computer. :!: 

Thanks for the help.

Brian.

---

### Post by ckr on 2005-01-25
Just a quick note that I found the "LABEL" problem.  It was a listing in the fedora fstab file.  I fixed that, but now I get a similar error when checking the root filesytem,"e2fsck: Cannot continue".  It then drops out to a filesystem recovery cli.

Brian.

---

### Post by piedamaro on 2005-01-25
[QUOTE=ckr]Just a quick note that I found the "LABEL" problem.  It was a listing in the fedora fstab file.  I fixed that, but now I get a similar error when checking the root filesytem,"e2fsck: Cannot continue".  It then drops out to a filesystem recovery cli.

Brian.[/QUOTE]
 if it doesn't work from the command line (like hard sik not found or similar), it will not boot. Try a different hd parameter.

---

### Post by ckr on 2005-01-26
I finally got it to boot! :-P 

When Fedora's fstab was set up, it used the partition labels instead of the /dev locations.  Once I changed the / and swap partitions to /dev/hdc3 and swap to /dev/hdc4 it booted fine.

For the record, here's the grub listing that worked.

Title         Fedora Core 3
root         (hd0,2)
kernel      /boot/vmlinuz-2.6.9-1.667  ro  root=/dev/hdc3 rhgb quiet
initrd        /boot/initrd-2.6.9-1.667.img

Thanks to all those that helped. :smile: 

Brian.

---

