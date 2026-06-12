---
title: "Test SLi"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Inhumane on 2007-02-10
I just ran glxgears and I'm getting around ```
39500 frames in 5.0 seconds = 7899.971 FPS

``` Which is very bad for Opty 165 @ 3 gig + 512x2 OCed RAM + SLi 7600GT.
Is there a way I can confirm SLi is indeed working? I have the latest drivers from nVidia and I am showing two cards in the nvidia config tool, but the low scores are a cause of suspicion

---

### Post by Inhumane on 2007-02-10
Bump

---

### Post by fain on 2007-05-15
i have the same cards with options "SLI" "yes" 
and i get about the same fps
36508 frames in 5.0 seconds = 7301.551 FPS
39798 frames in 5.0 seconds = 7959.459 FPS
39820 frames in 5.0 seconds = 7963.889 FPS
39817 frames in 5.0 seconds = 7963.323 FPS
39793 frames in 5.0 seconds = 7958.577 FPS
39844 frames in 5.0 seconds = 7968.798 FPS
38128 frames in 5.0 seconds = 7623.074 FPS
36974 frames in 5.0 seconds = 7394.284 FPS
36966 frames in 5.0 seconds = 7393.042 FPS
39268 frames in 5.0 seconds = 7853.443 FPS
with beryl enabled


and 
41151 frames in 5.0 seconds = 8230.049 FPS
44129 frames in 5.0 seconds = 8825.775 FPS
61364 frames in 5.0 seconds = 12272.709 FPS
79733 frames in 5.0 seconds = 15946.463 FPS
79606 frames in 5.0 seconds = 15921.104 FPS
60551 frames in 5.0 seconds = 12110.105 FPS
44114 frames in 5.0 seconds = 8822.684 FPS
46058 frames in 5.0 seconds = 9211.493 FPS
44309 frames in 5.0 seconds = 8861.767 FPS
44671 frames in 5.0 seconds = 8934.139 FPS
 with metacity

i would like to know of a way to enable the sli hud bars as they are not in my nvidia-settings program my drivers came from the [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) repo.

---

### Post by MichiganMan on 2007-05-22
From 	[9755 readme appendix here:]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-w.html")


[INDENT]Why is glxgears slower when SLI or MultiGPU is enabled?
	
When SLI or MultiGPU is enabled, the NVIDIA driver must coordinate the operations of all GPUs when each new frame is swapped (made visible). For most applications, this GPU synchronization overhead is negligible. However, because glxgears renders so many frames per second, the GPU synchronization overhead consumes a significant portion of the total time, and the framerate is reduced.[/INDENT]


I just got SLI working yesterday with a couple of 7600gs'.  You can see if you're in SLI mode by going to the Nvidia Settings (I'm doing this using the Nvidia driver installed by Envy) Go down to the GPU's. There should be two listed no matter if you're in SLI or not, but if you are, you should see SLI in the Graphic Card Information.  

Another way to check is look for SLI Enabled, or something to that effect in the Xorg.0.log in System Log viewer.

This is just what I remember, sorry I can't be more exact in my quotes as I went back to my single 6800GT. :)

---

### Post by fain on 2007-05-23
thank you very much :) i found outthat my sli wasnt enabled cause i commented it out at one time lol. so i enabled AFR and the log and nvidia-settings said SLI but... as soon as i start glx gears my whole system crashes. i cant even ctrl alt f1 to a terminal :( i have to do a hard reset. so i enabled it as auto. this works better but still locks up at certain times. i played nexuiz for a while and it worked great the whole time, and glxgears worked great but as soon as i started SWG it crashed and last night one of gnomes screen savers crashed it. im going to make a new thread about this problem. thanks for the info much appreciated.

ps whats the difference between multigpu and sli?

---

### Post by MichiganMan on 2007-05-23
[I]
ps whats the difference between multigpu and sli?[/I]

Thats in the readme too:

[INDENT]The distinction between SLI and MultiGPU is straightforward. SLI is used to leverage the processing power of GPUs across two or more graphics cards, while MultiGPU is used to leverage the processing power of two GPUs colocated on the same graphics card. If you want to link together separate graphics cards, you should use the "SLI" X config option. Likewise, if you want to link together GPUs on the same graphics card, you should use the "MultiGPU" X config option. If you have two cards, each with two GPUs, and you wish to link them all together, you should use the "SLI" option.[/INDENT]

---

### Post by fain on 2007-05-24
ic thanx again :) 

my bad i totally missed the readme link

---

