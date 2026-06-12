---
title: "ubuntu on Fujitsu Stylistic 4120P"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by themsn on 2009-04-28
Hi-

I'm trying to install Ubuntu on my tablet pc (Fujitsu Stylistic 4120P)

From this help page:
[https://help.ubuntu.com/community/FujitsuStylisticST4000](https://help.ubuntu.com/community/FujitsuStylisticST4000)
it's apparently doable.

I'm not too good with linux, so I don't know what to do with the xorg.conf and xf86Fpit.c files.

I read that 8.10 won't work, so I assume that 9.04 definitely won't work, but when I try 8.04, I just the white bar screen of death as Mekon88 described:
[http://ubuntuforums.org/showthread.php?t=726930&highlight=st+4120p](http://ubuntuforums.org/showthread.php?t=726930&highlight=st+4120p)

Can anyone help me out on how to get the thing installed and then how to apply the xorg.conf and xf86Fpit.c fixes?
I can't find any contact info of the guy who wrote up the help page, so now I turn to the community for help.

thank you.

---

### Post by Mark Phelps on 2009-04-28
I've got 8.04 working on my Fujitsu 4020 tablet PC -- but it took a lot of work.  I booted from both the 8.10 LiveCD and the 9.04 LiveCD and discovered three problems in both cases:
1) Tablet buttons will not work -- period!
2) Stylus doesn't work properly until I replace the "updated" xorg.conf with the one I hand-built for 8.04
3) Stylus will no longer "rotate" in Tablet mode -- making the tablet surface useless for writing as a tablet.

I can try to hunt down the web page reference that I used for the 4020, but your's is a different machine and the same stuff might not work.

BTW, given the loss of functionality with 8.10 and 9.04, I've decided NOT to upgrade the tablet PC but am waiting for Windows 7 to come out and try that.  I was able to find Vista drivers for all the devices on the 4020, so I already have the drivers that Seven will need.

---

### Post by themsn on 2009-04-28
Thanks for your reply. :)

hmmm... 
From what I've read, windows7 doesn't have any drivers for my st4120p.  So that is also another reason why I'm turning to Ubuntu.

I just wish the guy's contact info was listed on the help page that I linked above.  Because he was able to get quite a bit of stuff up and running.

so would you mind telling me how you got X to even load?  I can't install or even Live Run ubuntu because X in its default setting (and even in safe mode) will not display the install wizard page that I've seen screenshots for.

thank you.

---

### Post by Mark Phelps on 2009-04-29
> **themsn said:**
> From what I've read, windows7 doesn't have any drivers for my st4120p.  So that is also another reason why I'm turning to Ubuntu.
Seven uses Vista drivers.  If you google for your machine, you will find several websites that will have Vista drivers for different Fujitsu models.  I was able to use some newer model drivers for my older tablet PC.
> 
so would you mind telling me how you got X to even load?  
In my case, X loads just fine.  I have an Intel 915GM driver chipset; I think yours might be different.  Ubuntu was able to find and load the drivers without any intervention from me.

---

