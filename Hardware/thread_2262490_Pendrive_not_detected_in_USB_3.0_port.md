---
title: "Pendrive not detected in USB 3.0 port"
date: 2015-01-25
forum: Hardware
---

### Post by kuckunniwi on 2015-01-25
Hi,

This might be a stupid question, but I'll go ahead and shoot anyway, since there's nothing to lose (besides self-esteem) :)

I recently bought a Lenovo Yoga 2 Pro, which I'm running Kubuntu Trusty on (64-bit). Since it has an SSD and limited disk space (the price to pay), I bought a 128 Gb Kingston Datatraveler G4 (USB 3.0, backwards compatible with USB 2.0) to put some music on and play it from there, to not fill up my HD, and not have my external HD plugged in all the time.

The laptop has two USB ports: 1 USB 3.0 & 1 USB 2.0 (sigh...). The pendrive is detected on the 2.0 port, but not on the 3.0. Playing music from the 2.0 port is proving a bit *unsatisfactory*, as most of my music is in FLAC and the read speed seems to be insufficient (or perhaps that's not the case, but the audio freezes often, as if buffering).

When plugged into the 3.0 port, the pendrive isn't detected (which is odd, as my WD Passport is also USB 3.0 and is detected without issues).

***cat /etc/mtab*** doesn't display the disk (obviously, as it isn't mounted)

***lsusb*** actually lists a *Bus 003 Device 050: ID 0951:1666 Kingston Technology *, so the system does recognise its presence to some extent...

***dmesg*** produces the following output:```


[10587.745141] usb 3-2: New USB device found, idVendor=0951, idProduct=1666
[10587.745150] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10587.745156] usb 3-2: Product: DataTraveler 3.0
[10587.745160] usb 3-2: Manufacturer: Kingston
[10587.745164] usb 3-2: SerialNumber: ***********************
[10592.751371] usb 3-2: Set SEL for device-initiated U2 failed.
[10597.755428] usb 3-2: Disable of device-initiated U1 failed.
[10597.758964] usb 3-2: Disable of device-initiated U2 failed.
[10597.758979] usb-storage 3-2:1.0: USB Mass Storage device detected
[10597.759230] scsi58 : usb-storage 3-2:1.0
[10597.762935] usb 3-2: Set SEL for device-initiated U1 failed.
[10597.766436] usb 3-2: Set SEL for device-initiated U2 failed.
[10598.876960] usb 3-2: reset SuperSpeed USB device number 59 using xhci_hcd
[10598.903568] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800362bba80
[10598.903572] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800362bbac0
[10601.070026] usb 3-2: USB disconnect, device number 59
[10603.908251] usb 3-2: Set SEL for device-initiated U2 failed.
[10604.477028] usb 3-2: new SuperSpeed USB device number 60 using xhci_hcd
```

What could be the issue, and what might I be able to do to fix it? Thanks in advance for any suggestions, and particularly for your patience! :D

---

### Post by kuckunniwi on 2015-01-25
Almost forgot, this is the output of a few relevant commands when the drive is plugged into the USB 2.0 port:

cat /etc/mtab
```
/dev/sdb1 /media/travis/KINGSTON vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,flush,uhelper=udisks2 0 0
```

sudo fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64   241659903   120829920    b  W95 FAT32
```

dmesg
```
[11828.212581] usb 2-1: new high-speed USB device number 10 using xhci_hcd
[11828.446578] usb 2-1: New USB device found, idVendor=0951, idProduct=1666
[11828.446588] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11828.446593] usb 2-1: Product: DataTraveler 3.0
[11828.446598] usb 2-1: Manufacturer: Kingston
[11828.446601] usb 2-1: SerialNumber: *********************
[11828.446883] usb 2-1: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[11828.446893] usb 2-1: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
[11828.447575] usb-storage 2-1:1.0: USB Mass Storage device detected
[11828.447761] scsi130 : usb-storage 2-1:1.0
[11830.149192] scsi 130:0:0:0: Direct-Access     Kingston DataTraveler 3.0 1.00 PQ: 0 ANSI: 6
[11830.149449] sd 130:0:0:0: Attached scsi generic sg1 type 0
[11830.150836] sd 130:0:0:0: [sdb] 241660916 512-byte logical blocks: (123 GB/115 GiB)
[11830.151406] sd 130:0:0:0: [sdb] Write Protect is off
[11830.151409] sd 130:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[11830.151972] sd 130:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[11830.158570]  sdb: sdb1
[11830.160930] sd 130:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by sudodus on 2015-01-25
Sometimes the handshaking between pendrives and the USB system in the computer (hardware and firmware) does not work properly. It is particularly difficult when booting, and often works better when using the drive for data storage. But it seems that in your case this particular pendrive has problems in the USB 3 port also for data storage.

I think that it is correctly partitioned and formatted (because it works in the USB 2 port). What can you do?

See these links (and links from them) to get tips and ideas what might help.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

1. Try another brand or model of USB pendrive. I have good experience of Sandisk Extreme,Transcend and Kanguru USB 3 pendrives and also a Kingston Datatraveler Ultimate ***G3*** (32 GB) USB 3 pendrive, which are well recognized in USB 3 ports. 

Right now my Kingston Datatraveler Ultimate ***G3*** (32 GB) USB 3 pendrive is a boot drive with Debian Jessie, and I tested right now, that it really can boot from a USB 3 port.

If you don't want to buy and fail again, ask if some friend or colleague  has a USB 3 pendrive, that you can try in your computer. Otherwise you  have a fair chance to succeed with the pendrives that work for me. You  can get more detailed information if you wish.

2. There are cases, when a pendrive is better recognized via a ***USB hub*** than directly. So you might have better luck if you connect your pendrive via a USB 3 hub. But there are also cases when it works directly and not via a USB hub.

---

### Post by kuckunniwi on 2015-01-25
Thanks a ton for your quick reply, sudodus!

I booted into Windows to see if it would recognise it in the USB 3 port, and no problem, so it's not a hardware issue. Could it be a compatibility issue with this specific model and linux kernel/firmware? From what I saw on the speed tests, the speed is definitely sub-par, so in USB 2....waaaay to slow. 

I don't think I have the receipt anymore, and this 128 Gb pen wasn't cheap, so I'd ideally like to find a way to get it working on the USB 3 port in Linux, even if speed isn't stellar, rather than buying another device.

I took a look at the other link you sent, but am unsure how that applies to my specific case, since I'm not trying to use this drive as a boot device, but just as storage and for on-the-fly music playing. 

Is there anything else I can do? What exactly do the following lines from dmesg mean, and can anything else be done to correct this issue?

```
[10592.751371] usb 3-2: Set SEL for device-initiated U2 failed.
[10597.755428] usb 3-2: Disable of device-initiated U1 failed.
[10597.758964] usb 3-2: Disable of device-initiated U2 failed.
```

By the way, I'm aware that replying to this kind of issue can be tedious and time-consuming, and I really appreciate your help. I'll do some research of my own and see if I can come across a solution, but any extra help to point me in the right direction would be very much appreciated. 

THANKS!!!

---

### Post by kuckunniwi on 2015-01-25
Looks like I'm not the only person having this problem with this specific pendrive, on a Lenovo laptop...

[http://askubuntu.com/questions/444897/usb-3-0-not-recognized-by-usb-3-0-port]("http://askubuntu.com/questions/444897/usb-3-0-not-recognized-by-usb-3-0-port")

---

### Post by sudodus on 2015-01-25
> **kuckunniwi said:**
> Thanks a ton for your quick reply, sudodus!

I booted into Windows to see if it would recognise it in the USB 3 port, and no problem, so it's not a hardware issue. Could it be a compatibility issue with this specific model and linux kernel/firmware? From what I saw on the speed tests, the speed is definitely sub-par, so in USB 2....waaaay to slow. 

Yes, and since it works in Windows, it might be worthwhiie to try other Ubuntu versions or linux distros. Since USB 3 is rather new, and your pendrive too, it might be worthwhile to try something newer than what I usually recommend (14.04.1 LTS), so try 14.10 or the current daily build of Vivid Vervet, to become 15.04 in April: [http://iso.qa.ubuntu.com/qatracker/milestones/326/builds](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds), or some other well-known linux distro.
> 
I don't think I have the receipt anymore, and this 128 Gb pen wasn't cheap, so I'd ideally like to find a way to get it working on the USB 3 port in Linux, even if speed isn't stellar, rather than buying another device.

I took a look at the other link you sent, but am unsure how that applies to my specific case, since I'm not trying to use this drive as a boot device, but just as storage and for on-the-fly music playing. 

Is there anything else I can do? What exactly do the following lines from dmesg mean, and can anything else be done to correct this issue?

```
[10592.751371] usb 3-2: Set SEL for device-initiated U2 failed.
[10597.755428] usb 3-2: Disable of device-initiated U1 failed.
[10597.758964] usb 3-2: Disable of device-initiated U2 failed.
```

I'm no good at reading dmesg lines, and a cannot tell anything from those lines. Let us hope someone who knows will read this post and chip in with good advice.
> 
By the way, I'm aware that replying to this kind of issue can be tedious and time-consuming, and I really appreciate your help. I'll do some research of my own and see if I can come across a solution, but any extra help to point me in the right direction would be very much appreciated. 

THANKS!!!

It might still be worthwhile to ask if you can borrow another USB 3 pendrive and check if it works.

---

### Post by kuckunniwi on 2015-01-25
Did a couple of tests (if you can call them that)

- Goot a hold of a transcend 16Gb USB 3 drive: it works fine in the USB 3 port on the Yoga2Pro.
- Tested the Kingston pen on another Laptop (Dell XPS 14z) running the same distro, same version, and it works flawlessly on the USB 3 port. 

It must be a (kernel?) support for the USB 3 port on the Lenovo. Will follow your advice and download the Kubuntu 15.04 Alpha 2, for instance (or even the 14.10 Plasma 5 preview), boot it live (from the USB 2 port) and see if there are any changes.

Once again, thanks for all your help!

---

### Post by sudodus on 2015-01-25
You are making progress. Good luck with your further tests :-)

---

### Post by kuckunniwi on 2015-01-26
Thanks!

Formatted the drive again to make sure it wasn't the issue. To no avail, as expected. Tried on the Dell: worked fine.

Booted *Kubuntu Vivid Alpha 2* live from the USB 2 port and...bam! The Kingston worked fine. I reckon that since Vivid is scheduled for release in April, I can live with USB 2 speed 'til then. My lil' laptop is my work tool, everything is set up to my liking (includin Vbox), and I don't fancy risking system stability by experimenting with different upstream kernels just for the sake of getting that particular pendrive to work. 

Although the issue remains in Trusty, it's as good as solved as far as I'm concerned, so I'll go ahead and mark the thread as solved.

Cheers!

---

### Post by kuckunniwi on 2015-01-26
I could also try Utopic but...Vivid's Plasma 5 desktop is gorgeous and extremely snappy! As the good ol' Kubuntu junkie I am, I reckon it'll be worth the wait :D

---

### Post by sudodus on 2015-01-26
Congratulations :KS

---

