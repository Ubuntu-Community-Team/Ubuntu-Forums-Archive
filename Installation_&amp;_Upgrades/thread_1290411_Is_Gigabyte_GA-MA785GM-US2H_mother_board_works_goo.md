---
title: "Is Gigabyte GA-MA785GM-US2H mother board works good in Ubuntu?"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by Green_Star on 2009-10-13
I am planning to build a HTPC using following MB/Processor. I would like to know how much this MB is supported in Ubuntu? My main concern is about display drivers, does Ubuntu use GPU well with proprietary drivers or it fall back to processor?

[http://www.ncix.com/products/index.php?sku=42121&vpn=785GM-X2-245&manufacture=Bundle%20Deals&promoid=1051](http://www.ncix.com/products/index.php?sku=42121&vpn=785GM-X2-245&manufacture=Bundle%20Deals&promoid=1051)

---

### Post by Mr_Freez3 on 2009-10-14
From what I have read in product reviews, this MB works well with Ubuntu Karmic...I bought the same bundle you are thinking about, but I'm waiting for my memory to ship, so I haven't assembled my system yet.  If you didn't buy yours yet, there's a cheaper deal you might want to look at here:

[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.273662]("http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.273662")


Here is a review from Newegg.com, running Jaunty:

> 
N/A
    Tech Level: high
    Ownership: 1 day to 1 week
    This user purchased this item from Newegg

	
10/13/2009 5:45:51 AM

Rating + 5 Couldn't be happier

Pros: My last board was a cheap-o f**con. I had some issues with it and ended up regretting that I did not spend a little extra to get a quality board from gigabyte. I've always had good success with gigabyte, so they've won me over.

This board was no exception. This model had a few nice things above some of the other boards (4 RAM slots, firewire, esata on the back, all 3 video connectors). Lots of solid caps and sturdy looking components. It's built like a tank with 2oz copper printed circuit board. It also has a 8-pin CPU connector. I only had 4-pin, so I plugged it in and it seems fine.

The 785g handles video nicely..heads and tails above the intel G43 I was using.

Cons: None to report.

Other Thoughts: Paired with the 620 Propus Athlon x4, it's a pretty snappy build at a good price. I'm running ubuntu 9.04. The generic radeon driver worked, but I downloaded the newest catalyst driver (9.9) and installed since the proprietary driver that ubuntu 9 uses doesn't support this chipset. The install was *very* easy, chmod +x it and execute. Everything else seems to work by default, although I haven't tried the audio since I have a separate card. 


Here's another review from Newegg.com, running Karmic Beta:

> 
N/A
    Tech Level: average
    Ownership: 1 week to 1 month

	
10/6/2009 11:14:15 AM

Rating + 5 Good board

Pros: Great onboard video, good connections. Great HTPC board.

Cons: For the price? None.

Other Thoughts: Runs Linux Ubuntu 9.1 Karmic Koala Beta like a champ with my AMD Regor 245 and OCZ 1066 ram. I tried Ubuntu 9.04 but found issue with the AMD video driver leaving an "Unsupported Hardware" watermark icon on my lower left screen. I tried the Alpha 6 and then the Beta of Karmic and it works great. The EXT4 boots very fast. 

---

### Post by Green_Star on 2009-10-15
Thanks man. I read the first review yesterday. Any way I have few questions. How is the GPU support for this MB in Ubuntu? Does it work well with drivers from ATI? 

Another thought I am thinking about following board because of the nvidia linux support, can you comment on this? 

[http://www.asus.com/product.aspx?P_ID=ovqEgLFRjnSClhSV&templete=2](http://www.asus.com/product.aspx?P_ID=ovqEgLFRjnSClhSV&templete=2)

---

### Post by lifeform23 on 2009-11-02
I just built a system with this board and I can tell you what I've discovered so far.

VIDEO
All of the video outputs work very well with the proprietary drivers installed.  I have one problem at the moment that I am working through. That is, on my 37" LCD there is a 2 inch black border all the way around the desktop.  This is occurring using the HDMI cable. This did not happen on my 32" LCD or using the other outputs.

SOUND
I haven't been able to get the digital audio to work though the HDMI output or through the optical output.  The analog audio is working quite well.  I do plan on continuing to work out the problems with the digital audio out

NETWORKING
The gigabyte LAN is awesome!  Works like a charm without any tinkering.
 
The general performance  of this board as been impressive, but I won't be happy until I figure out how to get rid of the black border and get the digital audio outputs working

---

### Post by rtalcott on 2009-11-02
I have this board...spdif optical works for me..I am running Karmic 64 bit...I have no complaints or problems with this board!
rt

---

### Post by Green_Star on 2009-11-02
I too setup Ubuntu 910 32bit for now (waiting for new HDD, RMA). Graphics working fine, compiz too. 

Can you tell me whether compiz working fine in 64bit? I am planning to install again once I get my new HDD. For now HDMI with sound working fine.

So far no complaints.

---

### Post by MaindotC on 2009-11-02
I installed the latest cd image of 64 (which I don't see as any different than rc5 with the latest updates installed) on a separate partition and installed the latest ATI driver from ATI's website, which doesn't seem to be any different than the one available in the repos, and desktop effects worked just fine, very smooth scrolling.  Unfortunately Counterstrike still crashes xserver so I'm still holding onto my Hardy machine.

---

### Post by rtalcott on 2009-11-02
Green_Star...yes...it's working for me.
rt

---

### Post by Green_Star on 2009-11-02
> **lifeform23 said:**
> I just built a system with this board and I can tell you what I've discovered so far.

VIDEO
All of the video outputs work very well with the proprietary drivers installed.  I have one problem at the moment that I am working through. That is, on my 37" LCD there is a 2 inch black border all the way around the desktop.  This is occurring using the HDMI cable. This did not happen on my 32" LCD or using the other outputs.

SOUND
I haven't been able to get the digital audio to work though the HDMI output or through the optical output.  The analog audio is working quite well.  I do plan on continuing to work out the problems with the digital audio out

NETWORKING
The gigabyte LAN is awesome!  Works like a charm without any tinkering.
 
The general performance  of this board as been impressive, but I won't be happy until I figure out how to get rid of the black border and get the digital audio outputs working

I think I have solutions for your block border problem, I will write about the solution once I go home and start my ubuntu machine. My digital audio thru HDMI also working fine.

---

### Post by lifeform23 on 2009-11-02
turns out my HDMI sound problem was just that I had missed a audio setting.  Now to get rid of this darn black border

---

### Post by lifeform23 on 2009-11-02
go away black border

---

### Post by lifeform23 on 2009-11-02
Black border is gone via overscaling in the ATI driver GUI.  Everything is awesome.  You can build with this board confidently

---

### Post by Green_Star on 2009-11-03
I fixed the HDMI sound by going to 

Right Click on sound icon on task bar => Sound Preferences => Output tab => Select HDMI radio option.

And I fixed the block border with executing following commands with startup after 20sec of GDM start
> aticonfig --set-dispattrib=tmds2i,positionX:0
aticonfig --set-dispattrib=tmds2i,positionY:0
aticonfig --set-dispattrib=tmds2i,sizeX:1920
aticonfig --set-dispattrib=tmds2i,sizeY:1080


I do not know how to do the ovrscaling, @lifeform23, could you explain how to do that?

I figured it out but not sure, please confirm following method

ATI Catalyst Control Center => Expand Display manager tree => Select DTV under the tree => In Adjustments tab "Scaling options"

have you done like above?

---

### Post by lifeform23 on 2009-11-04
That is exactly it

---

### Post by Green_Star on 2009-11-04
> **lifeform23 said:**
> That is exactly it

Yup, thanks man. I tried after I posted here and it worked fine. Great.

---

