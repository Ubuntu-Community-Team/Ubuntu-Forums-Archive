---
title: "backlight will not turn on"
date: 2009-05-27
forum: Hardware
---

### Post by deludere_ipsum on 2009-05-27
Hi guys, 

I'm having a major issue with a HP Pavilion zv5000 running Jaunty. A couple of days ago I changed the settings in the power manager from hibernate when lid is closed to blank screen when lid is closed. The first time I actually closed the lid after this change, the screen blacked out and never lit up again, not even while booting. It was obviously just the backlight since all the pixels were there when lit by an outside source. For a while I was not sure that it was a software problem, although the chances of the of the lamp dying on me at the same time I changed the power management status was infinitesimal, but I was assured of this when I ran the following line:

```
sudo vbetool vbefp getbrightness 
```and it returned 0. The setbrightness option does work and returns a "Real mode code failed" error.

Both of the following lines do nothing, while changing the parametter to "off" for either one will blank the screen. I tried  them both in x and in console mode.

```
sudo vbetool dpms on 
sudo radeontool light on
```I've seen a lot of simmilar issues with other laptops and Ubuntu versions but never one where there was no way to turn the backlight back on. It does not light, nor did it light at any point after I closed the lid that first time around. It does not seem to be a hardware problem as the switch for the lid works just fine (it turns off the touchpad when pressed), the pixels are all displaying properly, and the coincidence would be just too big for a CCFL to fail right after the seetings were changed. Does anybody have any ideas?

Thanks!

---

