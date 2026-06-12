---
title: "LCD monitor and 1440x900 resolution problem"
date: 2009-07-06
forum: Hardware
---

### Post by lapa678 on 2009-07-06
Hi there folks!
Two days I've been working on this and cant get the stuff working on my machine.
I've got LG W1942S LCD panel with 1440x900 resolution, nvidia 9500 graphic card. Some time ago I had power downs in my town - my linux box was turned off the hard way :P . After this it seems like something is screwed:
- I can't get 1440x900 resolution to work on Ubuntu 8.04/9.04 
- I've been installing nvidia drivers and on 9.04 my LCD is recognized as CRT. On 8.04 ubuntu starts with low-res...
- On windows everything work OK.

It seems like I've looked every post to solve this but no good so far. Power-down would suggest hardware failure ... but on windows everything works just fine.  

I'd really appreciate all your help folks!
Tom

(ps. I'm new here .... be forgiving;) )

---

### Post by gruffy-06 on 2009-07-29
Hello, I've found a solution, though I'm not sure if it will work on your system too.

You might want to modify your *xorg.conf* file and change the refresh ranges to match your monitor's settings. The part you need to configure looks something like this:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "[insert make name here]"
    ModelName      "[insert model name here]"
    [B]HorizSync       43.0 - 70.0
    VertRefresh     50.0 - 75.0[/B]
EndSection

You should set *HorizSync* and *VertRefresh* to the maximum possible ranges that your monitor supports, which can usually be found in the specifications section of your instruction manual. However, the information in my TV manual is quite sparse, so I fiddled around with *HorizSync* a little until I was able to select 1440x900 from the Nvidia-Settings tool. Modify *HorizSync* with care, as unsupported rates can damage the screen.

---

### Post by markst on 2009-08-02
Thanks for your message.  I had tried a lot of things...but changing refresh rates did the trick.  Looking up my monitor specs from the manufacturer's website and modifying the refresh rates in xorg.conf then rebooting gave me a whole new bunch of resolutions to choose from.  I know my monitor can only do 1440x900 so I went with that.  Working great!  Thanks!

p.s.  My monitor is an Acer X193W in case anyone has had similar issue.:popcorn:

---

### Post by dhane1000 on 2010-08-26
> **gruffy-06 said:**
> Hello, I've found a solution, though I'm not sure if it will work on your system too.

You might want to modify your *xorg.conf* file and change the refresh ranges to match your monitor's settings. The part you need to configure looks something like this:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "[insert make name here]"
    ModelName      "[insert model name here]"
    [B]HorizSync       43.0 - 70.0
    VertRefresh     50.0 - 75.0[/B]
EndSection

You should set *HorizSync* and *VertRefresh* to the maximum possible ranges that your monitor supports, which can usually be found in the specifications section of your instruction manual. However, the information in my TV manual is quite sparse, so I fiddled around with *HorizSync* a little until I was able to select 1440x900 from the Nvidia-Settings tool. Modify *HorizSync* with care, as unsupported rates can damage the screen.

You sir are a life saver, Thank you so much. Just installed 10.04 lts yesterday and I'm having problems about getting to 1440x900 res. Searched for many solutions but yours sir worked for me. i even copied your Horizsync an Vertrefresh. :KS

---

### Post by T. Amaral on 2011-12-27
Thanks, gruffy-06. After trying a lot of things unsuccessfully, your  suggestion was the one that worked. Release 11.04 x86_64 with an Asus VW193D-B monitor. I think Ubuntu's Monitor Preferences  dialog should allow editing the HorizSync and VertRefresh ranges, for  example through an Advanced sub-dialog explaining at the top that those  ranges should match manufacturer's specs.

---

### Post by Danzel on 2012-12-24
Some problem - now it is solved: I've changed the VGA cable; it is a matter of quality/attenuation. Try it with confidence.

---

### Post by overdrank on 2012-12-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

