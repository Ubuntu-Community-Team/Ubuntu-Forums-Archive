---
title: "using Saitek Gamer's Keyboard"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by astronouth7303 on 2006-11-22
Ubuntu edgy eft, kept up-to-date.

I have a [saitek gamer's keyboard](http://www.saitekusa.com/usa/prod/gamerskey.htm) which is recognized perfectly as such and works perfectly as far as the main keyboard goes, media keys included.

How do I use the extra command pad? It works (ie, it sends data to /dev/input/event* when I push buttons on it) but I don't know how to configure Linux/X to use it.

---

### Post by MonkeyWrench32 on 2006-12-01
I have one of these myself and I'd appreciate some help if at all possible.

---

### Post by astronouth7303 on 2007-01-10
Any news with this? I am still clueless as to how to do this.

---

### Post by MonkeyWrench32 on 2007-01-11
I had no luck whatsoever.  I just unplugged it.  :(

---

### Post by tecslicer on 2007-01-16
I am in the same boat. The keyboard proper works without a hitch but the command pad has nothing doing. But it does light up.

---

### Post by astronouth7303 on 2007-04-07
I have managed to figure out that the event devices (the last or two of /dev/input/event2 through /dev/input/event4) are very parsable. It emits packets of 16 bytes, 4 packets for each key press (2 on down, 2 on up). The first 6 bytes are a timestamp (but shuffled up), and then there are 10 bytes of flags.

You could write a daemon to read this and then forward it to a more conventional input, or even perform actions on it. The daemon itself could easily be in a script.

If you want to understand what's going on, I  suggest running `sudo cat /dev/input/event4 | od -x` and start hitting buttons.

---

### Post by astronouth7303 on 2007-05-17
I have written a daemon that reads the event device and forwards events as signals over dbus. The problem is that my simple client can't receive the signals.

Anyway, if you want to play around with it, I'd be more than happy to send it to you.

---

### Post by astronouth7303 on 2007-05-22
I've written a basic daemon and and test client to deal with the command pad. They're both written in python 2.4 and up. The only other requirement is the python-dbus package. There is a good chance it will not work on non-x86 systems. The tarball is attached.

The hardest part will probably be determining the correct device to use. My suggestion is to run the command:
```

lshal | grep -C 5 "Chicony USB Gaming Keyboard Pro" | grep "/dev/input/event"

```
and use the highest number that appears.

Alternatively, open the device manager (hal-device-manager) and look for the USB Gaming Keyboard Pro. Under the third USB HID Interface, select "Chicony USB Gaming Keyboard Pro", and select the Advanced tab. Use the device file under either "input.device" or "linux.device_file".

No matter which version you use, it should be in the form of "/dev/input/event#", where the # is some digit (in my case, /dev/input/event3).

Instructions:
[list=1]
[*]Download and extract tarball
[*]Modify etc-commandpadd.conf and change "/dev/input/event3" to whatever you found above
[*]Run ```
sudo make install
``` in the directory you extracted to. This installs the necessary configuration files.
[*]To run the daemon, run commandpadd as root. (sudo ./commandpadd)
[*]The test client is cpd-test. All it does is print out detected events. No more. Run it from a terminal and watch the events go by.
[/list]

If anyone has problems with this, please post here. This is under-development software. While it shouldn't ruin your computer or your life, I can't guarantee it won't.

I know digging up the device is a pain. I'll make it automatic before I officially release this.

(In case you care: GNU GPL)

---

### Post by astronouth7303 on 2007-05-26
I've finished version 0.2.2. The major thing is that it now autoconfigures and it supports multiple pads. (why would you want 2 keyboards? I don't know.) You may remove /etc/commandpadd.conf.

It is also packaged as a .deb file, instead of a source tarball. It is available at [http://www.astro73.com/download/deb/cmdpadd_0.2.2_all.deb](http://www.astro73.com/download/deb/cmdpadd_0.2.2_all.deb).

cpd-test has been incorporated into the python modules, so you must now run ```
python -m commandpad.client
```

Note that there still is no real client. I am open to suggestion as to what exactly a "real client" should do.

---

### Post by TemplaraPheonix on 2007-07-09
As much as I applaud you for taking the initiative on this one, won't it have been easier to have X map the keys? This may or may not be possible, though. If someone with the extra pad could run:

xev | grep keycode

in an xterm or konsole and then press some regular keys and extra ones, I'd be much obliged. 

I have the non-gamers (i.e. the eclipse without the pad) and was trying to hack on a few extra keys (I don't need a whole pad but 4-8 hotkeys would be nice) since the connections exist on the board to add some switches. However, I'm not sure if this is possible. If I try to connect contacts on the board to simulate key presses I don't get reliable codes. I'm not sure if this is an electrical / keybounce issue or if the kernel driver just isn't capable of doing this. As mentioned above the keyboard is detected as the Chicony USB Gaming Keyboard Pro, not the Saitek Eclipse though I don't know if this matters. As far as regular keyboard (including the multimedia keys) everything else seems to work.

---

### Post by astronouth7303 on 2007-07-09
> **TemplaraPheonix said:**
> As much as I applaud you for taking the initiative on this one, won't it have been easier to have X map the keys?

The problem is that X doesn't pick it up at all. I would love to route it through X (because then you hook into everything else), but frankly, I don't know how.

If someone could write an HID driver for X, you may have the appreciation of hundreds of gamers.

---

### Post by TemplaraPheonix on 2007-07-10
Did you try the:

xev | grep keycode

If it does give sane output, (i.e. one keycode per key, the same keycode per key, etc.) you just map the keys like multimedia keys. This tutorial: [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys) is the Ubuntu version of what I was trying to do as most of the stuff besides the wizard is just stock X.

The XF86Launch keys (0-F) in /usr/lib/X11/XKeysymDB were what I was looking to assign to hotkey start some applications. I'm sure there are tools (or it would be trivial to make one) to map some of these unused message strings into macros of other key combinations for gaming. Not sure if it would be responsive enough.

However, please do try 

xev | grep keycode

and press some keys on the keyboard and gamepad. Either way, I'm very interested in the results.

---

### Post by astronouth7303 on 2007-07-11
This was already suggested. No, it doesn't output anything.

---

### Post by TemplaraPheonix on 2007-07-12
Thanks for trying.

---

### Post by astronouth7303 on 2007-07-15
Good news!

The package xserver-xorg-input-evdev contains the evdev driver for XOrg.

My current solution also uses evdev, I just didn't know it.

I'm currently reading through the docs and attempting to come up with the right configuration for the Saitek Gamer's Keyboard command pad.

I'll post instructions when I finish.

---

### Post by astronouth7303 on 2007-09-17
IT WORKS!!!

[http://www.astro73.com/blog/command-pad-success/]("http://www.astro73.com/blog/command-pad-success/")

It's not user-friendly, but it works.

I've attached the source code. You need SWIG, python2.5 headers, and the linux headers (on top of the usual gcc/make/etc).

---

### Post by platinummonkey on 2007-09-18
Sweet! okay now how to you set that up and working. Ive already make'd it, but cant seem to get it to run they way it was intended :P  (I was in the process of mapping keys the long way when I stumbled on this :P much relief :P)

---

### Post by astronouth7303 on 2007-09-18
> **platinummonkey said:**
> Sweet! okay now how to you set that up and working. Ive already make'd it, but cant seem to get it to run they way it was intended :P  (I was in the process of mapping keys the long way when I stumbled on this :P much relief :P)

It's not really intended for end users.

You have to run cmdpadd as root (sudo).

After running make, listkeys will print to stdout which keys are available to use. uinput.html will also list them (Linux only pays attention to the KEY_* constants).

To reconfigure the key mappings, you have to open up cmdpadd in a text editor of your choice and change MAPPING. The buttons go 1,2,3,...8,9,A,B. You change the KEY_* constant (keep the "uinput.", period included) to what you want. I've found that many keys (esp those with values at or above KEY_MIN_INTERESTING) are ignored by most apps. If it starts putting out errors, read the Python tutorial to learn basic syntax.

Also remember that this inserts keys at the lowest level. If you have your right super key configured as your compose key, then any buttons set to KEY_RIGHTMETA will also act as compose.

At this point in time, I can not provide support of any kind. If you want to send patches, that's great. If not, wait. Let me borrow a warning:
[quote=Brion Vibber][FONT="Courier New"]**  WARNING: USE OF THIS ALPHA RELEASE MAY INFEST YOUR HOUSE WITH  **
**  TERMITES, ROT YOUR TEETH,  GROW HAIR ON YOUR PALMS, AND PASTE  **
**  INNUENDO  INTO  YOUR  C.V.  RIGHT  BEFORE  A  JOB  INTERVIEW!  **
**  DON'T SAY WE DIDN'T WARN YOU, MAN. WE TOTALLY DID RIGHT HERE.  **[/FONT][/quote]

---

### Post by platinummonkey on 2007-09-18
[quote=astronouth7303]To reconfigure the key mappings, you have to open up cmdpadd in a text editor of your choice and change MAPPING. The buttons go 1,2,3,...8,9,A,B. You change the KEY_* constant (keep the "uinput.", period included) to what you want.[/quote]

ah, thats the answer I was looking for :P thx :P

---

### Post by Sockerdrickan on 2007-09-20
Guys can I get a confirm that the keyboard works in feisty/gutsy and the back light stuff?

---

### Post by platinummonkey on 2007-09-20
Yeah it does, backlight definetly and the volume buttons as well. :P but Im actually not using this keyboard with my ubuntu system :P Im using it with my arch system.   Astronouth7303's program works quite well, although im currently trying to program some nifty macros for it :P ill post some instructions as well :P

---

### Post by Sockerdrickan on 2007-09-21
HELLYEAH I'm buying one!

---

### Post by Wamoc on 2008-01-11
I also have this keyboard, and the main keys and volume buttons worked from install. The backlight also did, but the odd thing for me is the leds for caps/num/scroll lock wont light up. They did right before I switched to ubuntu while I was in my windows install. Anyone have ideas to fix this?

---

### Post by mtristan on 2008-04-12
Hi,
I have this keyboard since 4 months, and I tried to get the command pad working with my own way, but... not very useful ^^
Now, I found your post, and I just wanted to know if you had found a user friendly way to get it working, because I haven't found how to use your solution yet... 
Thanks for news.
See You

---

