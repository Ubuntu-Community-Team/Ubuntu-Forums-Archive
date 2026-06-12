---
title: "bamboo fun"
date: 2010-02-18
forum: Hardware
---

### Post by portets on 2010-02-18
well i just got my bamboo fun in the mail today.
but i can't get it working. :(

i went through all of the guides i could find here. i even tried a modified version of the wacom driver i found here. nothing at all. i already installed the driver and wacom tools through the package manager. rebooted. tried plugging it into every usb port.

typing
```
xinput --list
```it doesn't show up in the list. and

```
xsetwacom list
```doesn't do anything either

9.10 if that helps

---

### Post by Favux on 2010-02-18
Hi portets,

Karmic.  What is the model of your Bamboo Fun?  Is it a:  CTH661?

---

### Post by portets on 2010-02-18
yes, CTH-661

i already tried: [http://ubuntuforums.org/showpost.php?p=8262965&postcount=541](http://ubuntuforums.org/showpost.php?p=8262965&postcount=541)
and: [http://ubuntuforums.org/showpost.php?p=8129913&postcount=144](http://ubuntuforums.org/showpost.php?p=8129913&postcount=144)
following those steps didn't help.

i found out that the device does show up when typing "lsusb". so it isn't a connectivity issue like i thought. that and my girlfriend is in love with it on her windows pc ;), works great there....

---

### Post by Favux on 2010-02-18
OK, you're on the old P & T thread where Ayuthia just got the stylus and eraser working.  To get touch working you want the [Wacom Bamboo Pen and Touch Series Development]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") thread.  As you can see the patches ob1kenobi and Ayuthia developed there were submitted to the LWP and are now mostly in the new development version of linuxwacom 0.8.5-10 (the first to support the Bamboo P & T's).

Ob1kenobi's last patch set is probably better than 0.8.5-10.  It's linked in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") on the old thread.  0.8.5-11 isn't due out for a few weeks.

Good luck!

---

### Post by portets on 2010-02-18
thank you thank you thank you!
i was starting to regret buying this!

everything works great now. my only problem is that touch is kind of messed up. using my fingers causes the pointer to jump around and stuff.

but no complaints because it's beta

---

### Post by Favux on 2010-02-18
Great!  :)

That's why Ping at the LWP is delaying 0.8.5-11.  He isn't happy with touch and is working on it.

Can you tell me which .fdi you are using and whether wacomcpl is working for you?

---

### Post by portets on 2010-02-18
probably a good idea. now that i rebooted touch is only working  when i use my entire palm on the surface. pushing kind of hard too.

i think i'm using the one titled "Favux_new-generic_rc2_10-linuxwacom.fdi.txt".
and no, wacomcpl just comes up as a blank grey window with a scrollbox on the left and no text

edit: and also, "xsetwacom list" returns nothing

---

### Post by Favux on 2010-02-18
Could I see the output of?:
```
xinput --list
```

---

### Post by portets on 2010-02-18
yeah, here it is:

```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom BambooFun 2FG 6x81"    id=2    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 740
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 500
        Resolution is 1
"Wacom BambooFun 2FG 6x81 touch"    id=3    [XExtensionKeyboard]
    Type is Wacom Touch
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 9
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 740
        Resolution is 25
    Axis 1 :
        Min_value is 0
        Max_value is 500
        Resolution is 25
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
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom BambooFun 2FG 6x81 pad"    id=4    [XExtensionKeyboard]
    Type is Wacom Pad
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 8
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 0
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 0
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 4 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 5 :
        Min_value is 0
        Max_value is 71
        Resolution is 1
"Wacom BambooFun 2FG 6x8 Pen0"    id=5    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 9
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21648
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13530
        Resolution is 2540
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
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom BambooFun 2FG 6x8 Pen0 eraser"    id=6    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 9
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21648
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13530
        Resolution is 2540
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
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Power Button"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=9    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=10    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=11    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Acer Crystal Eye webcam"    id=12    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=13    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=14    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1

```

---

### Post by Favux on 2010-02-18
I'm going to assume you got the .fdi in correctly and it's the only linuwacom.fdi installed and that you do not have Wacom sections in xorg.conf.  If I'm wrong or you have questions ask.

Alright, it is seeing your Bamboo and calling stylus a couple of things:
```
"Wacom BambooFun 2FG 6x81"    id=2    [XExtensionPointer]
and
"Wacom BambooFun 2FG 6x8 Pen0"    id=5    [XExtensionKeyboard]

```
Partly this is due to LWP changing device naming slightl, also maybe partly due to them forgetting to include udev rules.

I think we can fix this if you want to work with me a little.

---

### Post by portets on 2010-02-18
actually, it looks like i have two "10-linuxwacom.fdi".
one in: /usr/local/share/hal/fdi/policy/20thirdparty
one in: /usr/share/hal/fdi/policy/20thirdparty

and no, nothing about wacom in xorg.conf.

> **Favux said:**
> I think we can fix this if you want to work with me a little.

sure, i could do that. :)
just know that my linux skills are mediocre.

---

### Post by Favux on 2010-02-18
Great!  Not a problem.  Could you show me the two .fdi's?  That would help me get a handle on things.  I'm assuming the one in:
```
/usr/share/hal/fdi/policy/20thirdparty/
```
is the one I asked you to intall.

Do you know where the one at:
```
/usr/local/share/hal/fdi/policy/20thirdparty
```
came from?

---

### Post by portets on 2010-02-18
yeah, it looks like the first one is the correct one. i'm not sure about the second one. the second one is just the first one with two added lines.
i think it came from a different thread on this forum. not sure which one anymore. should i delete it?

oh and the correct one has 49 lines of code, but your rc2 has 95.it looks like things didn't copy over correctly. should i re-copy/paste your "Favux_new-generic_rc2_10-linuxwacom.fdi" into the file?

---

### Post by Favux on 2010-02-18
Yes to both questions, remove the one in the wrong place and make sure the one in the correct place has just the contents of my .fdi.

Be sure to make backups of both files first!  I'd still like to see what was in each location if you are feeling ambitious.

With the right .fdi in the right place reboot and then let's see what 'xinput --list' and 'xsetwacom list' look like.

---

### Post by portets on 2010-02-19
alright. here's the 10-linuxwacom.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
    <append key="wacom.types" type="strlist">eraser</append>
    <append key="wacom.types" type="strlist">cursor</append>
    <append key="wacom.types" type="strlist">pad</append>
------    <append key="wacom.types" type="strlist">touch</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf;FUJ02e5;FUJ02e7;FUJ02e9">
    <append key="info.capabilities" type="strlist">input</append>
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
    <merge key="input.device" type="copy_property">serial.device</merge>
    <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
    <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009;WACf00A;WACf00B;WACf00C;WACf00D;WACf00E;WACf010;FUJ02e7;FUJ02e9">
      <!-- Serial tablets with touch capabilities -->
      <append key="wacom.types" type="strlist">touch</append>
    </match>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
      <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
      <append key="wacom.types" type="strlist">eraser</append>
      <append key="wacom.types" type="strlist">cursor</append>
-------      <append key="wacom.types" type="strlist">pad</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```p.s. i put dashes in front of the two lines that the .fdi in the correct place had. the dashed lines weren't in the incorrect file.

here's xinput --list
```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Acer Crystal Eye webcam"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=9    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"eraser"    id=10    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 9
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21648
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13530
        Resolution is 2540
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
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"stylus"    id=11    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 9
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21648
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 13530
        Resolution is 2540
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
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"pad"    id=12    [XExtensionKeyboard]
    Type is Wacom Pad
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 8
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 740
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 500
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 4 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 5 :
        Min_value is 0
        Max_value is 71
        Resolution is 1
"touch"    id=13    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 740
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 500
        Resolution is 1
```xsetwacom list used to return nothing, but now:
```
eraser           eraser    
stylus           stylus    
pad              pad       
touch            touch
```and wacomcpl shows "eraser", "stylus", and "pad" now. but when i click on any of them i get the error:

> can't read "isLCD(211)": no such element in array
can't read "isLCD(211)": no such element in array
    while executing
"if { ![ string compare $type "pad" ] } {
        if { $hasPad($model) } {
        createPanel 0 1 0 0
        }
    } elseif { ![ string compare $type "touch" ] } {
..."
    (procedure "updateDevice" line 24)
    invoked from within
"updateDevice"
    (command bound to event)

---

### Post by Favux on 2010-02-19
Hi portets,

Progress!  The .fdi in the wrong place is the old default linuxwacom.fdi.  The one with the two extra lines is the new default .fdi that came with 0.8.5-10.

OK, the device list in linxwacom is now populated by selecting a device doesn't work and gives the error message.

I need to think about it a bit.

Could you reboot and if still seeing the same thing post the following:
```
lshal>portets_lshal.txt
```
It'll be in /home/username.  And also Xorg.0.log in /var/log.  You'll need to compress both by right clicking on them and using Create Archive.  Then you can attach them to your next post using Managing Attachments below.

---

### Post by portets on 2010-02-19
here you go:

[ATTACH]147545[/ATTACH]

---

### Post by Favux on 2010-02-19
Thanks!  Give me a bit to look at it.  I gather the same error in wacomcpl after rebooting?

---

### Post by portets on 2010-02-19
oh no! another spambot! ^

and yes, same error.

---

### Post by Favux on 2010-02-19
Alright, pad is rejected:
```
(II) config/hal: Adding input device pad
(**) Option "Device" "/dev/input/event8"
(**) pad: always reports core events
(**) pad device is /dev/input/event8
(**) pad is in relative mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) pad: serial speed 9600
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
pad Wacom X driver can't grab event device, errno=16
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=740 maxY=500 maxZ=1023 resX=2540 resY=2540  tilt=disabled
```
and I don't know why.  And then I think the Synaptic Touchpad driver is grabbing your touch.  We can change the Synaptic .fdi to block that.

We may spend a while figuring this out.  My suggestion is to try to re-compile 0.8.5-10 using the [LinuxWacom HOW TO]("http://ubuntuforums.org./showpost.php?p=6546012&postcount=1").  Maybe there's a problem with the source Ayuthia linked you to but more likely you were missing libraries or dependencies.  What do you think?  I think if it works, it would be faster.

---

### Post by portets on 2010-02-19
did all of that. no change at all.. :|

it never said anything about missing dependencies either

---

### Post by Favux on 2010-02-19
OK, thanks for trying it.  Is anything working, like the stylus?

Here's the [Synaptic fix]("http://ubuntuforums.org/showpost.php?p=8823142&postcount=875").  With luck that will get you touch like it did for nossifer.

xsetwacom list is still showing stylus, eraser, touch and pad?

I'm beginning to think they broke wacomcpl for the Bamboo P & T's in 0.8.5-10.  They were trying to add some options for the Bamboo.  Wacomcpl in 0.8.5-10 works fine on my tablet pc so it may be Bamboo P & T specific.  I just noticed one reporting on linuxwacom-discuss wacomcpl not working and he's on Mandriva!

---

### Post by portets on 2010-02-19
yeah, the stylus works fantastically! eraser, pressure sensitivity, the calibration is spot on. but touch is terrible. multitouch doesn't work, and like i said earlier the cursor won't move anywhere unless i use my whole palm.

thanks i'll try the synaptic fix in a few minutes.

and yes, xsetwacom list still shows all four things.

maybe they did break the cpl. but shouldn't wacomcpl still work for me since i have the fun p & t?
i looked at the specifications and my device is exactly the same as a p & t, just a little bigger. but maybe i'm thinking wrong, my device is probably pretty different inside.

---

### Post by Favux on 2010-02-19
Sorry, I was using a shorthand.  We started calling all 5 tablets P & T's.  All five are listed in the post #384 I linked you to.  3 of them, including yours are pretty much identical.  Yours just is the top of line, bigger, more pressure levels, etc.

Hope the fix works.  Synaptic Touchpad would explain why it is so crummy.

---

### Post by portets on 2010-02-19
thanks, it made it a bit better. the touch only works for one or two seconds at a time now verses none before. multitouch works every once in a while too. i don't have to use my whole palm either.

if i sit there making zoom gestures for about ten seconds or so it'll zoom in a little bit.

another thing i noticed is that  the buttons change every reboot. after some reboots the top two buttons are scroll up and down respectively, and the two lower buttons are unassigned. after other reboots the two middle buttons are left and right mouse click with top and bottom unassigned. every time the middle buttons were the assigned ones, touch wouldn't work at all. when the top two were assigned the touch would work a little.
right now the middle are assigned, so i'll keep rebooting until the top two are assigned and see if touch works better.

thanks for going out of your way to help me though. much thanks :D

---

### Post by Favux on 2010-02-19
Hi portets,

Thank you!  You've helped me a lot.  I'm now certain it's not the .fdi causing the problem, it is the new wacomcpl.  The one thing you might try doing is adding the udev symlink rule as described in #384 post.  They left that out in 0.8.5-10, it will be in 0.8.5-11 they promised, which may be why Synaptic is grabbing touch.

It sounds like you now have linuxwacom running touch.  You can check the Xorg.0.log to verify along with 'xinput --list'.

Yeah, they also changed the device naming a little for 0.8.5-10, and as you noticed it is a mess.  Hopefully they'll get it all straightened out in 0.8.5-11.

If you go futher on the thread the Synaptic fix was on you'll see some scripts for configuring since wacomcpl won't work.

Honestly you might be better off going back to ob1kenobi's v.2 patch linked in #384.

---

### Post by portets on 2010-02-19
cool, thanks! so would i add:

```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00d3", SYMLINK="input/tablet-wacom-bamboo-pen_touch-$env{WACOM_TYPE}"
```

to the wacom rules file? 00d3 is my product id.

this is probably the last thing i'm trying until 0.8.5-11 comes out. i'm not too concerned with my control panel yet, as long as it's working within two or three months.

---

### Post by Favux on 2010-02-19
That's the right symlink.  Yes add it to the table.  The one in 5-11 will probably be a little different.

I sure hope it's sooner than 2-3 months.  Lucid is out in less than two months!

---

### Post by portets on 2010-02-19
it didn't change anything. but oh well, at least it's working somewhat.

thank you very much for all of your time and help! :D
it's appreciated so much, i can finally draw now.

i'll probably be back asking more questions when 0.8.5-11 is out. and yeah, hopefully that's somewhat soon. it doesn't look like too much needs fixed right now. just preventing touchpads from stealing input, and control panel fixing. at least for me

---

### Post by thomasbechtold on 2010-02-27
I have a Bamboo Fun CTH 661 and use Ubuntu Lucid (10.04) and there's no HAL available.
I posted bug reports. See [1] and [2].

Can anybody help how to get the Tablet working correct? I just can use hover with the pen.

$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; "TPPS/2 IBM TrackPoint"                 	id=10	[slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom BambooFun 2FG 6x8 Pen4" eraser   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom BambooFun 2FG 6x8 Pen4"          	id=14	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom BambooFun 2FG 6x85"              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=6	[slave  keyboard (3)]
    &#8627; "Video Bus"                             	id=7	[slave  keyboard (3)]
    &#8627; "Sleep Button"                          	id=8	[slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"          	id=9	[slave  keyboard (3)]
    &#8627; "ThinkPad Extra Buttons"                	id=12	[slave  keyboard (3)]

$ xsetwacom list
"Wacom BambooFun 2FG 6x8 Pen4" eraser ERASER    
"Wacom BambooFun 2FG 6x8 Pen4" STYLUS    



[1] [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/527912](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/527912)
[2] [https://sourceforge.net/tracker/index.php?func=detail&aid=2958923&group_id=69596&atid=525124](https://sourceforge.net/tracker/index.php?func=detail&aid=2958923&group_id=69596&atid=525124)

---

### Post by Favux on 2010-02-27
Hi thomasbechtold,

You don't need HAL/.fdi, you go back to using a xorg.conf.  Samples in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

I don't know if the X driver xf86-input-wacom 0.10.3 (Lucid package:  "xserver-xorg-input-wacom (1:0.10.3+20100109-1ubuntu1)") is recent enough to support the Bamboo Fun.  Also you probably need a 0.8.5-10 wacom.ko (usb kernel module/driver).

You may need to clone git master xf86-input-wacom and install and compile 0.8.5-10 wacom.ko and compy it into place (don't install linuxwacom).  I think they will work with each other, but not 100% sure.  You will need to install a xorg.conf.  All of this is described in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

I'd start with the xorg.conf and if that doesn't get some function go to compiling and installing xf86-input-wacom.  And if that doesn't get it going then compile the wacom.ko.

Good luck!

---

### Post by thomasbechtold on 2010-02-27
Thanks for the answer.
i already have compiled my own wacom.ko kernel module (from 0.8.5-10) and also installed the new xf86-input-wacom driver.
i'll try the xorg.conf stuff soon and hopefully this will work for me.

---

### Post by thomasbechtold on 2010-02-27
I got all working, but the touch is always clicking when i touch, so 1x touch = 1x click. That's unusable.
How can i fix this?
Another problem is, that i can not use my pen in relative mode. why not?

My xorg.conf looks like this:
Section "InputDevice" 
      Identifier        "stylus" 
      Driver            "wacom"
      Option		"Device"	"/dev/input/wacom"
      Option            "Type"           "stylus"
      Option            "USB"            "on" 
      Option            "Button2"        "3"  # make side-switch a right button 
      Option            "Mode"          "Relative"
      #Option            "TopX"           "225" 
      #Option            "TopY"           "225" 
      #Option            "BottomX"        "26300" 
      #Option            "BottomY"        "16375" 
EndSection 

Section "InputDevice" 
      Identifier        "eraser" 
      Driver            "wacom"
      Option		"Device"	"/dev/input/wacom"
      Option            "Type"           "eraser"
      Option            "Mode"          "Relative"
      Option            "USB"            "on" 
EndSection 

#Section "InputDevice"
#	Identifier	"pad"
#	Driver		"wacom"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"pad"
#	Option		"USB"		"on"
# remove comment if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
#EndSection

Section "InputDevice" 
      Identifier        "touch" 
      Driver            "wacom"
      Option		"Device"	"/dev/input/wacom-touch"
      Option            "Type"          "touch"
      Option            "USB"           "on" 
      Option            "Mode"          "Relative"
      #Option            "TopX"           "200" 
      #Option            "TopY"           "225" 
      #Option            "BottomX"        "4000" 
      #Option            "BottomY"        "3875" 
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice	"stylus"
	InputDevice	"eraser"
#        InputDevice	"pad"
	InputDevice	"touch"	
EndSection

---

