---
title: "Sound Problems with your LAPTOP ...?"
date: 2008-08-24
forum: Hardware
---

### Post by lobo_blanco on 2008-08-24
Hi All,

First, I'd like to thank those who have contributed to this forum, there will always be common issues that need to be resolved and through your efforts and contributions here, you've made life a lot easier for newbies and seasoned Ubuntu users alike - THANK YOU!u

For the record this is my setup:
Ubuntu 8.40 dual boot with XP (I hope to soon abandon XP entirely, as soon as I get my business finances into GnuCash and learn to use it effectively)
Sony VAIO, VGN-FS920 laptop.

I love UBUNTU and have found the transition from XP to Ubuntu an easy one in most respects. I have, however, had problems getting the audio to work for both DVD's and in Firefox 3.

It's my understanding that the sound issues with Firefox are Flash related but also due to my onboard sound card (Intel 82801FB HDA).
I have also found that many laptop users have been experiencing these problems.

Well, you guessed it, the answer may be right here on this forum.
I tried a lot of tips but had no luck until I found the following link.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I think you'll find that this link applies to many laptops.
By following the tutorial step by step I was able to get my Sony VAIO laptop sound working great with DVD's, Pandora, and in Firefox. (It's a fairly lengthy resolve but well worth it if it can solve your laptop sound problems.)

Some highlights of my experience. I think there may be a typo or two in the commands given and after downloading the suggested files, you will need to be sure that you get them into the ALSA folder to proceed with the command line instructions, but most is common sense and should be fairly obvious once you embark on journey through this tutorial.

I've found that if something doesn't work or make sense then I usually just back up a move and figure out what the problem is. The important thing is to work through the information and use your common sense and you'll do fine. ( After all, if I can do this as a newbie, you can too)

Note: Even though my laptop is a Sony, I ended up using the Acer configuration to get Alsa to work (It is clearly suggested that for laptops try the acer model - you'll see what I mean when you go through the tutorial).

I also had to change the Firefox settings.
FIREFOX_DSP="aoss" 
sudo gedit /etc/firefox/firefoxrc

Make sure to do a reboot and also make sure all sound settings are in Autodetect rather than OSS or other.

I ended up using Kaffeine for DVD's which seems to work better for me than Totem. I had to make sure the settings in Kaffeine were set to 'auto' also for things to work properly.


I appologize if this post is not clear and concise about the whole process, but if you go to the link that I list above, I think it spells out most of what I had hoped to get across to those of you who have tried numerous ways to get your sound working, but have, so far, had little luck.

Good luck and have patience. This link should get Alsa working for you and the end result emulates 'oss', so it should cover the bases in getting your (laptop) sound working. Worked for me and I had tried various other fixes with no luck.

Dave

---

