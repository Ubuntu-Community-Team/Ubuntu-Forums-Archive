---
title: "Lenovo 3000 V100 : no documentation in wiki ?"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by Plume on 2007-02-24
Hello,

I am a future user of ubuntu, searching right now for "the" laptop that will suit me : its main features should be a good compatibility with ubuntu (I am an absolute beginner) and to be compact and lightweight.

The lenovo 3000 V100 looks really fine to me... but I can't find it in the wiki list of laptops. Still, I found on the forum that some members seem to have it. 
So, would it be possible that you, happy/unhappy users of this notebook, give me your opinion on

- how the install of ubuntu was ? (problems with sound, wifi or so ?)
- how it is, in general : battery life, components quality, etc. (in particular, I am worried by the mirror-like screens : is this one really shiny ?)

In short, would you advise it to an absolute beginner of ubuntu who will use for simple applications (internet, latex and openoffice, mainly).

Thank you in advance for your comments.

---

### Post by cmavr8 on 2007-02-28
Hi, I have Lenovo 3000 V100 for 7 months and running Ubuntu on it from the first moment. (Ok, I run windows for the first minutes to enjoy IBM utilities...)

I have had problem finding other people with Ubuntu on this laptop...

Anyway, with the current version of Ubuntu (edgy eft 6.10) my wifi is working almost perfectly. (I'll explain later)

Sound is strange. It works every two reboots, then doesn't work for another two reboots, then works again etc.

Standby works ok. Actually, standby FIXES sound and Wifi problems! So If I boot and I have no sound, I standby and wake it up immidiatelly and I have sound.

Wifi works on every boot, but not always after waking up. So I go in standby and wake up and it then works.

Standby used to crash by pc sometimes (could not standby, just blank screen for hours. ALT+PrtSc+S+U+B needed to reboot) but it's been a while... Maybe the new kernel resolved this.

Otherwise volume controls work perfectly, dual cores recognized outofthebox.
Hibernate works but not always.
Now, some usb devices have problems after resuming from hibernation.
The camera does not work and needs lots of work to make it work (if it can be done) from what I read. Fingerprint also needs work but can be done from what I read. (haven't tried yet)

What else do you want to know? Battery consumption on standby is 5%/hour I think.
Battery lasts the same as in windows I think.

Maybe I should email to the guys moderation the wiki... But they'll want confirmations so I don't have time for this... I'll just report in this thread.

I have a document where I note anything I should do to a fresh Ubuntu install in the V100. Let me know if you guys are interested...

I hope I help..

---

### Post by Plume on 2007-03-01
Thanks ! it's just what I wanted to know. I am a bit worried by the sound problems but will go for the adventure anyway (ordered this V100 yesterday).

I plan to install the dapper version, normally. If too many important things don't work I will switch to edgy (and feisty is not far...). 

Concerning your document for a fresh ubuntu, yes, I am interested ! 

Thanks again for your reply.

---

### Post by david2b on 2007-03-01
> **Plume said:**
> Thanks ! it's just what I wanted to know. I am a bit worried by the sound problems but will go for the adventure anyway (ordered this V100 yesterday).

I plan to install the dapper version, normally. If too many important things don't work I will switch to edgy (and feisty is not far...). 

Concerning your document for a fresh ubuntu, yes, I am interested ! 

Thanks again for your reply.


Thanks!!!!
I've just received a v100 today, and plan to install edgy or feisty. I'm interested by your document for a fresh ubuntu
TIA

---

### Post by cmavr8 on 2007-03-01
> **Plume said:**
> Thanks ! it's just what I wanted to know. I am a bit worried by the sound problems but will go for the adventure anyway (ordered this V100 yesterday).

I plan to install the dapper version, normally. If too many important things don't work I will switch to edgy (and feisty is not far...). 

Concerning your document for a fresh ubuntu, yes, I am interested ! 

Thanks again for your reply.

Sound is not giving me too much trouble... Standingby and resuming is easy.
Webcam and standby/hibernate problems make me sad... But we'll fight them!
Why not edgy from the beginning???

---

### Post by Plume on 2007-03-02
> **cmavr8 said:**
> 
Why not edgy from the beginning???

Errr
1) because I have a cd of dapper already
2) because I am an absolute beginner and was told that the dapper drake is better than the edgy eft, for those who don't want to spend too much time "fighting" with their os.

But I can still change my mind, especially if you tell me that certain functionalities work better with edgy. So, would you suggest to install edgy instead of dapper ? In graphic mode or alternate ? And by the way, is the hard drive of this V100 "one piece" or already with 2 partitions ?

Thanks !

PS : I will have loads of time to prepare the install because my laptop will arrive only in 1 or 2 weeks (because I asked for a keyboard that's not in stock)...

---

### Post by david2b on 2007-03-02
First boot with Feisty live CD. Most of hardware seems to work.
Sound : ok
touch pad : ok
wifi : not tested, but recognized, and seems to be ok
ethernet : not tested, but recognized


Don't know how to refuse Vista licence, but once it's done, I'll install Feisty!

---

### Post by david2b on 2007-03-04
ok, i've just installed feisty (herd 4).

Wifi is ok ! No problem to connect
Sound is strange : everything was playing ok with the live CD, and it doesn't work anymore since ubuntu is installed
I don't dare to upgrade to herd 5!!! ;-)

---

### Post by cmavr8 on 2007-03-04
If you reboot one or two times?Does it work then?

Any problems with suspend/hibernate?
No camera, right?

---

### Post by david2b on 2007-03-04
no more sound, even with 10 reboot. I've tried to disable modem in bios, but laptop didn't boot!
suspend / hibernate not tested.
I'll plug my EOS Digital Camera tomorrow.

Any idea for sound ?

---

### Post by cmavr8 on 2007-03-04
Tried disabling ESD from sound options?
Did you play with the settings in the first tab of sound preferences?

---

### Post by hey560 on 2007-03-04
david2b:

I got sound working with my N100 which has same sound card as you and same issues with edgy.

You have to recompile ALSA with latest version and add a compile flag for our sound card:

[http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel)

Check it out, its not hard at all to do if you've used console before.

---

### Post by cmavr8 on 2007-03-04
Ok, here's the ODT file, as promised.

It contains the changes I do in a fresh ubuntu install. DO NOT do everything that I do. Be skeptical. Just grab the idea, google it, and if you like it use it.

I have no responsibility for damage you do to your working OS while following my notes.

Remember: It's just MY notes. It's not a formal document.

Gray sentences mean you don't need to do this in Ubuntu 6.10.

---

### Post by david2b on 2007-03-05
suspend / hibernate works perfectly ! (Lenovo 3000 v100 with Feisty Herd 4)
I've plugged my EOS Digital Camera.... ubuntu sees it : "would you import photos ?" , i said "YES" but nothing comes after.

No more sound at all.
I'll check it today

---

### Post by david2b on 2007-03-07
Sound is working!!! You have to activate modem in bios. Boot sequence is longer, but worthy ;-)

---

### Post by mahershi on 2007-03-24
Hi! You can check my Lenovo 3K V100 install notes on my blog:

[http://srmiocc.blogspot.com/2007/02/ubuntu-everywhere-well-almost.html](http://srmiocc.blogspot.com/2007/02/ubuntu-everywhere-well-almost.html)

Mahesh

---

### Post by cmavr8 on 2007-03-29
It's unbelievable but I managed to get my sound working right after MONTHS of searching...
It was just 
    * sudo aptitude reinstall alsa-base
    * sudo aptitude reinstall libasound2
but I think I have done it already once or twice...

Maybe the third time was needed...

---

### Post by q335r49 on 2007-04-10
Hi guys, I've been following this thread and thinking of buying a V100.  Have you guys had any problems as this chap has had?

[http://ubuntuforums.org/showthread.php?t=381611](http://ubuntuforums.org/showthread.php?t=381611)

It seems that CPU frequency scaling works, but that the fan doesn't work?  Has anyone had any problems with this -- i.e. it running really hot?

---

### Post by cmavr8 on 2007-04-11
My sound is broken again! No fix found...

q335r49, I don't think I have problems like these..
My temperatures are almost always below 70 degrees celcius.

Exception: [http://ubuntuforums.org/showpost.php?p=2430130&postcount=12](http://ubuntuforums.org/showpost.php?p=2430130&postcount=12)

---

### Post by cmavr8 on 2007-04-23
Upgraded to Feisty Fawn 7.04.

Sound even worse now. Skype won't recognise my sound devices. Avidemux won't play audio ("trouble initializing audio device" error when ALSA is selected, no error, no sound when DUMMY selected) and Totem Movie player won't start (crashes on start).

reinstalled audio device but nothing changed...

Rhythmbox plays music normally

---

### Post by Plume on 2007-04-29
Hi,

I installed Feisty this morning (my first Linux !) and it worked really fine.
There is sound and hibernation worked (I tried once only...). 
Of course integrated camera is not recognised. The only problem I noticed until now is that the headphones don't turn off the speakers... I hope it can be fixed somehow.

I guess the more I will use it, the more troubles I will come into. And you will problaby hear about it :-) But whatever, it is much better than vista's dictatorship !

---

### Post by cmavr8 on 2007-04-29
Yeah, vista must vanish.

I haven't heard of that problem on feisty/V100 yet...

My sound seems to work good now (after restarting 5 times after upgrading)...

---

