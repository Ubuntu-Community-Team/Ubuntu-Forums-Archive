---
title: "Pixart: 093a:2468 webcam problems with 7.10"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by gibbsuk on 2007-11-24
ok, i know there are hundred of threads on this subject but i have tried them all and nothing working.
The problem
My webcam wont work - when i plug it in the led flashs for 5 second and then goes off. Camorama returns "could not connect to video device"

lsusb returns
Bus 004 Device 051: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
lsmod returns
gspca                 608336  0 

using the compatibility list on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) i am unsure of which driver i need - the ID appears to suggest i use spac5xx but the name suggests Gspcav1 (which i think i have running)

I have tried using easycam and easycam2 but both of these error, i have tried using easyspac - that runs and instals (in french) but when i modprobe i doesn't appear. - i have tried installing spac5xx manually but thats doesn't work either.

All documentation suggests that it should be plug and play on gusty but its not working, i think i have to uninstall gspac and install spac5xx but im not sure!

thanks

---

### Post by gibbsuk on 2007-11-24
Dmesg returns

[17505.160000] usb 2-1: USB disconnect, address 6
[17509.940000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[17510.228000] usb 2-1: configuration #1 chosen from 1 choice
[17510.232000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)

if it helps...

---

### Post by gibbsuk on 2007-11-28
Bump :(

---

### Post by gibbsuk on 2007-12-03
tried it on my other gusty box and the samething happens, any ideas anyone?

---

### Post by chiron69 on 2007-12-04
Good afternoon, I do have exactly the same problem with this webcam. Can anybody help? ;-)

---

### Post by nikolay28 on 2007-12-05
I have the same problems, i tried this but it did not worked for me, maybe it helps you

[http://ubuntuforums.org/showthread.p...t=trust+webcam](http://ubuntuforums.org/showthread.p...t=trust+webcam)

---

### Post by nikolay28 on 2007-12-05
Ok now it works :)
you have to copy the gspca.ko file to

/lib/modules//kernel/drivers/usb/media/
/lib/modules/ubuntu/media/gspcav1/

then rmmod gspca

plug in the camera again and the hurray it works :-D

---

### Post by gibbsuk on 2007-12-05
i don't have a directory

/lib/modules//kernel/drivers/usb/media/

should i create one?

---

### Post by gibbsuk on 2007-12-08
also what is rmmod?
thanks

---

### Post by owen5 on 2008-01-26
rmmod is how dynamic modules are unloaded from the system.


I'm having the same problem and I want to try your solution, but can't find where the package manager stores gspca.ko to try copying it

any help?

---

### Post by owen5 on 2008-01-26
well, I finally compiled a copy of gspca.ko from source and copied it, but it didn't work.  I don't know if its conflicting with the versions I'd already installed, but I used dpkg to remove the gspca package and i don't know how to make sure they're aren't any other copies haning around.  dmesg reports

[29550.017953] usb 1-4: new full speed USB device using ohci_hcd and address 13
[29550.231342] usb 1-4: configuration #1 chosen from 1 choice
[29550.268209] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)
[29550.280452] usbcore: registered new interface driver gspca
[29550.280471] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered



when i plug in the camera

---

### Post by beauty on 2008-03-30
Did anybody ever get this camera to work?  I'm running Ubuntu 7.10 and get this:
```
$ lsusb
Bus 002 Device 007: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam

```

so figure the drivers are installed (?).

I've poked all over the web and nothing I've tried helps.  Looking for video in /dev gives this:

```
$ ls -l /dev | grep video
crw-rw---- 1 root   video      10, 175 2008-03-30 14:39 agpgart
crw-rw---- 1 root   video     195,   0 2008-03-30 14:41 nvidia0
crw-rw---- 1 root   video     195, 255 2008-03-30 14:41 nvidiactl
crw-rw---- 1 root   video      81,   0 2008-03-30 16:25 video0

```

I made sure that I exist in the group 'video' by checking

```
$ cat /etc/group | grep video
```

However, when I run 'camorama' ([camorama.fixedgear.org]("http://camorama.fixedgear.org")) all I get is 
> Could not connect to video device (/dev/video0).  Please check connection.

- doesn't matter if I run it as 'sudo camorama'.

Any ideas before I throw up my hands?

---

### Post by goobster71 on 2008-05-16
I was able to get mine working with Ubuntu 7.10.

I wrote up some instructions here:

[http://lesvanbrunt.blogspot.com/2008/05/making-gigaware-25-297-webcam-work-with.html]("http://lesvanbrunt.blogspot.com/2008/05/making-gigaware-25-297-webcam-work-with.html")

---

