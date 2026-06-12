---
title: "FN+key Brightness adjust not working."
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by yorkshire_spam on 2008-01-10
Hi all,
My FN+function key support on my laptop seems a bit patchy.

The keys that adjust the volume work fine (FN+F5/F6) but the keys that should adjust LCD brightness (FN+F7/F8 ) do nothing,
After a bit of digging I find that the volume keys generate scancodes, but the brightness keys do not.
Do I need to "tweak" my xkb files to sort this out, or am I missing something more obvious?
Cheers,
Sam

---

### Post by Kralizec on 2008-01-10
I'm curious about this as well. I don't know when it happened but my brightness control keys stopped working too.

---

### Post by yorkshire_spam on 2008-01-11
I think mine stopped working when Gutsy arrived, but not 100% sure.

---

### Post by Kralizec on 2008-01-11
I'm fairly sure mine started when I upgraded to Gutsy as well.

---

### Post by yorkshire_spam on 2008-01-11
Looks like a [known bug]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/152323")

---

### Post by Pandemic187 on 2008-01-13
Mine doesn't work either. Just curious - what kinds of laptops are you all using? Mine is a Compaq Presario v3000T.

---

### Post by Kralizec on 2008-01-13
I'm using a Gateway MX6446. My brightness up/down keys aren't actually on the F# keys, they're on the arrow up/down keys, but I figure its the same problem. On a different note, I have a brightness max/min key that automatically sets the brightness to the maximum or minimum and it still works fine.

---

### Post by Quilzas on 2008-01-14
Just installed 7.10 on my Fujitsu T2010 tablet tonight.

The brightness keys don't work.  But this seems to be a bug form what I'm reading.

However, I also cannot find a manual way to change the brightness!  o.o  
There is nothing in power management relating to the brightness at all.
Am I missing a package or something?

---

### Post by yorkshire_spam on 2008-01-15
My laptop is a cheap and cheerful Novatech (nude - no OS pre-installed)
Brightness and power-save stuff work fine under XP and Feisty, but not at all under Gutsy.
Trying to roll my own kernel on the older sources to see if it cures the problem.

---

### Post by Quilzas on 2008-01-15
Though reading some help files and some more in the forums, it seems to be an issue where the GConf policy keys are not allowing me access to the brightness controls.  No matter how to try to do it.

A friend, who is much more familiar with Fujitsus than I, mentioned that with Fujitsus, the brightness is a hardware function that would need to be mapped to some keys.  I have yet to pull more information out of him on this.

---

### Post by yorkshire_spam on 2008-01-17
I get the feeling that it's a kernel issue, if I boot into a console and monitor the scancode events I don't get any for my brightness keys (but I do for other "special" keys)

---

### Post by rosegarden78 on 2008-01-19
Try typing this command in a terminal
 
 xgamma -gamma 0.75
 
 I have posted my own solution here:
 
 [http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by rosegarden78 on 2008-01-19
Or type the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by p1977p on 2008-01-22
I'm having the same problem with the Fn+F7/F8 not generating codes. I have a Compaq presario v3000 laptop with an nVidia card. 

However I have found a way about this. See my post below:
[http://ubuntuforums.org/showthread.php?p=4183973#post4183973](http://ubuntuforums.org/showthread.php?p=4183973#post4183973)

---

