---
title: "Touro- External HDD not detecting with Ubuntu 11.10"
date: 2013-12-26
forum: Hardware
---

### Post by praveennin on 2013-12-26
Dear All:

I have bought an External HDD today. My Concern is , it is not getting detected by Ubuntu. Since I'm new to ubuntu, I don't have any idea of how to fix this issue.
Could any one please help me out?

Thanks in Advance,
Buddy.

---

### Post by sanderj on 2013-12-26
Is your external HDD a USB-drive? If so, disconnect the drive, open a terminal (CTRL ALT T), type "lsusb", then connect the drive and again type "lsusb": there must be one new line. Can you post that line here?

Furthermore, after connecting the USB drive, in the terminal type "dmesg", can copy-paste the last 15 into this thread.

---

### Post by mörgæs on 2013-12-26
11.10 is out of support. Better to begin with a fresh install of 12.04 or 13.10.

---

### Post by praveennin on 2013-12-27
hi sanderj

New line after "lsusb" ----> Bus 002 Device 005: ID 4971:1020 SimpleTech 

After "dmes", here are the last 15 lines

[ 7939.121712] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121725] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121738] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121748] sd 6:0:0:6: [sdh] READ CAPACITY failed
[ 7939.121754] sd 6:0:0:6: [sdh]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 7939.121764] sd 6:0:0:6: [sdh] Sense not available.
[ 7939.121774] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121786] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121805] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121816] sd 6:0:0:6: [sdh] Write Protect is off
[ 7939.121824] sd 6:0:0:6: [sdh] Mode Sense: 00 00 00 00
[ 7939.121834] sd 6:0:0:6: rejecting I/O to offline device
[ 7939.121843] sd 6:0:0:6: [sdh] Asking for cache data failed
[ 7939.121851] sd 6:0:0:6: [sdh] Assuming drive cache: write through
[ 7939.122154] sd 6:0:0:6: [sdh] Attached SCSI disk

Thanks,
Praveen.

---

### Post by praveennin on 2013-12-27
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar939075_12.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=939075") 				 				 					 						 	[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") 	 

Upgrading the version is not that easy since it is my office lap, I need to reinstall everything from the scratch !! So help me out with the best possible option.

---

### Post by sanderj on 2013-12-27
> **praveennin said:**
> [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar939075_12.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=939075") 				 				 					 						 	[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") 	 

Upgrading the version is not that easy since it is my office lap, I need to reinstall everything from the scratch !! So help me out with the best possible option.

So the Google search term is: "Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK" " rejecting I/O to offline device"

Live-boot Ubuntu 13.10 from DVD or USB-stick (no need it install it), and connect the drive again ... what is the result?

---

