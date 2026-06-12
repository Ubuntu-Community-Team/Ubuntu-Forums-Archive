---
title: "Mac with Virtual ubuntu"
date: 2009-02-03
forum: Hardware
---

### Post by fuzzybear3965 on 2009-02-03
Ok So my friend just installed ubuntu on top of mac via VirtualBox. The options for VirtualBox include enabling 3d acceleration so it is supported. However, compiz will not work on virtual ubuntu. No error codes, just non-functional key presses. Also, the resolution of his fullscreen virtual box maintains a 800x600 resolution on a 17" screen. I've tried reconfiguring xorg and modifying xorg from text to no avail. Can anyone solve these problems?

---

### Post by 00b00nt00 on 2009-02-04
My understanding is that, as of the moment, Virtualbox only supports OpenGL 3D in Windows guests.

So no compiz for you, my boy ;)

---

### Post by fuzzybear3965 on 2009-02-04
Where did you hear this?  Not that I doubt you, but I could find nothing on the internet about it.

---

### Post by 00b00nt00 on 2009-02-05
If memory serves me correctly, this info was tucked into the Virtualbox users' manual.

...about the resolution problem; you'll have to install 'Guest Additions' from one of the Virtualbox menu tabs (I can't remember which), and basically run a script in the terminal with the sudo command. It's not hard, but please read the users' manual.

Compiz is a no-no, but you should have no problems with the resolution.

---

### Post by vevo on 2009-02-05
> **fuzzybear3965 said:**
> Also, the resolution of his fullscreen virtual box maintains a 800x600 resolution on a 17" screen. I've tried reconfiguring xorg and modifying xorg from text to no avail. Can anyone solve these problems?

I have just installed ubuntu8.10 on macpro with virtual box and get the same video problem: can't get more than 800x600.

I tried to modify xorg.conf replacing

```

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
EndSection

```
with
```

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1280x800" "1024x768" "800x600"
EndSubSection
EndSection

```

but I get an error when re-booting, and i have to switch back to the original xorg.conf to boot.

Anyone can help?
thanks,
vevo

---

### Post by vevo on 2009-02-05
SOLVED:I installed Guest Addition:

boot you guest os, than from VirtualBox click on Devices->Install Guest Addition

wait a bit.. an image will appear on the desktop of the hosted OS

go into the hosted os, from a terminal:
```

$sudo /media/cdrom/VBoxLinuxAdditions-86.run

```
or
```

$sudo /media/cdrom/VBoxLinuxAdditions-amd64.run

```
according to your system architecture.

For further info:
[http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/](http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/)

vevo

---

### Post by fuzzybear3965 on 2009-02-05
Vevo and 00b00nt00... you both receive my heartfelt gratitude and eternal thanks.

I love community spirit.

---

