---
title: "Hauppauge HVR 4000 thread"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by speedytortoise on 2007-04-29
Since there hardly seems to be anything on the HVR-4000 on any linux site, and hardly anything on any site at all yet, I thought it best to make a new thread on installing this for linux.

So far I have managed to find a driver being written here: 
[http://linuxtv.org/hg/~stoth/hvr4000?cmd=summary;style=gitweb](http://linuxtv.org/hg/~stoth/hvr4000?cmd=summary;style=gitweb)

I've installed it by using the make all / make install and its installed nicely (I think).  I've managed to get Kaffeine to recognise there is a TV tuner there now, which is a step ahead of what I had before, and XawTV finds something, albeit a blue screen with no signal - again a step further from what I had before.  

The chap writing the drivers does say they are still in early development, so I'll be keeping a close eye on these.

If anyone has any advice or has actually got their card working it would be great to know :) 

In the mean time I'll post any updates on getting the thing working myself here.  

P.S I am a noob so this may take a while 8-[

---

### Post by MMoudry on 2007-07-27
Hey,
I tried to make this run on Feisty server 64 bit and so far I have managed to compile it, detect all the DVB-T channels, however after tuning to a channel and saving a stream there seem to be some sort of problem with it. I don't get a stream at all from /dev/dvb/adapter0/dvr0, it stays empty.

 I manage to save some data dvbstream however those data are unreadable even with VLC. I haven't tested all possible combiunations of configuration etc so I'll keep my findings posted here.

MM

---

### Post by MMoudry on 2007-07-27
All right I got my card working in 64 bit feisty server and DVB-T scheme. I am able to stream TV to all computers in my house (although I need to buy a new switch because the streams are eating all my bandwith). This card rocks :P

MM

---

### Post by zaziork on 2007-08-27
Have you managed to get the S-Video input working? I'm on Feisty but haven't had much luck with this card yet..

---

### Post by MMoudry on 2007-08-27
The S-Video input is not working from the sloth repository. There is however a patch that is available and when you apply it to the code repository and recompile the S-Video should work. I'll try to find this information for you, I've seen it on the site's mailing lists.

MM

---

### Post by zaziork on 2007-08-27
> **MMoudry said:**
> The S-Video input is not working from the sloth repository. There is however a patch that is available and when you apply it to the code repository and recompile the S-Video should work. I'll try to find this information for you, I've seen it on the site's mailing lists.

MM

Thanks, that'd be great. I have some stuff that I'd like to record from my Sky+ box (digital satellite PVR) to my Linux RAID, and that requires the S-Video. Last I heard, the Hauppauge cards still didn't have a decoder module or card reader for SKY's encrypted channels, which means I have to resort to connecting to the sat. decoder box via S-Video.

---

### Post by lorispadua on 2007-10-18
Maybe this can be  useful 

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/293961](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/293961)

---

### Post by zaziork on 2007-10-20
> **lorispadua said:**
> Maybe this can be  useful 

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/293961](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/293961)


Thanks for that. I'll have a go and post the results later. Do you have this card, and if so, have you managed to get the S-Video input working?

---

### Post by SeanHodges on 2008-01-03
Hey, 

I'm looking to get a second tuner for my MythTV box, and am hoping to get an HVR card this time around (to take advantage of digital AND analog input).

I'm interested how far you guys have got with getting this card to work? I'm prepared to do a bit of grafting to get the thing to work, but I'm hoping to hit the ground running, if you know what I mean ;)


Cheers,

Sean

---

### Post by greatone on 2008-06-19
to keep it up, i'm trying to install a hvr4000 on hardy (mythbuntu).
everythings fine. 
there's just a warning tdda9887 0-0043: i2c i/o error rc==121 (should be 4)
                       tuner-simple 0-0061 i2c ... same as above
but when i try to make a channelscan i become an error 
firmware timeout
cx24116 writereg:writereg error(err == -121, reg == 0xe0 value == 0x00
any hints?

---

