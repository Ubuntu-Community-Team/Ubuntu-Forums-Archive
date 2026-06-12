---
title: "Looking to buy Asus A8Js laptop - any problems with Edgy?"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by meldroc on 2006-12-01
I'm in the market for a new laptop, and I've been researching, and right now, the frontrunner is an [Asus A8Js]("http://usa.asus.com/products.aspx?l1=5&l2=132&l3=449&model=1373&modelmenu=2").  Sweet-looking machine - 2GHz Intel Core 2 Duo w/ 4MB cache, NVidia GeForce Go7700 w/ 512MB video RAM, 1GB main memory, 100GB hard disk, dual-layer DVD-RW, Bluetooth, wi-fi, and all the usual features.  It gets good reviews, and looks like a great laptop, though it has a relatively short battery life (probably because of the NVidia GPU.  I can live with that - I want to game on this system, so I'll sacrifice some battery life for great 3D, and NVidia has much better Linux drivers than ATI.)  It's a little pricey, but it's got a lot of horsepower.  Asus has a good reputation in my book - I've built desktop computers with their motherboards before, and I've always seen solid hardware from Asus.

From my Googling, most of the major components seem to work great in Linux, though I've seen some complaints that the built-in sound card and Ethernet adapter needed drivers that only made it into very, very recent versions of the Linux kernel.  I'm inclined to pull the trigger on this purchase very soon now, but I wanted to see if any other Ubuntu users had problems with this model of laptop.

---

### Post by didobuntu on 2006-12-01
what sound card is in this laptop. Is it an hda-intel with a realtek chipset? If yes you should see if the alsa driver support it.

Other thing, look if the nvidia driver is able to take into account the graphic card. If not, then don't worry. Nvidia always do a great job to update their products.

---

### Post by jml on 2006-12-01
If you like the ASUS laptop, check out a company called System 76.  They maintain a sub-forum on this site.  They sell laptops and desktops with Ubuntu preinstalled and they make sure everything works out of the box.  I believe the majority of their laptops are ASUS.  I don't work for the company, but I do plan to buy my next laptop from them.  I have read several favorable comments about both their products and their service on thes forums.

Joe

---

### Post by meldroc on 2006-12-02
I was looking into System76 - they had some nice looking laptops, but they're about $300 more expensive than the equivalent elsewhere.  Besides. they don't have a laptop based on the A8Js, and I'm drooling over that NVidia 7700 w/ 512MB RAM.

I've been around the block a few times with Linux, so I'm not afraid of installing it myself or even doing things like kernel wrangling.

IIRC, the sound-card is indeed an hda-intel w/ a Realtek chipset, though it's very new, so only recent kernels support it.  I imagine that I can get it to work w/ Edgy's 2.6.17 kernel, if not, I can roll my own kernel.

The video card's also pretty new, so it's possible that I'll have to upgrade to nVidia drivers newer than what comes stock with Edgy, but I vaguely remember that some other people were able to get it working using the stock Edgy drivers.  I might end up upgrading anyways to get Beryl working.

---

### Post by straxus on 2006-12-02
I just got that laptop.  I love it, but there are some sound issues [myself]("http://ubuntuforums.org/showthread.php?t=309707") and [others]("http://ubuntuforums.org/showthread.php?t=311035&highlight=volume")  are having.  I've tried the newest version of ALSA, to no avail.  I haven't tried a newer kernel yet, but I suppose that next.  If I can pull myself off of Zelda long enough to try one, I'll let you know how it goes.

---

### Post by meldroc on 2006-12-03
Just googled around, and found this thread: [http://www.notebookforums.com/thread179978.html]("http://www.notebookforums.com/thread179978.html") which might have some solutions for you, including putting some options into the alsa config file.

---

### Post by straxus on 2006-12-03
Thanks!  Putting the line: "*options snd-hda-intel position_fix=1 model=3stack*" into /etc/modprobe.d/alsa-base fixed all my issues.

---

### Post by meldroc on 2006-12-03
That makes me feel good about buying this laptop - the tweak to make the sound work on the A8Js is nice and easy.  Any other issues?  Wi-fi and gigabit ethernet work without problems?

---

### Post by straxus on 2006-12-04
WiFi and the ethernet worked out of the box.  Although I haven't plugged into a gigabit switch yet though, just 100Mbit.

---

### Post by meldroc on 2006-12-04
Here's one more question.  Shall I install old x86 Ubuntu or AMD64 Ubuntu on it?  IIRC, the Core 2 Duo supports AMD64 (or EM64T as Intel calls it.)

My desktop at home is an Athlon 64, but I'm currently running 32-bit x86 Ubuntu on it because at the time I installed it, AMD64 support was still iffy.  Now, it seems that AMD64 is working a lot better, but IIRC, some things don't work in AMD64.  Macromedia's taking their sweet time, so there still isn't an AMD64 version of Flash, and mplayer in AMD64 isn't able to poach 32-bit Windows codecs, so most of the proprietary video formats won't work.  I could probably make the switch to AMD64, but that's too much of a pain at this point - I'd have to nuke and reinstall.

I vaguely remember some workarounds, which mostly involve installing the 32-bit version of Firefox and mplayer so you can use 32-bit Flash and 32-bit codecs.

Is it worth the trouble to go 64-bit?  Or should I stick with 32-bit Ubuntu for a while longer?

---

### Post by dlai on 2007-01-03
Well I'm happy to hear that this computer seems to be working well, I'm aquiring one soon! Furthermore it is my personal experience and opinion that the perfomance gains and hassle with 64bit version is not worth it... But again it is my subjective opinion!

---

### Post by ZennouRyuu on 2007-01-04
This is good news to me, as this laptop will most certainly be my next. And I have no desire to let it boot up once running windows. 

Can you comment on the built in video camera? Does it work? If not can you post the appropriate section from 'lspci -v' so I can google it?

---

### Post by meldroc on 2007-01-04
I got some more information about the A8Js here: [http://www.rothlaender.net/a8js.htm](http://www.rothlaender.net/a8js.htm)

Reportedly, the webcam can be made to work in Linux, but you have to compile a kernel module to make it work.  The page above has some details.

---

### Post by mrfuzzemz on 2007-03-05
I've got everything working on my A8Js except for suspend.  Has anyone figured this out?

---

### Post by screamingmoses on 2007-03-13
I just purchased an Asus a8js, and have found the postings in this thread to be very helpful. I haven't tried suspending my notebook yet, but nearly everything else works really well.

My only complaint right now, which I've had on every linux notebook is a misbehaving touchpad. (I.e. the mouse will skip across the screen when moving the pointer.) I've tried tweaking the snaptics settings in xorg.conf + qsynaptics, however it hasn't entirely solved the problem yet.

d.

---

### Post by mrfuzzemz on 2007-03-13
I haven't had any issues with the touchpad.  Do you have xorg loading the Synaptic driver?

---

### Post by live4fun on 2007-03-18
Hi,

did you get your sound working properly? I have still one issue with it.
When I plug in my headset it still uses the build in mic instead of the just plugged in one.

All I altered so far was adding the following line to my /etc/modprobe.d/alsa-base

```

options snd-hda-intel position_fix=1 model=3stack

```

Do you experience the same behavior?

Best Regards,
Chris

---

### Post by mrfuzzemz on 2007-03-22
I can't say as I don't have a mic to plug in and have never had to.  I also haven't verified the functionality of the built-in mic.  Maybe someone else can report there experience with it?

---

### Post by straxus on 2007-04-25
> **live4fun said:**
> Hi,

did you get your sound working properly? I have still one issue with it.
When I plug in my headset it still uses the build in mic instead of the just plugged in one.

All I altered so far was adding the following line to my /etc/modprobe.d/alsa-base

```

options snd-hda-intel position_fix=1 model=3stack

```

Do you experience the same behavior?

Best Regards,
Chris

Same here.

---

### Post by dlai on 2007-06-09
I'm happy to report that gutsy is proving to have no problems with sound!

---

### Post by mrfuzzemz on 2007-06-09
> **dlai said:**
> I'm happy to report that gutsy is proving to have no problems with sound!

No need to make any edits and both line-in and built-in mic work?

How about the brightness-level increase key?

Thanks for the news!

---

### Post by dlai on 2007-06-10
> **mrfuzzemz said:**
> No need to make any edits and both line-in and built-in mic work?

How about the brightness-level increase key?

Thanks for the news!

Well, I'm not sure about, just didn't have the high noise sound when the sound was on...

Just tried out the mic, and in-line, could not get them to work right away, I'm not really sure what switches to hit in alsa-mixer.

No the brightness increase definitely doesn't work!

By the way, aren't you hanging around the Insanely Mac forum as well?

---

### Post by mrfuzzemz on 2007-06-10
I most certainly am. Have you tried osx86?

---

### Post by dlai on 2007-06-11
Yes... but just waiting for np_ to finish NvidiaEFI (I wonder if he could learn something from the Nouveau team), and javoloui to finish iwi3945...

---

### Post by mrfuzzemz on 2007-06-11
> **dlai said:**
> Yes... but just waiting for np_ to finish NvidiaEFI (I wonder if he could learn something from the Nouveau team), and javoloui to finish iwi3945...

I got wireless working by buying an Atheros card with the same chipset as used in MacBooks.  I have full resolution with MacVidia, but no QE/CI.  Hence I, too, am waiting for NVidiaEFI.

---

### Post by dlai on 2007-06-11
What about the rt2500/ralink chipset?

EDIT: Just found out that the manufacturers are doing the drivers themselves, I think?

---

### Post by mrfuzzemz on 2007-06-11
Hmmm.  I don't know.

---

