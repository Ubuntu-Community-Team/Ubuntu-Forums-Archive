---
title: "How to Assign rpool as Boot Drive in ZFS?"
date: 2020-08-13
forum: Hardware
---

### Post by chilewskirbuu on 2020-08-13
I added a third HDD and it ressigned my boot drive from sda6 to sda1, have loaded from grub Rescue and used:

[https://askubuntu.com/questions/1225751/recovering-a-borked-grub-with-a-ubuntu-19-10-zfs-root-filesystem#:~:text=Recovering%20a%20borked%20GRUB%20with%20a%20Ubuntu%2019.10,options%29%2C%20booting%20in%20the%20System%20Setup%20by%20default](https://askubuntu.com/questions/1225751/recovering-a-borked-grub-with-a-ubuntu-19-10-zfs-root-filesystem#:~:text=Recovering%20a%20borked%20GRUB%20with%20a%20Ubuntu%2019.10,options%29%2C%20booting%20in%20the%20System%20Setup%20by%20default).

set root=(hd0,gptXXX)
linux /BOOT/ubuntu_YYY/@/vmlinuz root=ZFS=rpool/ROOT/ubuntu_YYY boot=zfs
initrd /BOOT/ubuntu_YYY/@/initrd.img
boot

I can Boot into OS put I still Get Path of /COW error :)
and when i restart goes back to Grub Rescue so Boot drive isnt sticking goes back to sda1

I am having a bit of trouble understanding these zpool commands on how assign my sda6 rpool to main boot drive along the lines somewhere the Third HDD reassigned it to sda1 i think. :)
Is this what i am aiming for is to Assign rpool on sda6 to root boot? Because it seems to have assigned it to sda1 Fat32

zpool status
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 0 days 00:00:02 with 0 errors on Sun May 10 00:24:03 2020
config:

    NAME        STATE     READ WRITE CKSUM
    bpool       ONLINE       0     0     0
      sda6      ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: DEGRADED
status: One or more devices has experienced an error resulting in data
    corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
    entire pool from backup.
   see: [http://zfsonlinux.org/msg/ZFS-8000-8A](http://zfsonlinux.org/msg/ZFS-8000-8A)
  scan: scrub repaired 0B in 0 days 00:06:57 with 1 errors on Sun May 10 00:30:59 2020
config:

    NAME        STATE     READ WRITE CKSUM
    rpool       DEGRADED     0     0     0
      sda7      DEGRADED     0     0     0  too many errors
errors: List of errors unavailable: permission denied

errors: 1 data errors, use '-v' for a list

says its using sda6 atm but when i reboot it doesnt stick to sda6 it goes back to sda1 in GRUB rescue mode in which i have to renter ZFS commands to boot form sda6.

I tried also which for some reason temporarily worked until i updated:
[https://community.linuxmint.com/tutorial/view/245](https://community.linuxmint.com/tutorial/view/245)


shell to root su -

fdisk -l

note the linux partition, eg /dev/sda4

then do as you said above

mount /dev/sda4 /mnt  (sda1 in my case worked temp)

grub-install --root-directory=/mnt/ /dev/sda

but in my travels i realized Hrm this is not for ZFS :)

I need the Replicant Version Of ZFS commands for this i think would work if any has offhand fast I neeed Cheatcode ty <3
Thank you So i need some help on how to Mount ZFS rpool as my sda6 boot <3
Will continue to try to understand the ZFS system in the Meanwhile thanks!!!

---

### Post by chilewskirbuu on 2020-08-15
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Added resume to /etc/initramfs-tools/conf.d with resume=UUID=XXX
# update-initramfs -u
Works but 
Update-grub     still Path of /COW

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass)

sudo dpkg-reconfigure grub-pc
for command:
resume=UUID=XXX shows up but still get Path of /COW?
what to enter in this configure tool? so grub can update?

---

### Post by chilewskirbuu on 2020-08-16
[https://gist.github.com/ninetyfivenorth/76bc629b9c83ce75b28d0b9790c1aa79](https://gist.github.com/ninetyfivenorth/76bc629b9c83ce75b28d0b9790c1aa79)

mount
parted -l
fdisk /dev/sda

sudo -i

mkdir /mnt
mount /dev/sda1 /mnt
cd /mnt
ls -l


grub-install --recheck --root-directory=/mnt /dev/sda  OH REALLY?

grub-install --recheck --root-directory=/mnt /dev/sda --force

this forces assignment of sda to root

Problem:
I can assign Root Grub to sda1 where the boot/grub is works but Then i get error to boot into ZFS gave to reassign root as sda6 where rpool is how to fix hmm.
set root=(hd0,msdos1) can find grub here.
set prefix=(hd0,msdos1)/boot/grub
linux /boot/vmlinuz root=/dev/sda ro
initrd /boot/initrd.img

but this cant find vmlinuz img or initrd img so wont boot.

set root=(hd0,msdos6)
linux /BOOT/ubuntu_XXX/@/vmlinuz root=ZFS=rpool/ROOT/ubuntu_XXX boot=zfs
initrd /BOOT/ubuntu_XXX/@/initrd.img

This boots to ZFS but cant find grub now lol :( where am i caught in this mouse trap HAAAALP!
So why grub in /dev/sda1 hd0,msdos1 /boot/grub
but vmlinuz img and initrd are in rpool/BOOT/ubuntu_XXX
I Can't install Grub to sda6 rpool because cant read because zfs Hrm.

---

### Post by chilewskirbuu on 2020-08-17
Update to My insanity:
......
Removed everything i did put grub back to normal and initramfs

/var/lib/dpkg/

added folders 
alternatives info updates
why i dont understand
This fixes alll my Errors except updating GRUB kernel 
SO what NEXT HMM SEE?

---

### Post by chilewskirbuu on 2020-08-22
I ended up reinstalling ,partitions became some type of a problem had about 15 of them drno why just have 3 basic partitions Ext 4 without ZFS till i get better :) I think my base partitions was the problem i didn't do auto partition install and somehow made some extra unnecessary partitions which created some kind of conflict with the Main partition not being set as boot drive also through Bios.
Summary:


set preifx =(hd0,XXX)()    
set root=(hd0,XXX)
linux /BOOT/ubuntu_YYY/@/vmlinuz root=ZFS=rpool/ROOT/ubuntu_YYY boot=zfs
initrd /BOOT/ubuntu_YYY/@/initrd.img
boot


set prefix=(hd0,msdos1)/boot
set root=(hd0,msdos6)
linux /BOOT/ubuntu_XXX/@/vmlinuz root=ZFS=rpool/ROOT/ubuntu_XXX boot=zfs
initrd /BOOT/ubuntu_XXX/@/INITRD.IMG


This settings worked for me to boot but i couldnt get grub update to stick because it kept identifying my sda1 as fat 32 then sda6 as ZFS i couldnt quite figure out to to get this setup :P

---

### Post by sigo2 on 2021-06-08
it is tricky. debconf cannot fix many hairy ZFS situations IMHO

---

### Post by sigo2 on 2021-06-08
I noted that one cannot boot Ubu-ZFS when another harddrive with Ubu-ZFS is plugged into a SATA socket, because the pool names clash or something. goes "cannot import pool" on me.

Didier mentioned this:

> [h=2]Multiple machines[/h]  Something that isn&#8217;t really well supported nowdays was multiple  OpenZFS installations on the same machines. This isn&#8217;t fully complete  yet (you can&#8217;t have 2 pools of the same name, like rpool or bpool),  but if you install manually a secondary machine on the same pools or  different ones (with different names), this is handled by ZSys and our  grub menu!



---

