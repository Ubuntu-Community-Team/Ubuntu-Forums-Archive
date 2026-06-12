---
title: "help with tablet recogntion"
date: 2010-04-13
forum: Hardware
---

### Post by khryss on 2010-04-13
i have an acer travelmate c110 tablet pc (with stylus), i would really love to run xubuntu on it but when i install everything works great except the right click is suppose to be the button on the side of the stylus and it is not. ive tried changes(many of them) to the wacom config file, but all that does is stop the stylus from working at all , i really dont want to go back to windows ..... please help (if anyone is running this setup SUCCESSFULLY i would love your wacom config file or files or instructions on how to remap the right click to where its suppose to be) thanks

---

### Post by Favux on 2010-04-14
Hi khryss,

Welcome to Ubuntu forums!

Which release of Ubuntu/Xubuntu are you using?

We probably need to look at a couple of things.  In a terminal enter:
```
xinput --list
```
and
```
xsetwacom list
```
and post the output for each.

Hope this helps.

---

### Post by khryss on 2010-04-14
xubuntu 9.10 .... hoping the final release of 10.04 will fix this (the betas havent yet)
ok sorry it took me awhile 1st 
xinput --list got
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
"Wacom Serial Tablet PC Pen Tablet/Digitizer"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"    id=3    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"Sleep Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=7    [XExtensionKeyboard]
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


next 
xsetwacom list got
nothing it says xsetwacom isnt installed (which i know it is as i already did that)
so i went to the package mgr to look for and reinstall xsetwacom .... and with all repositories enabled its not there either!?!?!?!?!
also for some reason my wireless dosent work now for some reason (which totaly defeats the purpose of having a tablet in the first place

you know how long ive been TRYING to run any linux???? 3 years of sheer HELL!!!!
everybody says oh its easy, ..... it just works, ..... yea right 
i need to know what im doing wrong

---

### Post by Favux on 2010-04-14
Hi khryss,

Sorry to hear that.  We should be able to get your Wacom digitizer setup anyway.  Right now according to xinput your devices are:
stylus = "Wacom Serial Tablet PC Pen Tablet/Digitizer"
eraser = "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

For wacomcpl and xsetwacom commands to work (you enter wacomcpl in a terminal and the wacom calibration and configuration gui pops up) the names HAL is returning need to be changed to stylus and eraser.  Use the new-generic .fdi attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Instructions are in "Section 2: Configuring the Wacom Tablet/Devices" / "b) Jaunty and Karmic-configuring through a wacom.fdi".

Then to set up wacomcpl go to "Section 3: Calibrating your Tablet or Tablet PC".

---

### Post by khryss on 2010-04-14
i did all that (that i could understand) with my last install before this and thats what im talking about whenever i mess with the .fdi files the whole thing stops working ... maybe i just cant grasp this

---

### Post by Favux on 2010-04-14
> whenever i mess with the .fdi files the whole thing stops working
Hmmm.  Maybe you should describe how you are editing your .fdi files.  In other words use your own words to describe your understanding of the instructions.

---

### Post by khryss on 2010-04-15
ok i haven't tried this in a while as it had me VERY frustrated so if you tell me what to type in the terminal to get the wacom directory and have the files be editable ill tell you which .fdi file i did this with (i know it was the main config file as the few tutorials i read told me)

first i just put the downloaded .fdi file in that directory with the other one and named it custom settings ... that did nothing

so next i replaced the config file with the downloaded file and renamed it to what the original was ..  that stopped everything from working

then i opened both files in text editor and copied and pasted a few lines, and the whole document ... and both of those options stopped everything from working also
(i thought that mabye something was hidden in the name of original file)

and ive done all these steps with several downloaded .fdi files

---

### Post by khryss on 2010-04-15
Oh and I got the wacomcpl command to work and it is blank nothing to select nothing to configure (just as it was when I've tried this before )

---

### Post by Favux on 2010-04-15
Right, wacomcpl will be blank until you get the new .fdi in.

It's actually hard to get a boot hangup with a .fdi file.

You want to completely replace the contents of the default 10-linuxwacom.fdi with the entire contents of the new .fdi, but you will leave the name the same.  You are trying to make it too complicated.  Section 2b tells you how to make the back up and edit the file.  Once you've back it up you edit it with the gksudo gedit command.  Delete the entire contents.  And then copy and paste the entire contents of the new .fdi opened in a regular text editor, Save and reboot.  Terminal and Text Editor/gedit are in Applications > Accessories.

> i replaced the config file with the downloaded file
If you are talking about the xorg.conf in /etc/X11, you do not need to touch that or add any Wacom stuff to it.  Messing with this file will call cause boot hangups unless you're careful.

---

### Post by khryss on 2010-04-15
ok i didn't mean it wouldn't boot after editing the .fdi file i meant the stylus wouldn't work (sorry)
i did this
"replace the contents of the default 10-linuxwacom.fdi with the entire contents of the new .fdi, but you will leave the name the same."
here
"then i opened both files in text editor and copied and pasted a few lines, and the whole document ..."
and also when i said 
" i replaced the config file with the downloaded file"
i meant the .fdi not xorg.conf in /etc/X11
when i replace the contents of the default 10-linuxwacom.fdi i did use  gksudo gedit command .... and the stylus stopped working all together ... is that when i use wacomcpl because its still blank

---

### Post by khryss on 2010-04-15
sorry im dense

---

### Post by Favux on 2010-04-15
No worries, let's just get you set up.

If you think you've changed the .fdi correctly let's see what the output of this command:
```
xinput --list
```
in a terminal looks like.  Copy and paste the command.

---

### Post by khryss on 2010-04-15
ok im at work right now but as soon as i get home ill post the output of that for you ... its 11:00 now that will be 5:30ish

---

### Post by khryss on 2010-04-15
i havent switched the contents of the fdi files because it wont let me ... ive tried
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
but it acts like its doing something , asks me for my password , and then does nothing and the prompt comes back ... so what now

---

### Post by khryss on 2010-04-15
ok 
xinput --list ... says
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
"Wacom Serial Tablet PC Pen Tablet/Digitizer"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"    id=7    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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

---

### Post by Favux on 2010-04-15
No error messages?  Does Xubuntu use a different Text Editor than gedit (Gnome editor)?  You should be able to check in Synaptic Package Manager if gedit or somethingl else is installed.

OK, the new .fdi isn't installed otherwise:
stylus = stylus
eraser = eraser

not the long names.

---

### Post by khryss on 2010-04-15
I did the new fdi right before xinput -- list do I have to restart?

---

### Post by Favux on 2010-04-15
You need to be root/super user to edit that file, hence gksudo (ie graphical sudo).  Then reboot.

If you use your file viewer and navigate to the 10-linuxwacom.fdi and look at the file (probably right click on it and choose view in txt editor) you can see if the changes took.

---

### Post by khryss on 2010-04-15
yes i got gksudo to work ... and restarted , and how would i know if the changes took i have no idea what im looking for
anyway here it is after i restarted
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
"stylus"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"stylus cursor"    id=3    [XExtensionKeyboard]
    Type is Wacom Cursor
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"eraser"    id=4    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 21240
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 15980
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"Sleep Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=9    [XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"    id=10    [XExtensionPointer]
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

---

### Post by Favux on 2010-04-15
Congratulations!  Looks like you've got it.  Now in a terminal:
```
xsetwacom list
```
will return output instead of being blank which means wacomcpl will have options.

---

### Post by khryss on 2010-04-15
ok it says stylus and eraser .... i still dont know how to make the button on the side of the stylus the right mouse button ... is the button on the side of the stylus stylus or eraser???

---

### Post by khryss on 2010-04-15
never mind i got it ... THANK YOU SOOOOOO MUCH for your help ... might you be able to help me figure out y my wireless isnt working?

---

### Post by Favux on 2010-04-15
Great!  Now remember to follow section 3 to set up wacomcpl's .xinitrc to run every time you boot.

Do you know the manager of your wifi chipset?  For example Broadcom.

---

### Post by khryss on 2010-04-15
only thing i can find on google for wireless is intel

---

### Post by khryss on 2010-04-15
also could not complete step 3 as it wouldnot let me edit the file from this
# invoke global X session script
. /etc/X11/Xsession
to this
# invoke global X session script
#. /etc/X11/Xsession

when i tried to open it with gksudo it was just blank?

---

### Post by Favux on 2010-04-15
Well I meant in your documention or the spec.s at the manufacturers website selling it.

But you can get it by entering in a terminal:
```
lspci
```
The output isn't that long.  For exacomple my wifi chipset looks like:
> 03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by khryss on 2010-04-15
no documentation bought on ebay ... to old to be on acer website
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
is that what you need?

---

### Post by khryss on 2010-04-15
the light on the side says its working , when i right click on the network at the top it says wired network auto eth0 , under wireless there is nothing

---

### Post by Favux on 2010-04-15
I'm pretty sure that Intel has non-proprietary linux support for it's chipsets, so it should just work.

If it was proprietary you'd want to check the box in front of "Software resticted by copyright, etc." in Software Sources.  System > Administration > Software Sources. Then you run Hardware Drivers in System > Administration.

But now you have the right key words to search the forums or google for help, ie:  Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04).  Good luck!

---

