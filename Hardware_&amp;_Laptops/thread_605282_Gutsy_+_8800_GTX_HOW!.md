---
title: "Gutsy + 8800 GTX HOW!?"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by Urinemachine on 2007-11-06
Guys I am frustrated.  I just booted and installed off of the alternate CD.  Now I reboot expecting a command line, but no, I get a blank screen and no response from the system. What the hell.  How do we install Gutsy on an 8800GTX machine?!

---

### Post by Urinemachine on 2007-11-06
What I have tried in the interim:

Booted from 32 bit live CD with some success which is fine... but I have a 64 bit CPU.

So I went in recovery on my 64 bit Gutsy install and set the xorg.conf to vesa driver and like 1024x res.  I get "running in low resolution mode" now, and when I hit continue, it goes to a blank screen.

This sucks.

I got NVIDIA 100- drivers on a CD but I can't install them in recovery mode because it complains of no kernel files.  And I can't get kernel files because in recovery I have no eth0.  Ugh.

---

### Post by Fire_Chief on 2007-11-09
Have you tried using Envy?```
sudo apt-get install envy
sudo envy -t
```

---

### Post by outlaw93 on 2007-11-09
I was having the same chain of events as the original poster with my 8800 GTX and 64-bit 7.10.  I found this thread searching for a solution.  When I try to run the envy command suggested above (sudo apt-get install envy) from the recovery mode, I get an error message that it can't open the package.  Like the poster said above, in recovery mode, I don't think there is an active ethernet connection and I'm not even sure if the cdrom drive is mounted.  How can I make the envy package available to install from "apt-get" command?

---

### Post by outlaw93 on 2007-11-09
I found the answer from another post.  I booted into the recovery mode in order to get a working command prompt.  I then edited the GRUB menu:

nano gedit /boot/grub/menu.lst

scrolled down to the line where Ubuntu 7.10 is loaded and removed the options "quiet" and "splash".  CTRL-X to exit and save, then rebooted (choosing normal Ubuntu mode on GRUB menu).

Ubuntu then properly booted to the graphical desktop and I could then activate the proper restricted NVIDIA driver (System/Administration/Restricted Drivers Manager) for the 8800GTX.

Everything works great now.

---

### Post by Urinemachine on 2007-11-11
I can't even get that far :(

---

### Post by Fire_Chief on 2007-11-14
Urinemachine,

What happens when you try to boot into Failsafe (recovery) mode from GRUB?

---

### Post by Urinemachine on 2007-11-20
> **Fire_Chief said:**
> Urinemachine,

What happens when you try to boot into Failsafe (recovery) mode from GRUB?

Bad things.  I get a terminal I think, but I can't access internet because eth0 and such aren't initialized.  I haven't once booted into a graphical display.

---

### Post by MonkeyFit on 2007-11-28
> **outlaw93 said:**
> I found the answer from another post.  I booted into the recovery mode in order to get a working command prompt.  I then edited the GRUB menu:

nano gedit /boot/grub/menu.lst

scrolled down to the line where Ubuntu 7.10 is loaded and removed the options "quiet" and "splash".  CTRL-X to exit and save, then rebooted (choosing normal Ubuntu mode on GRUB menu).

I booted into recovery mode, and typed that in.  There was no splash option there that I saw, but I did remove the "quiet" option.  I am still getting this problem.  It was a problem I had with both Fiesty, and now Gutsy.  It wouldn't even boot into the liveCD for me.  Well, it would, sort of.  It shows a black screen, but I've noticed it does seem to respond to commands.  I press ctrl+alt+del, wait a couple seconds and then hit enter.  In about 20 seconds, my computer restarts, leading me to believe that the system is indeed booting to the desktop, it's just not actually outputting an image to the monitor.  I'm trying this on Kubutnu 7.10, but it was exactly the same with both Ubuntu and Kubuntu 7.04, so I don't think trying Ubuntu 7.10 will make any difference.

**EDIT:** Ok, I'm just stupid.  I'm not use to using commandline text editors and didn't realize the text wasn't wrapping.  I scrolled all the way over and found both options and deleted them.  It let me into the GUI and now I can play around.  Next step is for me to get dual monitors working.  Thank you so much outlaw93.:D

---

### Post by Sicundercover on 2007-12-07
Im having the same problem but when I use

```
nano gedit /boot/grub/menu.lst
```

The nano page comes up but the file is blank.

Any ideas?

---

### Post by KevLeviathan on 2007-12-08
I got Gutsy working easily on my 8800GTS, here's how:
I used the live cd. When choosing your boot option, choose safe graphics mode. Before booting to that though, press F4 to manually set the VGA mode to 800x600x32. Now press F6 to enter advanced options. It will open all the launch parameters - find where it says "splash" and change that to say "nosplash". Also, at the very end of the line (as far right as you can go) add noapic. 
This let me boot into the livecd and install ubuntu. After you install, run all the updates and reboot.
Once you've rebooted, use the restricted drivers manager to install the drivers for your card (System>Administrator). Finally, reboot. You should be running at your native resolution now with proper drivers!
If all went well, use the edit feature in grub to test booting without noapic. If you can boot without it, permanently remove it from /boot/grub/menu.lst.

---

### Post by Fire_Chief on 2007-12-08
> **Sicundercover said:**
> Im having the same problem but when I use

```
nano gedit /boot/grub/menu.lst
```

The nano page comes up but the file is blank.

Any ideas?

You're trying to call two different text editors. Nano and Gedit are both text editors. Try just doing```
sudo gedit /boot/grub/menu.lst
``` or```
sudo nano -w /boot/grub/menu.lst
```

---

