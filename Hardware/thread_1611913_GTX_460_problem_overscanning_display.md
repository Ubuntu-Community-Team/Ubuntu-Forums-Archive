---
title: "GTX 460 problem: overscanning display"
date: 2010-11-02
forum: Hardware
---

### Post by robbib on 2010-11-02
Hello,

this is my first post to the forums so please be gentle :)

Problem: i recently bought a new gfx-card,** Nvidia GTX 460**. *earlier *i used 8800 GTS.

Once i startup ubuntu 10.10, it shows a screen and i did change nothing after i switched the card. But, the screen looks like its "overscanned", which means you can see like 80% of the screen around the center. the menubar and taskbar is out of screen. Nvidia-settings shows the correct, native resolution of my display (1920x1200). i guess my display is doing it wrong: Im using a **Viewsonic vx2835wm**

I have a dualboot windows7-x64 and it works perfectly fine over there. When windows boots up to full resolution, my panel shows "DVI"-mode and everything works just fine.
When booting Ubuntu, the panel shows "HDMI AV" and one can hear noise out of the speaker (even with volume=0/panel) and it looks like its connected with an analoge cable, cause one can see "gaussian noise" in the picture as well. It is connected with a DVI->HDMI-Cable, which was part of delivery and used it since ever.

Im not a linux expert, but i already tried purging the nvidia-current and xserver-xorg completely, reinstalling both but the issue remains unsolved.

I have another, smaller panel to test as well, its a Dell FP19something and that one works perfectly fine within both linux and windows, though it is not capable of HDMI/HDCP.

Anyone have a clue what to do about that?

(Sorry, english is not my native language)

---

### Post by robbib on 2010-11-02
a few hours later i was able to eliminate the errors mentioned above by performing the following actions:


[LIST=1]
[*]extract EDID-binary of my panel by using nvidia-settings
[*]modify EDID-binary using [http://analogbit.com/software/edid_disable_exts](http://analogbit.com/software/edid_disable_exts) to disable hdmi support
[*]modify xorg.conf =>  Option         "CustomEDID" "DFP-0:/path/to/modified.edid"
[*]reboot, be happy that it shows "DVI" instead of "HDMI AV" and enjoy a much clearer screen
[/LIST]
All this was possible because i found a website that lead me through the process:

[http://analogbit.com/node/23](http://analogbit.com/node/23)

I attached my final modified version of the edid-binary to use it with X. this is for my panel, and only a panel called: Viewsonic vx2835wm

For someone having a similar problem this thread might be a solution. If i found it earlier it would have saved hours of time. 

Thank you for reading.

---

