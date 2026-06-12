---
title: "Plugging in USB devices causes machine to reboot"
date: 2008-11-14
forum: Hardware
---

### Post by Nancy Dz on 2008-11-14
I have a new 8.04 install.

Every time I plug in any usb device, the machine reboots.

But if I plug in the device before I turn the machine on and boot with it plugged in works fine.

Any way to fix this so I can plug jump drives in when ever I want to instead of having to shut down and start up to get them to work?  It shouldn't have to do that.  Also does that with other USB devices as well.

If there is some code I need to enter to do it then please post what that is too... I am a new user and don't know much code yet.  

Thanks!  :)

---

### Post by Nancy Dz on 2008-11-15
Has anyone else had this problem before?

Is it a common error?

---

### Post by DieB on 2008-11-16
Never ahd that problem - don't know how it comes to be ....

is it a fresh install you use? if not what did you change?

what release are you using?

this might make it easier for others to help you.

---

### Post by Nancy Dz on 2008-11-16
Yes it is a new install of 8.04 and it has been having that problem from the beginning.

Thanks.

---

### Post by DieB on 2008-11-17
All updates installed?

---

### Post by Nancy Dz on 2008-11-17
Yes it is up to date.

---

### Post by Yezinki on 2008-11-17
Do yo have a dual boot with windows on this machine?

---

### Post by Nancy Dz on 2008-11-18
It is a clean install of Hardy on a new hard drive.
It is my only operating system.

Thanks, sorry I didn't think to answer that right away.

---

### Post by Yezinki on 2008-11-18
Are the usb devices plugged in when you turn the machine ON?

OR do you plug them in later?

Probably it's the settings in your BIOS.

Just my thoughts,

Regards,

Yezinki.

---

### Post by Nancy Dz on 2008-11-18
When I plug in any usb device in like you would normally when the operating system is up, the machine reboots.

But if I plug in the device before I turn the machine on and boot with it plugged in works fine.

I had a hard drive with windows installed previously and the USB worked fine so I think that would mean it wasn´t the bios wouldn't it? FYI... I have removed the old windows hard drive completely.  

Thanks for helping me try to figure this out!  :)

Sorry that I don't know enough about Linux yet to know what info would have been more helpful to put in my original post.

---

### Post by Yezinki on 2008-11-18
I am Novice (MD trying to become a Geek..failing miserably lol), just try to use my neurons & help if possible.

Personally feel its your machine's BIOS....could be wrong.

What Ubuntu are you running.....if 8.10 was it a clean install or a upgrade?

Regards,

Yezinki.

---

### Post by finito on 2008-11-18
OH my, asking the same questions again and again, for which the answer are already there.

Your USB port is/are busted, You need to get a POWERED external usb hub. You should have at least one USB port where this doesn't happen if not then they are probably gone.

Good Luck

---

### Post by Nancy Dz on 2008-11-18
All ports work completely fine on windows.

It is a linux issue.

Thanks for your suggestions. :)

---

### Post by finito on 2008-11-18
Hmm strange, did you try getting all the updates.

---

### Post by Yezinki on 2008-11-18
Your main board's bios needs to be updated.....run a bios agent scan.....to confirm it.

Bios agent scanning is done only in windows mode.....

Regards,

Yezinki.

---

### Post by Nancy Dz on 2008-11-19
I update very regularly.  The updates don't seem to affect it.  I haven't tried upgrading to  8.10 to see if that would help yet but since I am so new to linux I thought I should troubleshoot in 8.04 first.

---

### Post by Yezinki on 2008-11-19
Check if there is an update for your main board's bios?

I know your Ubuntu is updated.

Regards,

Yezinki.

---

### Post by Nancy Dz on 2008-11-19
I don't see how it can be the bios if they work completely fine with windows but don't work right when I put in a new hard drive with linux.

It seems like it must be some kind of linux issue to me.

---

### Post by Nancy Dz on 2008-11-19
Hmmm... could it be a driver issue even though I have had no other issues with drivers in linux?

---

### Post by DieB on 2008-11-19
instead of trying to brick your system by bios-update.

i would recommend to use either/both 7.10 and 8.10 releases of ubuntu to see if it makes any difference. [I guess u needn't to install it, just start the live-cd and plug in/out usb] If the problem occurs still. Pls lett us know what > lspci | grep USB spits out.

so we can look if similiar problems have been reported on that hardware.

---

### Post by Nancy Dz on 2008-11-20
> **DieB said:**
> instead of trying to brick your system by bios-update.

i would recommend to use either/both 7.10 and 8.10 releases of ubuntu to see if it makes any difference. [I guess u needn't to install it, just start the live-cd and plug in/out usb] If the problem occurs still. Pls lett us know what  spits out.

so we can look if similiar problems have been reported on that hardware.

Thanks! I will try that and see what happens.
I have never tried creating a live cd before but I will try that. :)

---

### Post by Yezinki on 2008-11-20
> **Nancy Dz said:**
> Thanks! I will try that and see what happens.
I have never tried creating a live cd before but I will try that. :)

[http://biosagentplus.com/?PHPSESSID=it3vkgbh80cdepur9h0mo9vha7](http://biosagentplus.com/?PHPSESSID=it3vkgbh80cdepur9h0mo9vha7)

Try this in windows.

---

### Post by Nancy Dz on 2008-11-20
I am not comfortable with the idea of flashing my bios.
Thanks though.  :)

---

### Post by Yezinki on 2008-11-21
No problem do what you feel comfy with!

Regards,

Yezinki.

---

### Post by Nancy Dz on 2008-11-23
Thanks so much for your help everyone! :D

I created a live cd for 8.10 and USB did not reboot the machine.  It also did not seem to recognize them and they did not appear in my computer when I plugged them in.

I think that may be partly because I could not log in as myself on the computer running live cd therefore I only had limited access.

What's next?  :)


FYI... Removable drives and media doesn't have a storage tab on in my system.

Several books have said to go to that tab and check Mount removable drives when hot-plugged, mount removable media when inserted, and browse removable media when inserted.  Is there some package/synaptic package I have to install for this tab to show up in removable drive and media?

Or is that tab not a part of the 8.04 instalation?

Can someone else with 8.04 check that for me?  :D

---

### Post by DieB on 2008-11-24
Ubuntu should atleast show you newly inserted USB-media under Places - on some machine it takes a bit (but no longer than two minutes) - if no new media appears in "places" it might be something with the hardware recognition.

so pls run:

> lspci

in terminal (Applications-Asse..) and post what it throws out (really interesting are those parts with usb in it), so we can check if others had similar problems with this hardware.

---

### Post by Yezinki on 2008-11-24
```

FYI... Removable drives and media doesn't have a storage tab on in my system.
```

Woh that's new....

Regards,

Yezinki.

---

### Post by Nancy Dz on 2008-11-29
lspci | grep USB

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

---

### Post by skozzy on 2008-11-30
I had this problem, linux or windows same problem, I checked the voltage from the power supply and saw a momentary drop when the usb device (anything usb) was plugged in. So I replaced the power supply with a higher powered one and it now works fine.

So that might be something for you to look in to.

---

### Post by Nancy Dz on 2008-11-30
Hmmm.... USB works fine in windows.  I don't think my power supply would cause that problem in linux only.  It started when I installed linux.

---

### Post by skozzy on 2008-11-30
Oh well, it was worth mentioning.

---

### Post by Nancy Dz on 2008-11-30
Yeah, I never would have thought of that.  Thanks.

---

### Post by t1m44 on 2009-01-28
I've had this problem over several releases of Ubuntu but for me it's sporadic. I'm currently on Intrepid, with kernel 2.6.27-9-generic.

I would have thought it's an electrical / motherboard problem, but the kernel always detects and scans the device before the reboot. Here's the relevant entries from /var/log/syslog. The only entries within an hour of the crash were from CRON (only the last of those entries is shown). Other logs with entries at the same time (kern, messages, debug) are almost identical.

Jan 28 11:10:01 hobbes /USR/SBIN/CRON[10077]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 11:11:34 hobbes kernel: [ 9890.708016] usb 1-2: new high speed USB device using ehci_hcd and address 3
Jan 28 11:11:34 hobbes kernel: [ 9890.862223] usb 1-2: configuration #1 chosen from 1 choice
Jan 28 11:11:34 hobbes kernel: [ 9890.946793] usbcore: registered new interface driver libusual
Jan 28 11:11:35 hobbes kernel: [ 9890.964506] Initializing USB Mass Storage driver...
Jan 28 11:11:35 hobbes kernel: [ 9890.966378] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 28 11:11:35 hobbes kernel: [ 9890.967226] usbcore: registered new interface driver usb-storage
Jan 28 11:11:35 hobbes kernel: [ 9890.967880] USB Mass Storage support registered.
Jan 28 11:11:35 hobbes kernel: [ 9890.968684] usb-storage: device found at 3
Jan 28 11:11:35 hobbes kernel: [ 9890.968688] usb-storage: waiting for device to settle before scanning
Jan 28 11:11:40 hobbes kernel: [ 9895.968622] usb-storage: device scan complete
Jan 28 11:13:10 hobbes syslogd 1.5.0#2ubuntu6: restart.


I'm really not sure how to diagnose this. Can anyone recommend next steps? Thanks.

---

### Post by t1m44 on 2009-01-28
I forgot to mention that the crash was after plugging in a thumb drive and it took a couple seconds before it restarted. I also use a usb printer, scanner, webcam, camera, external HD, and previously a usb keyboard. The device doesn't seem to matter and it only happens maybe 1 in 15 times. It also doesn't seem matter how many devices I'm using at once. For the above crash, I only had a mouse plugged in:

$ lsusb 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

thanks again

---

### Post by t1m44 on 2009-01-31
Here's /var/log/syslog when my system didn't crash after plugging in that same device:

Jan 31 14:19:02 hobbes kernel: [  285.332026] usb 1-2: new high speed USB device using ehci_hcd and address 3
Jan 31 14:19:02 hobbes kernel: [  285.482834] usb 1-2: configuration #1 chosen from 1 choice
Jan 31 14:19:03 hobbes kernel: [  285.647868] usbcore: registered new interface driver libusual
Jan 31 14:19:03 hobbes kernel: [  285.682328] Initializing USB Mass Storage driver...
Jan 31 14:19:03 hobbes kernel: [  285.686368] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 31 14:19:03 hobbes kernel: [  285.688484] usbcore: registered new interface driver usb-storage
Jan 31 14:19:03 hobbes kernel: [  285.688988] USB Mass Storage support registered.
Jan 31 14:19:03 hobbes kernel: [  285.689644] usb-storage: device found at 3
Jan 31 14:19:03 hobbes kernel: [  285.689652] usb-storage: waiting for device to settle before scanning
Jan 31 14:19:08 hobbes kernel: [  290.689139] usb-storage: device scan complete
Jan 31 14:19:08 hobbes kernel: [  290.690637] scsi 4:0:0:0: Direct-Access     Generic  USB  SD Reader   1.00 PQ: 0 ANSI: 0 CCS
Jan 31 14:19:08 hobbes kernel: [  290.695236] sd 4:0:0:0: [sdc] 3854336 512-byte hardware sectors (1973 MB)
Jan 31 14:19:08 hobbes kernel: [  290.696651] sd 4:0:0:0: [sdc] Write Protect is off
Jan 31 14:19:08 hobbes kernel: [  290.696661] sd 4:0:0:0: [sdc] Mode Sense: 4b 00 00 08
Jan 31 14:19:08 hobbes kernel: [  290.696665] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan 31 14:19:08 hobbes kernel: [  290.703881] sd 4:0:0:0: [sdc] 3854336 512-byte hardware sectors (1973 MB)
Jan 31 14:19:08 hobbes kernel: [  290.704970] sd 4:0:0:0: [sdc] Write Protect is off
Jan 31 14:19:08 hobbes kernel: [  290.704980] sd 4:0:0:0: [sdc] Mode Sense: 4b 00 00 08
Jan 31 14:19:08 hobbes kernel: [  290.704984] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan 31 14:19:08 hobbes kernel: [  290.705949]  sdc: sdc1
Jan 31 14:19:08 hobbes kernel: [  290.707872] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Jan 31 14:19:08 hobbes kernel: [  290.708473] sd 4:0:0:0: Attached scsi generic sg4 type 0
Jan 31 14:19:09 hobbes hald: mounted /dev/sdc1 on behalf of uid 1000

I think it's work noting that when it crashes it takes a while before the system resets. After plugging the device in, it's still ok for a second or two. The screen goes blank for a few seconds and then the system restarts.

Any ideas?

---

### Post by Nancy Dz on 2009-01-31
Still having the problem... 
Anybody know what this means???

Got an error box that says...

USB View error

Verify that you have USB compiled into your kernel,
have the USB core modules loaded and have the usbdevfs 
filesystem mounted.

---

### Post by DominaDoom on 2009-02-11
> **Nancy Dz said:**
> Still having the problem... 
Anybody know what this means???

Got an error box that says...

USB View error

Verify that you have USB compiled into your kernel,
have the USB core modules loaded and have the usbdevfs 
filesystem mounted.

I'm getting the same USB View error.  My USB ports are sending power to devices, but Intrepid 8.10 will not detect any devices with any programs that I have installed.  Repeat, "NO USB DETECTION IN INTREPID".  This is not a new problem.  My USB Modem sporadically works, and I didn't realize that it was due to the lack of USB device detection until I tried to detect my Nikon D80 and my SD card reader.  Both of these photo devices should have immediate detection in 8.10 according to the three different Ubuntu books that I have.  I occasionally have had issues while booting with my USB modem plugged into the USB port.  My boot will freeze, and I thought that it was due to detecting the USB modem, but it did start to boot with the modem plugged in a few weeks ago, and I was able to detect the modem and use it after the successful boot.  So this problem has been on again off again, but I never know when it will work and when it won't.  It's really inconvenient.

---

### Post by jeli on 2009-03-09
I had the same problem.  As soon as I plug in my usb thumb drive, the system restarts.  It's a problem with nautilus trying to browse the newly inserted media.

solution can be found on this page: [https://answers.launchpad.net/ubuntu/+question/30501](https://answers.launchpad.net/ubuntu/+question/30501)

---

