---
title: "Asus laptops:"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by iLoVe.cF- on 2006-09-12
Hi there guys.. Post all Info you know about asus laptops. and i will post mine so we gather everything in my forum =)

I will cover Asus A3E

Works outta the box:
touchpad
Usb
wireless
lcd(With i915 resolution)
Dvd burner
sleep, hibernate
clone display (with config)

Things you have to fix
Video card: here is my info: i915 videocard
glxgears fps 650 here highest seen on i915 1200
compiz with aiglx is reported for best performance with the i915

DO NOT INSTALL DAPPER cuz broken dri!
Games run not good at all driver support is bad :'(

Sound.

Have to edit files and install alsa on new.

More info will come later about how to`S

---

### Post by daller on 2006-09-12
Please use the WIKI for such test-results:

[https://wiki.ubuntu.com/LaptopTestingTeam/Asus](https://wiki.ubuntu.com/LaptopTestingTeam/Asus)

Your laptop is not there, so please create this:

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA3E](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA3E)

Use this template:

```
 * Contact: Julius16
 * Brand: Sony
 * Make : VGN
 * Model: FE21B
 * Website: www.sony.com

== Current Issues ==
Edgy untested
## List any issues you have with the current development release here

== System Info ==
{{{
bios-version:R0130J3
system-manufacturer:Sony Corporation
system-product-name:VGN-FE21B
system-version:C3LMEK8C

2.6.15-26-686

}}}

== Hardware details ==
|| || in Dapper (current stable)? || in Edgy (current development)? ||
|| Installation works? || Untested || Untested ||

||<-4> '''Hardware Information''' ||
||<-4> '''Screen & Monitors''' ||
||<|2> '''Device''' ||<-2> '''Works?''' ||<|2> '''Bug #''' ||
|| in Dapper (current stable)? || in Edgy (current development)? ||
|| Screen || Yes || Untested || ||
|| Correct resolution? || Yes || Untested || ||
|| Correct refresh rate? || Yes || Untested || ||
|| 3D Acceleration || Yes || Untested || ||
|| External monitor works? || Yes || Untested || ||
|| External monitor - mirrors || Yes || Untested || ||
|| External monitor - extend desktop || Yes || Untested || ||
||<-4> '''Power Management''' ||
|| Battery detected? || Yes || Untested || ||
|| Hibernates? || Yes || Untested || ||
|| Sleep || Yes || Untested || ||
|| Dim monitor on battery || No || Untested || ||
|| Blank monitor on inactivity || Yes || Untested || ||
|| Lid Close || Yes || Untested || ||
|| Cpu frequency scaling || Yes || Untested || ||
||<-4> '''Sound''' ||
|| Sound works? || Yes || Untested || ||
|| Correct volume? || Yes || Untested || ||
|| Hardware volume switch || Yes || Untested || ||
|| Headphone jack || Yes || Untested || ||
|| Mic jack || Yes || Untested || ||
||<-4> '''Networking''' ||
|| Wired NIC || Yes || Untested || ||
|| Wireless NIC || Yes || Untested || ||
|| PCMCIA NIC || Untested || Untested || ||
|| Firewire || Untested || Untested || ||
|| Bluetooth || N/A || N/A || ||
|| Modem || Untested || Untested || ||
|| Infrared || N/A || N/A || ||
||<-4> '''Touchpad & Mice''' ||
|| Touchpad || Yes || Untested || ||
|| Touchpad - Doubletap = double click || Yes || Untested || ||
|| Touchpad - Scroll down side || Yes || Untested || ||
|| Touchpad - turned off while typing || No || Untested || ||
|| External mouse - USB || Yes || Untested || ||
|| External mouse - Serial || N/A || N/A || ||
||<-4> '''Docking Station/Port Replicator''' ||
|| AC through replicator || Untested || Untested || ||
|| USB || Untested || Untested || ||
|| Serial || Untested || Untested || ||
|| Parallel || Untested || Untested || ||
|| External Monitor - VGA || Untested || Untested || ||
|| External Monitor - DVI || Untested || Untested || ||
|| Modem || Untested || Untested || ||
|| NIC || Untested || Untested || ||
|| PS/2 || Untested || Untested || ||
||<-4> '''Additional Hardware''' ||
|| Fingerprint reader || N/A || N/A || ||
|| CD/DVD drive || Yes || Untested || ||
|| PCMCIA cards || Yes || Untested || ||
|| Parallel Ports || N/A || Untested || ||
|| Card reader(s) || Yes || Untested || ||



## Add or remove keys as needed for your laptop. Fill out action
||<-6 tablewidth="75%"> '''Function and other keys''' ||
||<|2> '''Fn key''' ||<|2> '''Operation''' ||<|2> '''Keycode''' ||<-2> '''Works?''' ||<|2> Bug # ||
|| in Dapper (current stable)? || in Edgy (current development)? ||
|| + F5 || || || No || Untested || ||
|| + F6 ||  || || No || Untested || ||
|| + F7 ||  || || No || Untested || ||
|| + F10 || || || No || Untested || ||
|| + F12 ||  || || No || Untested || ||
||<-6> '''Other special keys''' ||
||<|2> '''Key''' ||<|2> '''Operation''' ||<|2> '''Keycode''' ||<-2> '''Works?''' ||<|2> Bug # ||
|| in Dapper (current stable)? || in Edgy (current development)? ||
|| S1 ||? || || No || Untested || ||
|| S2 ||? || || No || Untested || ||

=== Notes ===

Dimming works with smartdimmer. Battery doesnt quite work right. No status and some wrong acpi signals. On  wakeup, sound is stuttering.


----
CategoryLaptop

```

Not a user? - Then register!

This is of great help to the rest of the community!

---

### Post by daller on 2006-09-12
"Do not install dapper!" - What does that mean?

...you are posting in the Dapper forums!

Are you running Breezy?

---

### Post by daller on 2006-09-12
To make things easier, I've created the page for you:

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA3E](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA3E)

Beware! - It doesn't show Breezy results! - only current stable and development (dapper and edgy!)

Please check if the "Yes", "No" and "Untested" matches your experience! - If not, please change, or post me, then I'll change it!

---

### Post by rsvr on 2006-09-12
Have ASUS W2V. Running dapper.
Sound/Network/wireless all work.

Video. Used ATI driver and got 1650x1050 screen.Mod xorg.conf and also worked with generated version.

Tried Memphis (sound crap)
Mandrake - no problem
Fedore - crap.
Looking to try Gentoo next.

---

### Post by daller on 2006-09-12
> **rsvr said:**
> Have ASUS W2V. Running dapper.
Sound/Network/wireless all work.

Video. Used ATI driver and got 1650x1050 screen.Mod xorg.conf and also worked with generated version.

Tried Memphis (sound crap)
Mandrake - no problem
Fedore - crap.
Looking to try Gentoo next.

Same goes for you...

Please check if all information here is correct:

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusW2V](https://wiki.ubuntu.com/LaptopTestingTeam/AsusW2V)

---

### Post by cosh1 on 2006-09-13
w5a working fine here with xgl/compiz (that is if you are forgetting about the bluetooth and camera)

---

### Post by daller on 2006-09-14
> **cosh1 said:**
> w5a working fine here with xgl/compiz (that is if you are forgetting about the bluetooth and camera)

Please check if this is correct:

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusW5a](https://wiki.ubuntu.com/LaptopTestingTeam/AsusW5a)

---

