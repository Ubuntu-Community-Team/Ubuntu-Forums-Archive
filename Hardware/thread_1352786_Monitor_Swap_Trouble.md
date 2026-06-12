---
title: "Monitor Swap Trouble"
date: 2009-12-12
forum: Hardware
---

### Post by Celli on 2009-12-12
I've been using Hardy Heron for a few months on a third-hand Compaq Presario S3200NX with the original monitor with few problems.  I was recently given a new-to-me flatscreen (Gateway 900W, mfg June 2006) for use instead and attempted to install it with no luck.

Here's what I've managed to see on the monitor:
Monitor on, computer off: black screen, orange power button
Both on: (1) power button turns blue, (2) initial startup screen & blue power button, (3) black screen & blue power button, (4) menu countdown & blue power button, (5) black screen & blue power button, (6) ubuntu loading screen & blue power button, (7) black screen & blue power button.

It'll stay that way for some time.  If I press my delete key the CPU beeps & I can hear the CPU working throughout but no view onscreen.  The power button stays blue.  Eventually I get sick of this and turn the CPU off.  Some text flashes onscreen and off again before I can read it, and the power button turns orange.

I got sick of this after several tries spanning two hours or so, and plugged the original monitor back in.  The colors are different....  the formerly solid orange task bars are now green on the left and verging on red on the right, but it seems a sick monitor is better than one that won't work at all.

What can I do to install my new monitor and/or make my old one go back to normal?

---

### Post by PRC09 on 2009-12-12
I dont have 8.04 on a machine right now but there was a tool in synaptic called displayconfig-gtk that you could use to change monitors and resolutions and such.Dont know if it will help as I havent used it.It was/is supposed to be buggy and has been removed from 8.10 onwards but it might help....

---

### Post by Celli on 2009-12-12
I'll have to check that out.  I left the computer off all night and now the screen's back to normal.  Thanks!

---

### Post by Celli on 2009-12-12
Took a look in synaptic, displayconfig-gtk was already installed.  I reinstalled it, then turned everything off and plugged the new monitor in again.  Same thing.

This time, at least, my old monitor is normal when I switched back.

---

### Post by PRC09 on 2009-12-12
There is a tutorial on how to use it at the following link just in case you need it...

[http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/)

---

### Post by Celli on 2009-12-12
So I'd run the program to configure the new monitor before I plug it in?

---

### Post by PRC09 on 2009-12-13
Sorry for no reply sooner,last minute shopping...I should have asked if you had tried booting into recovery mode and arrow down to the Try to repair graphics problems.Sometimes that will help.As for how or when to run the tool I havent run it so I am sorry I dont know........

---

### Post by Celli on 2009-12-15
ok, I think I'll try to get one of my friends who is more well acquainted with Ubuntu to help.  Thanks!

---

