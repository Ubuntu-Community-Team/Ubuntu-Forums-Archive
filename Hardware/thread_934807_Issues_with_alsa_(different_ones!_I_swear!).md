---
title: "Issues with alsa (different ones! I swear!)"
date: 2008-10-01
forum: Hardware
---

### Post by cshotwell on 2008-10-01
Long time listener, First time caller.


I installed Hardy on my aspire 6920 about a month ago. After getting everything working properly and such, I have decided to revert back from the OSS 4 sound driver to alsa because OSS just didn't sound right.

i followed this post :
 [http://ubuntuforums.org/showpost.php?p=5539687&postcount=331](http://ubuntuforums.org/showpost.php?p=5539687&postcount=331)
to attempt to remove OSS and then this little guy :
[http://ubuntuforums.org/showthread.php?t=852295&highlight=8920&page=2](http://ubuntuforums.org/showthread.php?t=852295&highlight=8920&page=2)

 to get it back up and running.

I may have left an OSS module still on, but i don't know what that means so i wouldn't know how to fix it. 

Typing alsamixer gets me this:

alsamixer: function snd_ctl_open failed for default: No such file or directory


basically i have scoured around extracting, compiling, installing, doing god knows whatever people tell me trying to get it to work. I have considered reinstalling Hardy, but I'm sure there is a simpler way.


Any help would be insanely appreciated, I can provide any information needed.  Thank you very much, I should have tried this awhile ago.

---

### Post by cshotwell on 2008-10-04
yeah, reinstalled ubuntu, did the fix and it works.  mostly.

internal speakers work dandy.  However the headphone jack and others are a little funky. sound only comes out of the black port, when it should be coming out of the green.

It is also impossible to completely mute my laptop speakers.  I can uncheck the headphone box in GNOME alsamixer, and it drastically cuts my internal sound, but the mini subwoofer is still kicking.  

also sound does not work on youtube, but on other video sites, such as break, it works fine.

---

### Post by markbuntu on 2008-10-04
You can look in my guide here, read the very first section and then there is some links near the beginning about HDA chips which you should look at to get the mic switching working and a Multiple Application Sound Sharing section for getting everything dialed in. Or you could just read the entire thing and all the links and become a Ubuntu Hardy Sound Guru if you have a spare few days.

---

