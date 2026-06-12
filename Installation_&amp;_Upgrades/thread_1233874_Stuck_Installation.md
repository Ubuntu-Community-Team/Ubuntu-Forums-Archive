---
title: "Stuck Installation?"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Angus1 on 2009-08-07
Hi all,
Im new to this forum, and ubuntu in general, so this is probably a really simple problem, but i can't find a solution...

Anyway, when i boot from my ubuntu CD, it loads up, and i get a menu where i can chose between Trying with installation, installing ect, when i chose install, or try it, i get a bar, with a little orage blob going backwards and forwards, then, after a wile the blob gets stuck a one end, and gets a bit longer, then just sits there, and does nothing... Ive checked for defects, and there arn't any, but have you got any idea what this could be?

Im using a AMD Sempron 2800+ cpu running at 2ghz (wont clock any higher :() and 512mb of ram. Using the standard 32bit ubuntu, but now donwloading 64bit to try that :)

Any ideas?

Thanks,
Angus

---

### Post by phillw on 2009-08-07
[SIZE=2]A Very quick one to check - Was the CD you are using burnt at a slow speed ?  X4, or below. There have been sad reports of people having problems with discs burnt at higher speeds.[/SIZE]

[SIZE=2]As your computer appears to be a 32 bit one, the 64bit version will not work.

Hope this helps.

Regards,

Phill.
[/SIZE]

---

### Post by Angus1 on 2009-08-07
Thanks :D Ill try that :) I just let the burning software burn it at whatever speed it liked, wich with my cds appears to be 52x :o

---

### Post by Angus1 on 2009-08-07
No luck  :( Same problem, burnt it at 1x... Maby it doesn't like my hardware :confused:

---

### Post by Angus1 on 2009-08-07
Ok, its a hardware problem, works fine on my normal PC.... Hmmm...

---

### Post by Angus1 on 2009-08-07
Strange, xubuntu works fine... Going to try redownloading ubuntu :)

---

### Post by Angus1 on 2009-08-08
xubunu doesn't work, freezes later on :(

---

### Post by jaywebster on 2009-08-08
I have the same problem, except my pc restarts instead of freezes. :-(

---

### Post by Kyalin on 2009-08-08
I am having a similar problem as well. But when the install goes through selecting language, loading bar going back and forth then the command prompt appears with text stating info about references to documentation and how to use sudo for administrator tasks. tried startx but that failed.

Seems Jaywebster is having a similar problem in thread [B]Installation Problem.

Goin**g to try installing on other computer to see if it gets past this point eg is it hardware or software**.
[B]
I am installing ubutu-8.04-desktop-emc-aj13-i386[/B]
[/B]

---

### Post by Kyalin on 2009-08-08
I tried installing on other machine and it got through to the next section of install. I changed over the cd drives and tried again on my machine, but no luck. I did notice though that before the command prompt opens up some script is displayed on the screen stating could not display... then it jumps to new screen. Is there a way to access the install log? I believe this page has vital information that would help me fix this problem.

---

### Post by jaywebster on 2009-08-08
I am installing it now through the alternative cd, and everything seems to be going fine, so I think must be something to do with the graphics card.

I shall come back if it all works out to let you know :-)

---

### Post by jaywebster on 2009-08-08
Well it all installed fine, then when it went to boot up, it restarted as soon as it got to the ubuntu loading bar.

I think its the graphics card. I am using a Radeon 7000, so quite old it might not be supported??

---

### Post by Kyalin on 2009-08-08
I though i had it sorted, i selected F4 safe graphics mode and it got past the previous point which i was having trouble with and displayed the desktop screen with the artistic bird. However it hung there and did not display anything else. Tried the boot from the cd and found that it too got to the same position but eventually presented a window stating "There was and error starting the GNOME Settings Daemon", Error message " Did not receive a reply. Possible causes include:the remote application did not send a reply. the message bus security policy blocked the reply. the reply timeout expired, or the nework connection was broken."

Although this does not mention anything to do with the graphics card i believe that it is the root of the cause aswell. I am downloading the alternative CD now. I thought that there would be a selection to install using text instead of having to download another ISO.

I am using a SIS 6326 AGP graphics card, also an ancient graphics card. 

Will let you know if the Alternative install works.

---

### Post by jaywebster on 2009-08-08
I have fixed it :-)

I have onboard graphics and Radeon 7000 graphics card.

What I had to do is, set the onboard graphics in the BIOS then install unbuntu. Worked fine..

I wanted to use my Radeon 7000 in linux, so you have to tell unbuntu to ignore the onboard.

Next in terminal type "sudo nano /etc/modprobe.d/blacklist.conf"
add these lines to the end
blacklist agpgart
blacklist intel_agp
those entries force Ubuntu to ignore the onboard video preventing the kernel panic system hang.

You can then use your other graphics card, but not your onboard, so depends on your situation.

Hope this helps you :-)

---

### Post by Kyalin on 2009-08-08
Mine is fixed too, installed with Alternate and that went smoothly. Up and running.

---

### Post by Angus1 on 2009-08-08
Ok, thanks, ill try changing card :) just a random card i grabbed from one of the many old PCs i have lying round :) This PC has cost me £10 so far :p

---

### Post by Angus1 on 2009-09-13
Hmm, not woking with new card (sorry for long brake, holidays, other problems ect :)) ill try fiddiling round with the bios...

---

