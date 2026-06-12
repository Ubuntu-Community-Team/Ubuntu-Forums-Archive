---
title: "Wacom Intuos3 - lost eraser after updating driver"
date: 2009-07-30
forum: Hardware
---

### Post by skullmunky on 2009-07-30
SOLVED: if you build a newer wacom driver from source, it really is important not to uninstall the xserver-xorg-input-wacom package but instead just manually install the module yourself.

The Ubuntu package includes a couple of useful things that the upstream source does not, like custom udev rules.  For me that didn't matter, but what did matter is the location of the script hal-setup-wacom.  Installing from source puts it in /usr/libexec, but Ubuntu wants it to be in /usr/lib/hal.  I moved it there and now I get the eraser and pad back.  Hooray!  And now I know more about how HAL works.  Double Hooray!

I notice karmic will have this newer version of the wacom driver anyway :)  

Original post below:
--------------
I've read through the other Wacom threads here which are rich and full of great information, but I'm not quite sure exactly which direction to go here.

I have an Intuos3, running Jaunty.  It worked well out of the box (hotplug, pen, eraser, pressure), but I couldn't get TwinView to work.  I installed linuxwacom 0.8.3 from source, and now TwinView works fine; but, I've lost the eraser tool.  I've tried a lot of different fdi files, and I can't get the eraser back.  Everything else works.  

Wacdump shows me events for the eraser, as well as the pads, buttons, and tilt.  But, xinput only shows the one device, and xidump only responds to the pen, not the eraser.

I'm actually having the most success with the default Jaunty fdi - any others I've tried seem to lose the pressure axis.

My current configuration:

1. Removed wacom-tools and xserver-xorg-input-wacom
2. Built linuxwacom 0.8.3.  Here's how I did it:
```

./configure --prefix=/usr
make
sudo checkinstall make install

```

I set the prefix because otherwise stuff goes in /usr/local and doesn't work.

I notice in some other posts it's recommended NOT to make install but instead manually copy only the .ko file - why is that?

3. fdi file:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
    <match key="info.product" contains="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
</deviceinfo>

```

4. nothing in xorg.conf or udev/rules.d

5. wacdump /dev/input/input3 : everything works

6. xinput -list: 
```

"Wacom Intuos3 9x12"    id=6    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 7
        Num_axes is 6
        Mode is Absolute
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 60960
                Resolution is 5080
        Axis 1 :
                Min_value is 0
                Max_value is 45720
                Resolution is 5080
        Axis 2 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1
        Axis 3 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 4 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 5 :
                Min_value is -900
                Max_value is 899
                Resolution is 1

```
5. xidump -u raw Wacom\ Intuos3\ 9x12
works, but no eraser

6. GIMP

pen works, pressure works, but no eraser

7. xsetwacom set "Wacom Intuos3 9x12" TwinView horizontal

works

I feel like I missed a small but crucial step somewhere ... any hints?  

thanks!

---

### Post by Favux on 2009-07-30
Hi skullmunky,

Nice job.  Very clear post.

---

