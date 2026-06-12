---
title: "Compiz Animation configuration problem"
date: 2008-10-27
forum: General Help
---

### Post by tezer on 2008-10-27
Hello!
I am using Mint 5.0 Elyssa, which is nice.
I am absolutely happy with it if not one small problem.
When I try to change Minimize Animation options in CompizConfig's Animation nothing changes! All changes work ONLY for Close/Open options. All other settings (Focus Animation and Shade Animation) are also NOT configurable (I can write whatever options I want but nothing happens). When I enable Minimize Effect (and have to disable the Animation) everything works fine - windows minimize/restore just the right way.
Whatever option I choose in the MinimizeAnimtion tab, the behavior doesn't change (it is always Glide2 on restoring a window and it simply disappears on minimization - no effect at all).
Here is the configuration string of my MinimizeAnimtion (I tried different):

```
    MagicLamp 250 ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```



It doesn't seem to be a hardware problem (all other settings work fine and compiz-check is all OK:

  ```
  Distribution:          Linux Mint
    Desktop environment:   GNOME
    Graphics chip:         ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
    Driver in use:         fglrx
    Rendering method:      AIGLX

    Checking if it's possible to run Compiz on your system...

    Checking for texture_from_pixmap...               [ OK ]
    Checking for non power of two support...          [ OK ]
    Checking for composite extension...               [ OK ]
    Checking for FBConfig...                          [ OK ]
    Checking for hardware/setup problems...           [ OK ]
```

---

### Post by tezer on 2008-10-28
Thank you for viewing my post!
Anyone answer? Please...

---

### Post by ellalan on 2008-10-28
Try this 
magic lamp 300 (type=Normal | Dialog | ModalDialog | Unknown).

---

### Post by tezer on 2008-10-28
Thank you for your advice, but it didn't work :(

---

### Post by loomsen on 2008-10-28
Are you sure you have the RegEx Matching plugin enabled?

CCSM->Utility

---

### Post by tezer on 2008-10-28
> **loomsen said:**
> Are you sure you have the RegEx Matching plugin enabled?

CCSM->Utility

Yes. The funny thing is that Open / Close settings work fine! But Minimization just doesn't change whatever I do...
Is there a config file that may be corrupt?

---

### Post by loomsen on 2008-10-28
Humm, maybe, dunno.

I can post my profile, I'm using gconf backend configuration, maybe you can start off with it, or at least try and see if this works...

You can also try and export your current profile, don't skip default values when prompted, and reimport. But I don't see how this would change anything.

Which compiz version so you use? I installed from git, installed protobuf extensions as well, and it works like a dream. Really some nice code from google.

protobuf-compiler python-protobuf libprotobuf-java libprotobuf-dev libprotobuf0

are the packages to get.

Maybe it's worth it to try and pull recent git compiz?

As I said, I like it.

---

### Post by tezer on 2008-10-28
> **loomsen said:**
> Humm, maybe, dunno.

I can post my profile, I'm using gconf backend configuration, maybe you can start off with it, or at least try and see if this works...

You can also try and export your current profile, don't skip default values when prompted, and reimport. But I don't see how this would change anything.

Which compiz version so you use? I installed from git, installed protobuf extensions as well, and it works like a dream. Really some nice code from google.

protobuf-compiler python-protobuf libprotobuf-java libprotobuf-dev libprotobuf0

are the packages to get.

Maybe it's worth it to try and pull recent git compiz?

As I said, I like it.

Thank you, loomsen.
I'll try to follow your advice.

---

### Post by tezer on 2008-10-28
By the way, I made a small experiment - killed compiz and started it in CLI. Here is what I got:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b60 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (bicubic) - Fatal: GL_ARB_texture_float not supported. This can lead to visual artifacts.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/backgrounds/bianca-blue.png
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (group) - Warn: No compatible text plugin loaded.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Shade event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Minimize event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.

```

Any ideas what's wrong?

Edit: I enabled the text plugin, nothing changed...

---

### Post by loomsen on 2008-10-28
Humm, dunno.

So, I don't know Mint, but you have gnome, do I get you right?

If so, try and add shames repository to your sources.list.

```

#shame compiz
#wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./

```

Use the wget line to add the gpg key to your trusted.db. Simply copy and paste it into a terminal. The last line should work for every debian based distro, and is usually pretty much on the edge. Actually 0.79 I think.

And make sure you purged everything compiz related prior to reinstalling it.

```
locate compiz | grep -v home
``` should give you a list of all residual files. make sure you delete all of them, and don't have compiz/emerald running.

If you clean everything up and install the packages from shames repo I cannot imagine why it shouldn't work a last.

Good luck.

And post your xorg.conf.

```
cat /etc/X11/xorg.conf
```

---

### Post by tezer on 2008-10-28
Thanks again, I'll try to as you advised. Meanwhile here is my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb,ru"
	Option		"XkbVariant"	",winkeys"
    	Option		"XkbOptions"	"grp:alt_shift_toggle"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by tezer on 2008-10-28
SOLVED!
You'll be laughing but I simply reset the open and close animation matches to defaults with the brush button under the match list and reconfigure them! (I read the solution from the Compiz forum)

Anyway, thanks to all who wanted to help, esp. loomsen!

---

### Post by Czar on 2008-11-21
> **tezer said:**
> SOLVED!
You'll be laughing but I simply reset the open and close animation matches to defaults with the brush button under the match list and reconfigure them! (I read the solution from the Compiz forum)

Thanks for the solution Tezer.  Setting compiz focus to the default (using the brush button) also solved these "/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event." errors.

---

### Post by wayfarer_boy on 2008-11-27
Strange, but it still hasn't solved my own minimize problem.  As others have found in this thread, all other actions work with the exception of minimize.  I've tried resetting all animations using the brush icon, but to no avail.

Tezer, do you have a link for the compiz forum where you found the solution?

---

### Post by wayfarer_boy on 2008-11-27
Solved it!  Unfortunately, I reset the settings to defaults in the main Compiz preferences before trying this, so I'm not entirely convinced that this solution would work had I not done that.  However, here it is:

If you don't have a Window List applet running on a panel, the minimize animations don't seem to work.  So, add the Window List applet to a panel and then minimize animations will return.

Once the minimize animations are working, you can then remove the Window List applet (if you don't use it) and edit the animation effects settings (Effects > Animations > Effect Settings) to "Zoom to taskbar on minimize" unchecked, or in the case of Zoom, "zoom from centre" to "On".

---

### Post by pethead on 2009-04-06
thanks.
now I had same problem and crack my brain to solve mininization animation.
now I knew how must to be solved!

---

### Post by karukera7 on 2010-02-23
hello guys,


I'm new to compiz and i need help to set up the Airplane effects(option : fly to taskbar on minimize), i already read several forums and i enabled "animation add-on" and "animations" within the effect section and also checked the Shift switcher option within the "window management" section.

could you please help me fix this out ? thanks

:(

---

### Post by mal93 on 2010-10-19
> **tezer said:**
> SOLVED!
You'll be laughing but I simply reset the open and close animation matches to defaults with the brush button under the match list and reconfigure them! (I read the solution from the Compiz forum)

Anyway, thanks to all who wanted to help, esp. loomsen!

Thanks, worked for me too!

---

### Post by modal1 on 2011-07-14
> **Czar said:**
> Thanks for the solution Tezer.  Setting compiz focus to the default (using the brush button) also solved these "/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event." errors.


I was getting that same Animation mismatch error on my Fedora box. Resetting them to defaults fixed my CPU spiking issue. Thanks for the solution!

---

