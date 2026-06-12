---
title: "X Server not starting on Edgy LiveCD - Intel 945"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by JohnPhys on 2007-01-20
Hey all,

I was trying to install Ubuntu on my buddy's new Gateway MP8708 (I think that's the model number, it's the only 17" widescreen gateway at bestbuy.com atm anyway...) and both the edgy and dapper livecd's can't seem to start the x server. 

The laptop has the intel 945 or 950 graphics (not sure which is the graphics, but it has that integrated chipset) with a Core 2 Duo T7200 processor.

It seems that the xserver detects the correct driver ( "i815" is the driver listed in xorg.conf) and for the screen it defaults to 16 bit color, as well as having the only resolution it detects be the native 1440x900 resolution of the attached screen.

In the xorg log file (and the gdm log file), it reports an error about not finding any suitable modes for the screen, as well as no attached screen?

I'm not very command line savvy, or I'd have more info.  I can try again sometime soon and write down selected results of lspci and xorg.conf if people would think it's useful.

I don't *think* the livecd's are damaged, as I'm typing this on another laptop with the same edgy livecd, though this particular laptop used a different chipset, has ati graphics, and isn't widescreen.

We would be extremely grateful for any help you could give.  Thanks in advance!

---

### Post by MarkRobert on 2007-01-20
I have a dell inspiron 6400 with the same chipset, slightly smaller screen. Did the graphical installer start ok? Or did it fail after making changes?

---

### Post by JohnPhys on 2007-01-21
Argh, it was a newb mistake.

I tried starting the graphical installer by doing 

```
sudo /etc/init.d/gdm restart
```

after I reconfigured the xserver.  However, I didn't realize that there was a /usr/sbin/gdm running, so that's why it never started.

Once I killed that process, all worked fine.

Thanks for the reply though!

---

