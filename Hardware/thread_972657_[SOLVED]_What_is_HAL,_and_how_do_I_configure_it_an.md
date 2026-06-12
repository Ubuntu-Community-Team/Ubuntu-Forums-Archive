---
title: "[SOLVED] What is HAL, and how do I configure it and my Wacom tablet?"
date: 2008-11-06
forum: Hardware
---

### Post by stephanecharette on 2008-11-06
In previous versions of Ubuntu (since 6.04? through to 8.04) I had the wacom-tools .deb installed.  A script that I would run on bootup after X was loaded would perform the following action to configure the buttons on my Wacom stylus:

```
xsetwacom -v set stylus Button1 "button 1"
xsetwacom -v set stylus Button2 "button 3"
xsetwacom -v set stylus Button3 "button 3"
```

This has worked for me for years.  But today I upgraded to 8.10, and I see this no longer works.  Running "xsetwacom list" does not list any devices.  And in xorg.conf, I see that all the lines that mention "wacom" have been commented as this example shows:

```
# commented out by update-manager, HAL is now used
#	InputDevice     "stylus"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#	InputDevice     "cursor"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#	InputDevice     "eraser"	"SendCoreEvents"
```

QUESTION #1:  What is HAL?

QUESTION #2:  Where or what do I configure to correctly set the stylus buttons on my Wacom Intuos 9x12 tablet?

Thanks!

Stéphane Charette

---

### Post by wgrant on 2008-11-06
X.org now uses HAL to automatically detect input devices. For tablet configuration, see [the documentation on the Ubuntu help wiki](https://help.ubuntu.com/community/Wacom).

---

### Post by stephanecharette on 2008-11-06
> **wgrant said:**
> X.org now uses HAL to automatically detect input devices. For tablet configuration, see [the documentation on the Ubuntu help wiki](https://help.ubuntu.com/community/Wacom).

Thanks, that link gave me the information I needed to get my Wacom tablet running like it did with past versions.  (Also explained why the puck and eraser no longer work, but I don't typically use those.)

Took a bit of playing around with the .fdi file to figure out the right options I needed.  For anyone else looking up this thread with a similar problem, here is the /etc/hal/fdi/policy/mywacom.fdi file I created:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Wacom tablet customizations.  This file contains just a few examples
  of what can be configured.  For additional information, see:
    1) https://help.ubuntu.com/community/Wacom.fdi
    2) http://linuxwacom.sourceforge.net/index.php/howto/inputdev
    3) http://ubuntuforums.org/showthread.php?t=972657
-->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
<!--    <merge key="input.x11_options.DebugLevel" type="string">12</merge> -->
<!--    <merge key="input.x11_options.CommonDBG" type="string">12</merge> -->
<!--    <merge key="input.x11_options.Mode" type="string">Relative</merge> -->
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
        <merge key="input.x11_options.Button1" type="string">1</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
        <merge key="input.x11_options.TPCButton" type="string">OFF</merge>
        <merge key="input.x11_options.KeepShape" type="string">OFF</merge>
        <merge key="input.x11_options.Rotate" type="string">NONE</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```

Stéphane Charette

---

### Post by Another Monkey on 2008-11-10
This is great, I am struggling to get a Wacom Graphire 4 working on 8.10.  If I figure out what the .fdi should look like, I will post it.

My main problem is that I seem to keep breaking it when I try to add support for the eraser and buttons on the tablet.  Unfortunately none of the documentation seems to help.

Should these be extra sections?
```
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
      </match>
    </match>

    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">erase</merge>
      </match>
    </match>

    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">pad</merge>
      </match>
    </match>
```

Anyone any ideas?

---

### Post by stephanecharette on 2008-11-10
> **Another Monkey said:**
> My main problem is that I seem to keep breaking it when I try to add support for the eraser and buttons on the tablet.  Unfortunately none of the documentation seems to help.

The link William included in the 2nd post of this thread was a great help to me.  Specifically for your question, note the following text at the top of that page:
> ... wacom tablets should work out-of-the-box with hotplugging, but only the stylus - including pressure and tilt - will work (no eraser, mouse or pad buttons)

So apparently eraser, puck/mouse and pad buttons wont work with this method.  For this, you'll need to look at the alternative setup called "Option B" on that page.

Of great help to me were the 2 debug lines in the .fdi I posted above:
```
    <merge key="input.x11_options.DebugLevel" type="string">12</merge>
    <merge key="input.x11_options.CommonDBG" type="string">12</merge>
```

This caused Wacom debug information to be appended to /var/log/Xorg.0.log every time I plugged in and unplugged my usb tablet.

Stéphane Charette

---

### Post by Another Monkey on 2008-11-10
Ah!  I had read that but interpreted it to mean "this documentation is not yet complete".  I will see if modifying the xorg.conf does the trick for me.

Thanks.

---

### Post by Azraelthe7th on 2008-11-23
I can say that Option B has been, to me, a disaster.  Either it breaks X or it doesn't work.

What's bad is that overall, I like how HAL works.  Everything just works fine "out of the box".  It's just too bad you can't configure everything properly afterwards.

---

