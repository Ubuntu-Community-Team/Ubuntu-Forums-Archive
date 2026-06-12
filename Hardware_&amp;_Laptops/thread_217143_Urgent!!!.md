---
title: "Urgent!!!"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by jkatana on 2006-07-16
ok i aksed in the fourms for help updating my driver some guy told me to use this script for nvidia i told him i had a ASUS on board video he said it would work... i tried it now i boot into text and cant even startx! this is so freaking annoying is there anyway to rescue my pc and get it to run on the normal driver, so i can install the correct one, thanks to a thread i found, i looked for somthing like this but found nothing anything anyone can contribute i would be so freaking happy. im on my alternate PC right now and remember all i can do is terminal stuff. with the pc im trying to fix thanks

---

### Post by bluecherry on 2006-07-16
Run "sudo dpkg-reconfigure -phigh xserver-xorg" from the terminal.

Then type "startx" and you should be fine.

/ps: try paragraphs next time you're around ;)

---

### Post by jkatana on 2006-07-16
ok, that didnt work, didnt work at all... now i can get to my login but it keeps redirecting me to it after i log in... and the only way i can even use my computer now is to go into rescue mode and startx... how do i set it to its old configurations?

---

### Post by ORBiTrus on 2006-07-16
Well, your old driver was likely nv, if that helps.

Just change your /etc/X11/xorg.conf file back by hand.  Generally speaking, all you need to do is add a new Driver section like so:

```

Section "Device"
  Identifier "nv-fallback"
  Driver "nv"
  BusIdD "PCI:1:0:0" # Eh, it's not always this...
EndSection

```

and modify your Screen section's Device line to read:

```

  Device "nv-fallback"

```

Use either Vi(m), Nano, or your choice of text editor.  IMO, getting your xorg.conf file working right is one of the best Linux training activities I can think of... never too surprising, but still a fair challenge.  Now wouldn't it be nice if Xorg had a modular config?...  Hmmmmm...

Oh, just a random tidbit - what Debian and Ubuntu call "Rescue Mode" is really just single-user system... more generally just known as "init 1" for Sys7 setups.

---

