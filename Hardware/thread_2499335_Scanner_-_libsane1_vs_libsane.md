---
title: "Scanner - libsane1 vs libsane"
date: 2024-07-23
forum: Hardware
---

### Post by WDYSUN on 2024-07-23
I am trying to install a Brother scanner on Ubuntu 24.04.  The problem is that `brscan-skey` requires `libsane` while this has been now replaced with `libsane1`. 

From what I understand `libsane` is perfectly compatible with `libsane1`. 

Is it possible to create an alias so that whatherver software tries to use `libsane` it is pointed to `libsane1`?

---

### Post by currentshaft on 2024-07-23
This should do the trick:

sudo ln -s /usr/lib/x86_64-linux-gnu/libsane1.so /usr/lib/x86_64-linux-gnu/libsane

I already have a similar link on my machine:

ls -l /usr/lib/x86_64-linux-gnu/libsane.so.1
/usr/lib/x86_64-linux-gnu/libsane.so.1 -> libsane.so.1.2.1

---

### Post by him610 on 2024-07-23
>  trying to install a Brother scanner on Ubuntu 24.0
How did you initially attempt to install the Brother scanner?
What model is the Brother scanner?

Reason I ask is that I successfully installed brscan4*.deb and brscan-key*.deb for a MFC-7360N a few weeks ago without any issues.

---

### Post by upsetti on 2024-08-01
Hey.

Sorry to join in.
But I have exactly the same problem (my thread is here: [https://ubuntuforums.org/showthread.php?t=2498856](https://ubuntuforums.org/showthread.php?t=2498856)) and I am going to update it, when I can resolve it here.

Same story: I am trying to install the default brother printer/scanner drivers, but it isn't working because of:
```

The following packages have unresolved dependencies:
 brscan-skey : Depends on: libsane (>= 1.0.11-3) but isn't installed
E: Unresolved dependencies. Try to »apt --fix-broken install« ...)

```
If the english text is not 100% accurate, that's because I installed a german language Version on my mothers PC and
translated it roughly. So it might not be 100% correct.

Your solution currentshaft unfortunately did not resolve the problem. I run into the same problem (unresolved depencies).
Do you, or anyone else have another solution please? :/

p.s. Btw. Whowever came up with the idea of renaming a dependency lib etc. that was a dang stupid idea ok?!
Why would you break something that was working beforehand?!? (it was working fine on my previous
ubuntu install. It not working any longer...is actually...aaahh! And I am not a novice on tech. Why would you do this?!)

---

### Post by currentshaft on 2024-08-01
apt

---

### Post by upsetti on 2024-08-02
Then, from memory, it fixes what was broken but the scanner is still not being detected.
But its ok. I just downloaded a scanner app for my mobile...for the amount of scanning I have to do it should be sufficient.
In general really not satisfying, but I really don't want to spend more energy and time on it. Maybe if there will be a solution in the future I am going to check for it again then, but for now I am done.

Thanks everyone who was trying to help! <3 !!

---

### Post by Yellow Pasque on 2024-08-02
[https://ubuntuforums.org/showthread.php?t=2498203&p=14193152#post14193152](https://ubuntuforums.org/showthread.php?t=2498203&p=14193152#post14193152)

---

