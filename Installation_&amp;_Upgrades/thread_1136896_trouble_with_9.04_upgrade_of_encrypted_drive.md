---
title: "trouble with 9.04 upgrade of encrypted drive"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by freelsjd on 2009-04-25
I have an Intrepid laptop that was installed using the "encrypt entire drive" option when created under Intrepid.  I recently upgraded the system to Jaunty.  The new 2.6.28 kernel would not boot the encrypted drive.  I am able to boot under the previous kernel option in the grub menu.  Any ideas or solutions ?

menu.lst inserted below:

# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,0)/grub/splashimages/guitar.xpm.gz
#foreground = ffffff
#background = 555500
default 1
timeout 8
#fallback 1
#color light-blue/blue white/blue
# leave commented since this is the default
# to get a different splash image, change the soft link
# ln -sf splashimages/guitar.gz splash.xpm.gz
# and rerun update-grub
#

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=/dev/mapper/lvm-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.28-11-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.27-14-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-13-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.27-13-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.27-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-12-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.27-12-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.27-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.27-11-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-10-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.27-10-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.27-10-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-8-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.27-8-generic root=/dev/mapper/lvm-root ro quiet splash 
initrd        /initrd.img-2.6.27-8-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by freelsjd on 2009-04-25
bump

---

### Post by unutbu on 2009-04-25
I have a guess about what's wrong: The initrd.img-2.6.28-11-generic in the unencrypted boot partition (hd0,0) does not know how to unlock the luks encrypted partition.
The intrepid boot stanzas use initrd.img-2.6.27-14-generic, which was created by the Alternate Installer CD, which generated an initrd which knows how to unlock luks encrypted partitions.

This is a guess. I'm not familiar with this problem nor its solution.

Perhaps an easy way to test if my guess holds some truth would be to edit /boot/grub/menu.lst and change 

```
title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,0)
kernel /vmlinuz-2.6.28-11-generic root=/dev/mapper/lvm-root ro quiet splash
**initrd /initrd.img-2.6.28-11-generic**
quiet
```

to
```

title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,0)
kernel /vmlinuz-2.6.28-11-generic root=/dev/mapper/lvm-root ro quiet splash
**initrd /initrd.img-2.6.27-14-generic**
quiet
```

Yes, this is using Intrepid's initrd.img-2.6.27-14-generic to (hopefully) boot Jaunty.

If this allows you to successfully boot Jaunty, or at least gets you a bit farther in the boot process, then perhaps my guess is on the right track. If so, I or others might be able to help you build a custom initrd for Jaunty (that can unlock luks encrypted partitions).

If the above suggestion does not work, then it's easy to revert by simply changing the line in menu.lst back to 
```

initrd /initrd.img-2.6.28-11-generic
```

---

### Post by freelsjd on 2009-04-26
OK.  I think you are on the right track.  I placed the lines into the menu.lst as you suggested below.  This time, the system tried to boot and got to the point of asking me for the passphrase for my encrypted drive and it would not accept it.  I was able then to choose the previous kernel level and boot as normal.
 
initrd          /initrd.img-2.6.27-14-generic
#initrd         /initrd.img-2.6.28-11-generic

The upgrade from hardy to intrepid did not have this problem.  

Can you give advice on creating the initrd,img correctly ?

---

### Post by unutbu on 2009-04-26
I've been doing some research on how to fix this problem (see 
[https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)
[https://help.ubuntu.com/community/EncryptedFilesystemHowto4](https://help.ubuntu.com/community/EncryptedFilesystemHowto4), and 
[http://ubuntuforums.org/showthread.php?t=819059](http://ubuntuforums.org/showthread.php?t=819059)), and it's becoming clear to me
that I don't know enough to confidently guide you through this. 

I don't want to suggest any command like "sudo update-initramfs -k all -c" without knowing exactly what I'm doing, since I don't know if a mistake could make your encrypted partition totally unaccessible. 

Also, it bothers me that the Intrepid initrd got you to the point where you were asked for your passphrase, but that passphrase was not accepted. 

I'll continue to research this, but unless you can figure it out, we may have to wait for someone with more knowledge to help out.

Another option would be to boot with the Intrepid kernel, backup your data, and do a complete, fresh reinstall 9.04 from the Alternate Install CD...

---

### Post by freelsjd on 2009-04-26
I don't want to do a fresh install.  I quit doing that in 1994 when I dropped Windows-3.1 in favor of linux in the first place.  We can figure this out.

I issued the following command while booted under 2.6.27-14-generic as root while running Jaunty:

update-initramfs -k 2.6.28-11-generic -c -v

This created a new initrd.img-2.6.28-11-generic in /boot.

I then tried to boot from the new kernel, and it did the same thing.  It runs up though grub, but instead of asking me for the encrypted-drive passphrase, I just get a blank screen.  I actually have to turn off the laptop and back on to get back the boot up sequence.

I have my notes at my work office on how I created this encrypted drive in the first place.  I will look through that tomorrow and see if I can figure out from there.

I really appreciate your help, and if you can think of anything else, please let me know.  I think this is looking more and more like a serious bug worth reporting.

---

### Post by freelsjd on 2009-04-27
I have corrected this problem by removing the "splash" option from the grub entries.  I also removed this from defoptions.  All works as it is supposed to for me now.

The splash option is an unnecessary nice feature, but for only the few seconds of bootup, it is not worth the hassle to fix it for me right now.

---

### Post by unutbu on 2009-04-27
Wow. Congratulations. Was removing splash the only thing required, or was update-initramfs also needed?

---

### Post by DocNielsen on 2009-04-30
Could you verify that you can boot 2.6.28-11-generic and mount a luks partition with it? I cannot. 

If i add the parameters to crypttab, the kernel simply stops mid boot. 
If i try it manually, ps axu shows cryptsetup as DL and modprobe for sha256 and sha1 is D.

[EDIT]
Never mind - it's via-padlock thats broken.

echo "alias sha256 sha256_generic" >> /etc/modprobe.d/aliases.conf

---

### Post by unutbu on 2009-05-03
Hi DanielBuus, welcome to the forums.
Here are instructions on how to encrypt your entire hard drive (minus /boot):

[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)

---

### Post by joebaker on 2009-05-08
Well, I've just backed up my home directory to an encrypted removable drive.
  I am not very comfortable about this upgrade. from 8.10 to 9.04.  I too have the Luks Encrypted LVM setup for everything but /boot.

---

