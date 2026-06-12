---
title: "USB driver problems?"
date: 2010-09-19
forum: Hardware
---

### Post by Cyclonis69 on 2010-09-19
I just switched over to ubuntu yesterday. During my last few months of using windows, I was having a problem with my mouses connectivity. Random intermittent disconnecting, then sometimes reconnecting shortly after, and sometimes not at all. Plugging the thing back in would make sure that it would usually allow around 5 minutes until another total power loss while plugged in, but not intermittent disconnect and reconnect. That could happen within another 20 seconds at times.

I have tried, in windows xp, downloading the latest mouse and keyboard drivers for my pc's chipset and the latest drivers for my mouse from razer. Neither of these solutions worked; and in fact the razer drivers totally thwarted my usage of the mouse, stating something along the lines of "service name already in use". Rather than trying to look up a means to fix it, I just decided to wipe out Windows and everything else on the machine (for like the 100th time), and try using ubuntu.

I am not sure what all you need to know, but I know the mouse is fine, as it works in other computers, even without having the drivers from razer installed it works fine.

Let me know if there is somewhere that I can get better specs please. The only thing I remember using for spec gathering is dxdiag, and I'm assuming ubuntu doesn't have that, per say...

Mouse: Razer Copperhead
PC: HP Media Center PC m7360n

---

### Post by mikewhatever on 2010-09-19
What exactly is the problem with Ubuntu. It's not clear from your post, but if the mouse problem persists, it strongly suggests that the problem is hardware related.

---

### Post by Cyclonis69 on 2010-09-20
I was afraid that would be the reply. I was just trying to see if someone had heard about any other reason besides that. I had heard that there was some kind of a problem with razer mice on ubuntu, but it seems to be having the same problem that windows was having, and nothing else...

It sounds like Ubuntu is doing fine, and my motherboard's not in good shape, as far as goes the usb ports...

Sigh... Hopefully I can find a replacement motherboard soon then...

Thanks for the help...

---

### Post by chewearn on 2010-09-20
Don't give up on the motherboard yet.  Sometimes, USB connectivity is due to old cables or the worn out USB connectors.

---

### Post by Cyclonis69 on 2010-09-20
Well. All of the ports reacted the same way to the mouse, which was a possible statement that the drivers were out of wack somewhere. I have a feeling that the chipset drivers are just not very good for the motherboard, or something to do with the USB ports isn't configured well. I haven't tested that theory at all, but that's my hunch...

I am thinking that it might not be worth my time to replace the ports on the motherboard, if that is the case. My other question would be, though, wouldn't the port problem effect other hardware? Why not the keyboard and printer as well? Why only the mouse? Also, I'm not entirely certain, but wouldn't the cord being a problem, cause the same effect on any other PC? The mouse works fine on every other PC I've tried it on...

Perhaps I should just try a cheapo new USB mouse, and see if that works...

Let me know if anyone has any other suggestions please...

And thanks for all the help so far, everyone!

---

### Post by chewearn on 2010-09-20
One thing to try is to keep the log viewer opened to display the system messages.  Look for any error or status messages when the mouse is acting up.

---

### Post by Cyclonis69 on 2010-09-22
Sweet. I will try out the log viewer when I get a chance too. I just bought a new house on Monday and am in the process of moving. May be awhile b4 I get back to this though. That will probably help!

Thanks again!

---

### Post by jjer on 2010-10-31
Also experiencing lagging mouse:

I recently installed Ubuntu 10.04 on my 3 years old Acer Aspire 7720G, as a replacement of MS Vista. This laptop has worked OK with Vista, without too many re-installations of the Microsoft OS. The mouse movement was smooth. I have decided that my active support of Microsoft buying and using their OS is now come to an end.

The laptop has Intel Core 2 Duo and Nvidia Geforce 8600M. I am using an optical USB mouse and/or the touch-pad.

When logged in the Ubuntu OS, the mouse pointer behaves as following:
- Sometimes the mouse pointer on the screen moves smoothly according to the movement of the mouse.
- More often the mouse pointer lags, perhaps time periods 0.1 - 0.5 seconds. The pointer stops during the lag period and jumps to a new position, that is in the general direction of the mouse movement. 
- Some times the time lag period is longer, perhaps up to 1-2 seconds, and is almost as the computer freezes.
- When the lag duration is longer than say 0.5 seconds, also the clock in the upper right corner get an delay and may skip a second (example: 11:30:45 -> (minor lags) -> clock updated to 11:30:46 -> (longer lag) ->  clock updates to 11:30:48 )
- A few times (say once every half hour - one hour, the lag seems to be a freeze of the OS because everything stops (also the clock stops updating the time and the clock jumps 10 - 20 seconds when the computer starts responding again). 

I have tried a few options in order to make the mouse movement smooth, based on google searchs:
- Change of display driver (and back to the default when not working)
- Installing "Gpointing Device Setting"
- Decreasing the sensitivity of the mouse
- Disable the option of "disable touch pad when using key board"

Still the problem is there. (Else, Ubuntu 10.04 works fine)

I guess the problem may not be directly related to the mouse or the mouse driver?

Edit: 
After a few hours I have digested the following thread "Ubuntu 10.04 (Lucid Lynx) Random Freeze / Hang-up"
[http://ubuntuforums.org/showthread.php?t=1478787&highlight=freeze&page=1](http://ubuntuforums.org/showthread.php?t=1478787&highlight=freeze&page=1)
and I guess I am experiencing a similar problem where the root cause may be any of reasons proposed.

---

