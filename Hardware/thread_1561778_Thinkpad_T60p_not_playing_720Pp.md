---
title: "Thinkpad T60p not playing 720Pp"
date: 2010-08-26
forum: Hardware
---

### Post by Fafler on 2010-08-26
I just brought a Lenovo Thinkpad T60p second hand. Angreat laptop for the prize. It's like owning an old mercedes benz. May not be the latest and fastest, but it has leather seats, the engine runs smooth, even after 300.000 kilometers and the the build kvality is just amazing.

Anyway, i can't get it to play 720p video. It almost good enough, but fast movements etc. looks bad. It's a Core Duo 2.16 ghz with 3 gb memory and a FireGL 5200 card, which is the same as a Radeon x1600. Screen resolution is 1600x1200 (thats why i brought it). I use stock X.org and radeon driver. Xorg.0.log doesn't say anything out of the ordinary. What really makes me wonder is that my old laptop, a Dell with 1.6 ghz Core Duo and x1400 could do it without the same problems.

I've tried using totem and mplayer. Totem is actually a bit better than mplayer and none of mplayers output drivers give better results. Turning off  speedstepping improves performance a bit. CPU usage is 100 %, typically with 80-90% used by totem and the rest shared betveen X.org and pulseaudio. I know the Radeons don't have Nvidia's vdpau possibility under Linux, but is there anything i can do to improve performance?

And a bonus question: Does anyone know how to check if the battery is one of those recalled by Lenovo? Ubuntu warns about it at startup and the FRU number matches, but to actually test it i need to run a price of Windows software. Needles to say, i'm not installing XP for that.

---

### Post by fcampbel on 2010-10-15
I'm sorry that I cannot help you.  Perhaps you would be willing to help me.  I have an old A21p that I am trying to learn Ubuntu on.  It has a 1600x1200 uxga screen but I do not know how to get Ubuntu to use that resolution.  It appears you have done it.  How?  Please remember that I am VERY new to Ubuntu and Linux.

Thank you, 
Fred.

---

### Post by tyler711 on 2010-11-30
Hi Fafler,
I know it's been awhile and I hope you have gotten your issues worked out.

However, I also have a T60p and understand the video issues.  

This video card has been a fight since the very beginning.  I am currently running 10.10 with the standard drivers, and have no acceleration.  But my resolution is correct and I can suspend and resume, which is actually quite impressive.

Looking back, the best luck I've had over the years was with 8.04 and 8.10.  These used an old enough version of Xorg (I think) that the ATI fglrx driver would install and run.  This was the only way I've ever had video acceleration in Linux on this laptop.

This video card has always been terrible headache.  Even in Windows, it became "unsupported" by ATI when they were bought by AMD (my laptop was still nearly new) so in Windows I often get bluescreens caused by the ATI driver when doing anything involving pretty graphics.

Now I know for next time, buy nvidia or at least do some research before buying!  I have a power-sucking "workstation class" video card that I paid extra for and I can't even watch youtube full screen :D.

---

