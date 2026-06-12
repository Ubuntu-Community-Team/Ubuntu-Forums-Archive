---
title: "root priveleges to Nvidia Forceware driver"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by gordong11 on 2006-03-29
Hi,

I downloaded Nvidia Forceware drivers to my desktop, but when U run the command:

Sh ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run

I get an error must be run as root

When I type:

Sudo ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run

I get bash, no file

Can anyone help please? ](*,) 

Thanks

---

### Post by endersshadow on 2006-03-29
[QUOTE=gordong11]Hi,

I downloaded Nvidia Forceware drivers to my desktop, but when U run the command:

Sh ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run

I get an error must be run as root

When I type:

Sudo ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run

I get bash, no file

Can anyone help please? ](*,) 

Thanks[/QUOTE]

Can we get a printout from your console?

Also, don't capitalize Sudo or Sh, make them sudo and/or sh...it's important.

---

### Post by gordong11 on 2006-03-29
admin@ubuntu:~$ sudo ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run
Password:
sudo: /home/admin/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run: command not found
admin@ubuntu:~$


ALSO

sudo: /home/admin/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run: command not found
admin@ubuntu:~$ sh ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run
Verifying archive integrity...OK
Uncompressing NVIDIA nForce drivers for Linux-x86 1.0-0310..........................................................................................................................................................................................................................................................................
nforce-installer: Error opening log file '/var/log/nvidia-nforce-installer.log' for writing (Permission denied); disabling logging.
admin@ubuntu:~$


THANAKS

---

### Post by endersshadow on 2006-03-29
Try this:

```
sudo sh ~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1.run
```

---

### Post by gordong11 on 2006-03-29
WOOOOOOOOOOOOOOOT Thanks

IT worked.....bashed my system so  needed to re-install ubuntu. I tries too many lother things to my shell.

Thanks so much!!  :D

---

### Post by gordong11 on 2006-03-29
Well Thanks I finally got it to work, but the install fails due incompatible kernel. I need serious help. but I dont know what to do next.

---

