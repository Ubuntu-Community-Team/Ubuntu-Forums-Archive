---
title: "Work around for toggling touchpads."
date: 2010-10-27
forum: Hardware
---

### Post by lupusnoctu on 2010-10-27
Hello all! I was having some trouble with my touchpad on my Asus G72GX laptop. I have two buttons, FN+F9 and a hardware button, that are meant to toggle my touchpad on and off, but in GNOME, it wasn't working. After some research, I found that I could use ```
$ synclient TouchpadOff=1
```to turn it off, and ```
$ synclient TouchpadOff=0
``` to turn it back  on, but this was cumbersome and slow, so I made a workaround! I hope this helps for anyone that's having a similar problem. It's a program I wrote in C/C++. It is free, open source software that I am releasing under GNU General Public License.

README:
```

			bTouch Version 0.0.4
			  Initial release
							
		 Copyright (C) 2010 E. Mark Anderson
					 
Introduction:
-------------

bTouch was designed to overcome an issue I was having with the touchpad
on my Asus G72GX laptop where in GNOME, I was unable to use either FN+F9
or the hardware button to toggle the touchpad on and off, even though the 
system recognized both events as XF86Tools. This program intelligently
decides if the touchpad should be on or off using the 'synclient' command
available on my Ubuntu system. It does *NOT* listen for any key events of any
sort. To use it the way it was intended, you'll need to bind a key to execute
this program.

bTouch is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

bTouch is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along
with this program.  If not, see <http://www.gnu.org/licenses/>.


Installation:
-------------

Installation should be very simple and standard for any program you install
from source. Just run ./configure, make, and make install (as root). The binary
should now reside in /usr/local/bin. Most systems have this in their PATH, so it
should now be able to run like any other system tool. To test this, open up a
terminal and type 'btouch --log' or 'btouch -l'.

If it works, it'll toggle your touchpad on or off and place a log in 
~/.btouch.log (note that this is a hidden file!). It is possible to 
change where it writes the log. If, for example, you want it written to 
/home/foo/Desktop/btouch.log, do 'btouch -l /home/foo/Desktop/btouch.log'. 
WARNING: This is *NOT* a fully safe function. Please see "Known Issues" below.


Configuring for use:
--------------------

This should be unneeded for KDE users. I don't know for sure, but on my system,
KDE properly toggles the touchpad on and off when I press either FN+F9 or the 
physical button. But I spend almost all my time in GNOME because my games run
better.

To configure GNOME to use bTouch, go to (System -> Preferences -> 
Keyboard Shortcuts) and click "Add". In "Name" type "Toggle Touchpad" and in 
"Command" type "btouch" and click "Apply". Now scroll down to the bottom of the
list of keybinds. You should see your new action. Click on it over in the 
"Shortcut" column, and press the key or key combination you want bound to it. 
Your key combination should now show in the Shortcuts column. Just click close and
You're done!

To test it out, press your new keybind. If the touchpad was on, it
should turn off. If it was off, it should turn on. ENJOY! :)


Known Issues:
-------------

The '--log' and '-l' switches are safe on their own, but do not yet check a 
specified file path for validity. Your system should be capable of protecting 
itself from a mal-formed path, or a path with insufficent privileges, but still:
BE CAREFUL WHEN PASSING A LOG PATH! SEE SECTIONS 15 AND 16 OF THE GNU General 
Public License, WHICH CAN BE FOUND IN 'COPYING' OR AT 
<http://www.gnu.org/licenses/>

Unable to create directories. Log file *MUST* be placed in an *EXISTING* directory.

Only works with touchpads that can be affected by the "synclient" command.

Does not have --help, -h, or -? switches yet.


Reporting Bugs:
---------------

If this program does not work, or you encounter a bug, please notify the developer.
Please include as many details as you can.

You may or may not recieve a reply, but rest assured that it will be read. 
Thank you.


Supporting Development:
-----------------------

The developer currently does not accept monetary donations of any kind and has no
plans to, but if you'd like to help keep this project going and are familiar
with C/C++, please consider offering your assistance to the developer, as he is
still learning the language.

If you would like to help with debugging, contact the developer and request a
copy of the latest debug build.

If you are not familiar with C/C++ or computer programming, YOU CAN STILL HELP! 
Comments, suggestions,and feature requests are welcome. 

```

---

### Post by jack frost on 2011-01-11
I just got one of these laptops for Christmas and really like it with Windows 7 64.  How well does this unit play with Ubuntu. I was going to try out the live cd;but have not had time to play around. On the full install is everything ok?  I was going to install 10.10 and maybe dual boot.  I had 10.10 on a desktop;but sold it to go laptop. thanks.
 
> **lupusnoctu said:**
> Hello all! I was having some trouble with my touchpad on my Asus G72GX laptop. I have two buttons, FN+F9 and a hardware button, that are meant to toggle my touchpad on and off, but in GNOME, it wasn't working. After some research, I found that I could use ```
$ synclient TouchpadOff=1
```to turn it off, and ```
$ synclient TouchpadOff=0
``` to turn it back on, but this was cumbersome and slow, so I made a workaround! I hope this helps for anyone that's having a similar problem. It's a program I wrote in C/C++. It is free, open source software that I am releasing under GNU General Public License.
 
README:
```

            bTouch Version 0.0.4
              Initial release
 
         Copyright (C) 2010 E. Mark Anderson
 
Introduction:
-------------
 
bTouch was designed to overcome an issue I was having with the touchpad
on my Asus G72GX laptop where in GNOME, I was unable to use either FN+F9
or the hardware button to toggle the touchpad on and off, even though the 
system recognized both events as XF86Tools. This program intelligently
decides if the touchpad should be on or off using the 'synclient' command
available on my Ubuntu system. It does *NOT* listen for any key events of any
sort. To use it the way it was intended, you'll need to bind a key to execute
this program.
 
bTouch is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
 
bTouch is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details.
 
You should have received a copy of the GNU General Public License along
with this program.  If not, see <http://www.gnu.org/licenses/>.
 
 
Installation:
-------------
 
Installation should be very simple and standard for any program you install
from source. Just run ./configure, make, and make install (as root). The binary
should now reside in /usr/local/bin. Most systems have this in their PATH, so it
should now be able to run like any other system tool. To test this, open up a
terminal and type 'btouch --log' or 'btouch -l'.
 
If it works, it'll toggle your touchpad on or off and place a log in 
~/.btouch.log (note that this is a hidden file!). It is possible to 
change where it writes the log. If, for example, you want it written to 
/home/foo/Desktop/btouch.log, do 'btouch -l /home/foo/Desktop/btouch.log'. 
WARNING: This is *NOT* a fully safe function. Please see "Known Issues" below.
 
 
Configuring for use:
--------------------
 
This should be unneeded for KDE users. I don't know for sure, but on my system,
KDE properly toggles the touchpad on and off when I press either FN+F9 or the 
physical button. But I spend almost all my time in GNOME because my games run
better.
 
To configure GNOME to use bTouch, go to (System -> Preferences -> 
Keyboard Shortcuts) and click "Add". In "Name" type "Toggle Touchpad" and in 
"Command" type "btouch" and click "Apply". Now scroll down to the bottom of the
list of keybinds. You should see your new action. Click on it over in the 
"Shortcut" column, and press the key or key combination you want bound to it. 
Your key combination should now show in the Shortcuts column. Just click close and
You're done!
 
To test it out, press your new keybind. If the touchpad was on, it
should turn off. If it was off, it should turn on. ENJOY! :)
 
 
Known Issues:
-------------
 
The '--log' and '-l' switches are safe on their own, but do not yet check a 
specified file path for validity. Your system should be capable of protecting 
itself from a mal-formed path, or a path with insufficent privileges, but still:
BE CAREFUL WHEN PASSING A LOG PATH! SEE SECTIONS 15 AND 16 OF THE GNU General 
Public License, WHICH CAN BE FOUND IN 'COPYING' OR AT 
<http://www.gnu.org/licenses/>
 
Unable to create directories. Log file *MUST* be placed in an *EXISTING* directory.
 
Only works with touchpads that can be affected by the "synclient" command.
 
Does not have --help, -h, or -? switches yet.
 
 
Reporting Bugs:
---------------
 
If this program does not work, or you encounter a bug, please notify the developer.
Please include as many details as you can.
 
You may or may not recieve a reply, but rest assured that it will be read. 
Thank you.
 
 
Supporting Development:
-----------------------
 
The developer currently does not accept monetary donations of any kind and has no
plans to, but if you'd like to help keep this project going and are familiar
with C/C++, please consider offering your assistance to the developer, as he is
still learning the language.
 
If you would like to help with debugging, contact the developer and request a
copy of the latest debug build.
 
If you are not familiar with C/C++ or computer programming, YOU CAN STILL HELP! 
Comments, suggestions,and feature requests are welcome. 

```

---

### Post by lupusnoctu on 2011-01-11
> **jack frost said:**
> I just got one of these laptops for Christmas and really like it with Windows 7 64.  How well does this unit play with Ubuntu. I was going to try out the live cd;but have not had time to play around. On the full install is everything ok?  I was going to install 10.10 and maybe dual boot.  I had 10.10 on a desktop;but sold it to go laptop. thanks.

Ubuntu 10.10 is working great for me on it. Just had that one quirk with the button for toggling the mouse, which is why I wrote this program. 

Of course, that's not saying anything about the defective display wires, causing the display to white out on me at random. But that's a relatively easy fix. If you have this problem, just pop off the hinge cap on the left side of the screen. That will expose some wires next to the hinge assembly. When my screen whites out, I just poke at them a little and the display comes back. Just remember that this is an issue with the hardware itself, not the software.

I also hope that you don't have one of the other problems mine has. Does windows stutter if you unplug from AC while powered up? If so, it will LOCK up in ubuntu. I don't know what's wrong with it, but I suspect a it's a faulty power supply system.  If yours is doing this and it's not to late to return it, I recommend you get that machine traded in for a more reliable brand such as HP. I was recently able to get an HP Pavilion dv7-4170us. I haven't had a chance to try linux on it yet, but so far it's been working much better in windows than my ASUS did in any OS.

Hardware defects aside, that machine is powerful and stable. If only it didn't have ASUS' shoddy craftsmanship and atrocious customer support, it would be a wonderful machine.

---

### Post by jack frost on 2011-01-31
> **lupusnoctu said:**
> Ubuntu 10.10 is working great for me on it. Just had that one quirk with the button for toggling the mouse, which is why I wrote this program. 

Of course, that's not saying anything about the defective display wires, causing the display to white out on me at random. But that's a relatively easy fix. If you have this problem, just pop off the hinge cap on the left side of the screen. That will expose some wires next to the hinge assembly. When my screen whites out, I just poke at them a little and the display comes back. Just remember that this is an issue with the hardware itself, not the software.

I also hope that you don't have one of the other problems mine has. Does windows stutter if you unplug from AC while powered up? If so, it will LOCK up in ubuntu. I don't know what's wrong with it, but I suspect a it's a faulty power supply system.  If yours is doing this and it's not to late to return it, I recommend you get that machine traded in for a more reliable brand such as HP. I was recently able to get an HP Pavilion dv7-4170us. I haven't had a chance to try linux on it yet, but so far it's been working much better in windows than my ASUS did in any OS.

Hardware defects aside, that machine is powerful and stable. If only it didn't have ASUS' shoddy craftsmanship and atrocious customer support, it would be a wonderful machine.

 
thanks for the reply.. I did an install today and dual booting right now. it picked up all the hardware and the webcam picture is even more clear than win7 in skype.  

No , I have not had any of those issues with the
  screen going white.. and none in windows.. I usually use a usb mouse so I don't have any issues with the touchpad.  I just got the burn effects rolling again and used the restricted nvidia driver and all is ok.

i just have to figure how to get total transparency in the taskbar

---

### Post by jack frost on 2011-01-31
> **jack frost said:**
> thanks for the reply.. I did an install today and dual booting right now. it picked up all the hardware and the webcam picture is even more clear than win7 in skype.  

No , I have not had any of those issues with the
  screen going white.. and none in windows.. I usually use a usb mouse so I don't have any issues with the touchpad.  I just got the burn effects rolling again and used the restricted nvidia driver and all is ok.

i just have to figure how to get total transparency in the taskbar


I actually found the fix for transparency:

[http://www.webupd8.org/2010/09/fix-gnome-panel-for-ubuntu-1010.html](http://www.webupd8.org/2010/09/fix-gnome-panel-for-ubuntu-1010.html)

I do have an issue of my laptop screen not coming up after it is in suspend..still checking that out.

---

