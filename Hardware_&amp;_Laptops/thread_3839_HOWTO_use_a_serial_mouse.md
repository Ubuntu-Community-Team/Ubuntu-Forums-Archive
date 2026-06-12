---
title: "HOWTO use a serial mouse"
date: 2004-11-09
forum: Hardware &amp; Laptops
---

### Post by Tommy on 2004-11-09
The ubuntu Warty installer (i386) apparently doesn't check to see which port the mouse is attached to. If you are installing on a PC with a mouse attached to a serial port (rather than the mouse port), here's what you need to do...

The installation will complete, and you will be able to log in but your mouse will not move or respond to button clicks. You need to reconfigure your xserver to see the mouse.

1.) Press Control-Alt-F1 to get to Virtual Terminal 1 (your screen will turn black and you'll see a login prompt).

2.) Login using your username and password.

3.) Enter the following command at the prompt:

sudo dpkg-reconfigure xserver-xfree86

4.) Press Return to accept the existing settings UNTIL you get to the selection for the mouse port.

5.) Choose whichever port your mouse is connected to:
a) first serial port: /dev/ttys0
b) second serial port: /dev/ttys1

6) Press Return to accept all the rest of the settings -- though on one or two you may have to press Tab to highlight the OK prompt before Return will work.

7.) After you finish configuring the xserver, you will get back to the black screen.

8.) Switch back to your xserver by pressing Control-Alt-F7

9.) Kill the xserver by pressing Control-Alt-Backspace (This is NOT Control-Alt-Delete, which will make the machine shutdown.)

10.) When the xserver restarts, your mouse should work normally. If not, you may have chosen the wrong port. If necessary, press Control-Alt-F1 to go back to the virtual terminal and reconfigure the xserver again (following the steps above).

---

### Post by shinobi.cl on 2006-12-06
Thays how its done.

Please note that this is only recommended if you just have the "normal" ubuntu installation CD, and a serial mouse

1st) Create a file named .xinitrc (i used vi to do it) in your home directory, with the following text

```

xterm -geometry +300+300


```

2nd) startx


Additionally, it your video card is too old, you can try

startx -- -depth 8

Then you will have an X session, with a focused console in the middle of the screen. Just type [FONT="Courier New"]sudo ubiquity[/FONT] and start installing!

PS: If the xterm does not get focus, change the geometry paremeters on .xinitrc until is positioned UNDER the mouse cursor in the middle of your screen.

---

### Post by Tommy on 2006-12-06
Cool... thanks for the update. It's been a LONG time since I wrote that, and Ubuntu Warty 4.10 didn't use ubiquity....

So for your HOWTO you might want to specify which version of Ubuntu you're using, and start from the beginning ... in your directions apparently you booted from the CD then saw a text prompt because X didn't start. Is that right?

I haven't tried my old serial mouse in awhile, though I probably still have it. I used to like it because it had three buttons... but I prefer optical mice AND you can get decent optical mice with scroll wheels for very little money at discount places. (Less than $8US.)


I just downloaded the Ubuntu Edgy 6.10 alternative disk because the regular desktop disk won't even finish booting on that old machine (too little memory). If you're trying out old hardware you should have the Alternative as well as the Desktop CD available because the Alternative has different packages available that are useful when you can't use X (or don't want it).

---

### Post by HyperHacker on 2006-12-24
OK, so...

"Package 'xserver-xfree86' is not installed and no info is available."

](*,)

---

### Post by Tommy on 2006-12-24
> **HyperHacker said:**
> 
"Package 'xserver-xfree86' is not installed and no info is available."


Yes, these directions were written a long time ago, for Ubuntu Warty 4.10. (The version from October 2004.) Some parts have changed a lot since then! xfree86 is no longer the video software, for example -- it's been replaced by xorg.

SO when you get to step 3, try this:

```
sudo dpkg-reconfigure xserver-xorg
```


(Note -- the configuration for the xserver will ask some technical questions about your hardware and the software needed to run it. If you know the answer, great, choose what you think is right. If you don't know, let it try to configure itself, usually by pressing the Enter key to accept its best guess.)

Please follow up on this thread and let me know how it does for you.

---

### Post by HyperHacker on 2006-12-24
That does bring up the configuration, but it doesn't ask anything about serial mice. It only asked for protocol (something PS/2 or Explorer PS/2) and whether to emulate a 3-button mouse. Later when I selected my monitor size (Simple, 15", because I don't know what this old monitor is capable of) it crashed, but the error message scrolled off the screen before I could read it.

[edit] I tried editing /etc/X11/xorg.conf manually, changing the "Device" setting under "Configured Mouse". "/dev/ttyS0" and "/dev/ttyS1" did nothing. "/dev/ttys1" (lowercase) crashed the X server with a lot of junk on the screen and several errors including "Cannot open device /dev/ttys1".

Hah! I got me a mouse by doing [this](http://ubuntuforums.org/showthread.php?t=206467). Commented out all the InputDevice sections except Generic Keyboard and Configured Mouse, and some references to them near the end of the file, set "Protocol" to "Auto" and "Device" to "/dev/ttyS0", and it works. :)

---

### Post by Tommy on 2006-12-27
> **HyperHacker said:**
> Hah! I got me a mouse by doing [this](http://ubuntuforums.org/showthread.php?t=206467). Commented out all the InputDevice sections except Generic Keyboard and Configured Mouse, and some references to them near the end of the file, set "Protocol" to "Auto" and "Device" to "/dev/ttyS0", and it works. :)

What a relief! I took awhile to respond because I haven't yet FOUND the old serial mouse I was using back then.

Before reading your update I did notice the open bug regarding serial mice, as described in that forum thread.  Maybe you will want to subscribe to the bug and can comment on it as it progresses. When it gets fixed you can try again and confirm whether the fix worked with your hardware:

[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/9068](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/9068)

I will subscribe to the bug, too, and IF my serial mouse turns up I can try it again....

---

