---
title: "[SOLVED] Make &amp;quot;xinput set-button-map&amp;quot; permanent?"
date: 2008-11-25
forum: Hardware
---

### Post by terryeden on 2008-11-25
Afternoon,

My [Evoluent Mouse]("http://www.evoluent.com/vm3.html") works fine - but I need to remap the buttons to get the best use of it.

I use 
```
xinput set-button-map "Kingsis Peripherals  Evoluent VerticalMouse 3" 0 2 4 3 5 6 7 8 1
```
to map the buttons to my preference.

However, when I reboot, the mapping disappears. Is there any way to make xinput run during boot?

Running 8.10 on a Dell Latitude D430.

Thanks

T

---

### Post by S_A_M on 2008-11-27
I'd like to know too. I think I've seen some references to putting it in a login script (like one of the rc scripts in /etc/), but I'm not sure that would do too well for me since I also lose my button map when the computer wakes up from sleep.

---

### Post by terryeden on 2008-11-27
I used the method described at [http://the-moni-blog.blogspot.com/2008/10/ubuntu-on-acer-tm-c300.html](http://the-moni-blog.blogspot.com/2008/10/ubuntu-on-acer-tm-c300.html)

Basically, go to System - Preferences - Sessions.

On the "Startup Programs" tab, click "Add".

In the "Command" field type / paste
```
/usr/X11R6/bin/xinput set-button-map "Kingsis Peripherals  Evoluent VerticalMouse 3" 0 2 3 4 5 6 7 8 1
```
(Or whatever your preferences are).

Give it a Name and a Comment so you remember what you have done, then hit "Save".

The next time you reboot or log in - your mouse will know your preferences!

Hurrah!

---

### Post by emergent on 2009-04-18
If you're running fluxbox, follow the above instructions and enter in your ~/.fluxbox/startup file.

---

### Post by nitindb on 2009-06-09
Although the above solution provided by terryeden works, I found another way of doing it without having to add to you're startup programs and is probably the 'correct' way of doing it. I have an Evoluent Vertical Mouse (version 2) and in Jaunty (9.04) I got it to work with the following fdi file contents which is placed in /etc/hal/fdi/policy/:-

> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.product" string="Kingsis Peripherals Evoluent VerticalMouse 2">
<merge key="input.x11_driver" type="string">evdev</merge>      
<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 9 8</merge>
<merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
    </match>
  </device>
</deviceinfo>

I named the above file as evoluent2-x11-mouse.fdi.

This method is a direct replacement for the old input parameters one previously entered in the xorg.conf file. A more detailed explanation can be found here:- [http://volatileint.blogspot.com/2009/03/creating-fdi-policy-files-for-hal.html](http://volatileint.blogspot.com/2009/03/creating-fdi-policy-files-for-hal.html)

---

### Post by commonplace on 2009-11-02
Sorry to necro this thread, but I thought it'd be better than starting a whole new one.

Can anyone tell me how to do this in KDE 4.x? I'm trying to add "xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 8 0 0 0 0 0 0 0" to my startup so I don't have to run it manually each time I login (this is to disable the touchpad tap-to-click option).

/Kevin

---

### Post by terryeden on 2011-01-07
It seems that the update to 10.10 has fundamentally broken this. See [http://daniel.hahler.de/hal-configuration-for-kingsis-peripherals-evoluent-verticalmouse-3](http://daniel.hahler.de/hal-configuration-for-kingsis-peripherals-evoluent-verticalmouse-3)

Additionally, xinput seems to have a but preventing it from recognising the device name.  As the id changes every time you re-plug your USB mouse, this is very annoying.

This is a quick fix for it.

This command will look for the ID of your mouse, then map the buttons to your choosing.

```
xinput set-button-map `xinput list | grep 'Kingsis Peripherals  Evoluent VerticalMouse 3' | grep -o [0-9][0-9]` 0 2 3 4 5 6 7 8 1 10 11 12 13
```

---

### Post by RedgeOnline on 2012-04-28
> **terryeden said:**
> It seems that the update to 10.10 has fundamentally broken this. See [http://daniel.hahler.de/hal-configuration-for-kingsis-peripherals-evoluent-verticalmouse-3](http://daniel.hahler.de/hal-configuration-for-kingsis-peripherals-evoluent-verticalmouse-3)

Additionally, xinput seems to have a but preventing it from recognising the device name.  As the id changes every time you re-plug your USB mouse, this is very annoying.

This is a quick fix for it.

This command will look for the ID of your mouse, then map the buttons to your choosing.

```
xinput set-button-map `xinput list | grep 'Kingsis Peripherals  Evoluent VerticalMouse 3' | grep -o [0-9][0-9]` 0 2 3 4 5 6 7 8 1 10 11 12 13
```

Thanks, this worked great. Just one problem for me: my mouse was listed twice in xinput list, so I had to slightly modify your code.

```
for id in `/usr/bin/xinput list | /bin/grep 'Logitech USB Receiver' | /bin/grep -o [0-9][0-9]`; do xinput set-button-map $id 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 17 16; done;
```

---

