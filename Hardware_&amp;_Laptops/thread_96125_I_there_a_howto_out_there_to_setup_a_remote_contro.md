---
title: "I there a howto out there to setup a remote control?"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by daller on 2005-11-28
Hi There,

When I bought my Medion desktop, it was shipped with a USB remote control.

Is there a way I can use it in ubuntu? (maybe as a second keyboard?)

---

### Post by MrFahrenheit on 2005-11-29
I beleive lirc is the program you're looking for

---

### Post by daller on 2005-11-29
[QUOTE=MrFahrenheit]I beleive lirc is the program you're looking for[/QUOTE]

How do I configure LIRC?

This is the output from dmesg:

[4308440.355000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4308441.234000] ati_remote 1-1:1.0: Input registered: X10 Wireless Technology Inc USB Receiver on usb-0000:00:1d.0-1
[4308441.234000] usbcore: registered new driver ati_remote
[4308441.234000] drivers/usb/input/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[4308441.234000] drivers/usb/input/ati_remote.c: Weird data, len=1 ff ff fe 00 00 00 ...

---

### Post by daller on 2005-11-29
It seems that it's ati_remote that takes care of it (not LIRC, is it?)

How do I configure all the keys?

Some of the keys do not send any keycodes, and others sends the wrong ones!

---

### Post by daller on 2005-11-30
This is the remote control:

[http://dallerweb.dk/ubuntu/medion_remote.pdf](http://dallerweb.dk/ubuntu/medion_remote.pdf)

...I've written down all the keycodes from the remote control...

A lot is missing, and some of them are wrong (Vol+, should be Vol-, and vise versa)

---

### Post by apollyonis on 2005-11-30
You're using Dapper, so I couldn't tell you with any certainty. In the command console:

```
gedit ~/.lircrc/lircrc
```

And to get an idea of what buttons are mapped to which code (I.E. Home or Play), type in console:

```
sudo irw
```

That will show you what the buttons display. The following is an example from what might be in the lircrc file:

```
begin
prog = mythtv
button = TV
repeat = 3
config = F1
end
```

In it, the button pressed is TV and what it sends as a signal to the computer is F1. The program corresponds with what program uses that sequence. Hope that gets you on the right track, assuming lircrc is set up in Dapper. (Which I hope it is...it was a pain to get the remote working on 5.10!) :p

---

### Post by daller on 2005-11-30
[QUOTE=apollyonis]You're using Dapper, so I couldn't tell you with any certainty. In the command console:

```
gedit ~/.lircrc/lircrc
```

And to get an idea of what buttons are mapped to which code (I.E. Home or Play), type in console:

```
sudo irw
```

That will show you what the buttons display. The following is an example from what might be in the lircrc file:

```
begin
prog = mythtv
button = TV
repeat = 3
config = F1
end
```

In it, the button pressed is TV and what it sends as a signal to the computer is F1. The program corresponds with what program uses that sequence. Hope that gets you on the right track, assuming lircrc is set up in Dapper. (Which I hope it is...it was a pain to get the remote working on 5.10!) :p[/QUOTE]

To be able to debug better, I'm actually trying this on a Breezy machine!

As it is now, I'm NOT using LIRC!

I plugged in the USB-thing, and the remote works as described in the pdf-file (in my last post)

---

### Post by daller on 2005-11-30
If I would like to report this as a bug, what concerning package should I report it for?

I think some of the buttons should have different keycodes...

In my opinion:

"MUTE" should send 160 (normal mute keycode, isn't it?)
"OK" should send "ENTER" (108)
"<- DELETE" should send "Backspace"

Is there some sort of standard in Keycode assignment?

My keyboard uses 174 for volume down, and 176 for volume up - On this remote it is opposite!

---

### Post by metoo on 2005-12-05
I think, this kind of remote sucks.
I have a slightly different one Q-Sonic which is a X10 as well. You might run a kernel driver at the moment, which I could not use. I actually played around to change the kernel driver to support mine, it worked but it would not de-register on rmmod and I gave up and I'm now using the IR remote from a SkyStar2 and Lirc. That works very well.

Lirc is probably supporting your remote as well and you might be in the position to assign key-commands to the remote keys by your own with it.

However, you have to compile the Lirc kernel modules by your own as Lirc is not part of the kernel and the way the scripting/configuration from Lirc is set up (not maintained) it will not be part of the kernel in a long time. (my bet)
(For instance, I have to use the 'homebrew' selection for the skystar2. Cards which you can directly select are outdated cards with mpeg2 decoders.)

So you have to download the kernel source, copy the kernel config from /boot and compile the kernel (don't install it!). With the configured kernel source run the script which comes with the Lirc package or do some fakeroot module-assistant then move the kernel modules to /lib/modules/yourkernel at the right place.
(This machine here does not have the card in it, no direct directory, sorry.)
Yes setting up Lirc is a PITA but once done it works very well.

---

### Post by daller on 2005-12-06
Well, do you know how I report changes to the ati_remote people?

As you can see in the pdf, the remote works with about half of the buttons!

Wouldn't it be easy for the developers (of ati_remote) to complete support for this remote control?

---

### Post by metoo on 2005-12-06
I'm not sure if this is the right solution.

When I looked at it, there where already 3 PCI identifier in it. I could easily add another one (seemed to be from the same family X10).
The mouse part worked OK, but the rest not, I had the impression, that the timings were completely different. Not 5 repeats but 2 signals about 1 second after each other (that was for my remote).

The key mapping is hard coded into the module. It is not working for you, but probably for the other remotes. So this would blow up the module to add another key mapping table.

Go lirc. This way you are much more flexible. This is actually a userland thing.

With lirc the daemon just get's the signal from the remote and to each signal you define a key from the remote (like signal xy = remote key "Play").

In another config file you define for each key the action, can be for an application (even when running in the background) or the window which has focus. This can be as easy like remote 1 key to keyboard 1 key pressed or remote "Play" key = p on keyboard or whatever.
So there are 2 config files in /etc/lirc/

Check the lirc web site, whether your remote is already (or at all) supported. There are predefined mappings for many remotes already there.

---

