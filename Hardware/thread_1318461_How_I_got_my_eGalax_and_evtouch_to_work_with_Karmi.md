---
title: "How I got my eGalax and evtouch to work with Karmic"
date: 2009-11-07
forum: Hardware
---

### Post by Ari Hyttinen on 2009-11-07
I'm posting this story in the hope that it'll help somebody else to get things to work for them, or perhaps even fix things so that this would happen automatically. I hope I'm not forgetting any critical step as I didn't keep notes.

I did this with fresh install of Ubuntu 9.10 Karmic Koala and default packages (xserver-xorg-input-evtouch), I didn't download or compile any extra software. I've read that things might be different with earlier Ubuntus or other distros, but I don't know.

First, to get the touchscreen orientation right, I had to add to file:
      /usr/share/hal/fdi/policy/20thirdparty/50-eGalax.fdi
these two lines (after maxy line, if that matters):
```

  <merge key="input.x11_options.rotate" type="string">CCW</merge>
  <merge key="input.x11_options.swapy" type="string">true</merge>

```I got the "rotate" and "swapy" keywords from [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html). At this point, don't worry if mouse cursor not anywhere close to where you touch the screen, just see that it moves in correct directions.


Then to get evtouch use the correct resolution,, I had to create xorg.conf as freshly installed Karmic doesn't have one by default:
```

  X -configure
  <copy created file to /etc/X11/xorg.conf)

```and add this to Section "Monitor":
```

  Option       "PreferredMode" "1680x1050"

```and this to Section "Device":
```

  Option      "Monitor-LVDS1" "Monitor0"

```Without this, the default X resolution was 1024x768 (due to multiple video outputs), and even though Gnome changes resolution after login, evtouch doesn't seem to notice that. If you have different resolutions in login screen and in the desktop, then this is probably the cause. Replace substring "LVDS1" above with whatever is the correct output (see /var/log/Xorg.0.log to find out the name), and resolution with whatever is the correct resolution.

Then I rebooted and did System->Administration->Calibrate Touchscreen from Gnome. Then I took the minx, miny, maxx and maxy values from calibration file:
      /etc/evtouch/config
and modified the familiar .fdi file to use them instead of what was there before:
      /usr/share/hal/fdi/policy/20thirdparty/50-eGalax.fdi
And final reboot, and it worked, and was calibrated well enough for finger touching at least!\\:D/

I couldn't figure out how to make any evtouch related changes to take effect without reboot. I didn't try very hard though, since Karmic boots so fast and I had automatic Gnome login enabled.


Feedback, corrections, suggestions and improvements welcome!

---

### Post by jneves on 2009-12-08
I don't know about you, but I had to delete /etc/evtouch/config so the touchscreen would stay calibrated on every boot.

---

