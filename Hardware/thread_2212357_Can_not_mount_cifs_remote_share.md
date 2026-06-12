---
title: "Can not mount cifs remote share"
date: 2014-03-20
forum: Hardware
---

### Post by Victor_Cotner on 2014-03-20
I am having a problem connecting via Ubuntu Server to a cifs drive attached the USB port on my router.  The router automatically appends "(A1)" to the end of the drive name and I think this is my problem.  My /etc/fstab looks like this...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--server--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=561853ab-01fb-4ad3-9154-ed24cd28b9f4 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--server--vg-swap_1 none            swap    sw              0       0
_//192.168.1.1/MediaDrive(A1) /media/public cifs guest 0 0_
~
I have underlined what i believe to be the problem.  when i the "sudo mount -a" command is issued i receive the following error...
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I can successfully map this drive in Windows.

Any and all help would be appreciated.
Thanks in advance...

Vic

---

### Post by steeldriver on 2014-03-20
Hello and welcome to the forums

You could try replacing the parentheses with their octal escape sequences i.e.

```
//192.168.1.1/MediaDrive**\050**A1**\051** /media/public ...
```

I know I've had to do that for spaces (where fyi the octal sequence is \040)

---

### Post by Victor_Cotner on 2014-03-20
I have tried what you suggested... it looks like this...
//192.168.1.1/MediaDrive\050A\051 /media/public cifs guest 0 0

i get the same error  :( :confused:


And thanks for welcoming me to the forums.

I also tried sudo mount -t cifs //192.168.1.1\050A1\051 /media/public
received the same 22 error

---

### Post by Victor_Cotner on 2014-03-21
I have solved this problem with the following line in my /etc/fstab

//192.168.1.1/MediaDrive(A1)                             /media/public     cifs    sec=ntlm,uid=1000,gid=1000,guest,_netdev     0       0

:P
Thanks for your help Steeler

---

