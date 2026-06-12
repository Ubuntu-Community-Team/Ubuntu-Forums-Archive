---
title: "Firefox causes full system freeze (hardy)"
date: 2008-09-25
forum: General Help
---

### Post by jayde_drag0n on 2008-09-25
every day. and sometimes several times in a day  firefox will freeze my entire system.. i don't mean firefox is unresponsive.. i mean no mouse movement, hitting ctrl+alt+f1 will NOT take me to the terminal screen so i can run killall.. no amount of keystrokes.. mouse commands will gain a response from my computer.. no options except to reboot.. this is REALLY irritating to say the least.
AMD 1.5GHZ
512MB Memory
80GB HD

---

### Post by lehvrhon on 2008-09-25
I have also experience the same, :(  I have also notice I run firefox everytime my sytem freezes, all I do is restart my system manually,,:(

---

### Post by cjpetrie on 2009-01-05
Same here, about once a day when loading with multiple tabs. First Firefox seems to freeze, then even the mouse. The only option is to power down
manually.  All software is up-to-date. In fact, I am now running Ibis
and the problem persists.

This is a serious problem. Is there no fix from the community?

---

### Post by albinootje on 2009-01-05
Try again with :
```

firefox -safe-mode

```
to find out whether it is really Firefox or Firefox add-ons and/or themes.
Do these crashes happen related to flash movies with sound or not ?
Did you run a memory test on your RAM memory ?
Can you post the output of :
```

dmesg

```

---

### Post by ithanium on 2009-01-05
try disableing all addons and enableing the one by one, maybe one of them causes your system to crash :| It also happened to me with a automatic reload addon

---

### Post by rwill19050 on 2009-01-05
Me too, it happens when trying to view a video on the BBC news site.
It causes a crash (screen turns monochrome) and won't allow me to shut it.
Have to log off and start again.
Had a play around, it seems that if you interrupt a playing video that causes a crash.
I had disabled the Windows Media player add-on in Firefox, but notice that the player on the videos for BBC site is Adobe. 
So, kind folks, any ideas please, I am new to Linux and am finding it a bit daunting in the 'terminal'
Still having a problem setting up our Skype webcam as well, (worked a treat in XP) but that is another problem :(

Richard

---

### Post by rwill19050 on 2009-01-07
No Answer, came the stern reply......   :(

So, here is another reason for newcomers to be very afraid of Linux.  :confused:
While 'they' all shout about the joys of 'Open Source' it seems the truth is that we (the uninitiated) are in the lap of the Gods. They may deem to help, but then perhaps not. :(
Looks like Microsoft XP is going to get another go  with me, as I need a properly working machine to work with. 
Shame about that.
I'll keep an eye on the news, see if anyone comes up with a solution to the difficulties we have encountered, in the meantime, back to the XP camp for me I'm afraid, (and there was me believing all the great things said about Linux).




> **rwill19050 said:**
> Me too, it happens when trying to view a video on the BBC news site.
It causes a crash (screen turns monochrome) and won't allow me to shut it.
Have to log off and start again.
Had a play around, it seems that if you interrupt a playing video that causes a crash.
I had disabled the Windows Media player add-on in Firefox, but notice that the player on the videos for BBC site is Adobe. 
So, kind folks, any ideas please, I am new to Linux and am finding it a bit daunting in the 'terminal'
Still having a problem setting up our Skype webcam as well, (worked a treat in XP) but that is another problem :(

Richard

---

### Post by adamlau on 2009-01-07
Believe the hype, rwill19050, believe the hype. Linux, Windows, Mac OS X (I run all three both at home and work), the deduction methods for Firefox issues are always the same. Back up and create a new profile. Scour the support sites of the various plugins you use for bug reports and the like. Verify you are using the latest version of Firefox. Try Konqueror and/or Opera. Visit mozillaZine Forums.

---

### Post by hangfire on 2009-01-07
> **rwill19050 said:**
> No Answer, came the stern reply......   :(


Wrong. There are suggestions to remove all add-ons and add them back in, if you wish, one at a time.

> **rwill19050 said:**
> 
So, here is another reason for newcomers to be very afraid of Linux.  :confused:

Shall I rant about the problems encountered with Firefox, or dare I bring it up, IE, on XP? No, I'll spare us.

Please spare us yourself.

> **rwill19050 said:**
> 
While 'they' all shout about the joys of 'Open Source' it seems the truth is that we (the uninitiated) are in the lap of the Gods. They may deem to help, but then perhaps not. :(

Guess what, the FREE support process for commercial software is the same as the FREE support process for FF & Open Source in general. You surf Google, you post on forums.

You can pay money to log an issue with Microsoft. They will tell you to reinstall, close the ticket, and take your money.

With FOSS you can find (with a minimal effort) the developer's website and actually log a bug report that will be tracked to some conclusion. Try that with Microsoft.

> **rwill19050 said:**
> 
Looks like Microsoft XP is going to get another go  with me, as I need a properly working machine to work with. 

Good luck, and don't let the door hit you on the way out. If you change your O/S every time you run into a problem, you'll run out of operating systems pretty quickly.

-HF

---

### Post by adamlau on 2009-01-07
rwill19050: Don't despair! If one source does not provide an answer, look towards another avenue of support. Thousands, perhaps millions of people use Firefox on a daily without issue. And just as many use Linux with nary a hiccup for perosnal and business production every day. You can be one of them.

---

### Post by rwill19050 on 2009-01-07
> **hangfire said:**
> Wrong. There are suggestions to remove all add-ons and add them back in, if you wish, one at a time.



Shall I rant about the problems encountered with Firefox, or dare I bring it up, IE, on XP? No, I'll spare us.

Please spare us yourself.



Guess what, the FREE support process for commercial software is the same as the FREE support process for FF & Open Source in general. You surf Google, you post on forums.

You can pay money to log an issue with Microsoft. They will tell you to reinstall, close the ticket, and take your money.

With FOSS you can find (with a minimal effort) the developer's website and actually log a bug report that will be tracked to some conclusion. Try that with Microsoft.



Good luck, and don't let the door hit you on the way out. If you change your O/S every time you run into a problem, you'll run out of operating systems pretty quickly.

-HF
I notice your comments come, not to assist, but to berate, well, yes thanks for that *assistance*, and f**ck you too, smart a**e
Just remember, out here are a lot of 'old' people (me at 64 years old and still trying) trying their best, and smartypants big headed comments like yours give the open source community a bad name.
Are all you Linux aficionados as bad as that, or is it just this big head?
Yes, I'll get chucked of this forum for my comments, but quite honestly, I can't be bothered the likes of you, life is too short, so no loss for me.
I would like to thank those who had *useful* suggestions to make, rest assured. I will be giving them a go.
And may you all be spared too many of the know it alls, like to show it alls.

---

### Post by dadozgb on 2009-01-07
> **rwill19050 said:**
> 
Just remember, out here are a lot of 'old' people (me at 64 years old and still trying) trying their best, and smartypants big headed comments like yours give the open source community a bad name.
Are all you Linux aficionados as bad as that, or is it just this big head?

There is no need for calling names. GNU/Linux is not OS for everyone. It's great OS, by my opinion far better than windows but it is not for everyone. Your problem is not caused by firefox than by a display driver or flash player and maybe combined both. Linux is a free OS but it's not a free lunch. To get best of it you have to know it. The more yu know it the more it will give you. And that's all.

---

### Post by hangfire on 2009-01-12
I help everyone I can, just check out my posting history.

I just get tired of the noobs berating Linux (and threatening to go back to Windows) because no one answered their question immediately.

Take a moment and read your own attitude in this thread. You complained after getting help... and ignoring it... what's up with that?

-HF

---

