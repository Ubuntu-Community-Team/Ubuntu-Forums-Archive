---
title: "Mount point does not exist"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by MacUsers on 2009-06-01
Greeting Guys,

I get this annoying message every time I try to mount  something from fstab. This is what I have in the "fstab":

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
UUID=20978c85-1c5b-48c3-a05e-6a33324c7a09 /               ext3    relatime,errors=remount-ro 0       1
UUID=2f19ba87-58b1-4add-bec2-a25aff822e7b /backUP         ext3    relatime        0       2
UUID=6ee9cf41-b1ab-46a4-ac32-4b7fbfed2727 /boot           ext3    relatime        0       2
UUID=77b6163f-3e30-488e-95e6-e9c2acd85674 /usr            ext3    relatime        0       2
UUID=eacc241f-312e-4cd3-8548-22229d2637c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Mount nMedia from TimeCapsule
//10.0.11.53/DataCenter/nMedia /home/santanu/nMedia   cifs   credentials=/root/.cifs_passwd,iocharset=utf8      0 0
```Every mount point/directory does exist and it actually mounts everything perfectly but the error message keeps coming back.
```
root@htpc:/# mount -aF
mount: mount point  does not exist
```Any idea how can I get rid of this error message? Thanks in advance. Cheers!!!

---

### Post by lensman3 on 2009-06-01
Do the "df" command from a text window.  Then try and mount each by itself.  The file /etc/mtab is a list of all currently mounted file systems.  See if one is missing in mtab versus /etc/fstab.

My guess is the last one with:
  //10.0.11.53/DataCenter/nMedia

The 10.0.11.53 IP number is a non-routable IP on the Internet.  If you happen to be at a University then the school could have 10.0.11.xx as a valid IP within the domain of the school.  

Can you "ping 10.0.11.53" and get responses?   

Recall that you can mount filesystems using "mount /", "mount /boot" and so on.  The swap should already be  mounted (or it better be).  The /etc/mtab file will tell you what is already mounted.

Good luck.

---

### Post by MacUsers on 2009-06-02
Thanks lensman for your input; appreciate it.

It's my home network (though I work for University) and 10.0.11.53 is the TimeCapsule, which is not world-accessible, but ping'able from intranet:

```
root@htpc:~# ping 10.0.11.53
PING 10.0.11.53 (10.0.11.53) 56(84) bytes of data.
64 bytes from 10.0.11.53: icmp_seq=1 ttl=255 time=0.143 ms
64 bytes from 10.0.11.53: icmp_seq=2 ttl=255 time=0.143 ms
64 bytes from 10.0.11.53: icmp_seq=3 ttl=255 time=0.143 ms
^C
--- 10.0.11.53 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4996ms
rtt min/avg/max/mdev = 0.116/0.135/0.143/0.017 ms
```As far as I see, 10.0.11.53/DataCenter is doing just fine here. I can access files from there without having any problem. /etc/mtab is just the one as it should be:

```
root@htpc:~# cat /etc/mtab 
/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda5 /backUP ext3 rw,relatime 0 0
/dev/sda2 /boot ext3 rw,relatime 0 0
/dev/sda7 /usr ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
//10.0.11.53/DataCenter/nMedia /home/sans/nMedia cifs rw,mand 0 0
```Only possible missing thing would be the "/dev/fd0" line in the /etc/fstab as I don't have any floppy drive physically attached but I don't think it matters. Commenting that line out didn't make things any better as well. Xan't see any thing in the /var/log/message or dmesg either. Any other thought? 

Thanks for your time. Cheers!!!

---

