---
title: "Garbled sound in 11.10, Thinkpad t60"
date: 2011-10-16
forum: Hardware
---

### Post by kolinab on 2011-10-16
I'm having problems with sound on my Thinkpad t60 - I've filed a big report:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370)

Sound is perfect in a new session, banshee, movies, flash audio, etc. is all great. I can listen to Banshee in the background no problem for 30 minutes or more. But once I try to do something else like open another application (in addition to firefox) the sound becomes garbled, 'burpy', I think the speed might even change very slightly.

A restart solves the problem for a short while.

Sound for me was perfect under Natty. The only sound related tweaking I have done is one small simple tweak described [here]("http://ubuntuforums.org/showthread.php?t=1858508") to enable the volume control buttons to work for me.

Anyone else experiencing something similar? I'm about to start troubleshooting as per instructions the [Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"). Any other troubleshooting advice?

[edit] I've done a completely clean install of the full release version 11.10 . . . - testing now . . . I'll slowly continue tweaking this install until I get it how I like and post results.

Strangely, I have NOT added ubuntu-restricted-extras and my system plays .mp3 fine. I thought it was required?

I have also realised that my thinkpad volume control buttons DO work out of the box, I just can't see what audio level they are controlling. I have my main sound now set to the unamplified level and so far things sound OK.

Everything WAS working fine - I had banshee playing mp3s in the background, then I took a skype call, paused banshee, and skype worked well for a time until I opened the dash to look for something and . . . then the sound started burping and garbling as before. I thought I had it fixed.

Sorry to bore you with the monologue but I'll post the results of my further troubleshooting here.

[edit 2] Now that I have my ears tuned to it, I hear the noise/interference almost all the time. Just scrolling up and down in a text file is enough to produce horrible interference/garbled sound. This is an absolute showstopper for me so I'm rolling back my main system to Natty. I'll monitor my bug report and watch for people having similar problems, hopefully it can be resolved. I realise this is early early days of the full deployment of Oneiric to the masses so I'm hopeful for a solution.

---

### Post by Noak on 2011-11-19
I'm having the same problems with my T60. Just like for you,the sound was A OK in natty, but now I have the exact same problems you describe here. Sound card on this one is an Intel HDA AD1981. Hope someone will figure out how to solve this because I am not knowledgeable enough about this myself.

---

### Post by taste of mint on 2012-03-29
I can haz the same problem with my t60? it has a radeon x1300 or something.

I have the same problem with both ubuntu and mint, first and foremost the volume control (using the mouse) goes from 0-100% and that part is labelled "unamplified" and you can push it about to 60-65% of the scale into the amplified part on silent stuff, like a silent youtube vid. Its a kind of weird function where you can actually overdrive the cirquits, but on vey silent videos it comes in handy. The downside is that on almost everything its very silent if you set it on 100% or the limit of the "unamplifed" part. Its nowhere near 2volts on 100% of unamplified. 

Turning it up to 100& of the amplified part results in massive noise and massive distortion. 
however this is die to the Connexant crap soundchip letting ubuntu do this, the connexant chips suck *** compared to even the cheapest realtek chips unfortunately. AND they induce/are sensitive to ground loops and what I guess is broadband noise emanating from the mains or whereever, probably from inside the computer too, this noise gets worse when the ground loop thingie starts to affect things. 

Its a very sorry *** construction if you ask me, and the whole computer is emanating lots of ultrasonic pwm/switching noise of very high amplitude like 10cm around it, and extremely high amplitude right above it. You would not believe!!

Also I have a few other problems which I am 100% sure you guys have too. First the sound "deteriorates" seemingly, of course this is not hardware related its software related or possibly driver or firmware-related. Its so strange, some youtube videos are 100% good sound quality and some of them (and its purely random, but always the same ones) are like 50% deteriorated. First I went nuts, what the hell is that!! But moving on to a new video its just like normal. I think this is flash related, I'm almost certain of it, or its implementation or something, I'm no scientologist.

EDIT: Yeah about the sound. I have noticed that even if a youtube video really sucks audiop quality wise, that deteriorated sound. If I'm streaming some audio with the movieplayer or whatever the default player is, or running audio with any audio player locally that audio is still good (unless you overdrive the chip that is, can't get around that), so this is flash related in some way.

Also I experience random logouts, and sometimes the whole computer restarts, and I can actually provoke this just by going to certain forums, and its 100% certain the computer will randomly shut down in one way or another within 30 seconds. The fault seems to be "pixbuf overflow" or some other crap. No one here on these forums knows how to fix this so your best be is to ditch the t60. you will never ever getting working good, it does not matter which ubuntu version you run. Hell I have at least 40 different distributions and they all play very bad with the t60 in one way or another, and all of them are totally unacceptable.

The t60 does not work with linux, any linux!

I have a t400 with intel graphics and that one works very good with all linux versions i've tried and all variants. I recommend getting a t400. Its absolutely flawless with 10.4 and mint 9.

The t60 seems to be a "problem model" even with windows.
I have no solutions! Instead I recommend you to change the computer and t400's are cheap now, costs almost nothing, and its a better functioning computer but much worse built mechanically. Thats the price you pay.

I'm installing xp on my t60 tomorrow, I hope it works better. Its actually made for that OS so I hope it does.:popcorn:

---

