---
title: "Issue after reverting Jaunty Xorg intel driver to 2.4"
date: 2009-08-06
forum: Hardware
---

### Post by phar0z on 2009-08-06
I'm experiencing many performances issues on my Toshiba notebook with my Intel graphics card. I've used to work with AccelMethod""uxa" according to [**this howto**]("http://ubuntuforums.org/showthread.php?t=1130582") that I've read.

Now, I reverted my jaunty xorg intel driver to 2.4, according to[ **this howto**]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").

My KDM is able to load, but when I'm starting KDE it hangs and unfortunately KDM appears again, whereas KDE disappears automatically. So I'm able to start the KDM login manager, but not able to start KDE completely.

This is the output of lspci:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

And here you see the output of spci --n | grep VGA 
```
[8086:27a2] (rev 03) 
```

I've noticed many people with the same chipset [**reported improvements**]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") here.

[**Here you can see my Xorg.0.log**]("http://pastebin.com/f4547ced3") 

[**Here you can see my kdm.log**]("http://pastebin.com/f7e24a46c")

Any kind of help would be highly appreciated. Thanks.

---

### Post by phar0z on 2009-08-07
I've also tried to boot without a xorg.conf file, so I counted on Hal. Unsuccessfully :(. I get exactly the same situation like I've described in my previous post.

---

### Post by petersohn on 2009-08-07
I had no problems with reverting. However, for me, UXA didn't work well, I used EXA instead, and put "MigrationHeuristic greedy" in xorg.conf.

---

### Post by phar0z on 2009-08-07
> **petersohn said:**
> I had no problems with reverting. However, for me, UXA didn't work well, I used EXA instead, and put "MigrationHeuristic greedy" in xorg.conf.

I've frequently adjusted my xorg.conf file :( 
I've tried them both.

---

