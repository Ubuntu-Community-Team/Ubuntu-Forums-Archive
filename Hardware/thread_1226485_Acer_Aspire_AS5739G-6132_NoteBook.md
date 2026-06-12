---
title: "Acer Aspire AS5739G-6132 NoteBook"
date: 2009-07-29
forum: Hardware
---

### Post by tuco penguin on 2009-07-29
Is anyone running this Acer laptop with Ubuntu?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834115592](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115592)

I happily made the switch to Ubuntu 2.5 years ago and successfully extended the life of my 2001 vintage desktop PC--no looking back, I love Ubuntu.  I'm in need of modern hardware, though.  I'm thinking laptop this time.  This Acer appears quite nice for the price.  My questions:

1.  Any Ubuntu-specific experience with this laptop you can share would be much appreciated.  Does all the hardware work?  What version of Ubuntu are you running?  I don't mind downloading a driver and tinkering a bit in config files to get things working, but I'm not too interested in building custom kernels or drivers.

2.  Specifically, is the GeForce GT 130M well supported in Ubuntu?  I have not heard of this graphics card before, but I know Nvidia is generally well supported.  The only gripe on this laptop I have read revolved around 64-bit driver support for the video card under Windows 7.  Is it a new product?  I'm not a gamer, but do like to run compiz and possibly 3D CAD at home in the future.

3.  Any non-OS related comments also appreciated.  Is this a high-quality laptop, or a flimsy POS?  Thoughts on Acer in general (customer support, build quality, etc.)

4.  I would be grateful for alternate laptop suggestions, also.  Keys for me are dedicated graphics card, Core 2 Duo or near-equivalent AMD (?) processor, sub-$800 price tag, and (obviously) good performance/driver support under Ubuntu.

Thanks for all input!

---

### Post by FrothySasquatch on 2009-07-30
Tuco,
I bought this laptop from newegg a few weeks ago. Hardware-wise, it's a very nice laptop, but there's something shady going on with the graphics drivers. I haven't been able to make it work in Linux - more details here: [http://www.nvnews.net/vbulletin/showthread.php?t=136322](http://www.nvnews.net/vbulletin/showthread.php?t=136322)
In windows, I upgraded to Windows 7 which is actually quite usable, but there also I'm not able to use the NVIDIA graphics. there is a driver installed when you receive the laptop, but it doesn't support CUDA, and trying to upgrade it was impossible - according to one of the reviews on newegg, Acer doesn't play nice with the NVidia OEM drivers. I'm trying to get something out of Acer on this, but I've more or less resigned myself to waiting for a decent driver release from Acer.
Linux may or may not be hopeless. There is another thread on nvnews ([http://www.nvnews.net/vbulletin/showthread.php?t=132041](http://www.nvnews.net/vbulletin/showthread.php?t=132041)) where someone had the same phenomenon, but their solution (a modified modeline) didn't help me.
So again, I like the laptop for what it is, but since I can't use the graphics card, I'd have to recommend against it. There is a Lenovo for $799 on newegg that seems to have pretty decent specs: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834146584](http://www.newegg.com/Product/Product.aspx?Item=N82E16834146584). If i had been able to get a refund for the Acer, this is what I would have gone with.
Hope this helps.
- Marcel
[]("http://www.nvnews.net/vbulletin/showthread.php?t=132041")

---

### Post by tuco penguin on 2009-07-31
> **FrothySasquatch said:**
> according to one of the reviews on newegg, Acer doesn't play nice with the NVidia OEM drivers.

Wow, thanks for the report!  I think I caught that comment about Acer not using NVidia OEM drivers on New Egg somewhere when I was skimming reviews and that is what prompted my post.  I'm glad I asked.

That Lenovo was on my radar, too.  Please do post back here if you get Ubuntu working.  I'm not sure how far off my purchase is.  Could be days, could be months.  If a solution appears, I'd love to know about it.  I really appreciate your sharing your pain to save me from the same experience.

Alternate laptop recommendations and comments from others on the Acer 5739 still solicited, too.

Cheers,
craig

---

### Post by FrothySasquatch on 2009-07-31
Maybe I spoke a bit too hastily... this afternoon I found that using the "ForceWare" drivers from laptopvideo2go works quite well. I now have full resolution ( 1366x768 ), hardware accel, CUDA...
So the Windows side works quite well.
Not sure when I'll have time to investigate the Ubuntu side again, but since semi-generic windows drivers did work, the linux side shouldn't be impossible, at least (which I suspected since I couldn't get the stock NVidia drivers to work). Maybe it's time to go back to those modelines...

---

### Post by FrothySasquatch on 2009-07-31
Oh, and to address some of your other questions:
- the laptop seems to be built very well. It's surprisingly light for its size, the screen hinges don't seem flimsy, and overall it makes a very good impression. The keyboard is nice too. It is surprisingly wide, though - wider than I expected. The dimensions are on the newegg site.
- customer support has been underwhelming relative to my personal expectations, but I have nothing to compare it to. I went back and forth via email with them, and it was rather pointless. phone support wasn't much better.
- the laptop doesn't ship with an OS CD - you're expected to burn your own. In addition, the HD has some sort of recovery partition (which I blew away almost right away).
- You do get a Windows 7 upgrade license with the purchase, and as I said, W7 is quite nice to use (once you get used to it). 
At home, I've been running Linux for probably 8 years or so until now, but I'm too lazy to be a zealot anymore. I'll take another shot at trying to set up the NVidia driver in Ubuntu, but if I don't get it working, I'll survive.

---

### Post by divedeep on 2009-07-31
> **FrothySasquatch said:**
> It is surprisingly wide, though - wider than I expected. The dimensions are on the newegg site.
Newegg shows this as 16.14" wide (16.14" x 11.25" x 1.37-1.63").  I found 14.6" (14.6" x 10.3" x 1.0" – 1.5”) on Acer's site but your comment has me doubting it.  16" seems a little wide for a 15.6" screen.  Could I impose for you to measure your laptop?

---

### Post by FrothySasquatch on 2009-07-31
Sure, I'll check when I get home. But you're probably right with 14.6" - It was just slightly to wide for my Timbuk2 laptop bag, and that one accomodates my work laptop which is probably about 13.5" wide. So that, together with the fact that it was listed as 16.4" at newegg, made me assume it's unusually wide.
But I'll double check.

---

### Post by tuco penguin on 2009-08-01
Hmmm... I wonder if something like an HP G60t configured with GeForce 9200M GE video and Core 2 Duo T6500 might be a good alternative.  With 3Gb RAM and goodies like webcam and bluetooth it configures to about the same price as the Acer (with possibly better customer support?).  But no fingerprint reader available, sadly.

Anyone with thoughts to share on the HP, re overall quality, compatibility with Ubuntu (GEForce 9200M GE video, keypad, wireless, webcam...)?  

(maybe a new thread is required?)

---

### Post by FrothySasquatch on 2009-08-01
> **divedeep said:**
> Newegg shows this as 16.14" wide (16.14" x 11.25" x 1.37-1.63").  I found 14.6" (14.6" x 10.3" x 1.0" – 1.5”) on Acer's site but your comment has me doubting it.  16" seems a little wide for a 15.6" screen.  Could I impose for you to measure your laptop?

Yep, the dimensions on the Acer website seem correct.
- Marcel

---

### Post by divedeep on 2009-08-05
> **FrothySasquatch said:**
> Yep, the dimensions on the Acer website seem correct.
- Marcel
Great, thanks a lot for checking that for me!

---

### Post by tuco penguin on 2009-08-05
Marcel,

After having seen this Acer in person (or its lesser-equipped cousins), I really like the size, weight, and ergonomics of this laptop.  And I agree that the build quality seems pretty good at first glance.  Like you, I can probably live with Windows 7 for a while (or with my 8 yr. old desktop this is intended to replace), with the belief the GT 130M GPU will be supported in Linux sooner or later... if I decide this is the right piece of hardware for me.  Can I ask a few more questions?

1.  What kind of battery life are you seeing with the Acer AS5739?
2.  Does it run particularly hot or impressively cool?
3.  Do you find it particularly noisy or quiet?
4.  The flat, floating-key keyboard works well for me (I'm sure this is personal), and looks fantastic when it is clean and new.  Looks like a crumb and dust-magnet though.  Any issues with this yet?

Anyone else with this laptop, please chime in too.

Thanks!
Craig

---

### Post by tuco penguin on 2009-08-14
Marcel/Frothy:

If you're still monitoring this thread... By any chance did you update the BIOS on your 5739G with version 3216 released by Acer on 7/28/09?

Craig

---

### Post by tuco penguin on 2009-08-16
For anyone still following the thread, a solution to the 6-screens problem with the GT 130M on the Acer 5739G seems to have been found.  In xorg.conf, set"ModeValidation" to "NoTotalSizeCheck"  See this thread over at nvnews:

[http://www.nvnews.net/vbulletin/showthread.php?t=137379](http://www.nvnews.net/vbulletin/showthread.php?t=137379)

Hope this helps someone.

---

### Post by sleepitoff on 2010-01-07
Digging up this thread here... 

I'm in the market for a new notebook and this one is a great price from Newegg and I think I'm going to order it. For those of you that were part of this thread before, how do you rate it? satisfied?

---

### Post by FrothySasquatch on 2010-01-07
I use it mainly as a desktop, except when travelling. Battery life is about 2-3 hours with minimal usage (web browsing, playing mp3s). One major annoyance is the fan control. Basically, it never really cranks the cooling fan up to full speed for more than a few seconds, so you get this annoying oscillating sound when you run any CPU- or GPU-heavy applications. Also, it tends to overheat when running graphics-heavy stuff. I'm using it with a coolermaster laptop cooling pad, and that helps somewhat, but I don't like the fact that there's no warning or anything - it just powers off hard when the GPU reaches a critical temperature.

---

### Post by tuco penguin on 2010-01-08
Getting everything working properly under Ubuntu took some work, which shouldn't phase a lot of forum viewers here, but it wasn't too bad.  I still don't have the headphone switch working, so I get sound from the speakers all the time which is one thing I'd like to fix, but I mostly use this from the sofa at home.  All in all I am satisfied with the laptop.  Gripes are minor:  

For a screen this size, the resolution is not spectacular.  I feel like I should see more in my windows on this screen.  My wife's Macbook has a screen with similar dimensions but so much more fits comfortably on it due to the higher resolution--clearly one place Acer saved money.

The battery life is not great--I usually get just over 2 hours from my sofa in Ubuntu... it's noticably better when I run Windoze 7 (which is very rarely).  So it is clear that the power managent software plays a big role.  I have not spent much time optimizing this in Ubuntu beyond the very basic power management settings.  For me, 2 hours is usually enough.

The touchpad placement is such that I often inadvertently tap it when I'm typing and I'm in the habit of pressing the touchpad lock key before lots of typing or plugging in a mouse when using it at a desk.

It arrives with a lot of Acer bloatware for Windows.

I do not have issues with the fan or fan noise, but I don't often run graphics intensive programs/games under Ubuntu.  I occasionally run Solidworks (3D CAD) under Windows and never noticed the fan, so this, too, could be a Ubuntu-specific issue for those who notice it.

On the good side, I find the size comfortable and I like the styling.  I was pleasantly surprised by the sound quality of the speakers--not audiophile quality, but pretty good compared to a lot of laptops.  It's plenty fast, and has quite a few features for a great price.  I think it is a very good value and it's hard to find a comparable laptop at this price or even a few hundred more bucks--at least it was six months ago when I was shopping.  It's not the best laptop on the block, but its very good for the money.

My $0.02... hope it's helpful.

---

