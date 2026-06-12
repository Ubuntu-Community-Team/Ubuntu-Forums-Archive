---
title: "Monitor calibration in Ubuntu?"
date: 2014-10-31
forum: Hardware
---

### Post by solars on 2014-10-31
Hi there,

I've got an Eizo CG 277 which is calibrated under windows (my main photo machine).
Since I've successfully connected my Ubuntu Laptop over HDMI, I'd also like to configure Ubuntu right.

Can anyone tell me how to do this? I assume I can somehow export the profile in windows (through color manager)
and use it under ubuntu? I couldn't find many good tutorials for wide gamut monitor calibration..

Thanks a lot,
Christoph

---

### Post by solars on 2014-11-06
does anyone know how to do this please?

---

### Post by coffeecat on 2014-11-06
I really have no experience of this - I'm posting mainly to let you know that it's fine to bump your post after about 24 hours if you don't get a response. Or say 18 hours or 30 hours to get to other time zones. Threads drop down steadily and you don't need to wait 5 days if you don't get a response.

But to get some momentum going, I found these on askubuntu:

[http://askubuntu.com/questions/424732/how-do-i-calibrate-colors-without-extra-hardware-like-dccw-exe-on-windows](http://askubuntu.com/questions/424732/how-do-i-calibrate-colors-without-extra-hardware-like-dccw-exe-on-windows)

[http://askubuntu.com/questions/9443/how-to-calibrate-the-monitor-on-an-ubuntu-system](http://askubuntu.com/questions/9443/how-to-calibrate-the-monitor-on-an-ubuntu-system)

They both mention gnome-color-manager. I've tried installing this and by selecting my monitor I could select a number of profiles, or select "other profile" to import from a file. Perhaps that might work with the profile generated in Windows. The package name is gnome-color-manager and it appears as "Device Color Profiles" in the Unity dash.

Good luck.

---

### Post by BlinkinCat on 2014-11-06
I was wondering if the name of the Monitor could be included in the title, perhaps to attract more attention.

---

### Post by coffeecat on 2014-11-06
The OP's question is about calibrating monitors in Ubuntu, not necessarily specific to their particular brand and model. Let's leave it be, shall we, otherwise we may put off people who have something to contribute, but who use Samsung, HP, Dell, etc, monitors, even though those may not come up to the standard of the professional quality monitor the OP uses.

---

### Post by tgalati4 on 2014-11-06
There are tutorials for how to generate an *.ICC color calibration file in Windows and place them in the correct place in Ubuntu.  They should get loaded automatically.  The color tools in linux are weak, but if you can generate a decent calibration file in Windows or Mac (where the tools are much better), then you can use those same calibration files.

"I don't want a long, boring, theoretical explanation.  I just want the answer."  Sorry, some theory presented below.

[http://ubuntuforums.org/showthread.php?t=2230531&highlight=color+calibration](http://ubuntuforums.org/showthread.php?t=2230531&highlight=color+calibration)

[http://ubuntuforums.org/showthread.php?t=2216371&highlight=color+calibration](http://ubuntuforums.org/showthread.php?t=2216371&highlight=color+calibration)

[http://ubuntuforums.org/showthread.php?t=2208544&highlight=color+calibration](http://ubuntuforums.org/showthread.php?t=2208544&highlight=color+calibration)

[http://ubuntuforums.org/showthread.php?t=2193766&highlight=color+calibration](http://ubuntuforums.org/showthread.php?t=2193766&highlight=color+calibration)

[http://ubuntuforums.org/showthread.php?t=2102686&highlight=color+calibration](http://ubuntuforums.org/showthread.php?t=2102686&highlight=color+calibration)

There's a color management Haiku in there somewhere.

---

