---
title: "Buying a new computer, will I have any problems running Ubuntu on it?"
date: 2008-08-04
forum: Hardware
---

### Post by Cuzit on 2008-08-04
This is the base model that I was going to get:

[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=desktops&a1=Category&v1=Entertainment+powerhouse&series_name=d5000t_series](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=desktops&a1=Category&v1=Entertainment+powerhouse&series_name=d5000t_series)

I was going to make a few tweaks, and end up with the following specs (quoted for ease of reading):

> Windows Vista Preinstalled (it better come with back-up discs so I can virtualize later...)

Intel(R) Core(TM) 2 Quad processor Q9300 (2.5GHz)

8GB DDR2 RAM

1GB NVIDIA GeForce 9800GT, 2 DVI, HDMI adapter

1.5TB 7200rpm SATA 3Gb/s two hard drives (2x750GB)

I'm not sure about the modem... this PC will be sitting right next to the router, so I'm not investing in wireless.  I'm having trouble finding what kind of modems come preinstalled on HP's... but modems tend to work by default, so that shouldn't be an issue with Ubuntu.

BluRay Burner/Reader (again, don't know brand.  I'm sure the HP website lists it somewhere, but I'm overlooking it... :\)  ...wait - can ubuntu burn/play Blurays anyway?  I can't get my laptop to acknowledge the existence of a blank DVD in the drive, let alone burn with it... Bluray can present more problems.  Does anyone have any experience with Bluray and Ubuntu?

SoundBlaster X-Fi Extreme Gamer Sound card

Will I experience any driver problems or any other errors with those specs?  As for the brands of several of the items, such as the RAM, Bluray burner, and modem... I really don't know.  I assume its whatever HP usually uses, but I can't find it on their website.

I really want to get Windows out of my life.  Sadly, I can't, so my plans are to emulate Vista (I'd like to avoid dualbooting if possible) so I can run my Zune software and games...  I've been missing out on too many games lately :D  Are there any problems with VirtualBox'ing Vista to play DirectX10 games... such as Gears of War or Crysis, to name a few examples?

The following two questions are slightly off-topic, but I might as well ask in one topic instead of making three of them. :)

I was looking at Ubuntu Studio.  Has anyone ever used it?  What's it like?  I assume its pretty much the same as Ubuntu, in that I could run all programs I run in Ubuntu on it, and everything generally works the same as in Ubuntu?

Finally, is there a great TVersity-like program that can make my PC a media server, streaming media to my PS3/360/other PCs?  Preferably supporting the file formats that the PS3 reads (MP3, Atrac, and WMA, I believe - I'm not sure if ogg is supported or not, tbqh).

Sorry for this long mess of questions, but I'm finally getting a new computer (first in six years, so I'm very, very happy), and I want to avoid Windows any time I can, but I don't want to give up my Zune and games (one of the reasons I'm opting for a pretty high-end PC like this) just to do that.  Thanks for any help. :D

---

### Post by kdb424 on 2008-08-05
That looks like it will work pretty well. Like most computers it may require more drivers, or tweaking, but it should work.

---

### Post by hotweiss on 2008-08-05
Keep in mind that the RAID configuration will not work via the motherboard, since it is only "soft RAID". You can either get a real RAID controller, or use Linux's dmraid. dmraid is Linux's version of "soft RAID"...

---

### Post by Cuzit on 2008-08-05
> **hotweiss said:**
> Keep in mind that the RAID configuration will not work via the motherboard, since it is only "soft RAID". You can either get a real RAID controller, or use Linux's dmraid. dmraid is Linux's version of "soft RAID"...

So how do I get dmraid?  I assume its in the repositories?

What about burning/reading blurays - I'm having trouble getting Ubuntu to recognize a blank DVD in the drive... so I'm worried about the blurays. :P

And are there any major known issues with that graphics card?  My laptop is a Dell Inspiron 1501 and it has an ATI card.  It took a while to get Compiz set up with it, but games work horribly.  I tried to download a few 3D games from Add/Remove Programs and Second Life from the Second Life website (Linux version ftw) but the screen flickers so bad they are all unplayable. :(  Any problems like that with the NVidia?

---

### Post by hotweiss on 2008-08-06
dmraid is available in the repositories and it will be pre-installed in Ubuntu 8.10.

You'll have to research Blue-Ray compatibility, I'm not sure myself.

As far as graphics cards are concerned, I have heard that people with the ATI 4850 and 4870 are having the best experience in Linux right now, as ATI has made those drivers open source.

If you can, build the computer yourself or go to a computer store and ask them to build one for you based on the parts you choose. Buying a ready build desktop from HP is not the best idea in terms of Linux compatibility and getting the latest hardware. Plus you can't overclock! I'm overclocking to 3.8 GHz now, try doing that on a Dell or on a HP.

---

### Post by Cuzit on 2008-08-11
I would love to build a new computer, but life is hectic right now, and I just don't have the time to mess with that.  I love computers and have done just about everything possible with them - from simple tasks like games to programming - but I have, strangely, never built my own rig, and before I jump right into that, I would need to do some research and take my time.  Money's tight right now, so I wanted to buy a pre-built rig I could pay off little by little - I believe that HP I linked was $50-ish a month.  Once out of college and have a place to live, I would LOVE to build my own PC - but that, sadly, is out of the question right now.

I just wanted to use Ubuntu on it, but oh well - it looks like I'll have a lot of driver problems.  But that's half the fun of Linux, right? :P  I guess I can't fully get rid of Windows... yet.  I don't really want to dual-boot, but I guess that's what I'll do. :D

---

### Post by Jaidee on 2008-08-13
You're also going to have to work to get the sound card working. I'm also using the X-Fi, and it's proving to be quite the pain. There is "early beta" support for it, but using OSS, not ALSA. (ALSA is used by 8.04 as default.) This then involves telling each application to output sound to OSS instead of ALSA. 

It hasn't been a great day for me.

ninja edit:

I got it working! It's tricky, but it took me around an hour, and that included research from scratch. I now have sound from all my applications through my X-Fi card. Now listening to Suicide is Painless by Johnny Mandel on Seeqpod. Delightful!
[URL="http://ubuntuforums.org/showpost.php?p=4874981&postcount=2"]
Here is the guide I used to get it working.[/URL]

As a bit of a rant though, I must say that I'm disappointed with teh lack of support for the latest Creative cards; this might be down to Creative, but it almost put me off Ubuntu. I'd hate for other newcomers to feel the same way.

---

