---
title: "Fujitsu Esprimo 6536 Fn keys"
date: 2009-05-01
forum: Hardware
---

### Post by sijp on 2009-05-01
Hi,

I just purchased a Fujitsu Siemense Esprimo 6535 Laptop. Almost everything works great. I have a problem with a few function keys.

**Setting up Brightness:**
The keys are being captured but are mapped incorrectly.
pressing the 'Brightness Down' key (Fn+F8 ) initiates Brightness Up and the 'Brightness Up' key (Fn+F9) simply types this character: ±.

the output of xev is:
```
$ xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
keycode 233 = (keysym 0x1008ff02, XF86MonBrightnessUp), state = 0x0
keycode 233 = (keysym 0x1008ff02, XF86MonBrightnessUp), state = 0x0
keycode 126 = (keysym 0xb1, plusminus), state = 0x0
keycode 126 = (keysym 0xb1, plusminus), state = 0x0
```


where/how can I edit the keycodes' actions?

**Shutting Down WiFi and Bluetooth:**
I've read it's not possible yet, but I was just wondering maybe I'm wrong.
the key does not produce any keycode, and according to google, it should be captured by ACPI. the key is Fn+F1

Thanks,
Shlomi

---

### Post by Barry Carroll on 2009-05-01
Hi Shlomi,

What you are looking for is a mapping in a hal config file that maps the keycodes to events.  The one you'll be looking for is something like ```
/usr/share/hal/fdi/information/10freedesktop/30-keymap-misc.fdi
```  That may be wrong as I'm recalling that from memory but in there you'll see how hal maps the codes to actions and I remember seeing some entry similar to your laptop in there.

You can file a bug on launchpad and somebody might make a fix for it or you can try DIY and perhaps submit a patch if you're successful.  Some good references are:

[https://wiki.ubuntu.com/Hotkeys/Architecture](https://wiki.ubuntu.com/Hotkeys/Architecture)  (look at the section for mapping codes)

[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

edit: also try looking for any recent blogs about linux on your laptop as I think HAL is common across a lot of distributions now.  You might need to use the **dmidecode** command in the terminal to print out your machine name as seen by linux so you can use that in the hal config file.

---

### Post by sijp on 2009-05-01
Thanks Barry,
I've managed to make the Brightness Down to lower the brightness by editing that file, but I can't figure out how to set the brightness up key.
the value is 126 so the Hex value is 0x7E. according to the first link, I should use this key code as is so I set it this way:

```
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.produc
t" contains="ESPRIMO Mobile">
          <append key="input.keymap.data" type="strlist">e06f:brightnessdown</ap
pend>
          <append key="input.keymap.data" type="strlist">7e:brightnessup</append>
        </match>
```

when pressing Fn+F9 which is 'Brightness Up' I still get the plusminus sign "±". My guess is something is capturing the keypress before hal. what should I do?

---

### Post by Barry Carroll on 2009-05-01
Just to check, did you restart hal or your system after making the change in the text file?  You can restart hal by doing ```
sudo /etc/init.d hal restart
```

I also saw this bug and thought that it might be related: [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/351533](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/351533)

---

### Post by sijp on 2009-05-02
Yes, I did restart it. That's when the Brightness Down key started to work properly.

I also noticed that bug before posting. The thing is my laptop's key codes are apparently different than those that are referred to in the bug report.

---

### Post by sijp on 2009-05-02
OK I got it!
Apparently Xev gave me the wrong keykode when pressing 'Brightness Up'. I tried using input-events instead which showed a different key code:
```
$ sudo input-events 4
/dev/input/event4
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

waiting for events
09:25:55.757918: EV_MSC code=4 value=239
09:25:55.757940: EV_KEY KEY_BRIGHTNESSDOWN (0xe0) pressed
09:25:55.757945: EV_SYN code=0 value=0
09:25:55.770556: EV_MSC code=4 value=239
09:25:55.770576: EV_KEY KEY_BRIGHTNESSDOWN (0xe0) released
09:25:55.770580: EV_SYN code=0 value=0
09:25:57.136509: EV_MSC code=4 value=206
09:25:57.136529: EV_KEY KEY_KPPLUSMINUS (0x76) pressed
09:25:57.136534: EV_SYN code=0 value=0
±09:25:57.147635: EV_MSC code=4 value=206
09:25:57.147656: EV_KEY KEY_KPPLUSMINUS (0x76) released
09:25:57.147660: EV_SYN code=0 value=0
```

I calculated hal's hex keycode using hex(VALUE-128+0xE0000) and changed it in 30-keymap-misc.fdi so now it looks like this:

```
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="ESPRIMO Mobile">
          <append key="input.keymap.data" type="strlist">e06f:brightnessdown</append>
          <append key="input.keymap.data" type="strlist">e04e:brightnessup</append>
        </match>
```

now it works perfectly. I'm going to post a bug for it now :-).

Thank you so much Barry!

---

### Post by metallus on 2009-08-24
@sijp: it worked just great for me on esprimo mobile v6545. but I have another unrelated problem. My onboard sd/mmc card reader seems to malfunction, also the wireless switch does not work. any thoughts on that?advices? thanks!

---

### Post by metallus on 2010-01-07
> **metallus said:**
> @sijp: it worked just great for me on esprimo mobile v6545. but I have another unrelated problem. My onboard sd/mmc card reader seems to malfunction, also the wireless switch does not work. any thoughts on that?advices? thanks!

It seems that ubuntu 9.10 works out of the box. Still having problems with the wlan switch (it does nothing). Other than that, all works just fine (including my sd/mmc card reader).

---

