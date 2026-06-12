---
title: "Connecting to a DLink DNS-323 NAS Device"
date: 2013-08-20
forum: Hardware
---

### Post by sean7 on 2013-08-20
I just loaded the latest stable Ubuntu.  This is my first install of linux and i am pretty excited.  The Ubuntu install went fine.  The problem is that the whole reason i am using Ubuntu is to build simple client desktop PC that can connect to a DLink DNS-323 that is on my network in order to view photos from the NAS.  I can see the NAS listed in linux but when i try to connect to it and put in the username and password, it will not connect.  The login screen just keeps popping up over and over.

I searched the forums and see a bunch of posts about how to try and mount the DNS-323 but honestly it seems a little over my head!  Can anyone give a new Ubuntu user some help on how to connect to the NAS folder?  The NAS has a static IP, and a username with password that work just fine from Windows machines.

-Sean

---

### Post by gordintoronto on 2013-08-20
I assume you mean, you installed Ubuntu 13.04? And you run File Manager (Nautilus) and click on Browse Network, and the NAS shows up? Then you double-click on it, you're asked for a username and password, and when you enter them, you are asked again?

---

### Post by sean7 on 2013-08-21
Well yes that all seems right except that I have installed the latest extended support Ubuntu. 12.04.

I also downloaded the 200 or so updates but still no luck. Any advice?

---

### Post by Morbius1 on 2013-08-21
There's a confluence of isses at work here I think. One problem is the DLink and it's use of an outdated samba server. The other problem is a change in security levels used by the Linux kernel to accommodate the modern Windows OS.

You can make a system wide settings change to accommodate the DLink but you risk not being able to access a share on your WIndows box - although Windows can auto-negotiate if set that way:

Edit smb.conf as gksu:
```
gksu gedit /etc/samba/smb.conf
```
Add these lines - right under the workgroup line:
```
client lanman auth = yes
client ntlm auth = yes
client ntlmv2 auth = no                      

```
Then try to access the DLink again through Nautilus.

A better way - at least a way to narrow this to only the DLink - is to access it manually:

First install the following package:
```
sudo apt-get install cifs-utils
```
And create the mount point:
```
sudo mkdir /media/DNS323
```
Then run the following command:
```
sudo mount -t cifs //192.168.0.100/Volume_1/share-name /media/DNS323 -o   guest,uid=1000,nounix,sec=ntlm,iocharset=utf8,file_mode=0777,dir_mode=0777
```
[COLOR=#0000cd]* Change 192.168.0.100, Volume_1, and share-name to their correct values for your 323 device.*[/COLOR]

If your share is password protected it get's even longer:
```
sudo mount -t cifs //192.168.0.100/Volume_1/share-name  /media/DNS323 -o   username=user_name,password=secret,uid=1000,nounix,sec=ntlm,iocharset=utf8,file_mode=0777,dir_mode=0777
```
[COLOR=#0000cd]*Change user_name and secret to their correct values for the 323 device.*[/COLOR]

---

