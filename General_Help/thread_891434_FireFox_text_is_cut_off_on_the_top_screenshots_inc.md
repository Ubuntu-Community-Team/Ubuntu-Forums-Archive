---
title: "FireFox text is cut off on the top *screenshots included*"
date: 2008-08-16
forum: General Help
---

### Post by Ralphie on 2008-08-16
I think the pictures can explain it better than I could:
[IMG]http://teamtreetops.com/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=214&g2_serialNumber=1[/IMG]

[IMG]http://teamtreetops.com/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=216&g2_serialNumber=1[/IMG]

It doesn't happen on all websites, but on most it does.

All links seem to be cut off as well. For instance, even if the whole text is visible, if it is a link, only the bottom half is active.

Very strange and quite annoying! Any ideas?

---

### Post by Ralphie on 2008-08-16
I'd like to ad that I've read elsewhere to uninstall plugins as a possible fix, this does not work. I can also say that the problem is happening in Epiphany Web Browser aswell

---

### Post by Ralphie on 2008-08-16
I just found that if I press the "PrintScreen" button, and take a screenshot, some (not all) text becomes full again.

Any ideas?

---

### Post by Ralphie on 2008-08-18
*BBUUMMPP*

Anyone out there?

---

### Post by Ralphie on 2008-08-23
:popcorn:

---

### Post by SPr on 2008-08-23
I don't actually know what the problem is but have you tried increasing/decreasing the font size or changing the font? Does either help? I suspect the answer to my next question will be "no" but I'll ask anyway: does it happen in any other applications?

---

### Post by Ralphie on 2008-08-23
> **SPr said:**
> I don't actually know what the problem is but have you tried increasing/decreasing the font size or changing the font? Does either help? I suspect the answer to my next question will be "no" but I'll ask anyway: does it happen in any other applications?

aaah thanks for replying :D
The size change is a good idea, but it did nothing :(

You may however be onto something about the font in general, I will have to look through a few pages and see if it is the same font causing the problems every time, I will report back when I look into it a little bit more right now

Also, It only seems to be happening over the web, through both Firefox and my only other browser, Epiphany.

---

### Post by Ralphie on 2008-08-23
hmm, it doesn't seem to be related to text style. 
Another strange thing I found, is that on some pages, the text is fully there, but then when highlighted, only half will highlight... Well, if I highlight the text on a page like this, then resize it (CTRL+Scroll wheel) the top half will then erase.

This issue almost has me wanting to reinstall my whole system... which is VERY unappealing right now :P

---

### Post by lukjad on 2008-08-23
Try looking at the page in another mozilla based browser. Try sea monkey, it is just like Firefox but faster. Tell us what happens. Also, try to view the page with other browsers. It could just be that the page is nonstandard and messed up.

---

### Post by Ralphie on 2008-08-23
You weren't kidding about seamonkey being fast, dang!
But, sadly, it has the same issue. :(

---

### Post by lukjad on 2008-08-23
Have you tried other browsers? Konqueror? Amaya? Epiphany? Galeon? Opera?

---

### Post by Ralphie on 2008-08-23
Yes, every browser tried has this issue

---

### Post by rossjman1 on 2008-08-23
Do you have msttcorefonts installed? If not try this:
```
sudo apt-get install msttcorefonts
```

---

### Post by Ralphie on 2008-08-23
> **rossjman1 said:**
> Do you have msttcorefonts installed? If not try this:
```
sudo apt-get install msttcorefonts
```

You just saved my web browsing experience!! :P
Thanks so much!

I honestly thought I had the core fonts installed, but that must have been on different installation of ubuntu.

wow, thanks a lot.
Also thanks to lukjad007 for giving a shot at helping me.

---

### Post by lukjad on 2008-08-23
Any time.

---

### Post by jmjohn on 2008-09-03
I have the same problem, but I have the fonts already installed.  It happens with multiple instances of Firefox or when I have way too many tabs open.  But I have 4GB of Ram and a 2.3 dual core intel processor.

It may be a problem with Compiz.  Here's a link:

[http://forum.compiz-fusion.org/showthread.php?t=6742](http://forum.compiz-fusion.org/showthread.php?t=6742)

Anybody?

-glass.dimly

---

### Post by Ralphie on 2008-09-03
You know, I have also found it happening again in certain instances. Not as much as when I did not have the fonts, but I have found it to happen on rare occasions. 

Do you have dual screens?
Someone on that other thread was relating it to that. 
(I myself do have dual screens)

---

