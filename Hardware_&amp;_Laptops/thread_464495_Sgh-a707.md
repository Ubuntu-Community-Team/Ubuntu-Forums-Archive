---
title: "Sgh-a707"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by gabx84 on 2007-06-04
Hey,

I just recently bought a phone that is a AT&T  SAMSUNG SGH-A707 and with it I have a 1 gig Sandisk memory card.  
Well it works fine hooking it up to windows, you put the usb in and it works like a usb drive.

But on Ubuntu the phone wasn't read at all, it would pop up an import folders option, but it would not recognize the phone as any camera (/proc/bus/usb/devices would say there was no driver), so I followed these directions in a hope of setting up some sort of connection:

[http://bitubique.com/content/view/26/42/](http://bitubique.com/content/view/26/42/)

I disabled acm, and changed the phone's driver to usbfs.  This somewhat worked since now when I plug in my phone I can get files from the phone to the computer... but its because Ubuntu still reads it as a camera and tries to take pictures off, but it now reads the phone as a Samsung YH-999  Portable Media Center.  I don't mind this too much (other than the obvious error which will probably bite me in the butt later), but I want to put files onto the phone and I can not seem to make the process work that way.  

Also, the driver goes through stages every time I plug it in at first, when the window pops up asking if I want to take photos off, the driver reads as such:

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=5a0f Rev= 0.00
S:  Manufacturer=SAMSUNG MTP Device
S:  Product=SGH-A707
S:  SerialNumber=A355458011990620
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=usbserial_generic  <-- Here
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=96ms

Then, when you ask it to take files from the "camera", it reads as: 

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=5a0f Rev= 0.00
S:  Manufacturer=SAMSUNG MTP Device
S:  Product=SGH-A707
S:  SerialNumber=A355458011990620
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=usbfs             <----- Here
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=96ms
 
Then last, after the files transfer, it reads as:

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=5a0f Rev= 0.00
S:  Manufacturer=SAMSUNG MTP Device
S:  Product=SGH-A707
S:  SerialNumber=A355458011990620
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)                     <------ Here
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=96ms

And it will not be recognized from there out.  Any help would be greatly appreciated as I don't have windows on my comp anymore and I really want to transfer files to my phone since I've never actually had an mp3 player so I got a phone/mp3 player this time.  Oh, and this is my first time on the forum as a registered user so.... hi.

---

### Post by gabx84 on 2007-06-04
I guess, more specifically since the file transfer works fine with Ubuntu thinking the phone is the Samsung camera, is there a way to "mount" the camera so that I can write to it, mount displays:

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/disk/by-uuid/4611eff7-f12d-4035-80ca-75c88636d8ef on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda4 on /media/sda3 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

