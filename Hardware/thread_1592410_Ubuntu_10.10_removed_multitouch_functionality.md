---
title: "Ubuntu 10.10 removed multitouch functionality"
date: 2010-10-10
forum: Hardware
---

### Post by Druidika on 2010-10-10
On my Asus UL30A notebook I was able to use gestures with up to three fingers before (at least in 9.04, 9.10 and 10.04), to scroll, right- or middleclick for example. The upgrade to 10.10 removed all that functionality and resulted in a major usability loss.

---

### Post by Nimless on 2010-10-10
> **Druidika said:**
> On my Asus UL30A notebook I was able to use gestures with up to three fingers before (at least in 9.04, 9.10 and 10.04), to scroll, right- or middleclick for example. The upgrade to 10.10 removed all that functionality and resulted in a major usability loss.

This is probably a regression, I heard they added a lot of new stuff related to multitouch with the utouch framework , you should probably file a bug in launchpad :(

---

### Post by kelvin.illa on 2010-10-16
I arrived at this thread thinking I had the same problem. I thought I lost my multi-touch: 2-finger scroll, 2-finger middle click and 3-finger right click. It turned out, mouse configuration was reset, and in the touchpad tab, "edge scrolling" was set instead of "two-finger scrolling." Also, 2-finger click is now right click, and 3-finger click is now middle click.

See if you have the same issue.

Cheers.

---

### Post by Druidika on 2010-10-19
That indeed almost fixed it, thanks! However, is there a way to revert the right- and middleclick behavior to the previous?

---

### Post by kelvin.illa on 2010-10-19
> **Druidika said:**
> That indeed almost fixed it, thanks! However, is there a way to revert the right- and middleclick behavior to the previous?

I'm glad it also worked for you, even just "almost."

Is there a way to revert? I'm sure there is--this is Linux after all. But I'm not one who knows how.

I guess you'll just have to get used to it. Right click is more often used anyway so it would be better off having the 2-finger click.

---

### Post by PJM619 on 2010-11-07
Could you tell me how you fix it? I don't understand if you do an regression or installed/changed the utouch.

Greetings,
   PJM619

---

### Post by arbrandes on 2010-11-07
For a fix, see the "Touchpad Fixup" on my U43JC post, here:

[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

There are other threads and bugs on Launchpad relating to this issue.

---

