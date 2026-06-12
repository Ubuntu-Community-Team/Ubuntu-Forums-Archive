---
title: "Toshiba Satellite A105-S4164 Internal Multi Card Reader"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by toddwbucy on 2007-06-03
I hope someone here can help as this problem has had me stumped for a while.  I am a relative and only slightly informed n00b so please have patience with me.  
I have a Toshiba Satellite A105-S4164 with an internal multi-card reader.  I currently have  Ubuntu Studio with Kubuntu desktop installed and am running with the 2.6.20-16 low latency Kernel.  I have been unable to mount my 128MB FujiFilm XD-picture Card.  

the out put from lspci is as follows:
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

output from dmesg when card is inserted.
[19100.006000] tifm0 : demand removing card from socket 0:0
[19218.936000] tifm_core: SmartMedia/xD card detected in socket 0:0

As you can see the card and reader are recognized by the system.  My problem is that I can't (or don't know how to) mount the card. I followed the instruction from the following bug report [https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/6262](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/6262).  But it did not work for me.  I also tried editing my fstab but this did not work either.

current fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e530da8a-4540-415a-934e-6ff26cd8387b /               reiserfs notail          0       1
# /dev/sda3
UUID=9a29aada-0fd6-422a-90d0-6300e9928c4c /home           reiserfs defaults        0       2
# /dev/sda2
UUID=b7689728-2b11-44b9-9678-8d8b188851e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

#media card reader
/dev/sdd1               /media/card_reader      auto   users,noauto,rw 0 0

however when I try manually mount I get the following error
$ mount /media/card_reader/
[mntent]: line 14 in /etc/fstab is bad
mount: can't find /media/card_reader in /etc/fstab or /etc/mtab

I have had some suggestions from my local linux users group (SATLUG) that the problem might be my mtab but have not been able to find it as of yet.

Current copy of my mtab
/dev/sda1 / reiserfs rw,notail 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-lowlatency/volatile tmpfs rw 0 0
/dev/sda3 /home reiserfs rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

If anyone can give me some advice or guidenc on this problem I would greatly appreciate it 

Thank you 
Todd

---

### Post by julianmag on 2008-05-11
Did you solve the problem? 

I've the same problem on my Toshiba laptop.

Julian

---

