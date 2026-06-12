---
title: "Fuji Finepix won't mount"
date: 2016-12-18
forum: Hardware
---

### Post by 6-dave-9 on 2016-12-18
I have a Fuji Finepix digital camera.  On my old computer which ran 14.04 it worked fine.  I purchased a new machine and did a fresh install of 16.04.  When I plug the camera in via USB the camera's connect light comes on and the camera screen says connecting then a second later the light goes off and the camera screen goes black which means it has disconnected.  A second later the light turns green and the camera screen says connecting, then it all goes away again.  This occurs in an endless loop. 

I've run lsusb while this goes on and sometimes the camera is in the list, sometimes it is not.  Another post related to cameras suggested doing a dmesg and that dumps out a lot.  What I see is a pattern where it starts to connect, finds an problem and then disconnects, over and over again.  Here is one cycle of what it says as it goes on over and over again.-

[  684.775063] sd 33:0:0:0: [sdb] Attached SCSI removable disk
[  685.851056] usb 1-2: new full-speed USB device number 36 using xhci_hcd
[  685.980592] usb 1-2: New USB device found, idVendor=04cb, idProduct=016e
[  685.980596] usb 1-2: New USB device strings: Mfr=0, Product=2, SerialNumber=3
[  685.980599] usb 1-2: Product: USB Mass Storage
[  685.980601] usb 1-2: SerialNumber: Y-750^^^^^041026XFPX0007021529
[  685.981275] usb-storage 1-2:1.0: USB Mass Storage device detected
[  685.982487] scsi host34: usb-storage 1-2:1.0
[  686.980184] scsi 34:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
[  686.981190] sd 34:0:0:0: Attached scsi generic sg2 type 0
[  686.982296] sd 34:0:0:0: [sdb] 1023120 512-byte logical blocks: (524 MB/500 MiB)
[  686.983330] sd 34:0:0:0: [sdb] Write Protect is off
[  686.983333] sd 34:0:0:0: [sdb] Mode Sense: 07 00 00 00
[  686.984419] sd 34:0:0:0: [sdb] Incomplete mode parameter data
[  686.984422] sd 34:0:0:0: [sdb] Assuming drive cache: write through
[  687.103165] usb 1-2: USB disconnect, device number 36

The camera still connects to my old 14.04 desktop and to my 14.04 laptop.  It's only the new 16.04 machine that is having problems.

I love these forums as they've gotten me through every other issue, but can't find a solution to this.

Thanks in advance for any help you can give,

Dave

---

### Post by mörgæs on 2016-12-20
How does the two old computers work in a live boot of 16.04? Do you still get the problem?

---

### Post by 6-dave-9 on 2016-12-31
Thank you for helping me and sorry for the delay, i took a week off for the Holidays.  

The old desktop has been scrapped so I can't do a live boot on it.  The 14.04 laptop is now running a fresh install of 16.04 and the camera works fine with it (and it worked fine with 14.04).  I did try a live boot on the problem machine and the camera was initially recognized and came up, but then it lost the connection and the endless loop of discover and disconnect started.  So I'm thinking it is the machine??  It is a Dell 3650 with an Intel i5-6400.

---

### Post by hanspeteriv on 2017-01-01
Can you please post the dmsg output you get when you connect the camera to the 16.04 laptop? Does that system mount it as mass storage as well? Or does it use Picture Transfer Protocol (PTP)?

When I connect my Finepix S2980 to my 16.10 Tablet it is successfully mounted using PTP.

---

### Post by 6-dave-9 on 2017-01-02
Thanks!! 

Here's the dmesg from when the camera is connected to  the 16.04 laptop.   This connection works fine.  I did notice the "not  properly unmounted" line at the end.  Odd that the laptop can handle  that while the desktop can't and disconnects. 

 I saw where it  suggests running fsck, and tired it, but it said it would cause file  system damage so I didn't go though with it.  Is there some way to fix  it?

  [93653.312067] usb 4-2: new full-speed USB device number 2 using uhci_hcd
 [93653.479090] usb 4-2: New USB device found, idVendor=04cb, idProduct=016e
 [93653.479109] usb 4-2: New USB device strings: Mfr=0, Product=2, SerialNumber=3
 [93653.479114] usb 4-2: Product: USB Mass Storage
 [93653.479119] usb 4-2: SerialNumber: Y-750^^^^^041026XFPX0007021529
 [93654.422878] usb-storage 4-2:1.0: USB Mass Storage device detected
 [93654.424483] scsi host2: usb-storage 4-2:1.0
 [93654.424730] usbcore: registered new interface driver usb-storage
 [93654.537765] usbcore: registered new interface driver uas
 [93655.428162] scsi 2:0:0:0: Direct-Access     FUJIFILM USB-DRIVEUNIT    1.00 PQ: 0 ANSI: 0 CCS
 [93655.430334] sd 2:0:0:0: Attached scsi generic sg2 type 0
 [93655.441118] sd 2:0:0:0: [sdb] 1023120 512-byte logical blocks: (524 MB/500 MiB)
 [93655.446155] sd 2:0:0:0: [sdb] Write Protect is off
 [93655.446165] sd 2:0:0:0: [sdb] Mode Sense: 07 00 00 00
 [93655.451140] sd 2:0:0:0: [sdb] Incomplete mode parameter data

 [93655.451149] sd 2:0:0:0: [sdb] Assuming drive cache: write through
 [93655.479130]  sdb: sdb1
 [93655.502141] sd 2:0:0:0: [sdb] Attached SCSI removable disk
 [93661.314157] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

---

### Post by hanspeteriv on 2017-01-02
I can't help with fsck, sorry. But a 'fix' might be to transfer all your files from the camera to your laptop and then use the camera's menu to reformat the SD card. There must be a better way though.

I notice that on your 16.04 desktop xHCI (USB 3) is used while your laptop uses UHCI (USB 1.x?)

[  685.851056] usb 1-2: new full-speed USB device number 36 using **xhci_hcd**
vs
[93653.312067] usb 4-2: new full-speed USB device number 2 using [B]uhci_hcd

[/B]What happens when you plug your camera into a USB 2 port on your desktop? Maybe your Camera doesn't like USB 3 ports? What is the exact model of your camera?

---

### Post by 6-dave-9 on 2017-01-02
Thanks for the great thoughts on this.  I have been using an empty card so I did reformat it.  No change.  Tried the rear USB ports which I assume are slower than the front ones.  No change.  Took some pictures with the camera in case it was a matter of there being no file.  No change, still didn't connect.  

Finally dragged out my old card reader.  I had quit using it because somewhere in a 14.04 update it just stopped working.  Hooked it up and it's working fine with 16.04.  

I prefer to use a card reader and had switched to USB only because the card reader had quit in 14.04.  With it working now I'm going to give up on connecting with USB and use the card reader.

Thanks again for you help. 

Dave

---

### Post by hanspeteriv on 2017-01-02
You're welcome, I'm glad you found a solution that works for you.

---

