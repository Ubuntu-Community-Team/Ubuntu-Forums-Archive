---
title: "gphoto2 errors"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by buddhagui on 2005-12-15
I am still trying to get this digital camera to work with Ubuntu, to no avail! It is a vivitar vivicam35 it is USB and just a small inexpensive camera I got as a gift. When I run gphoto I get unknown model: 105 error. On any other program, digicam and gtkam and others it cannot connect to the camera saying couldn't find device or couldn't communicate with device. 

Anyone have some info on this! I have been trying here for a week no luck! Any one with any info please help.

Thanks,
Chris

---

### Post by amohanty on 2005-12-15
Post the output of:
> gphoto2 --list-cameras | grep "vivicam" 

Or fire up gtkam and click on the camera icon. If it is not autodetected, you will have to hunt down the drivers. I think there is an experimental driver for it somewhere out there. If you can find the driver, I believe gThumb allows you to select the driver you want to use.

Finally is all else fails, try to mount the camera as a usb drive and see if you can copy off the files.

HTH
AM

---

### Post by buddhagui on 2005-12-16
There was no output to post. There must not be a compatible driver. I even tried the generic ones to the two different generic usb drivers on those camera protocols. I am going to try to mount as usb, but I'll have to do more research on how this is accomplished with Ubuntu. I'll post my results.

Thanks for the help, here goes another try!
Chris

---

### Post by amohanty on 2005-12-16
I think there is an app called usbview in the repos. Install it and check if you can see your device in there.

> sudo apt-get install usbview

also after hooking up the camera post the output of :

> lsusb

---

### Post by buddhagui on 2005-12-16
lsusb outputs the following: chris@ip62:~$ lsusb
Bus 001 Device 003: ID 2770:905c NHJ, Ltd
Bus 001 Device 001: ID 0000:0000

I am installing the usbview package now. Hope this works!

Thanks,
Chris

---

### Post by buddhagui on 2005-12-16
What dp I look for and how do I access the USB on command line?

---

### Post by amohanty on 2005-12-16
> Bus 001 Device 003: ID 2770:905c NHJ, Ltd

I think I saw the NHJ bit elsewhere and iwas associated with a Snap Digital camera. So it being detected. What you need to do is to mount it.

Ok try the following after plugging in the camera and powering it on.
1. > sudo modprobe usb-storage
2. Post output of
> cat /var/log/messages | grep usb
3. > ls /media

HTH
AM

---

### Post by buddhagui on 2005-12-17
Here is everything you asked about. Hope this helps, please let me know after this how exactly to access this.
chris@ip62:~$ sudo modprobe usb-storage
Password:
chris@ip62:~$ cat /var/log/messages | grep usb
Dec 15 11:20:10 localhost kernel: [4545164.849000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 15 11:20:11 localhost kernel: [4545165.184000] usb 1-2: USB disconnect, address 4
Dec 15 11:20:11 localhost kernel: [4545165.375000] usb 1-2: new full speed USB device using uhci_hcd and address 5
Dec 15 11:20:12 localhost usb.agent[4242]:      usb-storage: already loaded
Dec 15 11:20:13 localhost usb.agent[4315]:      usb-storage: already loaded
Dec 15 11:22:31 localhost kernel: [4545305.183000] usb 1-2: USB disconnect, address 5
Dec 15 12:21:27 localhost kernel: [4548841.599000] usb 1-2: new full speed USB device using uhci_hcd and address 6
Dec 15 12:27:15 localhost kernel: [4549189.933000] usb 1-2: USB disconnect, address 6
Dec 16 10:36:46 localhost kernel: [4628972.849000] usb 1-2: new full speed USB device using uhci_hcd and address 7
Dec 16 10:39:08 localhost kernel: [4629115.183000] usb 1-2: USB disconnect, address 7
Dec 16 10:45:08 localhost kernel: [4629474.849000] usb 1-2: new full speed USB device using uhci_hcd and address 8
Dec 16 10:49:30 localhost kernel: [4629737.683000] usb 1-2: USB disconnect, address 8
Dec 16 10:49:33 localhost kernel: [4629740.349000] usb 1-2: new full speed USB device using uhci_hcd and address 9
Dec 16 10:50:14 localhost kernel: [4629781.433000] usb 1-2: USB disconnect, address 9
Dec 16 12:45:32 localhost kernel: [4294677.352000] usbcore: registered new driver usbfs
Dec 16 12:45:32 localhost kernel: [4294677.352000] usbcore: registered new driver hub
Dec 16 12:45:32 localhost kernel: [4294677.587000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec 16 13:06:19 localhost kernel: [4296004.967000] usb 1-2: USB disconnect, address 2
Dec 16 13:11:15 localhost kernel: [4296300.708000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Dec 16 13:14:58 localhost kernel: [4296524.377000] usb 1-2: USB disconnect, address 3
Dec 16 13:17:59 localhost kernel: [4296705.435000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 16 13:24:29 localhost kernel: [4297095.153000] usb 1-2: USB disconnect, address 4
Dec 17 10:00:51 localhost kernel: [4371288.492000] usb 1-2: new full speed USB device using uhci_hcd and address 5
Dec 17 10:01:10 localhost kernel: [4371307.134000] usbcore: registered new driver usb-storage
chris@ip62:~$ ls /media
cdrom  cdrom0  floppy  floppy0  win  zip


Thanks,
Chris

---

### Post by amohanty on 2005-12-17
Ok from all the outputs the USB drive is being recongnized. To list the devices available to mount post the output of the following:

> ls /proc/bus/usb

To mount you can try the following, remove camera from box.
automount: usually this is handled by gnome-volume-manager so try this:

> sudo killall gnome-volume-manager

Then plug in the device.

Manual: plugin in camera and
> sudo mount -t usbdevfs none /proc/bus/usb


If this doesnt work, then sometimes usb devices are considered as emulated scsi devices and we can try and go that route.

HTH

---

### Post by buddhagui on 2005-12-18
Here is the output of /proc/bus/usb

root@ip62:/home/chris# ls /proc/bus/usb
001  devices

Also tried the gnome-volume-manager command but nothing really seemed to happen in case I am missing something. I am using Breezy so I don't know if it's a SCSI emulation thing because I thought that wasn't needed in the 2.6 series of kernels. I really don't have any experience mounting usb stuff. Could you tell me any more as far as manually mounting this thing just to get the pics off of it? Also One more thing when I try the mount -t command it says usbdevfs no such file system!

Thanks for all the help so far,
Chris

---

### Post by amohanty on 2005-12-18
> root@ip62:/home/chris# ls /proc/bus/usb
001 devices

This again tells me that you have one usb port on your system that is being recognized.

Try this then:

> sudo mount -t usbfs none /proc/bus/usb

---

### Post by buddhagui on 2005-12-18
Thought this output would be helpful too:

root@ip62:/proc/bus/usb# cat devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=Intel Corporation 82801AA USB
S:  SerialNumber=0000:00:1f.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=2770 ProdID=905c Rev= 1.00
S:  Product=USB Digital Still Camera
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=3ms

---

### Post by amohanty on 2005-12-18
> T: Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 9 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs= 1
P: Vendor=2770 ProdID=905c Rev= 1.00
S: Product=**USB Digital Still Camera**
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E: Ad=81(I) Atr=02(Bulk) MxPS= 64 Ivl=0ms
E: Ad=02(O) Atr=02(Bulk) MxPS= 64 Ivl=0ms
E: Ad=83(I) Atr=03(Int.) MxPS= 1 Ivl=3ms

As you can seen its there, I am surprised though that it is not being loaded as a usb drive. Now heres what we can try:

1. plug in the camera:
2. do the following:
> sudo mkdir -p /media/usbcam
mount -t vfat /dev/sda1 /media/usbcam

If you have sata or scsi drives, sda1 will probably not work. To verify do a :
> fdisk -l
if there is nothing like sda1, it shoudl work, if there is, try sda<next highest number>

HTH

PS also take a look at this, might be helpful:
[http://www.faqs.org/docs/Linux-HOWTO/USB-Digital-Camera-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/USB-Digital-Camera-HOWTO.html)

---

### Post by buddhagui on 2005-12-19
There are no scsi devs on my system. in /dev here is the ls:
acpi     kmem     ptyce  ptys8  ptyy2    tty40  ttydd   ttyS27  ttyvb
adsp     kmsg     ptycf  ptys9  ptyy3    tty41  ttyde   ttyS28  ttyvc
agpgart  log      ptyd0  ptysa  ptyy4    tty42  ttydf   ttyS29  ttyvd
audio    loop     ptyd1  ptysb  ptyy5    tty43  ttye0   ttys3   ttyve
cdrom    lp0      ptyd2  ptysc  ptyy6    tty44  ttye1   ttyS3   ttyvf
cdrw     lvm      ptyd3  ptysd  ptyy7    tty45  ttye2   ttyS30  ttyw0
console  MAKEDEV  ptyd4  ptyse  ptyy8    tty46  ttye3   ttyS31  ttyw1
core     mapper   ptyd5  ptysf  ptyy9    tty47  ttye4   ttyS32  ttyw2
dmmidi1  md0      ptyd6  ptyt0  ptyya    tty48  ttye5   ttyS33  ttyw3
dsp      md1      ptyd7  ptyt1  ptyyb    tty49  ttye6   ttyS34  ttyw4
evms     md10     ptyd8  ptyt2  ptyyc    tty5   ttye7   ttyS35  ttyw5
fb0      md11     ptyd9  ptyt3  ptyyd    tty50  ttye8   ttyS36  ttyw6
fd       md12     ptyda  ptyt4  ptyye    tty51  ttye9   ttyS37  ttyw7
fd0      md13     ptydb  ptyt5  ptyyf    tty52  ttyea   ttyS38  ttyw8
full     md14     ptydc  ptyt6  ptyz0    tty53  ttyeb   ttyS39  ttyw9
hda      md15     ptydd  ptyt7  ptyz1    tty54  ttyec   ttys4   ttywa
hda1     md16     ptyde  ptyt8  ptyz2    tty55  ttyed   ttyS4   ttywb
hdb      md17     ptydf  ptyt9  ptyz3    tty56  ttyee   ttyS40  ttywc
hdb1     md18     ptye0  ptyta  ptyz4    tty57  ttyef   ttyS41  ttywd
hdb2     md19     ptye1  ptytb  ptyz5    tty58  ttyp0   ttyS42  ttywe
hdb5     md2      ptye2  ptytc  ptyz6    tty59  ttyp1   ttyS43  ttywf
hdc      md20     ptye3  ptytd  ptyz7    tty6   ttyp2   ttyS44  ttyx0
hdd      md21     ptye4  ptyte  ptyz8    tty60  ttyp3   ttyS45  ttyx1
hdd1     md22     ptye5  ptytf  ptyz9    tty61  ttyp4   ttyS46  ttyx2
hdd10    md23     ptye6  ptyu0  ptyza    tty62  ttyp5   ttyS47  ttyx3
hdd11    md24     ptye7  ptyu1  ptyzb    tty63  ttyp6   ttyS48  ttyx4
hdd12    md3      ptye8  ptyu2  ptyzc    tty7   ttyp7   ttyS49  ttyx5
hdd13    md4      ptye9  ptyu3  ptyzd    tty8   ttyp8   ttys5   ttyx6
hdd14    md5      ptyea  ptyu4  ptyze    tty9   ttyp9   ttyS5   ttyx7
hdd15    md6      ptyeb  ptyu5  ptyzf    ttya0  ttypa   ttyS50  ttyx8
hdd16    md7      ptyec  ptyu6  ram0     ttya1  ttypb   ttyS51  ttyx9
hdd17    md8      ptyed  ptyu7  ram1     ttya2  ttypc   ttyS52  ttyxa
hdd18    md9      ptyee  ptyu8  ram10    ttya3  ttypd   ttyS53  ttyxb
hdd19    mem      ptyef  ptyu9  ram11    ttya4  ttype   ttys6   ttyxc
hdd2     midi1    ptyp0  ptyua  ram12    ttya5  ttypf   ttyS6   ttyxd
hdd20    mixer    ptyp1  ptyub  ram13    ttya6  ttyq0   ttys7   ttyxe
hdd21    mixer1   ptyp2  ptyuc  ram14    ttya7  ttyq1   ttyS7   ttyxf
hdd22    net      ptyp3  ptyud  ram15    ttya8  ttyq2   ttys8   ttyy0
hdd23    null     ptyp4  ptyue  ram2     ttya9  ttyq3   ttyS8   ttyy1
hdd24    port     ptyp5  ptyuf  ram3     ttyaa  ttyq4   ttys9   ttyy2
hdd25    ppp      ptyp6  ptyv0  ram4     ttyab  ttyq5   ttyS9   ttyy3
hdd26    psaux    ptyp7  ptyv1  ram5     ttyac  ttyq6   ttysa   ttyy4
hdd27    ptmx     ptyp8  ptyv2  ram6     ttyad  ttyq7   ttysb   ttyy5
hdd28    pts      ptyp9  ptyv3  ram7     ttyae  ttyq8   ttysc   ttyy6
hdd29    ptya0    ptypa  ptyv4  ram8     ttyaf  ttyq9   ttysd   ttyy7
hdd3     ptya1    ptypb  ptyv5  ram9     ttyb0  ttyqa   ttyse   ttyy8
hdd30    ptya2    ptypc  ptyv6  random   ttyb1  ttyqb   ttysf   ttyy9
hdd31    ptya3    ptypd  ptyv7  rtc      ttyb2  ttyqc   ttyt0   ttyya
hdd32    ptya4    ptype  ptyv8  shm      ttyb3  ttyqd   ttyt1   ttyyb
hdd33    ptya5    ptypf  ptyv9  snd      ttyb4  ttyqe   ttyt2   ttyyc
hdd34    ptya6    ptyq0  ptyva  sndstat  ttyb5  ttyqf   ttyt3   ttyyd
hdd35    ptya7    ptyq1  ptyvb  stderr   ttyb6  ttyr0   ttyt4   ttyye
hdd36    ptya8    ptyq2  ptyvc  stdin    ttyb7  ttyr1   ttyt5   ttyyf
hdd37    ptya9    ptyq3  ptyvd  stdout   ttyb8  ttyr2   ttyt6   ttyz0
hdd38    ptyaa    ptyq4  ptyve  tty      ttyb9  ttyr3   ttyt7   ttyz1
hdd39    ptyab    ptyq5  ptyvf  tty0     ttyba  ttyr4   ttyt8   ttyz2
hdd4     ptyac    ptyq6  ptyw0  tty1     ttybb  ttyr5   ttyt9   ttyz3
hdd40    ptyad    ptyq7  ptyw1  tty10    ttybc  ttyr6   ttyta   ttyz4
hdd41    ptyae    ptyq8  ptyw2  tty11    ttybd  ttyr7   ttytb   ttyz5
hdd42    ptyaf    ptyq9  ptyw3  tty12    ttybe  ttyr8   ttytc   ttyz6
hdd43    ptyb0    ptyqa  ptyw4  tty13    ttybf  ttyr9   ttytd   ttyz7
hdd44    ptyb1    ptyqb  ptyw5  tty14    ttyc0  ttyra   ttyte   ttyz8
hdd45    ptyb2    ptyqc  ptyw6  tty15    ttyc1  ttyrb   ttytf   ttyz9
hdd46    ptyb3    ptyqd  ptyw7  tty16    ttyc2  ttyrc   ttyu0   ttyza
hdd47    ptyb4    ptyqe  ptyw8  tty17    ttyc3  ttyrd   ttyu1   ttyzb
hdd48    ptyb5    ptyqf  ptyw9  tty18    ttyc4  ttyre   ttyu2   ttyzc
hdd49    ptyb6    ptyr0  ptywa  tty19    ttyc5  ttyrf   ttyu3   ttyzd
hdd5     ptyb7    ptyr1  ptywb  tty2     ttyc6  ttys0   ttyu4   ttyze
hdd50    ptyb8    ptyr2  ptywc  tty20    ttyc7  ttyS0   ttyu5   ttyzf
hdd51    ptyb9    ptyr3  ptywd  tty21    ttyc8  ttys1   ttyu6   urandom
hdd52    ptyba    ptyr4  ptywe  tty22    ttyc9  ttyS1   ttyu7   usplash_fifo
hdd53    ptybb    ptyr5  ptywf  tty23    ttyca  ttyS10  ttyu8   vcs
hdd54    ptybc    ptyr6  ptyx0  tty24    ttycb  ttyS11  ttyu9   vcs1
hdd55    ptybd    ptyr7  ptyx1  tty25    ttycc  ttyS12  ttyua   vcs2
hdd56    ptybe    ptyr8  ptyx2  tty26    ttycd  ttyS13  ttyub   vcs3
hdd57    ptybf    ptyr9  ptyx3  tty27    ttyce  ttyS14  ttyuc   vcs4
hdd58    ptyc0    ptyra  ptyx4  tty28    ttycf  ttyS15  ttyud   vcs5
hdd59    ptyc1    ptyrb  ptyx5  tty29    ttyd0  ttyS16  ttyue   vcs6
hdd6     ptyc2    ptyrc  ptyx6  tty3     ttyd1  ttyS17  ttyuf   vcs7
hdd60    ptyc3    ptyrd  ptyx7  tty30    ttyd2  ttyS18  ttyv0   vcsa
hdd61    ptyc4    ptyre  ptyx8  tty31    ttyd3  ttyS19  ttyv1   vcsa1
hdd62    ptyc5    ptyrf  ptyx9  tty32    ttyd4  ttys2   ttyv2   vcsa2
hdd63    ptyc6    ptys0  ptyxa  tty33    ttyd5  ttyS2   ttyv3   vcsa3
hdd7     ptyc7    ptys1  ptyxb  tty34    ttyd6  ttyS20  ttyv4   vcsa4
hdd8     ptyc8    ptys2  ptyxc  tty35    ttyd7  ttyS21  ttyv5   vcsa5
hdd9     ptyc9    ptys3  ptyxd  tty36    ttyd8  ttyS22  ttyv6   vcsa6
hpet     ptyca    ptys4  ptyxe  tty37    ttyd9  ttyS23  ttyv7   vcsa7
hwrng    ptycb    ptys5  ptyxf  tty38    ttyda  ttyS24  ttyv8   xconsole
initctl  ptycc    ptys6  ptyy0  tty39    ttydb  ttyS25  ttyv9   zero
input    ptycd    ptys7  ptyy1  tty4     ttydc  ttyS26  ttyva
That's all. I am not sure what to mount!

Thanks,
Chris

---

### Post by coolclassic on 2005-12-19
I have had a look at /etc/hotplug/usb/libgphoto2.usermap. You will see some entries for vivitar cameras. The entries you are intrested in are  0x2770   0x9120 the first set of numbers represent the vendor id. The second set is the product id this number you will have to change to 0x905c. To do this edit your libgphoto2.usermap copy the ViviCam3350 entry and paste it underneath and then edit the camera name and product id save the file and you should be able to use gphoto or other photo packages.

---

### Post by buddhagui on 2005-12-19
Tried this and still no luck. Is there something else to edit? Or is there another way at all? I have tried so much and I'd really like to get this so that other people will be able to use it as well.

Thanks,
Chris

---

### Post by amohanty on 2005-12-19
Plug in the camera and then post the output of the following:

> cat /proc/scsi/scsi
> ps aux | grep volume | grep -v grep
>  sudo modprobe usb-storage
lsmod | grep usb

Lets try and mount this sucker one way or another.
AM

---

### Post by buddhagui on 2005-12-20
here is all of the output you requested:
root@ip62:/home/chris# cat /proc/scsi/scsi
cat: /proc/scsi/scsi: No such file or directory
root@ip62:/home/chris# cat /proc/scsi/
cat: /proc/scsi/: No such file or directory
root@ip62:/home/chris# ps aux | grep volume | grep -v grep
chris     7588  0.0  2.7  17052  7024 ?        Ss   13:37   0:00 gnome-volume-ma nager --sm-client-id default4
root@ip62:/home/chris# modprobe usb-storage
root@ip62:/home/chris# lsmod | grep usb
usb_storage            64704  0
scsi_mod              124872  1 usb_storage
usbcore               104316  3 usb_storage,uhci_hcd
ide_core              125268  6 usb_storage,ide_floppy,ide_cd,ide_disk,ide_gener ic,piix
root@ip62:/home/chris#

I want to get this thing mounted bad! Thanks fo all your help!

Chris

---

### Post by buddhagui on 2005-12-20
sorry here is output as well of cat /proc/scsi/scsi:
root@ip62:/home/chris# cat /proc/scsi/scsi
Attached devices:
root@ip62:/home/chris# cat /proc/scsi/device_info
'Aashima' 'IMAGERY 2400SP' 0x1
'CHINON' 'CD-ROM CDS-431' 0x1
'CHINON' 'CD-ROM CDS-535' 0x1
'DENON' 'DRD-25X' 0x1
'HITACHI' 'DK312C' 0x1
'HITACHI' 'DK314C' 0x1
'IMS' 'CDD521/10' 0x1
'MAXTOR' 'XT-3280' 0x1
'MAXTOR' 'XT-4380S' 0x1
'MAXTOR' 'MXT-1240S' 0x1
'MAXTOR' 'XT-4170S' 0x1
'MAXTOR' 'XT-8760S' 0x1
'MEDIAVIS' 'RENO CD-ROMX2A' 0x1
'MICROTEK' 'ScanMakerIII' 0x1
'NEC' 'CD-ROM DRIVE:841' 0x1
'PHILIPS' 'PCA80SC' 0x1
'RODIME' 'RO3000S' 0x1
'SUN' 'SENA' 0x1
'SANYO' 'CRD-250S' 0x1
'SEAGATE' 'ST157N' 0x1
'SEAGATE' 'ST296' 0x1
'SEAGATE' 'ST1581' 0x1
'SONY' 'CD-ROM CDU-541' 0x1
'SONY' 'CD-ROM CDU-55S' 0x1
'SONY' 'CD-ROM CDU-561' 0x1
'SONY' 'CD-ROM CDU-8012' 0x1
'SONY' 'SDT-5000' 0x200000
'TANDBERG' 'TDC 3600' 0x1
'TEAC' 'CD-R55S' 0x1
'TEAC' 'CD-ROM' 0x1
'TEAC' 'MT-2ST/45S2-27' 0x1
'HP' 'C1750A' 0x1
'HP' 'C1790A' 0x1
'HP' 'C2500A' 0x1
'MEDIAVIS' 'CDR-H93MV' 0x1
'MICROTEK' 'ScanMaker II' 0x1
'MITSUMI' 'CD-R CR-2201CS' 0x1
'NEC' 'D3856' 0x1
'QUANTUM' 'LPS525S' 0x1
'QUANTUM' 'PD1225S' 0x1
'QUANTUM' 'FIREBALL ST4.3S' 0x1
'RELISYS' 'Scorpio' 0x1
'SANKYO' 'CP525' 0x1
'TEXEL' 'CD-ROM' 0x1
'YAMAHA' 'CDR100' 0x1
'YAMAHA' 'CDR102' 0x1
'YAMAHA' 'CRW8424S' 0x1
'YAMAHA' 'CRW6416S' 0x1
'3PARdata' 'VV' 0x20000
'ADAPTEC' 'AACRAID' 0x2
'ADAPTEC' 'Adaptec 5400S' 0x2
'AFT PRO' '-IX CF' 0x2
'BELKIN' 'USB 2 HS-CF' 0x402
'CANON' 'IPUBJD' 0x40
'CBOX3' 'USB Storage-SMC' 0x402
'CMD' 'CRA-7280' 0x40
'CNSI' 'G7324' 0x40
'CNSi' 'G8324' 0x40
'COMPAQ' 'LOGICAL VOLUME' 0x2
'COMPAQ' 'CR3500' 0x2
'COMPAQ' 'MSA1000' 0x1040
'COMPAQ' 'MSA1000 VOLUME' 0x1040
'COMPAQ' 'HSV110' 0x21000
'DDN' 'SAN DataDirector' 0x40
'DEC' 'HSG80' 0x1040
'DELL' 'PV660F' 0x40
'DELL' 'PV660F   PSEUDO' 0x40
'DELL' 'PSEUDO DEVICE .' 0x40
'DELL' 'PV530F' 0x40
'DELL' 'PERCRAID' 0x2
'DGC' 'RAID' 0x40
'DGC' 'DISK' 0x40
'EMC' 'SYMMETRIX' 0x242
'EMULEX' 'MD21/S2     ESDI' 0x10
'FSC' 'CentricStor' 0x240
'Generic' 'USB SD Reader' 0x402
'Generic' 'USB Storage-SMC' 0x402
'Generic' 'USB Storage-SMC' 0x402
'HITACHI' 'DF400' 0x40
'HITACHI' 'DF500' 0x40
'HITACHI' 'DF600' 0x40
'HP' 'A6189A' 0x240
'HP' 'OPEN-' 0x240
'HP' 'NetRAID-4M' 0x2
'HP' 'HSV100' 0x21000
'HP' 'C1557A' 0x2
'HP' 'C3323-300' 0x20
'IBM' 'AuSaV1S2' 0x2
'IBM' 'ProFibre 4000R' 0x240
'IBM' '2105' 0x400000
'iomega' 'jaz 1GB' 0x21
'IOMEGA' 'Io20S         *F' 0x8
'INSITE' 'Floptical   F*8I' 0x8
'INSITE' 'I325VM' 0x8
'iRiver' 'iFP Mass Driver' 0x80400
'LASOUND' 'CDX7405' 0x90
'MATSHITA' 'PD-1' 0x12
'MATSHITA' 'DMC-LC5' 0x80400
'MATSHITA' 'DMC-LC33' 0x80400
'MATSHITA' 'DMC-LC40' 0x80400
'Medion' 'Flash XL  MMC/SD' 0x2
'MegaRAID' 'LD' 0x2
'MICROP' '4110' 0x20
'MYLEX' 'DACARMRB' 0x20000
'nCipher' 'Fastness Crypto' 0x2
'NAKAMICH' 'MJ-4.8S' 0x12
'NAKAMICH' 'MJ-5.16S' 0x12
'NEC' 'PD-1 ODX654P' 0x12
'NRC' 'MBR-7' 0x12
'NRC' 'MBR-7.4' 0x12
'PIONEER' 'CD-ROM DRM-600' 0x12
'PIONEER' 'CD-ROM DRM-602X' 0x12
'PIONEER' 'CD-ROM DRM-604X' 0x12
'REGAL' 'CDC-4X' 0x90
'SanDisk' 'ImageMate CF-SD1' 0x2
'SEAGATE' 'ST34555N' 0x20
'SEAGATE' 'ST3390N' 0x20
'SGI' 'RAID3' 0x40
'SGI' 'RAID5' 0x40
'SGI' 'TP9100' 0x20000
'SGI' 'Universal Xport' 0x100000
'SMSC' 'USB 2 HS-CF' 0x440
'SONY' 'CD-ROM CDU-8001' 0x4
'SONY' 'TSL' 0x2
'ST650211' 'CF' 0x400000
'SUN' 'T300' 0x40
'SUN' 'T4' 0x40
'TEXEL' 'CD-ROM' 0x4
'TOSHIBA' 'CDROM' 0x100
'TOSHIBA' 'CD-ROM' 0x100
'USB2.0' 'SMARTMEDIA/XD' 0x402
'WangDAT' 'Model 2600' 0x200000
'WangDAT' 'Model 3200' 0x200000
'WangDAT' 'Model 1300' 0x200000
'WDC WD25' '00JB-00FUA0' 0x40000
'XYRATEX' 'RS' 0x240
'Zzyzx' 'RocketStor 500S' 0x40
'Zzyzx' 'RocketStor 2000' 0x40
root@ip62:/home/chris#

---

### Post by coolclassic on 2005-12-20
Just a thought have you tried a different usb port. I had a similar prob I just moved the connection to the ones at the back.

---

### Post by amohanty on 2005-12-21
First try coolclassic's suggestion. If it doesnt work, I had provided this above, did you try it? Even if sda1 does not exist in /dev, I think (I am not sure, but the following should work in most cases), the usb-storage module should provide the device. In any case try it:

>  
sudo modprobe usb-storage
sudo /etc/init.d/hotplug start
sudo mkdir -p /media/usbcam
sudo chgrp <your username> /media/usbcam
sudo chmod 770 /media/usbcam
mount -t vfat /dev/sda1 /media/usbcam


HTH

---

### Post by buddhagui on 2005-12-22
I tried it through another port on the comp, but alas no go! I also tried what you just suggested and mount -t didn't work becuase it said that there was no /dev/sda1 or sda or any of that. I am not sure what to do!

Thanks,
Chris

---

### Post by amohanty on 2005-12-22
Well before we try the last ditch effort i.e. buy a compatible card reader and plug you rmem card into it, can you plug in your camera and then post the output of:

> dmesg | tail -n 100

AM

---

### Post by coolclassic on 2005-12-22
A couple of things to try is:

1) When you connect the camera to the computer do you switch the camera on? If you don't the camera won't be reconised.

2) Before connecting the camera have a look at the ?media directory and see what folders are available. Then connect the camera and have another look.

---

### Post by buddhagui on 2005-12-23
Here's the output of dmesg:
root@ip62:/home/chris#  dmesg | tail -n 100
[4364691.575000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364691.665000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364691.665000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364694.215000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364694.215000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364694.338000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364694.338000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364699.760000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364699.760000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364699.892000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364699.892000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364700.117000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364700.117000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364700.290000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364700.290000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364701.942000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364701.942000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364702.123000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364702.123000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364702.878000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364702.878000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364703.050000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364703.050000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364711.910000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364711.910000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364712.083000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364712.083000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364713.780000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364713.780000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364713.936000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364713.936000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364714.798000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364714.798000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364714.971000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364714.971000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364717.446000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364717.446000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364717.627000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364717.627000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364718.456000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364718.456000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364718.628000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364718.628000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364719.706000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364719.706000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364719.907000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364719.907000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364729.254000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364729.254000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364729.360000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364729.360000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364733.609000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364733.609000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364733.757000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364733.757000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364734.355000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364734.355000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364734.486000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364734.486000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364738.837000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364738.837000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364739.002000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364739.002000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364739.550000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364739.550000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364739.698000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364739.698000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364740.423000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364740.423000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364740.563000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364740.563000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364746.437000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364746.437000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364746.543000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364746.543000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364747.777000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364747.777000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364747.917000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364747.917000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364806.760000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364806.760000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364806.928000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364806.928000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364808.337000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364808.337000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364808.451000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364808.451000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364816.438000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364816.438000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364816.611000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364816.611000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364817.539000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364817.539000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364817.741000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364817.741000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364819.499000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4364819.499000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4364819.639000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4364819.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4367496.745000] usb 1-1: new full speed USB device using uhci_hcd and address 2
root@ip62:/home/chris# 

I really got no clue on this! I also tried everything that coolclassic sugested. I really appreciate the help you guy's have been giving me. I hope this gets resolved somehow. Is there any other things to change in the gphoto2 file maybe to get the right driver. And also by the way there is no memery card. It's a standalone camera. Just the camera and it's storage. I've been reading some older docs before kernel 2.4 about two different camera protocols, that stuff doesn't seem to work either. There has to be something. I wish there was an experimental driver, I googled it, but nothing. Is there anywhere else to look for a vivitar vivicam35 driver? Any other sugestions?

Thanks,
Chris

---

### Post by amohanty on 2005-12-23
> I also tried what you just suggested and mount -t didn't work becuase it said that there was no /dev/sda1 or sda or any of that.

Well now I am at the end of my knowledge well. The only thing I can suggest would be to go out and get a card reader that is known to work with Ubuntu. Just make post regarding that. I am sure lots of ppl have gotten thtat to work.

HTH
AM

---

### Post by coolclassic on 2005-12-23
When was the last time you updated your system if you have a look at this thread it may help solve the problem.
[http://ubuntuforums.org/showthread.php?t=77141&page=4&highlight=mounting](http://ubuntuforums.org/showthread.php?t=77141&page=4&highlight=mounting)

One temp solution was to plug in your camera switch it on and then reboot computer if this works then try the other fixes mentioned in above thread.

---

