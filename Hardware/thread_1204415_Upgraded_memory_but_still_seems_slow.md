---
title: "Upgraded memory but still seems slow"
date: 2009-07-04
forum: Hardware
---

### Post by tmray on 2009-07-04
I recently upgraded my memory card and it shows up in bios and the windows partition is running much faster. But, my kubuntu 9.04 partition still seems to be really slow.

This is what it says from the terminal

free -m
                   total       used       free     shared    buffers     cached
Mem:          1507        698        808          0         22        321
-/+ buffers/cache:      354       1152
Swap:         1608          0         1608

Any thoughts on why it still seems slow?

Thanks.
Tom

---

### Post by darco on 2009-07-04
Seems strange from your output that the system is not fully utilizing your ram. For example, I have 8gigs and when I run the same command, it shows 7736 used from 7825 available.Thats how it should be, unused ram is wasted ram. When you say slow do you mean accessing the internet or when working with your files or both?

darco

---

### Post by earthpigg on 2009-07-04
if you weren't previously using up all your ram, forcing your system to use the swap partition, then what you describe is more or less to be expected.

one way to take advantage of your extra ram would be to use preload.

```
sudo apt-get install preload
```

restart, and make sure it is starting automatically... it should be in system-> preferences -> startup applications.

---

### Post by tmray on 2009-07-04
> **darco said:**
> When you say slow do you mean accessing the internet or when working with your files or both?

darco

It's both. Opening windows. Going site to site. etc...

---

### Post by tmray on 2009-07-04
> **earthpigg said:**
> if you weren't previously using up all your ram, forcing your system to use the swap partition, then what you describe is more or less to be expected.

one way to take advantage of your extra ram would be to use preload.

```
sudo apt-get install preload
```

restart, and make sure it is starting automatically... it should be in system-> preferences -> startup applications.
Just installed this and rebooted cant really tell if it made a difference or not yet. Gonna just work on the computer for a while and see what I think.

I didn't see it in the start up applications. Would it show up in a different place in Kubuntu?

Tom

---

### Post by darco on 2009-07-05
no you wont see it in the menu but you will when you boot up your pc....
It just preloads apps that it thinks you will open based on your past activity.

d

---

