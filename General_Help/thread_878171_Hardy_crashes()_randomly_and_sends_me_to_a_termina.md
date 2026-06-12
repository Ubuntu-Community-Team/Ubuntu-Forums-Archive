---
title: "Hardy crashes(??) randomly and sends me to a terminal looking screen"
date: 2008-08-02
forum: General Help
---

### Post by djrobthaman on 2008-08-02
Hi,

I'm running hardy and have encountered a problem that I'm not sure how to fix.  The session randomly just ends and I see the screen in the image that I've attached.

It's the screen that usually shows up when I press ctrl alt backspace, right before it goes to the log in screen (or at least it did in gutsy, haven't been running hardy very long and I haven't quite done that yet).  But in this case, it just stays there and does nothing else.

It seems to be pretty random, but at the same time always happens when I do something(eg.  this last time it happened when I pressed play on a myspace music player,  I remember also that it happened once when I moved the mouse to the corner I set up for the scale compiz plugin).

Anybody encounter this error?  Any idea on how I can fix it?

Thanks

---

### Post by djrobthaman on 2008-08-02
It happened again just a while ago (that's twice within as many hours).  This time I dragged an icon across my desktop from my tv to my monitor (I have big desktop set up on my ati x1300).  I don't know if there is any connection between these actions that cause the error, but one thing that was different was that this time it went all the way to the ubuntu log in screen so I didn't have to actually hit the restart button.

---

### Post by djrobthaman on 2008-08-11
So, I disabled big desktop a while back, thinking that that was the problem.  I guess I was wrong, because I just had another crash when I clicked my Show Desktop button.  No clue what the problem could be.  Looked at my system log and though I'm not sure if the time syncs up with the crash, I have an error message from pulse:

"pulseaudio[6345]: main.c RLIMIT_RTPTIO failed: Operation not permitted"

Could this be it?  If so, how do I fix it?  If not, how do I fix it?

Any help would be great.
Thanks

---

### Post by Crafty Kisses on 2008-08-11
That's either a video card issue, or your computer is overheating.

---

### Post by lavinog on 2008-08-11
Do you know what video card driver you are using?
Are you using the restricted driver?

---

### Post by djrobthaman on 2008-08-11
Well, I never had this problem running gutsy/feisty, and I'm pretty sure I'm not overheating (no real hard data on that though... could you suggest an easy to configure program to double check that, installed x-sensors but I haven't got it to work yet).

As for the video card, I'm using an [ATI Radeon X1300 256MB All In Wonder]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102661") and ,yes, I am using the restricted drivers

---

### Post by lavinog on 2008-08-11
hardy/gutsy/feisty all had different versions of the restricted drivers.
experienced has shown me that newer drivers can have more bugs than previous.
the hardy repositories use catalyst 8.3
8.7 is the most current and works fine for me.
8.4 and 8.5 worked fine for me too, but 8.6 made my system extremely unstable.

There have been a couple of bugs with ati's driver in the past that affect the cooling fan.

---

### Post by djrobthaman on 2008-08-17
Could you point me to a good set of instructions on installing 8.7?  I tried last night, followed ati's installation instructions and got it installed, but on compiz start up had the wsod.

---

### Post by DeathOnJuice on 2008-08-17
When you're at that terminal screen, try pressing Ctrl-Alt-F7 to take you back to X. If X actually crashed (which it probably did), this won't work. Do the same command but with another F key - say F2 - then try logging in and typing:

sudo /etc/init.d/gdm start

Hopefully that should get you graphics back without a restart. If not, it may provide some insight as to what is happening.

---

### Post by lavinog on 2008-08-18
> **djrobthaman said:**
> Could you point me to a good set of instructions on installing 8.7?  I tried last night, followed ati's installation instructions and got it installed, but on compiz start up had the wsod.

first prior to starting compiz make sure 3d works by running glxgears
also make sure you removed xserver-xgl since the new versions of fglrx no longer require it for compiz. Make sure compiz is the most up to date.

---

### Post by djrobthaman on 2008-08-18
lavinog - don't have xserver-xgl installed (figured that one out early, all that package does now is slow things down to a stand still)

deathonjuice - reverted to the ati driver in the hardy repos, so compiz is working again.  Don't think x actually crashed though, because if I typed "alt+f2" then "metacity --replace", even though I couldn't see anything while I was doing it, the white screen went away and I could see the desktop and everything on it.

---

### Post by lavinog on 2008-08-18
When the most recent driver was installed, did your X session crash (the original issue)

Also I had something similar happen to me last night: I was trying to play a dvd. I guess it was either too scratched up or not playable in linux, but the video was all garbled and about 3 secs into it, it stopped playing and X crashed. It automatically switched me to tty1 if I alt-f7 I got a black screen.

---

### Post by Ifrgtmyname on 2008-08-19
Same problem here, only started recently though, after running hardy since the week it was released it appears to be completely random. Sorry I can't be much help but I have nVidia onboard graphics and am using the restricted drivers, i'll be keeping my eye on this thread so feel free to ask any questions.

---

### Post by djrobthaman on 2008-08-20
lavinog - Don't think x actually crashed because if I typed "alt+f2" then "metacity --replace", even though I couldn't see anything while I was doing it, the white screen went away and I could see the desktop and everything on it and was able to operate everything like normal (except of course compiz).

---

### Post by lavinog on 2008-08-20
> **djrobthaman said:**
> lavinog - Don't think x actually crashed because if I typed "alt+f2" then "metacity --replace", even though I couldn't see anything while I was doing it, the white screen went away and I could see the desktop and everything on it and was able to operate everything like normal (except of course compiz).

No, I was referring to the original issue in your first post.
> The session randomly just ends and I see the screen in the image that I've attached.
Did X randomly exit with the latest fglrx driver and compiz dissabled.
If the latest driver fixed that problem, that could point to the solution to fix it...the white screen issue should be treated separately.

---

### Post by djrobthaman on 2008-08-20
oh.. i see, sorry :)
It didn't randomly exit, but I don't think I used the driver for more than 2 or 3 hours before I reverted.  So, it also could have just not showed up.

But, maybe we can assume that it did fix the crashing problem and try to address the white screen (if that is addressable).  What do you think?

---

