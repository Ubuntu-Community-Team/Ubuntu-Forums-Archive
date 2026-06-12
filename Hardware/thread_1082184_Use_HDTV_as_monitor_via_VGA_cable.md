---
title: "Use HDTV as monitor via VGA cable"
date: 2009-02-27
forum: Hardware
---

### Post by rwpage on 2009-02-27
I bought my laptop (Gateway P-6860FX) at the beginning of this school year, and I realized recently that I haven't utilized nearly half of the hardware capabilities of it. I have an HDTV that has a VGA port (not sure what to call it, but I'm sure you know what I mean) and so does my laptop. I do have a VGA cable, so I don't think this is rocket science.

I'm just not sure what to do on the Linux side to get it connected and working *PROPERLY.* I already tried fiddling around with the nvidia-settings tool and I messed up settings that resulted in me rebuilding my OS. If anyone could help me out on what to do, I'd appreciate it!

-- If you need to know, I was wondering how to hook up the HDTV as a "monitor" so that I could watch movies on it (and I already have the sound figured out).

---

### Post by nixscripter on 2009-02-27
The simplest thing to try is to hookup the VGA cable, and then try running in a Terminal: ```
xrandr --auto
```

It might not be pretty, but it should make sure everything is detected. If that works, then you can look at the Screen and Graphics control panel to configure it. It's under **Ubuntu Menu -> System -> Administration -> Screen and Graphics**

Hope this helps.

---

### Post by nickdbliss on 2009-02-27
Mine worked out of the box with my LCD HDTV. Lucky me here i guess.lol

---

### Post by Maheriano on 2009-02-27
If your HDTV only takes VGA in then it's not true high definition unfortunately. There should be a DVI or HDMI input for video and this is what you would want to put into it for digital video. However it seems like the only output you have on your computer is VGA so it will work and should work natively without any configuration but it won't look as good as it should.

---

### Post by rwpage on 2009-03-01
> **nixscripter said:**
> The simplest thing to try is to hookup the VGA cable, and then try running in a Terminal: ```
xrandr --auto
```

It might not be pretty, but it should make sure everything is detected. If that works, then you can look at the Screen and Graphics control panel to configure it. It's under **Ubuntu Menu -> System -> Administration -> Screen and Graphics**

Hope this helps.

Thanks, will try this. Only thing is that right now I looked and I don't see a "Screen and Graphics" item in the Admin menu.. is there a command I could run in the terminal to bring up the GUI?

And my HDTV has a HDMI-DVI port but I don't have a DVI port on my laptop unfortunately. I was hoping my HDTV was HDMI-HDMI but it isn't, so I'm stuck with VGA cables -_-

---

### Post by nixscripter on 2009-03-01
The Terminal equivalent of screen and graphics is displayconfig-gtk (assuming you're using GNOME). You'll need root priviledge though, so run: ```
sudo displayconfig-gtk
```

---

### Post by rwpage on 2009-03-01
> **nixscripter said:**
> The Terminal equivalent of screen and graphics is displayconfig-gtk (assuming you're using GNOME). You'll need root priviledge though, so run: ```
sudo displayconfig-gtk
```

Hmmm... I don't seem to have that command. If it helps you at all I'm using Ubuntu 8.10. If you have anymore advice, I'd appreciate it. I know I'm being a bit of a pain.

...Is there maybe a package I have to install?

---

### Post by nixscripter on 2009-03-02
I thought it was standard, but maybe it's beacuse I've got a Dell laptop preinstalled.

Did the **xrandr** command work?

---

