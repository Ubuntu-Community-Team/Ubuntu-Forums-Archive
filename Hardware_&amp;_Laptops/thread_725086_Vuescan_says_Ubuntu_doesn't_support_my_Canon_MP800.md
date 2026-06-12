---
title: "Vuescan says Ubuntu doesn't support my Canon MP800 (Scanner), but it does! What next?"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by OzzyFrank on 2008-03-15
[B]VueScan found a Canon MP800, but this scanner isn't supported on Linux. See the VueScan Release Notes for more information.

Press 'Close' to start using VueScan.[/B]

Simply put: ********! Yes, I know Canon couldn't care less about Linux users, but Ubuntu does support this printer (up to 600dpi, which is why I use TurboPrint). And as far as the scanner goes, out of the box Ubuntu can use this no frickin worries with apps like Xsane.

So what is Vuescan's problem? And, more importantly, is there a way to fix this? The recommendation involves installing another library, so would want some advice from those in the know before I proceed. Here is some general info, not regarding the MP800, but Ubuntu:

**If you're using a newer version of Ubuntu Linux, you can install the needed version of libstdc++ with the command "sudo apt-get install libstdc++5". If you're using a newer Linux distribution that's LSB compliant, edit "/etc/udev/rules.d/50-udev-default.rules", find the line that begins with "libusb device access" and change 0644 to 0666.**

I have no idea what the suggested library is for, and what LSB is, and whether Ubuntu 7.10 amd64 is compliant in that regards. Does the above suggestion seem safe enough? And if so, will it (possibly) fix things? Thanks in advance!

---

### Post by OzzyFrank on 2008-03-15
Oh,[COLOR="DarkRed"]** libstdc++5**[/COLOR] is already installed, so I suppose the question is whether **edit "/etc/udev/rules.d/50-udev-default.rules", find the line that begins with "libusb device access" and change 0644 to 0666** is safe enough to do and if it might work. I opened the file and it is blank, so I have nothing to change, or syntax to follow for putting it in myself.

---

