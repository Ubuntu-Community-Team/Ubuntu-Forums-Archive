---
title: "Cannot connect Treo 650 to my laptop"
date: 2008-10-29
forum: Hardware
---

### Post by davelbarton on 2008-10-29
OK, I'm having trouble getting my laptop, an HP Pavillion, to connect with my Treo 650.  This thing has three USB ports, and I don't know how to figure out which one is being looked at, and which device to connect to.  I have tried, under gpilotd, just about every combination they give me.  After I did some finagling to the fsck file as advised, usb appeared on the list, but that doesn't work either.  In fact, gpilotd seems to have problems as it stands.  When I start gpilotd by hand, after killing all possible daemons that may be lurking, I get this response:

root@Hypno:/home/dlb# killall -9 gpilotd
[1]+  Killed                  gpilotd
root@Hypno:/home/dlb# gpilotd
gpilotd-Message: gnome-pilot 2.0.15 starting...
gpilotd-Message: compiled for pilot-link version 0.12.3
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] 

(gpilotd:16872): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

(gpilotd:16872): libgpilotdcm-WARNING **: Number of devices is configured to 0

(gpilotd:16872): libgpilotdcm-WARNING **: No accessible devices available

(gpilotd:16872): libgpilotdcm-WARNING **: Number of PDAs is configured to 0
gpilotd-Message: Activating CORBA server
gpilotd-Message: bonobo_activation_active_server_register = 2
gpilotd-Message: Cannot register gpilotd because already active

I have no idea what to do with these warnings, nor do I know how to figure out which port this thing is on.  The cable itself provides power, and has worked on other computers, so I don't think it is the cable.  An appeal to dmesg gets this:

[61229.680087] usb 1-1: new full speed USB device using ohci_hcd and address 2
[61229.850807] usb 1-1: configuration #1 chosen from 1 choice
[61333.048628] usb 1-1: USB disconnect, address 2
[61341.248569] usb 1-1: new full speed USB device using ohci_hcd and address 3
[61341.418451] usb 1-1: configuration #1 chosen from 1 choice
[61418.360121] usb 1-1: USB disconnect, address 3
[

It does that all the way up through 15, then this appears:

[72629.615073] usbcore: usbfs: unrecognised mount option "none" or missing value
[72629.615117] usbcore: usbfs: mount parameter error:

I cannot get pilot-xfer to work on any device I can think of.  All the various permutations of the devices give this:

root@Hypno:/home/dlb# pilot-xfer -p /dev/ttyUSB1 -l
   Unable to bind to port: /dev/ttyUSB1
   Please use --help for more information

So I am pretty much stymied.  Can anyone help here?  I've gone through *lots* of logs that I found on google, and nothing seems to help.

---

### Post by davelbarton on 2008-10-30
Ah, the traffic, the traffic!  I'm hoping if I move this to the top of the heap in the morning, it will get a reply....

---

### Post by jbg7474 on 2008-10-30
BUMP!
Also can't get my Treo 755p to connect with gpilotd in Intrepid--this worked flawlessly in Hardy.  Can't get it done, no way, no how.  Driving me absolutely insane.

---

### Post by davelbarton on 2008-10-31
And bump again, with more data.  My flash memory stick also is not working.  I can see it in the device list (it is listed in fstab, for example, and the proc/bus/usb is certainly there.  But I can't mount it at a mount point, and I still can't get my USB to recognize my Treo.  I'm convinced this is all part of the same problem, and I really, *really* need help.

---

### Post by jbg7474 on 2008-10-31
I also had trouble getting a thumbdrive to mount!!  I didn't think they were related, but maybe they are!

Would someone who knows about the changes made between Hardy and Intrepid regarding USB hardware please illuminate?!?

---

### Post by jbg7474 on 2008-10-31
Discovered that I can mount the usb thumb drive, but only with as root.  Once mounted, I can read the files, but can't write, except as root.  Pretty annoying.  Have no idea where to make that adjustment.

---

### Post by jbg7474 on 2008-10-31
Oh, never mind.  My usb stick problem was because I had an entry in /etc/fstab for an ntfs usb drive that I was using.  So...plugged in the stick without the other drive plugged in, and it was trying to read it as ntfs, thus the problem.  Once I commented out the pertinent line in /etc/fstab, all was well.  

So, I seem to only have a problem with my Treo.  But I definitely still have that problem!!

---

### Post by themorningflight on 2008-11-01
I hope someone comes up with your answer soon as I have the same problem with my Treo 680. Worked great in Gutsy and Hardy but after upgrading to Intrepid it no longer connects. Serious problem as no longer synchronising diary :(

---

### Post by pistos on 2008-11-01
I can longer sync my Treo 680 with my computer since upgrading to 8.10 either. Everything worked great under 8.04 and lower.

---

