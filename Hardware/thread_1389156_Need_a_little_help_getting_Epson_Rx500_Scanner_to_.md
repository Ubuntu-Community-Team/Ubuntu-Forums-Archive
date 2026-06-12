---
title: "Need a little help getting Epson Rx500 Scanner to work, keep getting &quot;segmentation fa"
date: 2010-01-24
forum: Hardware
---

### Post by bomber991 on 2010-01-24
I select xsane, it loads up and gives me the option of which scanning device to choose.  In this case it lets me choose between my webcam and the epson scanner.  I choose the scanner, program thinks for a second and disappears.

I try opening xsane in the gnome terminal.  Same screen pops up letting me choose either the webcam or the scanner.  I choose the scanner, it thinks for a second and then disappears.  I notice in the terminal window that it says:
```
user@badass-penguin:~$ xsane
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:2271): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:2271): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:2271): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:2271): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault

```

I've also tried using "Scanner Utility" and got the same problem.  I then tried "Skanlite" and it seemed to be working.  My scanner started making noise, then it stopped and Ubuntu froze up completely.  I had to end up pressing the reset button on the pc :(

Anyways, I don't have a clue where to start with fixing this issue.  I'll try and list some relevant information, but if you need any more just let me know.  Thanks!

Ubuntu 9.10
Epson Stylus PHOTO RX500, connected w/ USB
Athlon 64 3700+, but running 32bit version of ubuntu.

---

### Post by ellgor on 2010-01-24
Hi,

Go to the "Avasys" site, its for Epsons' and get their Imagescan package, after a reboot should work no problem.

Regards, Ellgor.

---

### Post by bomber991 on 2010-01-24
Alright, I got it to work!  Thanks!  Now I noticed they also had some print drivers on that site that would allow me to view the ink levels.  That's another problem to solve for another day though.
[IMG]http://imgur.com/PEUbS.jpg[/IMG]

---

