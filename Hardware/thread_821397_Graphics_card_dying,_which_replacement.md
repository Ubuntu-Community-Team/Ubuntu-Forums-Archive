---
title: "Graphics card dying, which replacement?"
date: 2008-06-07
forum: Hardware
---

### Post by melat0nin on 2008-06-07
Hi all

Yesterday my Radeon 9800 Pro started exhibiting weird pink lines, which move when things happen on the screen.  I'm pretty sure it is beginning to die.  It's not overheating I don't think, because I have its fan (an IceBerq 4) running on full.  It also has the corruption when turning on the machine after being off for a night, and it's not in a warm room or anything like that - so I've ruled out overheating.

So, that said (and with the corruption happening right now - which i'm typing through :)) I think I have to get a replacement before the thing dies completely.  Interestingly, the corruption comes and goes while it's on, but I don't think that really means anything.

**So, I'm wondering what to get**.  I don't game on this machine any more, so I'm basically looking for something cheap (most important) which will run Compiz etc well.  The ability to play some 3D games might be nice but it's not a priority.

Obviously, my machine is **AGP** so the current choice is quite limited.  There are nice and cheap **nVidia** cards over at ebuyer, for example the **5200**.  I've had my fair share of headaches with ATi drivers, so I'm inclined to think that going over to nVidia is the best bet at this point.

Any help or suggestions would be much appreciated :)

EDIT:

How about something like [this]("http://www.overclockers.co.uk/showproduct.php?prodid=GX-095-OK&groupid=701&catid=56&subcat=411&name=OcUK%20GeForce%206200%20256MB%20DDR2%20HDTV/DVI%20(AGP)%20-%20Retail")?  It's silent, which is really nice (the 9800 Pro was always very loud)

---

### Post by melat0nin on 2008-06-07
I've just bought this:

[http://www.ebuyer.com/product/104734/show_product_overview](http://www.ebuyer.com/product/104734/show_product_overview)

which seems a good balance of value and performance.

If I've made a big mistake, please let me know so I can cancel the order!

I'm quite excited about moving back to the nVidia camp... will be interesting to see what the graphics set up experience is like.  It will also be nice to have a proper display settings applet! :)

---

### Post by tommcd on 2008-06-07
I happen to have the very same Asus nvidia 6200 in my Asus K8N rig in my sig. It has always worked well in linux (Ubuntu, Debian, Zenwalk, Slackware). Passive cooling too, so no noisy fan! You will want to use the nvidia-glx-new driver from the Ubuntu repos. It also works well with the linux driver from nvidia.com in Slackware. Good choice for a good, cheap AGP card.
I even play nexuiz, sauerbraten, Doom3 and Quake4 pretty well in linux on this card too.

---

### Post by melat0nin on 2008-06-07
> **tommcd said:**
> I happen to have the very same Asus nvidia 6200 in my Asus K8N rig in my sig. It has always worked well in linux (Ubuntu, Debian, Zenwalk, Slackware). Passive cooling too, so no noisy fan! You will want to use the nvidia-glx-new driver from the Ubuntu repos. It also works well with the linux driver from nvidia.com in Slackware. Good choice for a good, cheap AGP card.
I even play nexuiz, sauerbraten, Doom3 and Quake4 pretty well in linux on this card too.

That's really good to hear.  I'm particularly happy about the passive cooling, and being able to play the odd decent FPS is great.

What are the nvidia drivers like?  I've always read that nvidia was much better in linux for getting both Compiz and 3D to work.  Is that the case with this card?

---

### Post by tommcd on 2008-06-07
The nvidia drivers have historically worked better in linux than the ATI drivers from what I read. I have never used ATI though, so I have no experience there. Since AMD bought ATI they have opened up the source code for ATI to the linux community, so ATI drivers are getting better. I don't use compiz, but 3D gaming has worked very well for me in linux with this card.

When you get it install the nvidia-glx-new driver from the Ubuntu repos, then run "sudo nvidia-xconfig" in terminal. Then log out of X (ctrl + alt + backspace) or reboot and you should get the nvidia logo as X starts. To check direct rendering run "glxgears" in terminal. You should see the 3 gears spinning and get a decent frame rate (I get about 1500-1600 fps). Then run 
```
bash-3.1$ glxinfo | grep direct
direct rendering: Yes
bash-3.1$ 

```
and it should return "yes" as it did in my example.

---

### Post by melat0nin on 2008-06-07
> **tommcd said:**
> The nvidia drivers have historically worked better in linux than the ATI drivers from what I read. I have never used ATI though, so I have no experience there. Since AMD bought ATI they have opened up the source code for ATI to the linux community, so ATI drivers are getting better. I don't use compiz, but 3D gaming has worked very well for me in linux with this card.

When you get it install the nvidia-glx-new driver from the Ubuntu repos, then run "sudo nvidia-xconfig" in terminal. Then log out of X (ctrl + alt + backspace) or reboot and you should get the nvidia logo as X starts. To check direct rendering run "glxgears" in terminal. You should see the 3 gears spinning and get a decent frame rate (I get about 1500-1600 fps). Then run 
```
bash-3.1$ glxinfo | grep direct
direct rendering: Yes
bash-3.1$ 

```
and it should return "yes" as it did in my example.

Thanks for the info!

One thing just occurred to me.. I decided to try taking a screenshot of the corruption, and it showed up on the screenshot.  To me that suggests that the problem is with software and not hardware (if the hardware was failing surely the problem would be independent of the image the computer 'thinks' it is sending to the screen, and therefore the screenshot should be corruption-free).

I thought it might be a driver issue, but I'm dual booting with XP and I get the corruption there, too.

Unless I'm wrong about the above, is it possible that it's not actually the graphics card that's playing up?  Right now the corruption isn't showing, but next time it does I'll take a screenshot and post it here.

---

### Post by melat0nin on 2008-06-08
Here's a screenshot:

[IMG]http://i28.tinypic.com/11jy895.png[/IMG]

It seems 'selective'; different colours of corruption appear in different areas (program windows are usually pink while the desktop is usually green).

What do you think?

---

### Post by melat0nin on 2008-06-08
After reading [this page]("http://www.playtool.com/pages/artifacts/artifacts.html") I ran Memtest86+, and after one pass it found no problem with my system RAM.  After about 28 minutes, though, it started to corrupt:

[IMG]http://i28.tinypic.com/264mf51.jpg[/IMG]

Judging by the examples on the page above, my VRAM might be on the way out (I get the same kind of corruption).

---

