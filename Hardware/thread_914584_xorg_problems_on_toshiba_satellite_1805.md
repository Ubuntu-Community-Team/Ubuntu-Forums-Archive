---
title: "xorg problems on toshiba satellite 1805"
date: 2008-09-08
forum: Hardware
---

### Post by adamdddave on 2008-09-08
Trying to load ubuntu 8.04 onto a Toshiba Satellite 1805, Pentium 3 Processor, unsure of the speed at this point, 256 MB Ram and 8 gig hard drive. Quickly realized that I should go for the low memory approach, after the screen went blank after the loading bar filled.

 I found a post for this,

[http://ubuntuforums.org/showthread.php?t=781098&highlight=toshiba+satellite+1805](http://ubuntuforums.org/showthread.php?t=781098&highlight=toshiba+satellite+1805),

and it said try xubuntu or something light, so I tried to follow 
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

 After following the instructions up through loading fluxbox, I tried

```
$ startfluxbox
```

and was promptly told that xserver was not running. I then started xserver and saw a flash of text, then a black screen that would do nothing. I restarted the system and tried to log it

```
$ script -a -q booby.log
```

but could not run startx while logging. I tried tee, but didn't get a log. 

At this point, I may just try to go for the xubuntu livecd, since I have 256 mb ram, but I'd love to figure out what's wrong with xorg. I also tried xvesa, and it did nothing.

---

### Post by prshah on 2008-09-09
> **adamdddave said:**
> Trying to load ubuntu 8.04 onto a Toshiba Satellite 1805, Pentium 3 Processor, unsure of the speed at this point, 256 MB Ram and 8 gig hard drive. Quickly realized that I should go for the low memory approach, after the screen went blank after the loading bar filled.

At this point, I may just try to go for the xubuntu livecd, since I have 256 mb ram, but I'd love to figure out what's wrong with xorg. I also tried xvesa, and it did nothing.

The log for the Xorg will be /var/log/Xorg.0.log

As you've said, use the command ```
startx
``` from the prompt to start X. (Duh!)

If it returns to the prompt with an error message, post the error message (Most likely "Screens not found")

If you get a blank screen (after some flickering), most likely X is not detecting the screen/graphics card combo correctly. In this case, the Xorg.0.log file will give clues.

---

### Post by adamdddave on 2008-09-09
> If you get a blank screen (after some flickering), most likely X is not detecting the screen/graphics card combo correctly. In this case, the Xorg.0.log file will give clues.

tried looking at the Xorg.0.log file, but there wasn't anything wrong with it; no errors shown, nothing out of the ordinary it seems, though it said that it wouldn't load cryllic.

I'm going to try to reconfigure xorg, see if that makes a difference.

---

### Post by adamdddave on 2008-09-10
Problem solved via [http://ubuntuforums.org/showthread.php?t=587668&highlight=video+card+toshiba+satellite+1805](http://ubuntuforums.org/showthread.php?t=587668&highlight=video+card+toshiba+satellite+1805)

---

