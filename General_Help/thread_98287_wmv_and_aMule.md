---
title: "wmv and aMule"
date: 2005-12-02
forum: General Help
---

### Post by jkruer01 on 2005-12-02
When using aMule to download videos, everytime a wmv is downloaded, I cannot play it.  If it is a mpg, avi, asf, or anything else, it plays fine.  I know a lot of files are corrupted, but I have never had a single wmv that was downloaded correctly. 

Has anyone else had this problem?

Is there anyway to fix it?  I have tried using mplayer, totem, xine, etc.  When I try to open it with mplayer I get a message saying the filename indicates it is a WMV file but the contents indicate it is a ASF format.  I click cancel (the only button available) and it mplayer closes.  If I change the extension to wma, asf, mpg or anything else, it only plays a black screen.

When I open it in xine a scrambled movie just plays.

Again if it was a couple or even a lot that were broken I wouldn't think about it, but the fact that ever single wmv video I have downloaded doesn't work and the others formats do makes me curious.

Thanks!

---

### Post by jkruer01 on 2005-12-02
I forgot to mention.  I searched Google and found someone else with the exact same problem using Suse but no answer to the problem.

[http://forums.suselinuxsupport.de/lofiversion/index.php/t24863.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t24863.html)

---

### Post by Knowles on 2005-12-02
well wmv is a registered microsoft product in which it is abit dodgy playing such files on a linux distribution due to copyright (or so i have read) but there are codecs out there

---

### Post by jkruer01 on 2005-12-02
no, you don't understand, all other WMV files play fine.  Only ones that I download from aMule are broken.  

I can view others in a browser or standalone without a problem.

---

### Post by syklitengutt on 2005-12-06
I have the same problem with amule and wmv...
strange....... 
get a strange screen with allot of colors or this message:
This file is encrypted and cannot be played back
have the w32 codecs in.
even tried to play them with vlc without luck.

---

### Post by Neutrino on 2005-12-06
I think these movies are DRM protected. try running them under windows with media player it will request the licence.
I don't know if there are player under linux that support DRM.

---

### Post by syklitengutt on 2005-12-06
I dont think thats the deal.
All wmv and afs files downloaded by aMule cant be played.

---

### Post by jkruer01 on 2005-12-06
I agree.  If it is happening to every single one, something is wrong.

---

### Post by jkruer01 on 2005-12-06
is there anyone running Ubuntu that can download a wmv file from aMule and it works?

---

### Post by capdog on 2007-02-19
I know why this happens. Certain bad people release these encrypted WMV files onto P2P networks with the intention of exploiting the way the DRM license system works.

When you try open the WMV in linux, it just says that the file is encryped and leaves it at that.

Open it in Windows Media player, and it attempts to download a license by going to an internet address seemingly stored in the WMV. This pops up two or three internet explorer windows, normally p*rn sites, requesting your email address and details and advertising their wares. 

This is just another way that the evil spyware demons can get you! My advice? Don't download p*rn WMV files from dodgy P2P networks! :)

---

### Post by Spr0k3t on 2007-02-19
> **jkruer01 said:**
> is there anyone running Ubuntu that can download a wmv file from aMule and it works?

My advice here: Find a better format.  If you can't find a better format, keep looking, if that still doesn't work, refer to step 1.

WMV is not OS friendly.

---

### Post by Amaroq on 2007-03-20
Another way they can't get you that is, if you're using linux!

Is there a way to get them to unscramble? Of course, without leaving yourself vulnurable to the exploit.

---

### Post by medomedo on 2007-04-09
I am not sure if this theory is correct that WMV is not a single format rather than several (levels). Some of which can be played and others can not. 

Another possibility is that aMule doesn't download the WHOLE file and that those missing peaces are necessary for the file to be playable !!

I guess we need an expert in WMV codec to nail that down.

---

### Post by mingotta on 2007-07-02
> **capdog said:**
> I know why this happens. Certain bad people release these encrypted WMV files onto P2P networks with the intention of exploiting the way the DRM license system works.

When you try open the WMV in linux, it just says that the file is encryped and leaves it at that.

Open it in Windows Media player, and it attempts to download a license by going to an internet address seemingly stored in the WMV. This pops up two or three internet explorer windows, normally p*rn sites, requesting your email address and details and advertising their wares. 

This is just another way that the evil spyware demons can get you! My advice? Don't download p*rn WMV files from dodgy P2P networks! :)

After a lot of searching this sounds like the most reasonable explanation.
One more reason to fight DRM!

---

### Post by Hallvor on 2007-07-03
I agree. Haven`t downloaded a single WMV in years, because it is such a bad format and can contain malware - which is why these spamming lamers use the format in the first place. No real filesharer would release a file in WMV if they could avoid it - and they can avoid that by transcoding with VLC (or other tools).

Bottom line: Download xvids and be happy. Downloading WMV pr0n files is plain stupid.

---

