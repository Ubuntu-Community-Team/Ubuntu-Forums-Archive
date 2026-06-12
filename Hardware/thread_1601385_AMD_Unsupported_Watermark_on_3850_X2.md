---
title: "AMD Unsupported Watermark on 3850 X2"
date: 2010-10-20
forum: Hardware
---

### Post by BlueBoden on 2010-10-20
I'm using the proprietary driver which came with Ubuntu 10.10.

Everything seems to be working, even the advanced desktop effects, including compiz.. etc
The only problem I'm having, is this nasty logo at the bottom right corner.

I've tried to replace the control file, with one from the 9-3 drivers. This did not work.

I also tried to follow the instructions found on [http://ubuntuforums.org/showthread.php?t=1284491](http://ubuntuforums.org/showthread.php?t=1284491)
Replacing the control and signature files with those found in 10-9. This also didn't work!

---

### Post by P4man on 2010-10-20
From the catalyst 10.9 release notes:
[I]Note: The ATI RadeonTM HD 3870 X2 series of product is currently
not supported by the ATI CatalystTM Linux software suite.[/I]

Are you sure you are actually using the restricted drivers? Jockey saying they are installed doesnt mean they are loaded. Can you use the catalyst control center?

FWIW, you can use compiz just fine with the opensource drivers.

---

### Post by BlueBoden on 2010-10-20
> **P4man said:**
> From the catalyst 10.9 release notes:
[I]Note: The ATI RadeonTM HD 3870 X2 series of product is currently
not supported by the ATI CatalystTM Linux software suite.[/I]

Are you sure you are actually using the restricted drivers? Jockey saying they are installed doesnt mean they are loaded. Can you use the catalyst control center?

FWIW, you can use compiz just fine with the opensource drivers.

I'm using the fglrx driver which is included in Ubuntu. And yes catalyst dose work. :)

I found that the control file from the 8-10 drivers got rid of the logo. So simply replacing the control file in the Ubuntu fglrx driver, with the one from the 8-10 legacy drivers from ati, solved the problem. And I'm using the 3850 x2, not sure if theres much of a difference.

Now i just hope that movies will play properly. I hope to try out some video editing solutions on Ubuntu. But the lack of decent drivers, is really discouraging.

---

### Post by P4man on 2010-10-20
> **BlueBoden said:**
> 
I found that the control file from the 8-10 drivers got rid of the logo. So simply replacing the control file in the Ubuntu fglrx driver, with the one from the 8-10 legacy drivers from ati, solved the problem. And I'm using the 3850 x2, not sure if theres much of a difference.

The 3850 X2 isnt metioned, neither as supported or not supported. Im guessing its the same card as the 3870 X2 though, just lower clock.

> Now i just hope that movies will play properly. I hope to try out some video editing solutions on Ubuntu. But the lack of decent drivers, is really discouraging.

Well, good luck. You may need it. I have a 4870 and its my first ATI card. Also my last. Its a really pita under linux compared to all the nvidia cards I used to have. Driver issues of all sorts, no gnome-shell or unity, video decode acceleration is non existent.  I have a 5 year old budget nvidia card (7300) that can play back HD content that my ATI card cant. Go figure.

If that doesnt discourage you enough; know that video editing software is one area where I find linux lacking severely. There is some hope for the future, some highend professional suite (forgot the name) was going to be opensourced, but the current available "best" like kdenlive pale compared to any windows or apple suite. It might be okay to edit holiday movies, but to be brutally honest, windows moviemaker is probably better at that. Comparisons with adobe suits are pointless once you realize you cant even keyframe 99% of the effects and filters.

So, I use  sony vegas. It works just fine in my virtual machine. But like I said, good luck :)

---

### Post by BlueBoden on 2010-10-21
This is the first time i managed to get rid of the watermark, so I'm just as exited to try Ubuntu when web-developing. All i need for that is a good text-editor. Will take some time to transfer my work though.

Its funny, i also use Sony Vegas, and absolutely love it. We mainly just line up the videos, and stick them together with some dissolves. That is, we rarely use the stuff that require keyframes.

I had some problems with VLC player, the playback is really jerky/lagging. Then i tried the player which came with Ubuntu, installed the filters it asked for. And this plays most my movies fine. I haven't tried any HD martial yet though. Its just annoying having to fiddle around with codecs again, after all that time using VLC on windows.

Anyway, I'm off.. Thanks for trying though.

---

