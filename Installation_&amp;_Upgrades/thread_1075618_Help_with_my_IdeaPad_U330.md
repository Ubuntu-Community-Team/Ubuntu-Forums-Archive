---
title: "Help with my IdeaPad U330"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by dimensionpr on 2009-02-20
I have one IdeaPad U330 and i can not install ubuntu 8.10 I get a black screen where it tells me that Ubuntu is free and which everyone knows and if isnstal Ubunto is under my own risk. What's happening? I never had that before with my last laptop. Thanks.

---

### Post by Ryan B on 2009-04-09
I am running 8.04 on my u330. It seems to work fine (I am currently booting from Hardy which runs off an external USB drive).

In the BIOS (hit F2 when you boot), set the graphics card to 'discrete graphics'. This should get you past the black screen. I managed to get VESA drivers working with the 'switchable graphics' but not sure if that would work first time round.

Unfortunately with discrete graphics you will only get about 2hrs of battery life.

If you want to get the webcam working (I have not fiddled around with this yet), type at the command prompt to list the device: 

[FONT="System"]lsusb[/FONT]

The webcam on my u330 is 'Bison'. If you search the forums for 'webcam bison' there are some directions about how to get bison webcams to work.

Hope that helps. R

---

### Post by muadnu on 2009-06-08
I'm thinking about buying an Ideapad U330 and was wondering if you could give me some more advice. From the above post it seems that it's working well... I assume the ATI card is working (it's a shame the switchable graphics don't work though). But how would you rate it in general? I'm concerned because I've some seen pretty negative reviews on the web saying that Linux doesn't really work on the U330. I'm wondering if this is just about the switchable graphics issue or something more.

In particular, do the audio and mic work OBO? Does hibernate work?

Thanks...

---

### Post by Ryan B on 2009-06-09
Now I have had it for a while, I am a little disappointed with a few things on the U330, but for the price I paid $879 I can live with it. If I paid $1200, I would be very unhappy. I installed 9.04 on it. 

The Audio works fine (actually the speakers are louder than they are with Vista, though still not very good). Suspend and hibernate work (though hibernate is about as fast as rebooting). 

What does not work (out of the box) I only noticed 2 things: 
(a) switchable graphics, which means battery life is around 2hrs on the ATI card, which is the most disappointing aspect.
(b) Webcam and built in microphone (I haven't tested the mic jack). I had a look at trying to get this working (about 20mins of Google and did not see anything promising, so I still use the Vista partition for Skype). If anyone has had any luck, that would be great. With 9.04, lsusb now lists my webcam as 'Acer'

Grumbles
(c) The Bios has very few options (e.g. you can't switch of Bluetooth here. Someone mentioned lack of virtualisation options too, but I don't use that.
(d) I get the feeling that Lenovo don't care about linux. As Lenovo launches newer products, their IBM heritage gets weaker and with it linux support.

If you can live with short battery life and no webcam, and get a good price, the U330 is a reasonable buy. I am not sure what other models you are considering and your price range, this would probably guide my recommendation.

Hope that helps.

Just had a look at the U330 prices. Watch out on the specs, I noticed that Lenovo are trying to shift an inferior model to mine for $799. Mine has a P7350 processor, 3GB DDR3 Ram, 250GB harddrive, LED backlit screen. The $899 is most similar to mine, with bigger HD, slightly better processor, but no LED backlit screen.

---

### Post by muadnu on 2009-06-10
Thanks for the reply. I'm looking at the prices now, they went down by a couple hundred from the weekend.

I'm worried about the webcam and mic, I use them a lot and am not willing to use Vista just to be able to use Skype.

The other thing is about the LED backlit screen. How do you tell the difference between the $799 and the $899 models? I don't see any difference regarding the screen...

And one more thing... Do the multimedia buttons work ok?

The price is not bad, specially since they have a 10% going on until today. But since I'll be out of town for almost three weeks I think I'll better wait anyway...

---

### Post by Ryan B on 2009-06-10
I don't think the current U330 models are available with the LED backlit screen. They seem to only be available with TFT screens. This might not be a completely bad thing since they also say anti-glare. Mine has a glossy screen which is really reflective, but lack of LED, probably impacts screen brightness and battery life.

I know the webcam thing is a pain. Maybe with some effort, this can be fixed, but I haven't invested much time with it. Also there does not seem to be much of a u330 linux community for help with things like this.

One final thing I forgot, I don't think the SD card reader works in ubuntu. I tried putting in a sony promemory stick and it did not mount.

The multimedia keys work fine out of the box.

---

### Post by muadnu on 2009-06-10
Right... I sort of missed the TFT part. I guess not having a LED backlit screen affects the weight, I wonder by how much.

About the card reader, I don't think memory sticks work at all in Linux, something about Sony not having released some specs. In my current laptop I can read SD cards but not memory sticks.

Thanks again for your help!

---

### Post by coughlin on 2009-07-26
> **Ryan B said:**
>  I don't think the SD card reader works in ubuntu. I tried putting in a sony promemory stick and it did not mount. 

... neither did my Olympus card, ***BUT*** ...

I think that depends on the card reader **format**.  I did some research/homework on flash card formats (check Wikipedia) - before buying one ... and concluded that the "**HDSD**" format seemed the most non-proprietary and generic.  I found best prices within the HDSD format, as well ... obtaining a 16 Gig card for $32 a few months back.

Anyhow, the 16 Gig *_**HDSD card mounts, automatically, and works, fine**_*, on my U330 with 64 bit 9.04 Ubuntu.  

Look for an **HDSD** card, rated at least "**6**" (speed) ... mine is **astonishingly QUICK**    :)    ... i.e. NOTICEABLY faster than the stock 5,400 rpm hard drive !!! ... next best thing to an SSD drive.  I find that all my 'data' stuff only takes less than 3 Gig, leaving plenty of free space.

---

