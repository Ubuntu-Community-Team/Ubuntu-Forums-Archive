---
title: "buying a laptop; any info on ASUS C90S, or other suggestions?"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by slade on 2007-07-10
I need a laptop for college.  I like the specs and price of the asus C90S, but I'm worried about its compatability with linux.  Does anyone know if the laptop will work properly, with emphasis on the intel PRO/wireless 4965 card, built in webcam, built in card reader, and hibernate function?

or does anyone suggest another linux compatible laptop with similar specs and price?

---

### Post by mrphd on 2007-07-11
How much is the ASUS C90S and where are you based? Can you provide a link to a page with the C90S?

---

### Post by slade on 2007-07-11
[http://1toppc.com/Merchant2/merchant.mv?Screen=PROD&Product_Code=C90S](http://1toppc.com/Merchant2/merchant.mv?Screen=PROD&Product_Code=C90S)

I can get it configured as I want for ~$1500.  a comparable laptop pre-configured from dell or HP would be about $2500.  I'm based in the US.

---

### Post by mrphd on 2007-07-12
> **slade said:**
> [http://1toppc.com/Merchant2/merchant.mv?Screen=PROD&Product_Code=C90S](http://1toppc.com/Merchant2/merchant.mv?Screen=PROD&Product_Code=C90S)

I can get it configured as I want for ~$1500.  a comparable laptop pre-configured from dell or HP would be about $2500.  I'm based in the US.

This uses desktop components rather than laptop ones which is why I guess this is cheaper than the ones you looked at from Dell, etc. I personally don't think it is a good idea to have one with desktop components, but ultimately this depends on how portable and upgradable you want this to be. I imagine this will run quite hot... This is marketed as an upgradeable laptop, is this important to you? You will probably find some user reviews from  [http://forum.notebookreview.com](http://forum.notebookreview.com). I'm based in the UK, but there are a couple of US ASUS specialist resellers that post there also. It might be worthwhile checking them out.

I wouldn't expect any problems with the wireless, but getting the webcam to work, built in card reader, and hibernate to work properly may be more difficult... I'm a recent owner of an ASUS VX2 and haven't been able to get these working yet. If you search the forums you will see many posts on these things for different computers. Often they can be made to work, but it depends on the exact component model, and effort will be required.

---

### Post by slade on 2007-07-12
> **mrphd said:**
> This uses desktop components rather than laptop ones which is why I guess this is cheaper than the ones you looked at from Dell, etc. I personally don't think it is a good idea to have one with desktop components, but ultimately this depends on how portable and upgradable you want this to be. I imagine this will run quite hot... This is marketed as an upgradeable laptop, is this important to you? You will probably find some user reviews from  [http://forum.notebookreview.com](http://forum.notebookreview.com). I'm based in the UK, but there are a couple of US ASUS specialist resellers that post there also. It might be worthwhile checking them out.

I wouldn't expect any problems with the wireless, but getting the webcam to work, built in card reader, and hibernate to work properly may be more difficult... I'm a recent owner of an ASUS VX2 and haven't been able to get these working yet. If you search the forums you will see many posts on these things for different computers. Often they can be made to work, but it depends on the exact component model, and effort will be required.

As far as I know the only true desktop component is the processor, which cuts out a few hunded dollars.  this computer will probably be sitting on a desk 75% of the time.  I know the desktop processor means it will run hotter, but it looks like it has a lot of fans, i'm more worried about battery life.  the upgradability isn't all that important, its a plus but I doubt i'll need anything new.  the main plus of upgradability is that if anything breaks its easily replaceable.  I heard that even the sceen is upgradeable.

the wireless and hibernate functionality are the most important to me, followed by the card reader.  I don't care too much about a webcam or finger print reader.  I'm actually surprised that a lot of laptops have problems with card readers, my desktop's card reader worked perfectly.

I was hoping that someone had purchased this laptop already and installed linux, but I can't seem to find anyone.  I'm debating just going for it and seeing what happens...  unless there's another laptop with similar functionality/price that works well with linux that anyone would suggest.

this is one of those times that I wish linux was more mainstream, so there'd be more support...

---

### Post by QuacoreZX on 2007-09-01
I'll be installing Ubuntu on mine soon, but for the moment I'm having so many problems with Windows Vista (and yes, I'm afraid I need windows for a few scholastic functions), so I'm reformatting straight to WinXP, then I'll repartition and add vista.  Hope to get back soon!

---

### Post by slade on 2007-09-01
for anyone who finds this thread, i might as well update:

I ended up going with a lenovo thinkpad T61p, and have fedora and sabayon on it already.  I have a few issues, but most things are working fine.  sabayon installed almost perfectly, whereas for fedora I had to change the SATA controller from AHCI to compatability, do a text based install, full system update, and install the proprietary nvidia driver before x would start.  i tried ubuntu, it would have required the same thing.  the computer works well with the IPW 3945 wireless card; as far as I can tell, the only piece of hardware that doesnt work is the intel HDA ICH8 audio card; alsa currently supports up to ICH7.

windows vista crashed and burned on me within 15 minutes.  i moved the system restore partition to an external hdd and resized the vista partition, only to learn that resizing it causes it to no longer work...  so I had to order the reinstall CDs.

---

### Post by NateMan on 2007-10-18
Got my c90s working great with Ubuntu. I did an alt disc install to get around the 8600gt, after that no problems with the install. The main problem was getting the wireless to work properly, which I'm hoping is fixed in gutsy. Haven't got the webcam or fingerprint reader to work, although I haven't put much work into it. Have not tested HDMI out or the Esata in linux. Fairly compatible with ubuntu. It runs Compiz-fusion and emerald very well. Great fast laptop.

---

