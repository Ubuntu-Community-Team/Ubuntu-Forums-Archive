---
title: "Acer Aspire 5024WLMi - NO GRAPHICS in Ubuntu 6.06"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by ovimunt on 2006-06-24
To start with, I'm a COMPLETE BEGINER when it comes to Linux. I can fix pretty much anything in Windows but Linux seems impossible to me, at least for now.

Anyway, I've just installed Ubuntu 6.06 on my computer and I've got a bit of a problem. It would be great if someone could help me.

I've downloaded the DVD version of Ubuntu and first tried it Live. It didn't seem to work or at least I got no graphics whatsoever. I then tried the 'safe graphics mode' and it worked just fine.

After this I decided to try and install Ubuntu on a separate partion. Installation went smoothly (except for the WiFi which I know will need some additional work according to all ste stuff I've read around here), Grub works fine so I can use my Win XP, but again I get no graphics at all when trying to start Ubuntu. I did try to edit the boot lines in Grub and add 'xforcevesa' as it appears in the command line on the 'safe graphics mode' of the Live DVD but it still didn't work.

So I guess I'm stuck for now, good thing my Win XP starts just fine.

Anyway, if you've got an idea on how I can get graphics, please let me know.

Thanks

---

### Post by ovimunt on 2006-06-25
Problem solved, d**n it!

I mean, c'mon, this bl***y Linux can't be smarter then I am, right? (or so i hope :D)

The problem is that Xserver tries to display the image on the wrong device! You might know that the Acer Aspire 5024WLMi with ATI Mobility Radeon X700 has also a Standard Monitor connector, TV-Out and dual display capability besides its own screen. What probably happens is that the Xservers is sending the signal to the Standard Monitor connector. To sort this out you just need to tell it to also look for other display devices.

SOLUTION: (NOTE - ALL COMMANDS ARE cAsE sEnSiTiVe!)

1. After the drum sound press Ctrl+Alt+F1 once or several times until you're in text mode. 

2. Now enter your login and password details.

3. You're now in command line mode. Type the following lines:

[I]cd /
cd /etc/X11
sudo nano xorg.conf[/I]

Some of these commands are redundant but they'll get the job done.

4. You've opened the *xorg.conf* file in the Nano text editor. Scroll almost all the way down until you find these lines:

[I]Section "Monitor"
	Identifier	"Generic Monitor"
	Option ...
EndSection[/I]

5. Replace the line

*Option ...*

with

*Option "Monitor Layout" "LVDS,AUTO"*

I'm not 100% sure what this does but someone around here was saying that it tells the Xserver to look for additional display devices.

6. Press Ctrl+X. This will exit the text editor but first you'll be asked if you want to save the changes. Type Y and press Enter until you're back to the command line.

7. Type 

*sudo reboot*

This will reboot the system

That's it, everything should be just fine now. Good luck! ;)

---

