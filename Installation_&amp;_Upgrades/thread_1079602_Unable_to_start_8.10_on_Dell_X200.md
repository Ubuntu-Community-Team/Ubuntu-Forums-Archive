---
title: "Unable to start 8.10 on Dell X200"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by sailfishshooter on 2009-02-24
I have been trying to successfully install and run Ubuntu 8.10 on my Dell X200 (800 mhz Pentium III with 32K L1 Cache, 512K L2 Cache and 631M physical memory) since last Friday. I have no previous experience with Ubuntu (or Linux).

According to specifications I should be able to install and run Ubuntu 8.10. I have tried both Ubuntu 8.10 and 8.10 alternate. I appear to have successfully installed both 8.10 and 8.10 alternate, but in both cases the system "hangs" when the OS starts up, leaving me with either a brown screen with only a pointer (8.10) or a screen with four icons in the middle that do not work (8.10 alternate).

---

### Post by kestrel1 on 2009-02-24
Have you managed to run the Live CD first?
You may want to think about using 8.04LTS, it may work better.
Are you sure that the CD burnt correctly, try re-burning at a slower speed.
You could also take a look at Xubuntu, it is not as heavy on resources as Ubuntu & is recommended for older systems.

---

### Post by sailfishshooter on 2009-02-24
I was never able to run from the Live CD. Hung up every time 10-15 secs after the login prompt. That's when I decided to run the althernate install CD which did not offer the opportunity to run from the CD, only to install. So, I did the install. Installation completed. Pulled CD. Restarted computer, logged in, system "hung" with four icons in center of screen. Reboooted several times, always with the same result. Then, went back to the 8.10 CD and did an install rather than trying to run from CD. Installation completed. Removed CD and restarted computer. System "hung" after login prompt with pointer in center of brown screen. Pointer will move, but that is it.

I have not tried 8.04LTS yet or Xbuntu. Recommendation?

I did a disk verification on both disks and they passed, and I did burn at a slower speed.

---

### Post by kestrel1 on 2009-02-24
I would personally go for trying Xubuntu first, as the hardware is knocking on now. I suspect that there may be a problem with the graphics driver on Ubuntu 8.10.
You could also look at Puppy Linux, this has a very small foorprint, the download is only about 100mb & it runs a Live CD.

---

### Post by sailfishshooter on 2009-02-25
I have successfully installed and run Xubuntu 8.10 on my Dell X200. Learning my way around. Two questions:

1) Each time I reboot the computer it pauses at GRUB Step 1.5 and I have to hit ESC to enter a menu where I have been choosing Generic xx.xx.xx (forgot to write down the number) from a list of several options. Is this the way it is supposed to work? Or, can it be setup to automatically load the appropriate kernal? Am I loading the appropriate kernal?

2) Although the OS is recognizing available wireless networks I have been unable to connect. I believe this is due to the need for WPA encryption which is not an available option. How do I get updated drivers?

---

### Post by sailfishshooter on 2009-02-27
Also having problem with fonts randomly getting blocky in Firefox to the point where they are unreadable. . . . Nearing the point of frustration where I'm ready to go back to XP. I had such high hopes!

---

### Post by afdoughty on 2009-12-14
I run Ubuntu Jaunty fine one x200. The new version 8.10 didn't work for me either.

I find Ubuntu Januty very stable but slow. I tried Puppy on a USB install but no luck. Also Kubuntu was terrible. Also could get Fedora going so am about to try Linux Mint ..... 


The blocky Firefox thing is a problem I had too. In fact it was the whole system fonts. Here is the post that describes the fix

Re: Xubuntu 8.10 with Intel 830MG -> graphic errors
Quote:
Originally Posted by Newtothegame  
Ok so I am dealing with the same issue and after trying and having to do a complete xorg rebuild I moved to the IRC. This led me to a few other sources and an Xorg.conf edit. 

I am going to post my issues and then the whole xorg.conf file. 

First issue was on my dell x200 the cursor would disappear when i adjusted brightness. The next issue was the blocky characters and artifacts displaying on the screen after some time. This required me to add some text under the device section in xorg.

So what you need to do.This is for Xubuntu: Launch terminal> type (quotes removed) "sudo mousepad /etc/X11/xorg.conf" > hit enter > type password. This should launch an editable xorg file. Note the device section (this was the only place I made changes even though I am pasting the whole xorg file.) 

__________________________________________________ __________________________________

Section "Device"
Identifier "Configured Video Device"
Option "HWCursor" "false" 
Option "SWCursor" "true"
Option "MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
-----------------------------------------------------------------------------

So far this has worked for me. 

Now back to finals 

I have a Dell X200 with exactly the symptoms described in this thread and am a newbie to linux - loving the idea of no more Bill Gates but really struggling to get this all working.

When I tried to use your solution, for some reason launching from terminal would not allow me root access to the file and it could not be saved. So I saved a copy to the desktop and opened a file manager from the terminal and drag and dropped the file from the desktop to the etc/X11 folder and rebooted. It worked a treat. 

However, the next problem was firefox - the fonts there were still rendering very badly. I found a solution elsewhere based on changing a firefox setting (not a OS setting). 

Here's what I did:

In the firefox address bar type "about:config" [enter]
In the filter box type "dpi"
The settings for layout.css.dpi should appear in the list below
Change the value to '0' (zero) (right click on the number and select edit or change)
Restart firefox

-- this forces firefox to use system font settings and it all looks much better.

---

### Post by knuesel on 2009-12-14
installed xubuntu. could not find a less intensive graphics setting like there is on ubuntu. my laptop did a split screen on me. what to do ?

---

### Post by afdoughty on 2009-12-15
Just installed Linux Mint via Unetbootin on a USB stick. Much better install than Ubuntu Jaunty. The wireless worked straight off, no font or screen smearing issues, no tweaks of drivers. Almost a completely perfect install first time. Dropbox for linux also perfect install . Very impressed and recommend Linux Mint for all Dell X200 users out there. 

A

---

### Post by phild1087 on 2010-08-26
afdoughty, i'm just now looking to install linux on my X200. what version of linux mint did you install, and do you think that the newest one would work for an X200? Thanks!

---

