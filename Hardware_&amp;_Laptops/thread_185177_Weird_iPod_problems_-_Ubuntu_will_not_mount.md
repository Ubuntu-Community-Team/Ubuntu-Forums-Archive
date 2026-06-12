---
title: "Weird iPod problems - Ubuntu will not mount"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by snooo on 2006-05-31
Bought a brand new iPod cable this week to replace my old one, only to find that Dapper refuses to mount the drive. It has worked in previous version of the operating system (including Dapper), so I am a little confused.

When I plug in the iPod, the display will flash "Do not disconnect" for a few seconds, before dissapearing. Nautilius shows no sign of the iPod either in Places or computers.

This is the output I got from dmesg:```
[4295042.444000] usb-storage: device found at 21
[4295042.444000] usb-storage: waiting for device to settle before scanning
[4295047.549000] usb 5-1: reset high speed USB device using ehci_hcd and address 21
[4295047.667000] usb 5-1: can't restore configuration #1 (error=-71)
[4295047.667000] usb 5-1: USB disconnect, address 21
[4295047.668000] usb-storage: device scan complete
[4295047.772000] usb 5-1: new high speed USB device using ehci_hcd and address 22
[4295047.890000] usb 5-1: can't set config #1, error -71
[4295047.994000] usb 5-1: new high speed USB device using ehci_hcd and address 23
[4295048.114000] scsi5 : SCSI emulation for USB Mass Storage devices
[4295048.114000] usb-storage: device found at 23
[4295048.114000] usb-storage: waiting for device to settle before scanning
[4295053.115000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4295053.115000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4295053.117000] SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
[4295053.118000] sda: Write Protect is off
[4295053.118000] sda: Mode Sense: 64 00 00 08
[4295053.118000] sda: assuming drive cache: write through
[4295053.120000] SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
[4295053.121000] sda: Write Protect is off
[4295053.121000] sda: Mode Sense: 64 00 00 08
[4295053.121000] sda: assuming drive cache: write through
[4295053.121000]  sda: sda1 sda2
[4295053.187000] sd 5:0:0:0: Attached scsi removable disk sda
[4295053.187000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[4295053.188000] usb-storage: device scan complete
[4295053.858000] usb 5-1: reset high speed USB device using ehci_hcd and address 23
[4295053.974000] usb 5-1: can't restore configuration #1 (error=-71)
[4295053.974000] usb 5-1: USB disconnect, address 23
[4295053.974000] sd 5:0:0:0: SCSI error: return code = 0x70000
[4295053.974000] end_request: I/O error, dev sda, sector 80191
[4295053.974000] Buffer I/O error on device sda1, logical block 40064
[4295053.975000] sd 5:0:0:0: SCSI error: return code = 0x70000
[4295053.975000] end_request: I/O error, dev sda, sector 80193
[4295053.975000] Buffer I/O error on device sda1, logical block 40065
[4295053.975000] sd 5:0:0:0: SCSI error: return code = 0x70000
[4295053.975000] end_request: I/O error, dev sda, sector 80195
[4295053.975000] Buffer I/O error on device sda1, logical block 40066
[4295053.976000] sd 5:0:0:0: SCSI error: return code = 0x10000
[4295053.976000] end_request: I/O error, dev sda, sector 80197
[4295053.976000] Buffer I/O error on device sda1, logical block 40067
[4295053.980000]  5:0:0:0: rejecting I/O to dead device
[4295053.980000] Buffer I/O error on device sda1, logical block 40064
[4295053.980000] Buffer I/O error on device sda1, logical block 40065
[4295053.980000] Buffer I/O error on device sda1, logical block 40066
[4295053.980000] Buffer I/O error on device sda1, logical block 40067
[4295053.981000]  5:0:0:0: rejecting I/O to dead device
[4295053.981000] Buffer I/O error on device sda1, logical block 40128
[4295053.981000] Buffer I/O error on device sda1, logical block 40129
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.982000]  5:0:0:0: rejecting I/O to dead device
[4295053.983000]  5:0:0:0: rejecting I/O to dead device
[4295053.983000]  5:0:0:0: rejecting I/O to dead device
[4295053.983000]  5:0:0:0: rejecting I/O to dead device
[4295053.983000]  5:0:0:0: rejecting I/O to dead device
[4295053.983000]  5:0:0:0: rejecting I/O to dead device
[4295053.983000]  5:0:0:0: rejecting I/O to dead device
[4295053.984000]  5:0:0:0: rejecting I/O to dead device
[4295053.984000]  5:0:0:0: rejecting I/O to dead device
[4295053.984000]  5:0:0:0: rejecting I/O to dead device
[4295053.984000]  5:0:0:0: rejecting I/O to dead device
[4295053.984000]  5:0:0:0: rejecting I/O to dead device
[4295053.984000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.985000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.986000]  5:0:0:0: rejecting I/O to dead device
[4295053.987000]  5:0:0:0: rejecting I/O to dead device
[4295053.995000]  5:0:0:0: rejecting I/O to dead device
[4295053.995000]  5:0:0:0: rejecting I/O to dead device
[4295053.995000]  5:0:0:0: rejecting I/O to dead device
[4295053.995000]  5:0:0:0: rejecting I/O to dead device
[4295053.995000] sda : READ CAPACITY failed.
[4295053.995000] sda : status=0, message=00, host=1, driver=00
[4295053.995000] sda : sense not available.
[4295053.996000]  5:0:0:0: rejecting I/O to dead device
[4295053.996000] sda: Write Protect is off
[4295053.996000] sda: Mode Sense: 00 00 00 00
[4295053.996000] sda: assuming drive cache: write through
[4295054.014000]  5:0:0:0: rejecting I/O to dead device
[4295054.079000] usb 5-1: new high speed USB device using ehci_hcd and address 24
[4295054.195000] usb 5-1: can't set config #1, error -71
[4295054.298000] usb 5-1: new high speed USB device using ehci_hcd and address 25
[4295054.412000] usb 5-1: device descriptor read/all, error -71
[4295054.515000] usb 5-1: new high speed USB device using ehci_hcd and address 26
[4295054.529000] usb 5-1: can't set config #1, error -71
[4295054.632000] usb 5-1: new high speed USB device using ehci_hcd and address 27
[4295054.645000] usb 5-1: can't set config #1, error -71


```

Can anyone help me identify the source of this issue?

---

### Post by !nkubus on 2006-05-31
Have you formatted it with fat32?. And the other thing I always forget when I install new ipods on linux, is that they need to be "initialized" in Itunes before. Thefore the bad nes is that you need a windows machine and Itunes... to initialize it.

Hope it helps a bit


**EDIT sorry, I miss the cable part...*** my reply dosen't make sense any more

---

### Post by lkagan on 2006-05-31
Assuming you just bought a new cable and not a new iPod, don't worry about the initialization.  I don't recommend formatting the iPod with FAT32.  Linux handles hfsplus (native iPod) filesystems just fine.  However, in Breezy, you need to build (compile) your own fsck.hfsplus package in order to fix an iPod that you may have unplugged incorrectly.  Maybe in Dapper it's already included.  So if you have used the iPod previously, install fsck.hfsplus and run that on the iPod and that may fix your problem.

Now, I'm not sure if you machine is even able to read the iPod as a block device on /dev/sda.  I assume you got a new cable to replace your old one because of some similar issue you were having.  If that's the case, it may be a bad USB port or driver.  Can you connect other USB devices like a digital camera, keyboard, mouse, flashdrive?  If you can connect other USB devices successfully, that leaves the possiblity of a bad port on the iPod.  You might want to try plugging in the iPod into another computer and see if it recognizes it.  If another computer does recognize it, the problem is beyond my current knowledge.  

Again, it looks like there's bad block so get fsck.hfsplus.  This won't be fun if you've never build software before.  You'll have to get the build tools from the repository then get the source code which was created for BSD and then patch it with a linux kernel patch, then compile it.  There's a HOWTO that I followed somewhere that guided me through it step-by-step so I'm sure you'll be able to find it if you look.

Good luck and let us know how it turns out!

Larry

---

### Post by snooo on 2006-05-31
Um, it was initalised a long time ago. I've had this iPod since January - its a 4G click-wheel black and white edition, formatted under windows (FAT). So there shouldn't be any problems on that score.

---

### Post by snooo on 2006-05-31
Oh, and it did appear in Nautilius earlier - only to dissapear again :-/

---

### Post by Aewheros on 2006-05-31
I only have one thing to say to iPod users: use [Rockbox]("http://www.rockbox.org/").

It allows you to play open source formats such as ogg, mpc and flac.

---

### Post by snooo on 2006-05-31
[QUOTE=Aewheros]I only have one thing to say to iPod users: use [Rockbox]("http://www.rockbox.org/").

It allows you to play open source formats such as ogg, mpc and flac.[/QUOTE]

However much I'd love to use Rockbox, I currently can't even see my iPod's harddrive...

---

### Post by lkagan on 2006-05-31
I would then suggest you try dosfsck to check the drive for errors.  

Larry

---

### Post by snooo on 2006-05-31
[QUOTE=lkagan]Now, I'm not sure if you machine is even able to read the iPod as a block device on /dev/sda.  I assume you got a new cable to replace your old one because of some similar issue you were having.  If that's the case, it may be a bad USB port or driver.  Can you connect other USB devices like a digital camera, keyboard, mouse, flashdrive?  If you can connect other USB devices successfully, that leaves the possiblity of a bad port on the iPod.  You might want to try plugging in the iPod into another computer and see if it recognizes it.  If another computer does recognize it, the problem is beyond my current knowledge.  

Again, it looks like there's bad block so get fsck.hfsplus.  This won't be fun if you've never build software before.  You'll have to get the build tools from the repository then get the source code which was created for BSD and then patch it with a linux kernel patch, then compile it.  There's a HOWTO that I followed somewhere that guided me through it step-by-step so I'm sure you'll be able to find it if you look.

Good luck and let us know how it turns out!

Larry[/QUOTE]Thanks for the suggestion... I may look into formatting it - however I only have access to a PC version of iTunes and so whether I could initalise a HFS formatted iPod remains to be seen. It definiatly seems to be a problem with the hard drive tho...

---

### Post by lkagan on 2006-05-31
I wouldn't suggest formatting unless there is no other option.  The fsck.hfsplus I suggested only fixes an existing filesystem.  But on your FAT iPod use dosfsck, which does the same thing.  Again, this will perform the same thing as a windows checkdisk.  It will look for errors on the drive and try to fix them.  You probably won't lose anything.  If you do, it might be a single track and that's it.  And what's even better is that you already have dosfsck on your system!

Larry

---

### Post by snooo on 2006-05-31
[QUOTE=lkagan]I wouldn't suggest formatting unless there is no other option.  The fsck.hfsplus I suggested only fixes an existing filesystem.  But on your FAT iPod use dosfsck, which does the same thing.  Again, this will perform the same thing as a windows checkdisk.  It will look for errors on the drive and try to fix them.  You probably won't lose anything.  If you do, it might be a single track and that's it.  And what's even better is that you already have dosfsck on your system!

Larry[/QUOTE]

I'd try dosfsck, but I can't get the thing to mount for much longer than a few seconds... I'm also having similar problems in Windows. Me thinks I'll have to take it into an Apple store to get it checked out...

Thanks anyway.

---

### Post by lkagan on 2006-05-31
You shouldn't mount the iPod when running dosfsck.  Any filesystem checking on any filesystem should be done when the drive is unmounted.  So you wouldn't use dosfsck /media/iPod, instead you would use dosfsck /dev/sda1 (or sda2).

Larry

---

### Post by Elpram on 2006-09-17
Sorry to dredge this thread up but I seem to be having this exact problem, and it doesn't seem to have been resolved.  I plug in my ipod in Ubuntu (I'm new to linux) and it flashes Do Not Disconnect for a few seconds, then goes to the menu, and back and forth until the battery dies.  I tried the few tutorials with ipodslave and gtkpod; all to no avail.  The best I got was a device showing up when I connected, but it couldn't mount the volume.  I don't really know what to do, and I have very limited knowledge of linux (a week tops :P) but it works perfectly on windows, and im quite certain its FAT.  Let me know if there's anything you need (dmesg output mayhaps?)

Thanks!

---

### Post by Elpram on 2006-09-18
Well I found the solution.

I plugged it into the USB port in the back of my computer.

Anyone have any idea why the front ones wouldn't work?  Or how I could fix this? (not very urgent though... :P)

---

