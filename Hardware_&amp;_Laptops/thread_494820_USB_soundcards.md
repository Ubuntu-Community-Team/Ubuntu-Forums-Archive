---
title: "USB soundcards"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by smbm on 2007-07-07
Hi

Can anyone recommend a decent quality USB soundcard that works with Linux?

Has anyone had much luck getting this to work?

[http://www.m-audio.com/products/en_us/Transit-main.html]("http://www.m-audio.com/products/en_us/Transit-main.html")

Thanks in advance

Tom

---

### Post by talava on 2007-07-07
According to alsa, most standards compliant USB soundcards should work right out the box. Another question is how to know which sound cards are standards compliant since most manufactures just say their product works in XP and/or mac? Is a sound card that doesn't need drivers in XP standards compliant? I'm interestid in getting a sound blaster external sound card.

Alsas generic install instructions for non-compliant cards:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=USB&card=Generic&chip=Generic&module=usb-audio](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=USB&card=Generic&chip=Generic&module=usb-audio)

---

### Post by smbm on 2007-07-07
thanks for your reply. 

I've tried a quick google search to no avail. Will try again with more specific search terms.

If anyone else thinks of anything please let me know.

Cheers

Tom

---

### Post by paulg on 2007-07-09
The Transit works. See [here]("http://ubuntuforums.org/showthread.php?t=466667&highlight=Transit") for install instructions. 

I have heard that more current versions of the MobilePre have been USB class compliant and have worked fully without installing anything. The Transit may have undergone a similar update from M-Audio but if not the firmware loader should work for you by following the directions above. I know as a minimum [winston84]("http://ubuntuforums.org/showthread.php?t=492468") has his Transit working now but I am sure there are others.

---

### Post by talava on 2007-07-11
I just got home with my Sound Blaster connect usb sound device and it is working like a charm.

---

### Post by LDRoamer on 2007-07-11
I just got a turtle beach audio advantage micro and it works fine with fiesty. I had to go and change my sound over to usb audio under system -> preferences -> sound but other than that all I had to do was plug it in. Not all its features are recognized but it does work as a basic sound card. It has a S/PDIF out but I don't think it works without the right driver (which I suspect doesn't exist in the Linux world). It is pretty cheap (I think about $30 US - I paid $39 CDN). I got it from TigerDirect. The reason I got it was because fiesty broke the es1869 sound on my ancient Compaq laptop. This way I get sound albeit only with external speakers or headphones.  It sounds better to my ears than the onboard sound so that is good.

---

### Post by LDRoamer on 2007-07-11
Just an update. While I do have some sound it seems that not everything is working properly. For example I can play MP3's but system sounds don't work. I will investigate further and if I get it working fully I will post (I am talking here of the turtle beach usb card mentioned in my last post).

---

### Post by smbm on 2007-07-12
Hi, thanks for all your replies.

I've been looking into this in a little more detail and it seems that some cards are more hassle to set up than others etc. I've decided the Edirol UA-1EX  would be quite a good option given my budget:

[http://www.dv247.com/invt/30313/]("http://www.dv247.com/invt/30313/")

Any opinions?

Cheers

---

### Post by LDRoamer on 2007-07-13
I got my Turtle beach audio advantage usb card working fine. It was really quite simple once I found the solution (as most things are!).  My problem was that the card was not set as the default card despite being the only one in the system (I disabled the on board sound chip as it doesn't work in fiesty at this time - its an es1869).  What you need to do is the following (copied from another post):


had the same problem with my USB speakers, and after much searching found this solution:
Code:

asoundconf list

your USB headset/speakers should be in there (mine were just called "Audio"), now:
Code:

asoundconf set-default-card Audio

replace "Audio" with whatever your device is called. Now reboot and you're done.
__________________


I did this and everything now works perfectly. In my case the turtle beach card showed up as "default".  I thought this was not a reference to the card itself but the fact that there was a default card in the system. I was wrong. It was actually the name of the card. I enabled the es1869 and sure enough it showed two sound cards in my system, one the es1869 and the other just called "default".  I deduced that even though it was the only card in the system it was still trying to play system sounds through the on board card even though it had been disabled. Of course I wouldn't have had to find out all this if Fiesty hadn't broken my es1869 chip but that is a tale for another day.

---

### Post by djbon2112 on 2008-05-02
I got the Turtle Beach USB audio card, and I'm trying to get it working, however it doesn't appear to show up anywhere. asoundconf list simply lists my onboard (Intel onboard) but not the Turtle Beach. Any suggestions?

---

