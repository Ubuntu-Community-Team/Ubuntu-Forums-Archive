---
title: "AMD Radeon HD 7700 Ubuntu 13.10"
date: 2014-03-07
forum: Hardware
---

### Post by woodwork78 on 2014-03-07
Trying to install Ubuntu on my desktop.  I have 2 graphics cards, amd radeon hd 7700.  After boot, before I can enter my password, my monitor looks pretty much like this.  I was somehow able to enter my password and get here.  
[ATTACH=CONFIG]250936[/ATTACH]

I can get to the terminal by entering ctrl+alt+f1 and did sudo apt-update and sudo apt-upgrade hoping it might install some necessary driver for my video cards.  Any ideas?

---

### Post by phidia on 2014-03-08
I think the [guide here]("https://help.ubuntu.com/community/RadeonDriver") will be helpful. I do see from that that the 7000 series is not fully supported. You could check out the link to the bug report for your card from that guide also.

---

### Post by woodwork78 on 2014-03-20
Thanks [**[COLOR=#000000]phidia[/COLOR]**]("http://ubuntuforums.org/member.php?u=198354"), that link provided a bunch of info.  Not sure if it solves all the issues I'm having, but at least I know it's a bug and not user error.

---

### Post by Donut50 on 2014-03-21
And, did you got any good results with the guide provided by phidia?

---

### Post by woodwork78 on 2014-04-07
> **Donut50 said:**
> And, did you got any good results with the guide provided by phidia?

It didn't really help me solve the problem.  I'm still working on getting everything working on my desktop, but in the meantime I have a couple of laptops running fine.

I did get some advise to try booting with nomodeset.  Will try this tomorrow and let you know if it works.

---

