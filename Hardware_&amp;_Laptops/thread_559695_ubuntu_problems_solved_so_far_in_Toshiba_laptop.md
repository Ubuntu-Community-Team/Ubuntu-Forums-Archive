---
title: "ubuntu problems solved so far in Toshiba laptop"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by AnimateDeath on 2007-09-25
I will start this by saying that I am a complete noob to linux. I know nothing about how it works, or how to do anything with it. I have been a dos/windows user for 15+ years and have decided after multiple crashes with vista and the loss of a lot of important files and pictures, that i am going to go full Linux with Ubuntu 7.04.  I did a clean install of 7.04 and I will list my problems and soutions with my laptop. 

Toshiba Satellite A135-S4467.  This laptop has the Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz, the 945gm video card, the intel 82801G (ICH7 Family) High Definition audio.

My first problem was sound. I had none at all. After getting so mad that I thought I would explode I was finally pointed to this thread:  [http://ubuntuforums.org/showthread.php?t=539595](http://ubuntuforums.org/showthread.php?t=539595)   Following what he did step by step made my sound start working for mp3's and cd's.

My next problem, I had no sound when trying to view flash video.  I found this thread: [http://ubuntuforums.org/showthread.php?t=537070&highlight=no+sound+in+flash](http://ubuntuforums.org/showthread.php?t=537070&highlight=no+sound+in+flash)     Post #5 from "dentaku65" is what I used to make my sound work completely for everything. (Remember that this was done AFTER the previous post.)

I never had a problem with my video, network or wireless. They worked 100% from the beginning.

These are all the problems that I have had to overcome so far. I am sure there will be more to come since I know nothing of what I am doing. I'll keep this post updated with anything new as it comes. Hopefully this will help some people out. :guitar:

(a little side note: The sound works 100% but I still don't know how to stop the laptop speakers from running when I plug in my headphones)

---

### Post by AnimateDeath on 2007-09-27
Headphones wouldn't stop laptop speakers when plugged in.

The thing that fixed this for me is really weird and I can't explain it but it worked.

After trying forever to make the speakers stop when the headphones are plugged in, I got mad and shut off the laptop. When I had calmed down and started it back up again, I left the headphones plugged in to the jack (I normally never do this). Of course I hear the startup sound on the speakers even though the headphones are plugged in so I pulled out the headphones, started an mp3 and just for the hell of it plugged the headphones back in...... the laptop speakers shut off but the headphones continued to work. I unplugged the headphones and the laptop speakers come back on. Plugged them back in and laptop speakers shut off.

I had seen this being done to solve this problem in a post somewhere (I wish I could remember where it was now), but I dismissed it because I thought that there was no way that would do anything. I mean, it's a regular headphone jack, not usb or anything that would initiate change. But it did.

I decided it was a fluke so i wiped my HD did a clean install, updated, fixed my sound from the posts above, and had headphones and laptop speakers working at the same time. I restarted and still same problem.  I shut down, plugged in headphones, let laptop startup and logged in to ubuntu then unplugged the headphones, started an mp3, and plugged the headphones back in. The laptop speakers shut off and the headphones still worked...

So it wasn't a fluke...... I don't understand why that worked, but it did.

I called my brother (who is having the same problem) and told him about it. He tied it and it worked for him as well on a HP laptop.  I don't understand what makes this work, but it did.


**EDIT** I found the post that I got this from, I'll paste the post and link it afterwards.
 	
		
felmon davis   	
View profile
	 More options Sep 8, 1:10 am
Newsgroups: alt.os.linux.ubuntu, comp.os.linux.misc
From: felmon davis <dav...@union.edu>
Date: Sat, 08 Sep 2007 02:10:25 -0400
Local: Sat, Sep 8 2007 1:10 am
Subject: Re: headphones do not mute speakers [SOLVED]
Reply | Reply to author | Forward | Print | Individual message | Show original | Report this message | Find messages by this author

On Sat, 08 Sep 2007 01:50:41 -0400, felmon davis wrote:
> On Fri, 07 Sep 2007 22:39:56 -0400, Little Girl wrote:

>> A temporary fix that might get you through:

>> Type alsamixer in terminal.
>> Left and right key selects devices.
>> Use the m key to mute and unmute devices.

> naw, already been doing that blue in the face.

well, I am not sure what happened, I can only guess.

I compiled and installed new alsa drivers and fiddled with the alsa-base
config file, but no go.

I followed a tip in one of the links you provided where a person rebooted
with the headphones plugged in. when I did that, it worked!

and now I don't need to have the headphones plugged in at boot. I get
sound from the speakers with headphones unplugged but the speakers go mute
when the headphones are plugged in. that is what I wanted.

here is my guess: probably (!) rebooting after the driver install put in
the fix. (perhaps just restarting X would have sufficed, I cannot tell.)

anyway, I am relieved. thank you for those tips!

Felmon

Link:  [http://groups.google.com/group/comp.os.linux.misc/browse_thread/thread/08ffde1895f95655/0ea1e076865fe2eb?lnk=raot](http://groups.google.com/group/comp.os.linux.misc/browse_thread/thread/08ffde1895f95655/0ea1e076865fe2eb?lnk=raot)

---

### Post by jcsteele on 2007-09-27
AD,

  I have a similar notebook to yours, and the sound problem was an issue with 7.04, however It has since been fixed and a fix should be available, if you update your machine (works for me: sudo apt-get update && sudo apt-get upgrade && sudo apt-get install linux-686)

---

