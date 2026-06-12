---
title: "Can't detect second monitor"
date: 2010-10-11
forum: Hardware
---

### Post by gjivan72 on 2010-10-11
Hey, I have a [Gateway MX6030]("http://support.gateway.com/s/Mobile/Gateway/6000Series/5378nv.shtml") running Lubuntu 10.04. 

Using vesa drivers was the only option to install Lubuntu.

I am trying to plug in a second monitor in to the VGA port and get a some mirror mode going. I plug it in and nothing happens. I am a totally new at this. I been using Ubuntu. I looked under monitor settings and saw only one monitor was detected. I have read posts and it seems people have gotten this to work easily. Is there something else I am supposed to do? I know the monitor works. Tell me if you need more info!

Thanks
-G

Here is my xorg.conf..seems weird
> 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
~                                                                               
~                                                                               
~                                                                               
~                                                            


**EDIT 1**
I remember why I chose vesa drivers! [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) . I am going to try to change them using a work around.

**Edit 2**
> 
$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)

**SOLUTION **
Okay so this solution may only work for me but this is what I did.

Everything is based off of [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
1. Workaround A: Re-enable KMS by editing the .conf file
2. Reboot
3. Fail to load into X modify xorg.conf file and change vesa to intel 
4. At this point it automatically started X and I was in Lubuntu
5. Celebrate and plug in your external monitor. If it does not start look under Preferences -> Monitor Settings. You may have to turn it on.
6. Reboot
7. At this point my external monitor was freaking out so I than did GTT Incoherency Patch.
8. Reboot
9. External mointor works with intel drivers and no "freaking out".

---

### Post by P4man on 2010-10-11
Have you tried hitting Fn+F4 key to enable the external VGA?

---

### Post by gjivan72 on 2010-10-11
Wow good idea.... no that didn't work. Thanks for the response. My other function keys do something but not that one. Hmm would changing my drivers do anything?

---

### Post by P4man on 2010-10-11
Its entirely possible external vga doesnt work with the vesa drivers. Then again, you are right you have an intel 8xx gpu which may give you the issues you linked to if you use the intel driver. Perhaps give maverick a shot?

---

### Post by gjivan72 on 2010-10-11
Yea. So I changed the word vesa to intel. I tried booting up and I pressed fn+f4 at boot up and the external monitor worked. HOWEVER, I cant boot up and get a blank screen. This happened when I tried installing and had to use vesa drivers. I reverted back and now I can login to Lubuntu. I need to find some working intel drivers. Got to go to class Ill check back later.

I apologize if I use the terminology incorrectly. X = GUI

**Edit 1:** 
Okay so doing the thing above just allows me to see the loading screen but fails to load X. The resolution does seem better though. I tried 

Link: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
GTT Incoherency Patch: This produced the same thing as above. I was unable to switch back and could not load X. 

Than I tried on top of the GTT patch
Workaround F: Use UXA Rendering: This had the same results. I than switched back to my original xorg.conf file and I was able to boot back into Lubuntu with X. Not sure why switch xorg.conf files fixed the problem with GTT. However I uninstalled the GTT patch and now back to square one with no configurations. Will continue  with other configs!!!

This is what I got with:

$ lspci -nn | grep VGA
> 00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)

**Edit 2:**
The closet I can get is install that legacy patch. It boots up but I get to this process:258 GLIB warning which I normally get but than it boots up to the normal Lubuntu GUI X. I can switch using ALT function keys and the external monitor works. However, I can boot up to X. Any Ideas?

[B]
Solution Found See first Post [/B]

---

