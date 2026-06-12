---
title: "Using ir-keytable with MCE Remote and XBMC"
date: 2012-03-09
forum: Hardware
---

### Post by Dapennsta on 2012-03-09
Hey guys, I'm having some trouble setting up my Microsoft MCE remote keyboard media keys. Using RC-6 I can use the regular keyboard part as well as the mouse but I have to disable lirc in order for it to work. The problem here is I was using lirc for the media keys (play, pause, etc) but I cannot have lirc and RC6 running at the same time. Is there a way to customize ir-keytable so my media keys work with XBMC? I do know how to find the key codes for the media keys.

Any help would be much appreciated.

---

### Post by wyliecoyoteuk on 2012-03-09
You just need to edit the keymap in /lib/udev/rc-keymaps.
I did this for MythTV.
Use ir-keytable to get the codes, and enter them into the relevant keymap, with the corresponding commands.

[http://manpages.ubuntu.com/manpages/natty/man1/ir-keytable.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ir-keytable.1.html)
good luck :D

---

### Post by wyliecoyoteuk on 2012-03-09
This table may help:

[http://linuxtv.org/wiki/index.php/Remote_Controllers](http://linuxtv.org/wiki/index.php/Remote_Controllers)

---

### Post by Dapennsta on 2012-03-11
Awesome thanks a lot I got it to work pretty much the exact same way it was set up with lirc I just have another other small problem..

I'm having trouble tuning the delay and the period, I've tried numerous different combinations but I still find its repeating too many key presses.

Other then that, it is working perfectly. thanks again

---

### Post by wyliecoyoteuk on 2012-03-12
Good news :)
Please mark the thread [solved]
I have found that you need a reboot for some changes to take effect, not sure why. My Hauppuage remote does sometimes repeats if I linger a little on the keys, not really had time to fiddle.

---

### Post by Kissell on 2012-04-26
Hey guys.  I have ir-keytable working just fine.  Test shows it recognizes my button presses.  But XBMC doesn't recognize them.  I don't have lirc installed, so how to I tell XBMC what to use in the Lircmap.xml file?

```

ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1335478080.881956: event MSC: scancode = 77e15094
1335478080.881966: event key down: KEY_UP (0x0067)
1335478080.881969: event sync
1335478081.131382: event key up: KEY_UP (0x0067)
1335478081.131385: event sync
1335478082.083906: event MSC: scancode = 77e13094
1335478082.083916: event key down: KEY_DOWN (0x006c)
1335478082.083919: event sync
1335478082.333435: event key up: KEY_DOWN (0x006c)
1335478082.333438: event sync
1335478082.818888: event MSC: scancode = 77e19094
1335478082.818898: event key down: KEY_LEFT (0x0069)
1335478082.818901: event sync
1335478083.068421: event key up: KEY_LEFT (0x0069)
1335478083.068423: event sync
1335478083.338860: event MSC: scancode = 77e16094
1335478083.338870: event key down: KEY_RIGHT (0x006a)
1335478083.338873: event sync
1335478083.588423: event key up: KEY_RIGHT (0x006a)
1335478083.588425: event sync


```

---

### Post by wyliecoyoteuk on 2012-04-27
Not tried with XBMC, but the thing with the ir-keytable is that it mimics keyboard keys.
so if you map the buttons to the same keyboard keys that XBMC uses, it should all work ok, without Lirc.
For example, MythTV uses P for pause, so I mapped my pause button to KEY_P.

What keymap is it using?

---

### Post by Kissell on 2012-04-28
This is the keys are loaded via the /etc/rc.local file.
```
cat /etc/rc_keymaps/rc6_mce
# table rc6_mce, type: NEC
0x77e15094 KEY_UP
0x77e13094 KEY_DOWN
0x77e19094 KEY_LEFT
0x77e16094 KEY_RIGHT
0x77e1a094 KEY_PLAY
0x77e1c094 KEY_MENU

```

I know it's loaded because the -t parameter works for the tests, and the -r parameter shows the right button mapping.
```
ir-keytable -r
scancode 0x77e13094 = KEY_DOWN (0x6c)
scancode 0x77e15094 = KEY_UP (0x67)
scancode 0x77e16094 = KEY_RIGHT (0x6a)
scancode 0x77e19094 = KEY_LEFT (0x69)
scancode 0x77e1a094 = KEY_PLAY (0xcf)
scancode 0x77e1c094 = KEY_MENU (0x8b)
Enabled protocols: NEC 

```

In the test, if I press the left button it says KEY_LEFT, but inside XBMC if I press the left button, nothing happens.

---

### Post by Kissell on 2012-04-28
I changed KEY_PLAY to KEY_P and then started XBMC...  when I press P on the keyboard it will pause video...  but not when I press the key on the remote that is mapped as KEY_P using ir-keytable.

---

### Post by wyliecoyoteuk on 2012-04-29
You need to reload the keymap before it works, I found a reboot necessary.
My keymaps are in /lib/udev/rc_keymaps, not in /etc

---

### Post by Kissell on 2012-04-29
It is loaded on startup via the /etc/rc.local file.  They can be in any path because the /etc/rc.local file points to them in their path.  Or they can be put in the location where yours are...  either way they get loaded.  I've tried both.  

They are loaded.  No question about that.  Because "ir-keytable -t" works.  And it doesn't work if I remove the files and reboot.  

It just doesn't work inside the XBMC program.

---

### Post by wyliecoyoteuk on 2012-04-29
Sorry, but I don't use XBMC, I use MythTV, and it works in that.
Dapennsta managed to get it working with XBMC though...

If you press the button you mapped to P with the terminal open, do you get a P on screen?

---

### Post by Kissell on 2012-04-29
It says "KEY_P" when I do the test, but does not type P at the command prompt when I'm not doing the test.

```
ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1335720390.557246: event MSC: scancode = 77e1a094
1335720390.557255: event key down: KEY_P (0x0019)
1335720390.557259: event sync
1335720390.563231: event MSC: scancode = 77e1a094
1335720390.563234: event sync
1335720390.665227: event MSC: scancode = 77e1a094
1335720390.665229: event sync
1335720390.915005: event key up: KEY_P (0x0019)
1335720390.915008: event sync

```

---

### Post by wyliecoyoteuk on 2012-04-29
Just checked mine, and it types p in a terminal.
So it would seem that something is amiss.
Maybe the kernel module is not loading?

Try lsmod | grep mce

---

### Post by Kissell on 2012-04-29
lsmod looks good...  I must have really screwed something up when I was trying to get Lirc working...  

good news is I finally got Lirc to work...  so I guess I'll just use it instead of ir-keytable.  

Thanks for trying to help me figure this out.

---

