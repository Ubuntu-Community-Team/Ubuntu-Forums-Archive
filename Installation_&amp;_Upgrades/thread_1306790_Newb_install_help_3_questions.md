---
title: "Newb install help 3 questions"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by fokuslee on 2009-10-30
Hi Ubuntu Friends.
I have 3 questions

1st I am trying to install ubuntu on fake/bios raid b/c i already have windows xp and need to dual boot for games and programs. I am reading that alternative install cd has dmraid out of the box and its a straight forward install where i can see the raid and resize and create partitions for linux? can anyone confirm this? 

2nd is 64bit of ubuntu easy to use? Long time ago i tried linux and the 64bit required chrooting to get flash working is this still the case? 

3rd how much swap is enough, can i go without making any? since i don't see a need for pagefile w/ 4gig ram... or i just make 512mb swap so the system structure is kinda normal...

Thanks a bunch
oh ps is kiba-dock still alive?

---

### Post by earthpigg on 2009-10-30
1. never worked with raid, cant offer advice

2. ive been using only 64 bit for quite some time, works the same.

3. i have 6gb of ram and zero swap.... when firefox has memmory leaks, my computer locks up as a result. i know its ff because i have caught it in its initial stages of taking up 2 then 3, etc, gb of ram. unless hd space is at a premium, keep a swap around: at least it will give your computer a chance to run super slow for a bit and warn you that something is amiss. i have a 60gb ssd, so it isn't practical for me.

---

### Post by mac9416 on 2009-10-30
> 2nd is 64bit of ubuntu easy to use? Long time ago i tried linux and the 64bit required chrooting to get flash working is this still the case?

A friend told me to do this: 
[LIST=1]
[*]Download libflashplugin.so tar.gz from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
[*]Extract it
[*]Move it to $HOME/.mozilla/plugins/
[/LIST]

Good luck!

---

### Post by earthpigg on 2009-10-31
> **mac9416 said:**
> A friend told me to do this: 
[LIST=1]
[*]Download libflashplugin.so tar.gz from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
[*]Extract it
[*]Move it to $HOME/.mozilla/plugins/
[/LIST]

Good luck!

that may or may not work, but it certainly isn't the Ubuntu Way.

```
sudo apt-get install ubuntu-restricted-extras
```

done. the ubuntu way :D

---

