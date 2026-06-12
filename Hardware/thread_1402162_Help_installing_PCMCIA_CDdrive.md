---
title: "Help installing PCMCIA CDdrive"
date: 2010-02-08
forum: Hardware
---

### Post by thelockdude on 2010-02-08
I'm an absolute beginner to Linux. I've been browsing these forums for a few days to try to fix this problem on my own, but at this point, I think I need help, please.
 
I installed Ubuntu 9.10 on my old Sony Vaio laptop (6.5GB HD, 182MB RAM). This laptop uses the PCMCIA slot for the external CD drive. (I moved the HD to a different laptop to install Linux on it.)
 
Ubuntu installed fine. The PCMCIA slot works fine because I plugged a wireless LAN card into it and I was able to connect to the internet w/ no problem.
 
The CD Drive works fine when I plug it into a PCMCIA slot on a different laptop.
 
But the CD Drive won't work w/ Ubuntu.
 
The CD Drive came with some instructions for using with Linux. Here's what it said, and what I did (as root):
 
mkdir /mycdrom
mount /dev/hdf /mycdrom -t iso9660
 
here's what I got back:
mount: special device /dev/hdf does not exist
 
I don't know what to do from here - can anyone offer some advice??
 
Thanks
Dan

---

