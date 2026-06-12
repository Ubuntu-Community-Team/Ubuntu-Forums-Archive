---
title: "Widescreen Laptop is Stretched Out"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by chrisg0619 on 2006-12-28
I just installed Ubuntu and noticed that, on the generic widescreen monitor on my laptop, Ubuntu 6.10 is "stretched."  I ran "sudo dpkg-reconfigure xserver-xorg" and was able to select 1280x800 from there, but when I restarted X and went to "Screen Resolutions," the highest resolution available was 1024x768.  No matter what I do--I even inserted a modeline into xorg.conf--I can't get this widescreen to work.  Any help would be greatly appreciated.

---

### Post by kolinab on 2006-12-28
Do you know the chipset of your video adapte? I know on my widescreen I needed to 

```


sudo aptitude install 915resolution


```

to get the 1280 X 800 working.

I have some links regarding those issues.  

[http://www.ubuntuforums.org/search.php?searchid=11871904](http://www.ubuntuforums.org/search.php?searchid=11871904)
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

Let me know how that goes for you. Once I installed 915resolution things looked much more wonderful for me!

K

---

### Post by chrisg0619 on 2006-12-28
Works perfectly--thank you so much!!

---

