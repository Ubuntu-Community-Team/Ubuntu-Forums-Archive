---
title: "X11 middle click emulation not working"
date: 2009-11-23
forum: Hardware
---

### Post by A.S. on 2009-11-23
Hello,

I have currently installed the new release 9.10 of Kubuntu and most things are working, some things just out of the box and others after changing some settings.

The only thing which I could not get to work is the emulation of the middle button click by clicking the left and the right button of the DualPoint Stick buttons on a Dell D830 notebook.

With the buttons of the touchpad this emulation ist just working.

The ouput of hal-device is:
```

  ...
  input.x11_options.Emulate3Buttons = 'true'  (string)
  input.x11_options.EmulateWheel = 'true'  (string)
  ...
  input.x11_options.EmulateWheelTimeOut = '200'  (string)
  ...
  input.x11_driver = 'evdev'  (string)
  input.x11_options.EmulateWheelButton = '3'  (string)
  ...
  input.x11_options.XAxisMapping = '6 7'  (string)
  input.x11_options.YAxisMapping = '4 5'  (string)
  ...

```

Does anybody know what I could try to get this working?


Greetings

---

### Post by A.S. on 2009-11-29
Hello,

if I set the scrollbutton to the middle button - instead to the right button - the middle button click (paste) is working, but then scrolling is not working anymore.

Have anybody an idea what to try?

Greetings

---

### Post by opt1k on 2009-11-29
I dont mean to be rude but did you set 
Option "Emulate3Buttons"
under the input device section for your mouse in /etc/X11/xorg.conf
> **A.S. said:**
> Hello,

if I set the scrollbutton to the middle button - instead to the right button - the middle button click (paste) is working, but then scrolling is not working anymore.

Have anybody an idea what to try?

Greetings

---

### Post by A.S. on 2009-11-29
Hello,

there are no input devices configured in the xorg.conf. I think they are all configured with hal since Ubuntu 9.04.

I have set the Option "Emulate3Buttons" with the entry

```

<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>

```

in my fdi file.


Greetings

---

### Post by opt1k on 2009-11-30
> **A.S. said:**
> Hello,

there are no input devices configured in the xorg.conf. I think they are all configured with hal since Ubuntu 9.04.

I have set the Option "Emulate3Buttons" with the entry

```

<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>

```

in my fdi file.


Greetings

I found this thread that might help... im not familiar with that method of configuring xorg. 

[http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)

---

### Post by A.S. on 2009-12-02
Hello,

I think this thread does not help me with my problem. The configuration through hal with the fdi file looks ok. I could see the settings with xinput.

Thank you for your replay.


So, the problem still exists.

Has anybody an idea?

---

### Post by A.S. on 2010-05-10
Hello,

I have now installed Kubuntu 10.04 and have configured the touchpad in /usr/lib/X11/xorg.conf.d/20-trackpoint.conf like it is described in the wiki on ubuntuusers.de.

But the old problem still exists. Either middle button click is working or scrolling. Both together is not working.

Has anybody found a solution?

---

