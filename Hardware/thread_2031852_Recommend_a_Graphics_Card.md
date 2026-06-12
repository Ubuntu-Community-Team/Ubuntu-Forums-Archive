---
title: "Recommend a Graphics Card"
date: 2012-07-22
forum: Hardware
---

### Post by ghetto2ivy on 2012-07-22
I run a machine that hardware wise should be a speed demon (SSD, 2.8ghz Hexacore, 16gb ram) even my broadband should be plenty fast (50-60mbs). The one piece that is out of place is my video card -- an almost 5 years old nvidia 8500 GT. 

Since I don't play games in theory the video card should be plenty for what I do (encode video, photo editing, virtual machines, write software, serve media). But in practice, even gedit occasionally grays out on me! And the card stutters on minimizing and maximizing apps. 

So  want to upgrade the card, but find that the video card world is CRAZY compared to what it was five years ago!  Plain and simple can someone recommend a video card $50-$100, with passive cooling (or silent), that runs Unity3D well?

It seems that in that range now are the Nvidia Fermi and Radeon 54XX chips with between 0.5-3GB ram. 

So many threads are about fixing issues, I would appreciate a recommendation!

---

### Post by UltimateCat on 2012-07-22
:)
Hi:

It depends on what your running and if you need/want a dedicated card which can handle a lot more demands in the department of HD graphics.

Nividia has designed a G-force card that does well; but its all of what you need or want.  Nividia's wesite:

[http://www.nvidia.com/content/HelpMeChoose/fx2/HelpMeChoose.asp?lang=en-us](http://www.nvidia.com/content/HelpMeChoose/fx2/HelpMeChoose.asp?lang=en-us)

I have a Radeon/AMD 3100 and it works great.  Of course Radeon has increased their cards by now as my computer is 3 years old.
The website might help you to make your decision.

[http://www.amd.com/us/products/pages/graphics.aspx/](http://www.amd.com/us/products/pages/graphics.aspx/)

In some of the newer laptops there are AMD Radeon HD 7550m dedicated  1GB and 2GB cards.  These are the 2nd and 3rd generation developments so there are a few options but it can get expensive.

Good luck to you; hope this helped

---

### Post by ghetto2ivy on 2012-07-24
Thanks for the links the recommender looks great.

However, I'm wondering what people's experience has been, wondering if anyone has finds a $30-100 video card doesn't stutter on unity3d stuff?

I'm not tweaking it too much, but I know my 5year old card isn't cutting it anymore, still it has good specs (512mb gddr3, 128bit bus, pcie x16, etc).

---

### Post by mastablasta on 2012-07-24
wohaa , why 512MB ddr3 GPU card wouldnt' be a match for unity 3D? 
well i haven't tried unity but KDE with Kwin is blazing fast on my card (also old). maybe it has a better chip inside.
heck i know even the 256Mb AGP card works great in kde with all effects on. 
are you sure there isn't a but in drivers?

---

### Post by ghetto2ivy on 2012-07-24
Oh I agree, I thought my current card [COLOR="DarkRed"]should have been[/COLOR] be plenty fast! That's why I didn't upgrade it. 

Unity3d runs great on my wife's laptop and it's puny built in intel graphics. ON my desktop, Glxinfo shows everything ok (renders through the hardware, driver, etc). Yet it stutters at times, even on gedit, even just scrolling. Also compiz keeps utilizing 30% cpu (running a 6 core, 2.8 ghz cpu!)

It was happening on my old install, then did a fresh install to an ssd and it still continues! The last constant is the video card!

---

### Post by ghetto2ivy on 2012-07-25
MastaBlasta -- It was a driver issue! I switched the nvidia driver to the backported version and =wham= much better performance. glx gears for example went from ~500 fps to 2600 fps. Compiz is between 2-4% cpu. Even the actual system monitor which was at 30% cpu is now at 1-3%.

Phoronix Test for Unigene wasn't much better still 4fps, but I haven't played a computer game in 7 years let alone one at 1080p.

In case someone else needs to fix similar issues I am now running Nvida driver 295.49.

Now I have no excuse to buy a new card and I'll have to go find some other way to waste my money.

---

