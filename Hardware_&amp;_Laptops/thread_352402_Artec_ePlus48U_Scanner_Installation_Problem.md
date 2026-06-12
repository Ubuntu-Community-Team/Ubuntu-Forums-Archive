---
title: "Artec ePlus48U Scanner Installation Problem"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by drs305 on 2007-02-03
Edited: Fixed by adding driver file to several folders (don't know which one worked).  Is there a way to delete the post before anyone replies?

***

I've been reading posts for the past hour and still can't get my Artec ePlus48U scanner to work. I am a Linux newbie so I know enough to realize there are lots of possible reasons. I've shotgunned my attempts so I'm not sure exactly where I'm at, but I'll try...

I have sane and xsane applications. When I use lsusb it recognizes my scanner:
Bus 004 Device 002: ID 05d8:4003 Ultima Electronics Corp. Artec E+ 48U

Following the directions of another post, I put the Artec48.usb driver file found on the installation CD (from the XP directory?) into the following newly created location and put this line into artec_eplus48u.conf:
option artecFirmwareFile /usr/share/sane/artec_eplus48u/Artec48.usb
(note to self: I'm invoking xsane through the main Graphics/XSane Image Scanner menu, so I don't know if it's looking at the sane folder or not)

When I try to run the program, i get "No devices available".

I don't see the usb scanner mounted anywhere if it should be ( and don't know how to if so)

The "No devices available" suggests some possibilities, including:
Permissions do not allow, try as root  >> How?
The backend is not loaded by SANE >> How? and what is the exact name (artec_eplus48u ? )
The backend is not configured correctly >> How?

As I said, it would probably be easier just to start over, but this is where I am. I am more than willing to do the research if pointed in the right direction.

 Any help is appreciated.

Thanks.

---

### Post by RebounD11 on 2007-12-05
ok... I thinkI might be able to help you. I have an Artec E+ Pro scanner... somewhat similar to yours.

You said that lsusb recognizes your scanner. now what you should change in the /etc/sane.d/artec_eplus48u.conf are the following:

usb 0x05d8 0x4003

option artecFirmwareFile /usr/share/sane/artec_eplus48u/Artec48.usb

option ePlusPro   0

and 

device libusb:004:002

all these lines should be uncommented (without # at the beginning), and should look like above.

This worked for me... I hope it does for you too, though I can't get a preview with Graphics/XSane Image Scanner, I recommend using the Gimp, it still won't give you a preview (since it uses XSane Image Scanner) but you will be able to see the scanned image.

From the scanner's point of view Ubuntu is so far the worst distro ever :| ...IMO

EDIT: Just saw your edit :))

---

