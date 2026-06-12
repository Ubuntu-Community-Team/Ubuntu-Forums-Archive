---
title: "Sansa 8gig mp3 player wont mount..it used to though.."
date: 2009-12-12
forum: Hardware
---

### Post by binskipy2u on 2009-12-12
ive read every post on here after searching for Sansa.. nothing works.. is this a recurring problem? dont want to have to dual boot windows just to use my mp3 player.. it worked under ubuntu fine.. ubuntu 9.10
i'm using kubuntu 9.10..  please dont tell me there's a list of 20things to do just to get a simple mp3 player working.. when it used to work fine.. some one tell me what i'm doing wrong???
its annoying, i have like 2 gigs of songs, when i have more and cant' put them on there..
thanks

---

### Post by jacobs444 on 2009-12-12
in terminal what is the output of these commands:

lsusb

mount

---

### Post by binskipy2u on 2009-12-12
lsusb***

lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a48:5014 I/O Interconnect Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 0781:7434 SanDisk Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 005 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
***************
**the one that says sandisk corp, that's it.. but its not showing up in mounted devices in any way at all (i have it plugged in now)

mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /MyStuff type ext3 (rw)
/dev/sda7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
***************

don't see it on there i dont believe..

---

### Post by jacobs444 on 2009-12-12
Bus 001 Device 012: ID 0781:7434 SanDisk Corp. thats it, hold on.

---

### Post by binskipy2u on 2009-12-12
any idea why it would work in ubuntu 9.10 and not kubuntu 9.10?

---

### Post by jacobs444 on 2009-12-12
do you have any other drives in the computer? if not then try this in terminal.

sudo mkdir /media/sansa
sudo mount -t vfat /dev/sdb1 /media/sansa (if you get no errors then proceed to the next step.)
nautilus /media/sansa (if this gives an only root can do that error, then do)
sudo chmod 770 /media/sansa

---

### Post by jacobs444 on 2009-12-12
yeah, but just speculation that kde is buggier than gnome. Thats all I could come up with.

---

### Post by binskipy2u on 2009-12-12
mount: special device /dev/sdb1 does not exist

what gives? its plugged in... darn this is annoying

i see alot of sansa issues in here... isnt sansa mp3 just an external storage device/media device like anything else? whats so hard about kubuntu doing this?

---

### Post by jacobs444 on 2009-12-12
thats all I know to do, I wish I knew some more tricks, but thats the only way I know to force it. Just for stuffs and googles, you did check in computer, like gnome has places>computer.

---

### Post by jacobs444 on 2009-12-12
you could try to run gparted, and see if it is recognized in the drop down menu on the right hand top side.

System>Admin>gparted

if not listed then do 
sudo apt-get install gparted.

if drive is listed as sdx/sdy whatever, then replace the /dev/sdb1 with the /dev/sdx1 /dev/sdy1 respectively in the command issued earlier. Otherwise, try another usb port, and that is the last of my knowledge.

---

### Post by binskipy2u on 2009-12-12
nothing.. just the hard drive.. that's it.. i know it works, it plays, i use it, all the time.. i charged it long ago, with ubuntu 9.10.. but i plugged it in, says connected (doesn't say charging, thought it said that before though) but gparted ONLY shows the 500gig hd, no others at all.. even when i refresh devices..
this is damn annoying

there's no reason linux in this day and age, can NOT see a simple usb device plugged in across the same distro but with a different Window Manager..

---

### Post by jacobs444 on 2009-12-12
don't blame linux, linux sees the device when using lsusb. Don't give up, personally i have had many problems with the sansa's. It is them not linux. I hope you get this issue resolved, yet you are one more person to whom I must ask, How much did you pay for linux?


Oh, and it sounds like specifically a kde problem, so why not try the kde forums if there are any, this is why I recommend gnome. You know you can have both gnome and KDE installed at the same time and switch between them. They both have strengths and weaknesses, and I sincerely hope you have better luck in the future.

---

### Post by binskipy2u on 2009-12-12
its just annoying..something that works then suddenly doesnt.. just a pain.. no biggie.. thanks for all your help

---

### Post by binskipy2u on 2009-12-12
fixed it.. found this post from jan 2007...
*********************

I believe that the sansa cannot see files transfered via mtp(windows protocol)
when connected in msc(mass storage) mode.

i never went into usb settings, it always just "worked" in ubuntu..
i changed it to MSC and voila detected it right away..

any chance i can learn something if i'm impatient.. is a good thing..

thanks again

---

### Post by smurftheweb on 2009-12-14
Confirmed - I had the same issue in Ubuntu 9.10, and setting USB mode from Automatic to MSC on the device itself solved this immediately.

Thank you binskipy2u!

---

### Post by atropa on 2009-12-15
My sansa clip worked flawlessly in ubuntu 9.04. Only in ubuntu 9.10 it stopped doing so. Also in my case selecting USB Mode "MSC" in the player fixed it.

---

### Post by Roby718 on 2010-04-13
I have an 8gig sunsa fuse, it works on other computers, in MSC mode. Doesnt in ubuntu, tested other sansa, worked in ubuntu. Sorry for bad english. at work... :KS

---

