---
title: "Monitor Resolitions and Refresh Rates - Nvidia/KDE/IBM 6652"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by SadaraX on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: monitor, xvidtune, nvidia, nvidia-settings, resolution, KDE, video, display, refresh, refresh rate [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have one question and one problem. 

_My question_: How do you accurately tell what refresh rate your video/monitor is displaying at? I think KDE may be misreporting things to me. Currently everything looks alright, but KDE says I am running at 156Hz, while xvidtune says I am running 85Hz and nvidia-settings also says 85Hz. What should I trust?

_My problem_: I think I may have my video running properly, and KDE may be misreporting things to me. Or maybe not. You judge:

I just installed Kubuntu 7.04 Feisty on my system. Under 6.10 Edgy, using my Nvidia 6800 GT I was able to have my monitor run at 1280x960@85Hz beautifully (nvidia driver Linux Display Driver - IA32 Version: 1.0-8776). Now, under Feisty, with the 2.6.20-15 kernel I cannot compile the nvidia 8775 drivers, so I compiled their latest version 9755 drivers. Now I **cannot** get my monitor resolution to work at 1280x960@85Hz.

If I use the 'nv' driver, I can achieve 1280x960@85Hz but my video is very slow and underpowered. 
If I use the 'nvidia' driver, my system is very fast and uses the video-card's power, but I cannot select the refresh rate of 85Hz. 

I have tried many many things and I have had strange results. KDE reports my video refresh rate at numbers I have never seen before. Like 97Hz, 148Hz or 167Hz. Currently everything looks alright, but KDE says I am running at 156Hz, while xvidtune says I am running 85Hz and nvidia-settings says I am also running at 85Hz. What should I trust?

---

### Post by panty31772 on 2007-04-22
I am having that same issue ( also using kubuntu ) I do believe it it mis-reporting the refresh rates  , as my monitor doesnt even support the rate shown in "system  settings" !

Going to keep looking for info/solution to this problem ( though i dont believe it is causing any display /performance issues )

---

