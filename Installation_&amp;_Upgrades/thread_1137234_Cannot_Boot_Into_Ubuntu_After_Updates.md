---
title: "Cannot Boot Into Ubuntu After Updates"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by shgshs on 2009-04-25
Hello all, I'm new to this.

So I'm running Ubuntu 8.10 on a Sony Vaio VGN-SZ420n/b and the native os is Vista Business 32-bit. I partitioned the hard drive to dual boot Ubuntu. 

I tried to upgrade to 9.04 yesterday (April 24th) but I got an error, something like network, check your connection. But nothing was wrong with it. So I just said forget it, then it told me to do a partial upgrade, and the same problem happened. So I thought, forget it again. Then I had 700 or so updated to do, so I did them and they installed just fine, I rebooted, and now I get this:



Boot from (hd0,4) ext 3    3506a-79a-eb26-4e78-84bf-52f5f43b2cec
Starting up...
Loading, please wait...
Gave up waiting for root device.           Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root = (did the system wait for the right device?)

-Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/3506a79a-eb26-4e78-84bf-52f5f43b2cec does not exist. Dropping to a shell! 

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2 ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) help

Built-in commands:
_ _ _ _ _ _ _ _ _ _ _ _


.  :  [  [[  alias break cd chdir command continue echo eval exec
exit export false getopts hash help let local pud read readonly
return set shift source test times trap true type ulimit umask
umalias unset wait [  [[  ash awk basename cat chmod chrout chvt
clear amp cp cut deallocvt dumpkmap echo egrex eno expr false
fbset fdflush fgrep find grep hostname ifconfig ip kill lh loadfont
loudkmap ls mkdir mkfifo mknod mkswap mktemps more mount mv openvt
pidof printf ps pwd readlink reset rm rmdir sed setkeyoodes sh
sleep sort stat stay sync tail tee test touch tr true tty umount 
uname uniq wget yes


(initramfs)


Help?

---

### Post by shgshs on 2009-04-26
Bump.

---

### Post by Partyboi2 on 2009-04-27
Hi, maybe you have the wrong UUID listed in your grub menu.lst. Boot a ubuntu live cd and open a terminal (Applications>Accessories>Terminal)
then check what  partitions your ubuntu / is on
```
sudo fdisk -l
```then mount the partition with
```
sudo mount /dev/??? /media
```replace the ??? with the correct one from the output of fdisk -l eg 
```
sudo mount /dev/sda1 /media
```then type
```
sudo blkid
```this will output something like this:

```
dev/sda5: TYPE="swap" 
/dev/sda1: UUID="7093b79b-0c36-4fdf-a144-effefceb618d" TYPE="ext4" 
/dev/sda2: UUID="ff13903a-c958-47a0-8292-f482063226ee" TYPE="ext4" 
/dev/sda4: UUID="743f4e66-af27-4136-a9a5-d6751d631229" SEC_TYPE="ext2" TYPE="ext3" 
``` Take note of the UUID for your / partition 
then open your grub menu.lst
```
gksu gedit /media/boot/grub/menu.lst
``` Make sure that the UUID is the same as the output from the blkid command for your /  in these sections:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=[COLOR=Red]UUID=ff13903a-c958-47a0-8292-f482063226ee[/COLOR] ro
``````
## ## End Default Options ##
title        Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid        [COLOR=Red]ff13903a-c958-47a0-8292-f482063226ee[/COLOR]
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=[COLOR=Red]ff13903a-c958-47a0-8292-f482063226ee[/COLOR] ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

---

### Post by shgshs on 2009-04-27
I'll try that and let you know how it goes, thanks!

---

### Post by shgshs on 2009-04-27
Well I found it much too confusing, so I deleted the partition and installed 9.04. on it instead. 

So far everything is going well.

Thanks for your help anyways!

---

