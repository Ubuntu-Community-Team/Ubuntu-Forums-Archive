---
title: "USBCD810.ISO (Boot from CD to boot from USb Stick) only boots the GRUB"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by barci on 2009-02-03
Hello,

my LAPTOP does not support booting from USB.

I Burned the USBCD810.ISO and see only the GRUB and not my USb device (made the USB ubuntu with the ubuntu life Cd bevor)

any idea ???

---

### Post by caljohnsmith on 2009-02-03
How about downloading the [PLoP boot manager]("http://download.plop.at/files/bootmngr/plpbt-5.0.zip"), and in that zipped package you will find an ISO file you can burn to CD. Try that, and see if PLoP can boot your USB drive. Let me know how that goes.

---

### Post by barci on 2009-02-03
I've tried it.
It changes to the eh?? mode, then he tells me he will start from removabel drive. (sounds good, but:)

Then i see some ..................................................................

and nothing happens.

---

### Post by boof1988 on 2009-02-03
> **barci said:**
> Hello,

my LAPTOP does not support booting from USB.

I Burned the USBCD810.ISO and see only the GRUB and not my USb device (made the USB ubuntu with the ubuntu life Cd bevor)

any idea ???

The USBCD810.ISO may only boot the Ubuntu 8.10 LiveUSB.  I'm not sure about this.  Maybe someone else can correct me if I'm wrong.

Are you using the Ubuntu 8.10 LiveUSB with the boot CD you created?

Did you press enter when the GrUB menu showed on the screen?  The boot CD will not show the USB device.  It only shows the GrUB menu (unless you choose one of the options at the bottom of the GrUB screen).  I believe that you have to press enter to get GrUB to boot the USB.

I have included the screen shot of the GrUB menu.  Does it look that same as the one you see?

---

### Post by barci on 2009-02-03
Are you using the Ubuntu 8.10 LiveUSB with the boot CD you created?

Yes.

My Grub with USBCD810.ISO looks like this:

grub>_  (Cursor !!!)

With the Tool

plpbt-5.0.zip

it tells me:
Boot Cd-Rom Type: floppy booting
Booting from Removable media
.............................................:(:(:(:(

---

### Post by boof1988 on 2009-02-03
> **barci said:**
> My Grub with USBCD810.ISO looks like this:

grub>_  (Cursor !!!)

This indicates (I think) that the computer is only booting to a GrUB prompt and not the GrUB menu.

When you get to the:

```
grub>
```

You can try the following if you like (though I'm not sure if it will work or not):

```
grub> root (cd)
grub> kernel /boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true persistent
grub> initrd /boot/initrd.gz
grub> boot
```

The code above are the config lines the the USBCD910.iso uses to boot the USB.  So it may work or not.  I don't know how to check if the drivers for the USB are loaded or not at the point you get the:

```
grub>
```

Hope this helps.

---

