---
title: "HP Deskjet 5400 printer problem on Ibex"
date: 2008-11-26
forum: General Help
---

### Post by cybrsaylr on 2008-11-26
My HP Deskjet 5400 printer ran OK with 8.04 and just tried using it on 8.10 and have nothing but problems. It holds old print jobs and keeps trying to print them till paper runs out. I can't find a way to cancel the print jobs. As soon as I put a few sheets of paper in it starts up again on the old jobs. The black cart ran out of ink. I reloaded the ink and it still shows up empty on the HP toolbox I installed to see the ink levels. This printer runs normal when I run XP on this dual boot XP/Ubuntu system....it just won't run right when I switch to Ibex, while it did run OK with Hardy. 

Any ideas what's wrong?

---

### Post by cybrsaylr on 2008-11-26
I removed the 'HP toolbox' and rebooted and now the printer doesn't automatically turn on and keep cycling till it runs out of paper, like it was doing before but I still can't cancel and remove the print jobs stacked up to run.

ps: Spoke to soon, it started auto cycling again till it runs out of paper....

---

### Post by cybrsaylr on 2008-11-28
Just tried uninstalling printer then reinstalling it again.
Everything seemed OK.
Then got to the 'test page'.
Ran a test and the same bug happens again it just keeps spitting out blank sheets of paper till it runs out and won't give a good 'test page'.

Help?
Anyone?

---

### Post by cybrsaylr on 2008-12-01
Still looking ffor some help on this.

Also I refilled the black ink cartridge, I know it full but when trying to print, it sends a 'low ink' message on the top panel. Anyone know how to fix this? The HP Toolbox shows the 'black ink' as empty even though it's full.

---

### Post by shadowber on 2008-12-02
you might want to give [this]("http://ubuntuforums.org/showthread.php?t=996237&highlight=printer") a look....

---

### Post by cybrsaylr on 2008-12-03
shadowber,

Thanks, followed the directions in your link and my HP printer now appears to be working again with Ibex  instead of spitting out blank sheets of paper....):P

---

### Post by cybrsaylr on 2008-12-04
Still having a problem.
A 'test page' prints out OK.

Tried to print out a page off the internet and only part of it printed out on a standard sheet of paper. What prints out is the top left quarter of the sheet, while the right side and lower left side is blank!
Tried playing around with the print settings but can't get it to print out normally the full page desired. 
Haven't a clue what is going on.
When I switch over to XP on this dual boot system, it prints out the full page desired normally.

---

### Post by shadowber on 2008-12-04
Actually, since I switched to Ibex, I have almost the same problem, which is why I found your post, and the post I sent you to. anyway, now that you posted this problem, I have the same problem, and can someone help us???

---

### Post by cybrsaylr on 2008-12-04
I have a dual boot system XP/Ubuntu.
With XP, the printer works fine.
With Gutsy and Hardy the printer along with the HP Toolbox worked fine.
On Ibex is when the problems started and the HP Toolbox acts funny also, had to remove HP Toolbox with Ibex. I refilled the black ink cartridge but HP Toolbox still sees it as empty! I heard HP and some other printer companies did something to their ink cartridges, to show this to keep you buying their cartridges instead of refilling them but I don't know how to work around what they did to old used ink cartridges you use over.

My laptop has Vista/Ubuntu 8.04 on it and the printer works fine on both OSs. I'm afraid to upgrade to 8.10 on the laptop fearing the printer may not work properly on that either then.

---

### Post by cybrsaylr on 2008-12-06
Anyone have any ideas?

---

### Post by lokutus25 on 2008-12-07
Hi, I'm going through the same problems With Ibex and my HP 5440...I'm working on it too... :(

---

### Post by lokutus25 on 2008-12-07
I'm having the following errors in my syslog file when I try to print:

Dec  7 22:37:32 wsd-rio kernel: [435294.657185] usblp0: removed
Dec  7 22:37:32 wsd-rio hal_lpadmin: Running hal_lpadmin
Dec  7 22:37:32 wsd-rio kernel: [435295.209778] type=1503 audit(1228685852.971:12): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=20067 profile="/usr/sbin/cupsd"
Dec  7 22:37:33 wsd-rio hpijs: unable to set device=deskjet 3600, err=17 
Dec  7 22:37:33 wsd-rio hpijs: unable to read client data err=-2 
Dec  7 22:37:33 wsd-rio hal_lpadmin: hal_lpadmin triggered by usblp kernel module
Dec  7 22:37:33 wsd-rio hal_lpadmin: Using device ID from HAL database entry
Dec  7 22:37:33 wsd-rio hal_lpadmin: remove
Dec  7 22:37:33 wsd-rio hal_lpadmin: Found configured printer: Deskjet-5400-series
Dec  7 22:37:33 wsd-rio python: hp-makeuri[20075]: warning: hp-makeuri should not be run as root.

But I can't figure out which is the problem. A true kernel bug maybe?

---

### Post by cybrsaylr on 2008-12-08
> **lokutus25 said:**
> But I can't figure out which is the problem. A true kernel bug maybe?
I don't know what it is. 
All I can print out is a 'test page'.

---

### Post by ionFreeman on 2009-03-01
So, changing from foo to cups and recreating the printer, as per above, doesn't work, I gather. Has anyone solved this yet?

---

### Post by shadowber on 2009-03-02
Actually, I eventually just got rid of everything else, went to hp.com, and downloaded their driver for linux, and it works fine since then...

---

### Post by ionFreeman on 2009-04-18
That worked! HP.com redirects you -- the link for the script is at [http://sourceforge.net/project/downloading.php?group_id=149981&filename=hplip-3.9.2.run&a=38947651](http://sourceforge.net/project/downloading.php?group_id=149981&filename=hplip-3.9.2.run&a=38947651)
-- when it says 'restart', it means it's going to restart your computer, not the printer, which created a little awkwardness. The script also requires enabling the universe and multiverse repositories, so you may just be able to install hplip through Synaptic; running the script downloads gcc, among other things, and does a make right there.

Thanks!

---

