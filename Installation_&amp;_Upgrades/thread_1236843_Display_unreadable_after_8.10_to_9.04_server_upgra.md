---
title: "Display unreadable after 8.10 to 9.04 server upgrade on Dell Dimensions 5150"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by due23 on 2009-08-10
I had 8.04 server working as LAMP server, using MySQL database, dual booting with Windows XP. Two connected monitors would only work in clone mode. Resolution was 1280x1024. I tried to install and use a new version of ATI drivers to get dual screens working. This resulted in the displays going back to 800x600, with the system telling me there was a problem with the displays at boot up. I left the system in this state for several months and used it for Win XP only. Then I needed a LAMP server again.
 
I updated 8.04 to all the latest versions, no change to displays.
I updated to 8.10. Displays went back to 1280x1024, all looked god.
Then in a moment of madness I upgraded to 9.04. Now I am in trouble!
 
The ATI card has two outputs, DVI and ordinary VGA, with a 17" monitor on each.
After 9.04 has booted up, the DVI display is not driven at all, and VGA display show blocks of colour.
 
Tried to go into recovery, used the 'fix graphics problems' option, rebooted, same thing.
Tried to go into shell prompt, but the system doesn't like my password input. I am assuming it won't have chnaged since 8.04.
The only thing I have noticed as the system reboots after trying to fix the graphics problems is that an entry on the left, as the boot is scrolling up the page, called fglrx has [FAIL] in red on the right side of the screen. This sounds like the non-open source driver frm ATI.
 
I am now stuck. As you might gather from the above I am not very experienced with UNIX, having installed my LAMP server from the info on the Ubuntu site.
Incidentally, I also updated the system from 512MB to 8GB prior to all this, and found that 8.04 would not load (gave kernel panic) until I reduced the memory to 4GB.
 
Hardware:
Dell Dimensions 5150, Pentium D 2.8GH, memory 4GB, video adapter ATI Radeon x300 SE 128MB

---

### Post by zkriesse on 2009-08-10
Try downloading an Ubuntu 9.04 Desktop version from here. [http://www.ubuntu.com/](http://www.ubuntu.com/) Burn the ISO image to a DVD, stick it in the system and try the repair damaged system option.

---

### Post by due23 on 2009-08-10
Thanks for the quick response.
I will give your idea a try in the morning (midnight here now).
All the best

---

