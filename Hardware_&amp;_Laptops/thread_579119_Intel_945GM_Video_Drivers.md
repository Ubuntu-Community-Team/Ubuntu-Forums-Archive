---
title: "Intel 945GM Video Drivers"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by AgentGambell on 2007-10-18
Hey guys, I've installed 7.10, and I'm having some issues with the video. Right after I get it installed, video looks great, everythings working, then I decide I want to install Beryl. I run through a tutorial I found on it, reboot, and now the windows look like they wanna do the wave thing, but drag real bad. I don't think it's a weakness of the grapics card, as text scrolls the same way. It looks like Windows does when you don't have any drivers for your video card. I ran glxinfo | grep 'direct'     and came up with No (If you want to find out why, try setting LIBGL_DEBUG=verbose, but I'm not quite sure how to trouble shoot all this. Thanks for any help.

---

### Post by lincolnlad on 2007-10-18
If you've installed Gutsy, you don't need to install Beryl.  Gutsy comes with CompizFusion (Beryl's replacement) as the default desktop manager. Just go to the Appearance preference, Visual Effects tab.  If you want to tweak CompizFusion, install the compizconfig-settings-manager and set the Visual Effects tab to 'Custom'

---

### Post by gjohn2 on 2007-10-18
i have 945gm too and my laptop
is absolutely unusable.

stuck in 640x480 when it should be 1280x800

ugh. i hate this video card.  
i have been dealing with this damn card and 
its problems since breezy :(

---

### Post by androloog on 2007-10-19
I have the same video card.
When booted up from live gutsy cd, everything was fine. After installation completed, rebooted laptop, and it gave me vesa driver correct resolution but compiz was not working.

I booted up again live cd and compiz was working and the resolution was again 1280x800 as it should. So i replaced my xorg.conf with the live cd xorg.conf. Now it uses intel experimentary driver.
Rebooted and resolution was 12800x800 and compiz was working, except titlebar of windows is huge and the fonts are also huge and i am still looking for fix.

Otherwise it looks very promising.

---

### Post by SmileyChris on 2007-10-21
I've got the same video card also. Found in another post somewhere that you can go to *System > Preferences > Appearance*, then the *Visual Effects* tab, switch to *None*, then switch back to *Normal*.

---

### Post by androloog on 2007-10-22
> **SmileyChris said:**
> I've got the same video card also. Found in another post somewhere that you can go to *System > Preferences > Appearance*, then the *Visual Effects* tab, switch to *None*, then switch back to *Normal*.

Yes, that fixes it, but reboot and it is again big fonts, maybe it is a bug. It also freezes sometimes. Could anyone help


PLIIIIIZ

---

### Post by sixstorm on 2007-10-22
This is the same as the Intel X3100 right?  If so, I have CF running on "Extra" and it . . . is . . . beautiful!  There is a thread or two floating around here with the solution.

EDIT - Make sure you have xserver-xorg installed.

---

### Post by KCPokes on 2007-10-22
I have this chipset on my laptop and haven't had any issues, other then typically having to reconfigure Xorg after an install or upgrade (going from Feisty to Gusty required a reconfigure).  I am using the experimental driver, as well, at a resolution of 1400X900, and its been pretty stable, from what I've seen (and I've been running Feisty, with Compiz-Fusion, for the past 3 months or so).  I did run into some of the issues described (no title bars for windows after upgrade) but after cleaning up my sessions and rebooting, they've been resolved.  For a built-in graphics chipset I've had far more luck with this then any attempt at getting my ATI X1950 card working.

---

### Post by Linicks on 2007-10-22
Guys, some possible fixs for the issues seen here:

Resolution on Intel:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues)

The GM card:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

Maybe those links will help.

Nick

---

### Post by Seisen on 2007-10-22
Make sure you are using the i810 intel driver, that is what I use and it is fine.

---

### Post by Jorgel on 2008-01-15
Sorry to resurrect this old thread, but seems better than starting a new one.

I just installed 7.10 on my Toshiba Satellite laptop after partitioning my HD to dual boot with XP. I seem to have the same problem stated before, I go to Sys->Pref->App->Visual Effects and I'm not able to go into Normal or Extra it just gives me an error message.

When I go to see my Graphics driver it states that it's using **vesa-Generic Vesa....** , I try to change it to the Experimental Intel Driver as well as the i810 but it reverts to the **vesa** every time. My resolution is fine @ 1280 x 800.

Could somebody please help me? Thank You.

---

### Post by BuntuFreak on 2008-02-15
I'm in the same boat with one of my laptops. An HP DV 6000. But you are a little ahead of me. How did you find out what graphics driver is in use? Some command line tool? Because I can't figure it out. I do know I'm not using any restricted drivers. And the messages on this post refer to some i810 driver? Where do I get that?

---

### Post by trash on 2008-02-16
I was so happy to see an Intel driver update tonight, and as far as i know the Intel driver is more current than the i8xx and i9xx drivers(just so you know).
Also wanted to say that the update is a huge impovement on my machine, no more 20-40 second delay as the desktop loads:).

---

