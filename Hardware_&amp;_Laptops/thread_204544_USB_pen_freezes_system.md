---
title: "USB pen freezes system"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by adfe4sgsdg on 2006-06-27
Hi,
I have installed ubuntu 6.06 on a PII 500Mhz with 190MB ram and all went fine but when I plug a usb pen the sistem totally freezes (also the keyboard). I tried to manually load the usb_storage module but this did not helped. I tried also the latest nubuntu live cd and the usb problem still remains, so I think tha is a kernel problem (I tried both 386 and 686 kernels on the ubuntu dvd but without success).
Thanks
dat

---

### Post by pellgarlic on 2006-06-27
have you tried all usb ports on your computer to see if it happens with them all? for example, front-of-case usb extension ports have been known to be unreliable at times, and if you are using a usb hub, that could also potentially cause problems. 

so, just to make sure, have you tried using the usb ports that are motherboard-mounted? (at the back, beside the mouse, keyboard, ethernet, etc ports)

---

### Post by adfe4sgsdg on 2006-06-27
[QUOTE=pellgarlic]have you tried all usb ports on your computer to see if it happens with them all? [/QUOTE]
yes, of course

[QUOTE=pellgarlic]
so, just to make sure, have you tried using the usb ports that are motherboard-mounted? (at the back, beside the mouse, keyboard, ethernet, etc ports)[/QUOTE]
it's an old pc with an old case, the only 2 usb ports are at the back.

The strange thing is that even with the nubuntu live cd the system freezes, so I think that is a problem of some ubuntu kernel patches, when I can find some time for testing I will compile a vanilla kernel.

thanks
dat

---

### Post by pellgarlic on 2006-06-28
you could also try a different distro's live cd - knoppix for example, to see if it does the same thing.

---

### Post by adfe4sgsdg on 2006-06-28
[QUOTE=pellgarlic]you could also try a different distro's live cd - knoppix for example, to see if it does the same thing.[/QUOTE]

yes, I tried [dynebolic]("http://dynebolic.org/") an all went fine (usb works perfectly) but since the pc it's not for me but for a not informatic friend I searched for an easy to use distro.
I'm now thinking on setting up slackware instead (that I know better than ubuntu and doesn't have these problems even if it is necessary an little overhead of maintenance)
thanks
dat 

P.S. I have a 56k connection only so I can't download huge iso files, please don't tell me try fedora or suse or mandriva :(

---

### Post by pellgarlic on 2006-06-28
maybe you should make a bug entry on launchpad - i'm sure the ubuntu developers would rather have the opportunity to fix these problems, than just lose a potential user. i'm not sure of the process or protocol though, or whether this would consitute a "bug" - click on the "bug tracker" link at the top-right corner of this page, and check it out if you're so inclined.

---

### Post by adfe4sgsdg on 2006-06-28
[QUOTE=pellgarlic]maybe you should make a bug entry on launchpad[/QUOTE]

good idea, my next step will be reporting this "bug"
thanks for the help
dat

---

