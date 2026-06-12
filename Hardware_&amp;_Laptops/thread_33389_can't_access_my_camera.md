---
title: "can't access my camera"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by eewald on 2005-05-10
i can't access my camera (canon powershot pro1) in linux (hoary) - it does not mount and i can't mount it manually. 

if i connect camera via usb wire, nothing happens, although computer recognises "something happening," because dmesg reveals:
*usb 1-1: new full speed USB device using uhci_hcd and address 2*

it does not mount, though, and i can not mount manually: 
*sudo mount /dev/sda(1,2,nothing) /mnt/usb*
says:
*mount: special device /sda does not exist*

mount points created, camera's firmware updated, that's all i can say.

---

### Post by eewald on 2005-05-11
so, is there anybody who's got a clue, please?

---

### Post by David Haas on 2005-05-11
eewald--Perhaps what is said on this URL will help you: <http://www.tuxme.com/node/436>. Here, you'll see that the writer installed photos from a Canon Powershot G5 into Ubuntu Warty 4.10. The "gthumb" app is needed, but is in Ubuntu distros. Is yours installed? Please let me know how it goes, because I plan to purchase a digital camera soon.
David

---

### Post by triskele on 2005-05-11
Get a card reader. It's so much easier than going through the camera.

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=eewald]i can't access my camera (canon powershot pro1) in linux (hoary) - it does not mount and i can't mount it manually. 
.[/QUOTE]

I have the problem. I have a dirty fix for you (what I use). Take whatever program you want to use for pictures (I use digikam but any would work this way) and open it by using the run command with the words gksudo before it.

like:

gksudo digikam

or 

gksudo gthumb

or whatever. It works, but its not the best way....

---

### Post by David Haas on 2005-05-12
eewald--I myself followed the suggestions I gave you yesterday: Today, I uploaded pictures from my wife's new Nikon Coolpix 3700 to Ubuntu 5.04. With the camera off, I connected it to the on computer. I opened gThumb image viewer and turned on the camera. In gThumb, I selected File>Import photos. GThumb then asked for my camera model, which I selected from a very long and complete-looking list of cameras. Without even having to press the camera's import button, thumbnails appeared for every photo in the camera's memory. These were readily manipulated, saved, and printed. I may possibly not have recalled these steps in perfect order, but you won't be confused by the procedure. I hope it works for you and your camera.
David

---

### Post by eewald on 2005-05-13
of course libgphoto2 library was installed and gthumb as well. (powershot pro1 seems to be the only canon camera missing in gthumb's list, btw). to access my camera, i had to follow these three steps:

1) change file permissions of /proc/bus/usb, so user can access it 

2) add the following line to fstab file: 
none            /proc/bus/usb   usbfs   defaults,devmode=666 0 0

3) run sudo mount /proc/bus/usb every time after connecting camera. i get an error report (already mounted or /proc/bus/usb busy), but gthumb won't recognise camera otherwise. 

really dirty way  ](*,)

---

### Post by ohzopants on 2005-05-30
These methods work for me, but isn't there an easier (cleaner) way?

---

### Post by Musagetes on 2005-05-31
I'm having a similar problem with my Fujifilm Finepix1300. Rather old, but it works.

Now, I've tried both listed methods, but nothing seems to work.

I can see USB devices that I attach with usbview, with sudo tail -f /var/log/messages and simply by looking at files in /proc/bus/usb and /proc/scsi/usb_storage/.

This is from the tail -f:
```
Jun  1 02:25:07 localhost kernel:   Vendor: Fujifilm  Model: FinePix 1400Zoom  Rev: 1000
Jun  1 02:25:07 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Jun  1 02:25:07 localhost kernel: SCSI device sda: 16000 512-byte hdwr sectors (8 MB)
Jun  1 02:25:07 localhost kernel: sda: Write Protect is off
Jun  1 02:25:07 localhost kernel: SCSI device sda: 16000 512-byte hdwr sectors (8 MB)
Jun  1 02:25:07 localhost kernel: sda: Write Protect is off
Jun  1 02:25:07 localhost kernel:  /dev/scsi/host2/bus0/target0/lun0: p1
Jun  1 02:25:07 localhost scsi.agent[25589]:      sd_mod: loaded sucessfully
Jun  1 02:25:07 localhost kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0Jun  1 02:34:02 localhost kernel: Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01
```

This is /proc/bus/usb/devices:
```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04cb ProdID=0100 Rev=10.00
S:  Product=USB Mass Storage
S:  SerialNumber=Y-241^^^^^010327W0000003026818
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=05 Prot=00 Driver=usb-storage
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

And from /proc/scsi/usb-storage/2
```
   Host scsi2: usb-storage
       Vendor: Fujifilm
      Product: USB Mass Storage
Serial Number: Y-241^^^^^010327W0000003026818
     Protocol: Uniform Floppy Interface (UFI)
    Transport: Control/Bulk/Interrupt
       Quirks: SINGLE_LUN FIX_INQUIRY
```

And finally, /proc/scsi/scsi
```
Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Fujifilm Model: FinePix 1400Zoom Rev: 1000
  Type:   Direct-Access                    ANSI SCSI revision: 02
```

But whyyyyyy won't it auto-mount or just appear somewhere where I can get the content out of the camera? :(

Same thing occurs for me when I plug my mp3 player in. It's visible in the above mentioned spots, but doesn't mount at all. And I've edited fstab several times with no luck. My eternal gratitude to anyone who can fix this problem!

---

### Post by ad noiseam on 2005-09-04
I've got exactly the same problem with a Finepix 2600Z. It's recognized, but not mounted... :(

---

### Post by ad noiseam on 2005-09-06
Actually, I finally got my camera working, by doing what I describe in [this thread](http://www.ubuntuforums.org/showthread.php?p=335998#post335998) but with the camera. It works just fine.

---

### Post by undertakingyou on 2007-02-20
I was having the same issues and found that if I ran gthumb as sudo I could then import no problem.  I figured it must be a permissions issue.

I fixed this same issue by editing two files.  The first was the libgphoto2.rules file and the next was the permissions.rules file.  

Both are in /etc/udev/rules.d

I set the "MODE" to "0666" on all entries in the libgphoto2.rules file
And in the permissions.rules file I changed the "USB" line to "MODE="0666""

That has cleared it all up for me.

---

