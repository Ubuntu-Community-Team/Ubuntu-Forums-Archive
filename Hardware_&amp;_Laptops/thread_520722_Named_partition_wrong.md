---
title: "Named partition wrong"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by lunamystry on 2007-08-08
I am stupid!!!

I finally got around to creating a home partition for my PC. I found this guide:

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

I followed it and everything was great but it took a while. Before i go on, let me say that i was using copy and paste into terminal or text editor if i needed to change something. Okay so I waited for a long while for my home to be moved and backed up i think. Then when it was done I was suppose to enter this:

sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

which took me to the nano text editor. then I entered 

/dev/hda7 /home ext3 nodev,nosuid 0 2

which i did. The problem is that my partition is /dev/sda3 not /hda7 so now i would like to know if i can correct this stupid mistake. 

I tried to recover my system and that did not work, I still get an error that /hda7 does not exist when I try to boot. I cant access my folders anymore. Is there nothing i can Do?:-(

---

### Post by lunamystry on 2007-08-08
:(I try to recover my files and this happens:

ubuntu@ubuntu:~$ sudo mkdir /recovery
mkdir: cannot create directory `/recovery': File exists
ubuntu@ubuntu:~$  sudo mount -t ext3 /dev/sda1 /recovery
ubuntu@ubuntu:~$  sudo cp -R /recovery/home_backup /recovery/home
cp: cannot create special file `/recovery/home/home_backup/lunamystry/.gdesklets/sockets/%3A0.0': File exists

Maybe my title is bad. :confused::(

---

