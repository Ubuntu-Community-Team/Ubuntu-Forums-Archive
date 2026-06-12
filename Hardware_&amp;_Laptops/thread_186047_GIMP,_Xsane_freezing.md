---
title: "GIMP, Xsane freezing"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by metra on 2006-06-01
I'm still using Breezy.  My scanner is a canon Lide 35, USB.

A week ago I was using Gimp and wanted to scan. File>Acquire>Xsane>v4:'dev'video0

*FREEZE* 

Mouse won't move, nothing.  Had to power off.  I first tried to re-install gimp and xsane with Synaptic.

Then tried to scan directly using XSane.  Again, freeze.

Looked around the forums, in the terminal I did:          sudo sane-find-scanner
```

found USB scanner (vendor=0x04a9 [Canon], product=0x2213 [CanoScan], chip=GL841) at libusb:005:003
found USB scanner (vendor=0x04fc, product=0x0561) at libusb:004:002
```

Was the result, good news I guess?
I then did scanimage -L to check the backend's manpage. <--I have no idea what that means.
```

device `v4l:/dev/video0' is a Noname Flexcam 100 Camera virtual device
```

was the result of that. I'm sure  that all that is informative to someone, not me.
Why is it calling it a camera?  I have an Ezonics webcam (not working either, buit I haven't really tried yet.)

Found out I need to install SANE Genesys, I'm still figuring that one out.  

Even if I don't have the right driver for it, it should just tell me I don't have the right driver not locking up, right? 

Any help on the freezing, which is the main problem, or of course fixing it so it scans would be great.  Thanks.

---

