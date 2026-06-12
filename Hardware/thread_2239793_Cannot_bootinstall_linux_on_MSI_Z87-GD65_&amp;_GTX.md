---
title: "Cannot boot/install linux on MSI Z87-GD65 &amp; GTX 770 (i7-4770K)"
date: 2014-08-15
forum: Hardware
---

### Post by CraftThatBlock on 2014-08-15
I have been trying to install Ubuntu on my gaming PC (I use *nix on all my other machines) for quite a while, never got to it really because everytime I get this problem and can't get it to work.


So basically the problem is I insert my Live USB of 14.04.1 in the computer (tried front & back USB panels, both USB 3.0 and 2.0. Basically tried all ports) and booting my computer. I see the Mobo's splash page, then I hold F11 and I see the USB key listed. I selected it, and it boots into the "Try without installing, install Ubuntu, disk check, etc" page. Everything is fine up to here.


Next, when I select any options, the screen just goes black. I have tried to put my monitor's input from the mother board directly (usually into my GPU), and it didn't work.


I have no idea what this could be the problem. I would guess the GPU, but I don't really know.


About a year ago, I had a successful Ubuntu (13 I think, not too sure) install with no problem (except some drivers that I never got time to install) before getting my Windows installation (as said, this is my only gaming PC, as I do everything on Mac and Ubuntu for the rest).

---

### Post by CraftThatBlock on 2014-08-15
I've solved this. Looks like disabling Legacy and only having UEFI fixed it.
EDIT: nope!

---

### Post by CraftThatBlock on 2014-08-15
Nope! That didn't solve it. It booted once in the "Ubuntu loading" screen though.

---

### Post by em3raldxiii on 2014-08-16
Just to eliminate this as a possible issue, have you tried your live USB stick in another machine?  If it's corrupted, that could easily explain the issue, and a fresh boot stick might be the easy solution.  I have a few sticks lying around here that work fine for data, but have never worked as live sticks, either.  I haven't troubleshot why those ones don't work, but since the sticks are cheap, I just use a different one.

---

### Post by oldfred on 2014-08-16
Are you booting with nVidia card or Intel internal chip?  Intel may also need some boot parameters.

You need nomodeset boot parameter, with nVidia. I have to add nomodeset on every live boot and first boot after install or until I install nVidia proprietay drivers.

With UEFI, you have to add it to the grub entry. Press e for edit, and on linux line replace quiet splash with nomodeset.
If booting in BIOS mode you press any key at accessibilty icons(tiny person & keyboard) then f6 to add nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

