---
title: "Installation problem"
date: 2005-01-08
forum: Installation &amp; Upgrades
---

### Post by endtime on 2005-01-08
I'm pretty new to Linux; I used Mandrake for about a week before switching to Ubuntu Warty, which I like much more.  I installed it and everything was fine, except that there were some out of date packages in Synaptic.  So I decided to try the upgrade to Hoary.

Bad idea.  I broke my system past the point of recovery (for me at least) and so formatted and reinstalled Warty.  Now, when I install, I get an error trying to start the x-system and [FONT=Courier New]**apt-get update**[/FONT] yields 403 Forbidden errors.  I suspect that if I can get past the 403 errors I'll be able to get everything working, but I don't know how to do that.  I didn't get those errors the first time I installed...thanks for any guidance.

---

### Post by tiiim on 2005-01-08
> **endtime]I'm pretty new to Linux said:**
> **apt-get update**[/FONT] yields 403 Forbidden errors.  I suspect that if I can get past the 403 errors I'll be able to get everything working, but I don't know how to do that.  I didn't get those errors the first time I installed...thanks for any guidance.
 im sure there a simple way. Just reinstall again and format all paritions make sure nothing stays.

Did you also try sudo apt-get? Also if you want the latest stuff get the unofficial backports (see right menu on forum) its an updated warty but not unstable hoary.

---

### Post by endtime on 2005-01-08
I formatted fully the first time, and when I got these errors I did format again, manually editing the partitions that time to make sure.  Also, I should have been more specific...I did [FONT=Courier New]**sudo apt-get upgrade ** [/FONT] and **[FONT=Courier New]sudo apt-get update[/FONT]**.  I also tried **[FONT=Courier New]-f[/FONT]** and **[FONT=Courier New]-m[/FONT]** in there to no avail.  Appreciate it all the same, thanks.

I was wondering if the 403's had something to do with my SonicWall but I temporarily disabled the rule blocking open access to the subnet I was on and still got the 403's.

---

### Post by endtime on 2005-01-09
Well, after doing fierce and bloody battle with Debian proper until 3:30 AM last night, only to have a similar error, I realized that Ubuntu was not my problem, although I did still see some 403's.  But choosing Vesa instead of VGA for my video drivers (or whatever I was choosing, it was like 4:15 AM) seemed to solve the problem.  At least, that's what I did differently and I'm posting this from Ubuntu.  Anyway, thanks for the help tiiim.  Hopefully someone else will be making the same mistake as me one day and benefit from this.

---

