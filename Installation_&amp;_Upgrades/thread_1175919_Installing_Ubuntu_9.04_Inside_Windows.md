---
title: "Installing Ubuntu 9.04 Inside Windows"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by Klaw117 on 2009-06-01
I'm using the option to install Ubuntu inside Windows, so that I don't have to backup everything or lose data. I've made two Ubuntu CDs, but when I try to install, I get the same error:
[[IMG]http://img46.imageshack.us/img46/7254/ubuntuerror.jpg[/IMG]]("http://img46.imageshack.us/my.php?image=ubuntuerror.jpg")
Anyone know how to get past or fix this?

---

### Post by zvacet on 2009-06-02
Did you followed [these]("https://help.ubuntu.com/community/BurningIsoHowto") instructions to check everything before and after burning iso?

---

### Post by lisati on 2009-06-02
One option (described [here]("https://bugs.launchpad.net/wubi/+bug/370060")) is to try using the CD in another CD/DVD drive.

Also see [https://bugs.launchpad.net/wubi/+bug/366350](https://bugs.launchpad.net/wubi/+bug/366350)

---

### Post by Klaw117 on 2009-06-02
> **zvacet said:**
> Did you followed [these]("https://help.ubuntu.com/community/BurningIsoHowto") instructions to check everything before and after burning iso?
Did that, didn't work.
> **lisati said:**
> One option (described [here]("https://bugs.launchpad.net/wubi/+bug/370060")) is to try using the CD in another CD/DVD drive.
 
Also see [https://bugs.launchpad.net/wubi/+bug/366350](https://bugs.launchpad.net/wubi/+bug/366350)
 Can't, only have one DVD drive.
 
I'm thinking that the only way I can do this is to backup my files, partition the hard drive through Ubuntu, and do a full install, possibly losing my data and having to restore my backup.

---

### Post by StGeorge on 2009-06-02
See This:

[http://ubuntuforums.org/showthread.php?p=7359904#post7359904](http://ubuntuforums.org/showthread.php?p=7359904#post7359904)

Here is a link that will give you Ubuntu on a USB or Anywhere you want it.

No burning.

I am updating and stripping it now.

[http://sourceforge.net/project/showf...ease_id=626968](http://sourceforge.net/project/showf...ease_id=626968)

---

### Post by Klaw117 on 2009-06-02
> **StGeorge said:**
> See This:
 
[http://ubuntuforums.org/showthread.php?p=7359904#post7359904](http://ubuntuforums.org/showthread.php?p=7359904#post7359904)
 
Here is a link that will give you Ubuntu on a USB or Anywhere you want it.
 
No burning.
 
I am updating and stripping it now.
 
[http://sourceforge.net/project/showf...ease_id=626968](http://sourceforge.net/project/showf...ease_id=626968)
Thanks, but the first link didn't really help me and the second link doesn't work. I'm guessing putting Ubuntu on a USB is the same as this:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
 
Unfortunately, that only runs in 32-bit and I want to use 64-bit. Therefore, I think the only way this will work is if I backup my hard drive and do a full install of Ubuntu.

---

### Post by patioheater on 2009-06-02
:KSDon't forget to defrag first. To save the hassle of burning a disc, I just installed Daemon tools on the lappie, mounted the iso in the virtual drive gave it 25gb of space and off I went. Maybe not the correct way of doing it but it worked

---

### Post by Klaw117 on 2009-06-02
> **patioheater said:**
> :KSDon't forget to defrag first. To save the hassle of burning a disc, I just installed Daemon tools on the lappie, mounted the iso in the virtual drive gave it 25gb of space and off I went. Maybe not the correct way of doing it but it worked
Daemon Tools? I think I'll give that a try.
 
I managed to get into my log files, so I'm posting them here, so you guys can see what's going on. Download the two (I installed twice with no avail) file here:
[http://www.mediafire.com/?sharekey=a274981523781b225bf1f12f1ff3f30ae04e75f6e8ebb871](http://www.mediafire.com/?sharekey=a274981523781b225bf1f12f1ff3f30ae04e75f6e8ebb871)

EDIT: It works, but now I have another problem. I'm trying to hook up my HP DeskJet 612C printer and Ubuntu detects it, but when I tell it to print a test page, it prints a page with garbage characters on it and then keeps taking in paper and printing blank sheets. I turned it off, deleted the printer, and tried to detect the printer again. After detecting it, I tell it to print a test page and the same thing happens.

---

### Post by Klaw117 on 2009-06-02
Thanks! It works, but now I have another problem. I'm trying to hook up my HP DeskJet 612C printer and Ubuntu detects it, but when I tell it to print a test page, it prints a page with garbage characters on it and then keeps taking in paper and printing blank sheets. I turned it off, deleted the printer, and tried to detect the printer again. After detecting it, I tell it to print a test page and the same thing happens.

---

### Post by HectikDroid on 2009-06-02
Hi, Im kinda new to ubuntu, I was wondering if there is a difference in performance if I install ubuntu in wondows rather than partitioning my HD, and If I do install as a another boot will I lose my data and windows(vista)

---

### Post by Klaw117 on 2009-06-02
Installing inside Windows makes Ubuntu slightly slower, but if you have a decent computer, you should not see a noticeable difference.

Also, doing a full install by partitioning the hard drive does run the risk of destroying your data.

---

### Post by zvacet on 2009-06-05
@ **HectikDroid**

Dual boot is common way of installing Ubuntu and if you do it right you will not lose anything on your Windows side.

---

### Post by HectikDroid on 2009-06-05
Thanks Guys, I'm Using a gateway PC 2.8GHz 6GB Ram 500GB HD (400 free)..... I'm gonna install in a bit, I been a little busy. One more question, What do you recommend I set my installation size to? its set at 17GB default should I go with that? Thanks alot

---

