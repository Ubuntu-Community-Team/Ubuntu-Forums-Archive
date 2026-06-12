---
title: "nvidia, intrepid and 1366x768 and other weird resolutions"
date: 2009-01-20
forum: Hardware
---

### Post by c_c on 2009-01-20
Hi,
  Well, there are a lot of weird resolution screens (tv's / monitor's) that are being released nowadays. I have an Acer X193HQ LCM monitor 18.5" which has such a resolution.
  After a lot of searching I found the solution to getting these working.
 Just add the one line line to make your xorg.conf like so :-

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
[COLOR="Red"]        Option          "ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"[/COLOR]
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

  And enjoy your monitor at native resolution.
Hope that helps.

---

### Post by houstonbofh on 2009-02-07
I just want to say, I love you!  Really!

I have tried many threads, apps, modline generators...  I have had the virtual desktops still stuck at 1280x1024, or failsafe X at 800x600 with a giant screen off the edges.  I have used the most colorful vocabulary I know, and had the poor woman who has to put up with me eventually stop questioning my sanity, and just go directly on to morning it's passing.

And then I did this, and it immediately works!

Thank you!

And stats for the search engines...

It is a Vizio VX42L 42' 1080i 720p HDTV with support for 1366x768 and currently offers me 1360x768 and 1366x768.  (Along with other traditional resolutions)

---

### Post by Zyto on 2009-04-29
I just had to add my 2 cents worth on this post. And my many thanks. I've been looking all over the place to find a way to get my Vizio VX42L HDTV to display in its native 1366x768 using the Nvidia Accelerated driver (180 to be exact) but every time I installed any of the accelerated drivers the screen would default to 1024x768. I could manually select in the Nvidia server settings 1360x768, but the sides of the screen would be cut off and then after a reboot, it was back to 1024x768. Added the line to xorg.conf worked like a charm! I didnt even have to set it manually. I just rebooted and now I'm enjoying my native 1366x768. Which is great, because bluray movies would jump and chop, and the audio would become out of sync without the use of the Nvidia accelerated driver. So again Thank you so much for the help! and of course all the time you may have spent on finding this solution!
:guitar:

---

### Post by Phantoome on 2009-10-24
Well Thank u very very very much!
I didn't know google was that endless to find such a simple solution...

---

### Post by Bucky Ball on 2013-12-21
***Thread Closed.***

Just like to add that this fix is still working for the Acer X193HQ. It just worked for me using Xubuntu 12.04 LTS. Good luck all. 

I'm warning myself for necromancy and closing thread, ;)

---

### Post by Bucky Ball on 2013-12-21
***Thread Closed.***

Just like to add that this fix is still working for the Acer X193HQ. It just worked for me using Xubuntu 12.04 LTS. Good luck all. 

I'm warning myself for necromancy and closing thread, ;)

---

