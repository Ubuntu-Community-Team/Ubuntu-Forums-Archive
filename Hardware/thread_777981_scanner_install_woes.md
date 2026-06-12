---
title: "scanner install woes"
date: 2008-05-01
forum: Hardware
---

### Post by labud on 2008-05-01
xubuntu 7.10 w/ kde on P4 Biostar P4M80-M4 2.4gHZ 2.0mb ram HP Scanjet 3970
BTW, I am a beginner, so I had posted this in Beginner Talk, but in after thot maybe itshould go here. Sorry.

I have been struggling to get my scanner working using various info found thru google pages.
My last attempt using [http://tldp.org/HOWTO/Scanner-HOWTO/intro.html](http://tldp.org/HOWTO/Scanner-HOWTO/intro.html) has netted me some success, in that ubuntu finally sees scanner.

sane-find-scanner
found USB scanner (vendor=0x03f0, product=0x2305, chip=rts8822L-01H?) at libusb:005:009

following directions [section5 Testing your scanner] thru shell I did:

labud@LGraBow:~$ scanimage --list-devices
device `hp3900:libusb:005:009' is a Unknown RTS8822 chipset based flatbed scanner
labud@LGraBow:~$ scanimage hp3900:libusb:005:009 --format pnm > outfile.pnm
scanimage: open of device hp3900:libusb:005:009 failed: Access to resource has been denied

the above website then tells me I must [Section 7 TroubleShooting] have read & write access and to do that the following command is to be called

chown root.scanner /dev/usb/scanner*

...where root.scanner are the owner and group the device will now belong to. Obviously the specific command will vary by your system and the type of device, whether /dev/sg* on SCSI scanners, etc. It is important that you change the ownership of the device node itself and not the symlink; symlinks' ownerships are affected only by changing the parent devices or files they point to.

To see if your user account is a member of the group in question, as root issue the following command: grep -e scanner /etc/group. You should see something like the following:

scanner:x:103:

this was the respose I got:
labud@LGraBow:~$ sudo grep -e scanner /etc/group
scanner:x:104:hplip,labud,root

As far as I know I am labud, so why wouldn't I have access to scanner?


then I am supposed to do the following:

After this it's simply a matter of allowing read and write access for the user in question of the device like so:

# chmod g+rw /dev/usb/scanner0

I have looked in /dev/usb and the only file there is Ip0

I am lost. Can anyone help me, please?

P.S. On a more positive note, I have successfully loaded video driver for S3 Unichrome, my printer works and I am running Winmx thru Wine. So all is not bad, but this scanner problem is infuriating!

---

### Post by labud on 2008-05-04
Well Well Well
Problem seems to have solved itself!
On my next reboot, I found that scanner was working properly.
So, whatever I [?] did, maybe that [obviously] did the trick.

Onward and Upward

---

