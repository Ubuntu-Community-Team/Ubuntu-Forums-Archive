---
title: "screen keeps blacking out"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by X5-655 on 2005-09-07
my laptops screen keeps on constantly blacking out on me randomly..  moving the mouse brings the screen back up..

it's a Dell Latitude CSx.  please help!!  this problem is making me want to put the Windows XP hard drive back in

---

### Post by mlomker on 2005-09-07
[QUOTE=X5-655]it's a Dell Latitude CSx.  please help!!  this problem is making me want to put the Windows XP hard drive back in[/QUOTE]

Have you looked in the control panel already?  Look under power control and appearance & themes (screen saver).

---

### Post by X5-655 on 2005-09-07
[QUOTE=mlomker]Have you looked in the control panel already?  Look under power control and appearance & themes (screen saver).[/QUOTE]
yes, see here in my screenshot, it's already all unchecked..  also take notice, of the solid line going right down the middle of the power options, i am getting some screen corruption on my screen, which doesn't happen in windows, or any of my other linux machines..   ](*,)   this laptop drives me nuts..

---

### Post by mlomker on 2005-09-07
Heh, sorry...I was giving you instructions for KDE since I'm a Kubuntu guy.  What video driver are you currently using?  Should be a **Driver** line under the **Section "Device"** portion of the /etc/X11/xorg.conf file.

You could try switching that to vesa (slow, reliable, and not a lot of resolution) as a test.

---

### Post by X5-655 on 2005-09-07
[QUOTE=mlomker]Heh, sorry...I was giving you instructions for KDE since I'm a Kubuntu guy.  What video driver are you currently using?  Should be a **Driver** line under the **Section "Device"** portion of the /etc/X11/xorg.conf file.

You could try switching that to vesa (slow, reliable, and not a lot of resolution) as a test.[/QUOTE]
here's the whole section...

Section "Device"
	Identifier	"NeoMagic Corporation NM2360 [MagicMedia 256ZX]"
	Driver		"neomagic"
	BusID		"PCI:1:0:0"

---

### Post by mlord on 2005-09-07
Look for this line in /etc/X11/xorg.conf, and comment it out by putting a # in front of it:

Option  "DPMS"

---

### Post by X5-655 on 2005-09-08
[QUOTE=mlord]Look for this line in /etc/X11/xorg.conf, and comment it out by putting a # in front of it:

Option  "DPMS"[/QUOTE]
ok, that prevented the backlight from turning off, but the screen still goes black (but the backlight is lit)

---

