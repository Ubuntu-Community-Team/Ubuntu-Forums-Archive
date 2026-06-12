---
title: "nVidia GeForce GT550M"
date: 2011-10-22
forum: Hardware
---

### Post by SyntheticShield on 2011-10-22
Ive used Linux for a few years now and while Im no expert I can get around and usually solve most issues.  In that time I have mainly run Linux Mint.  Ive wanted to run Ubuntu for a while but that Unity side bar thingy kept me away because I really did not like it to say nothing of the issue of it being dang near impossible to shrink its width.

When it was announced that 11.10 would feature 5gb of storage in Ubuntu One I thought I could deal with it to have that space and keep my important stuff synchronized and it was a sizable step up from Dropbox.

At any rate, I decided to buy a new laptop and instead of just getting the standard entry level type laptop I decided to splurge a little and get one with a good graphics card and other nice stuff.  So I got a Dell XPS 17 L702X with the GT550M video card and JBL sound.

Everything was perfect until I tried to take advantage of the nvidia video card.  I figured it would require some form of restricted drive to get working but when I saw that nvidia has a driver download for linux I didnt figure I would have many issues. Boy was I surprised.

5 hours into trying to get this work and my brand new laptop sits on my desk, powered down because I cannot get the drivers to work.  I either have a broken boot up (wont boot in fact) or I have to settle for the default resolution and graphics ubuntu gives me from the fresh install.

I absolutely love linux but is a friggin dang shame that such popular video cards are not supported better.  The first laptop I have ever bought that had higher end hardware and it seems I will have to, after all this time, revert back to Windows to get use out of it.  

Right now, I dont know which is worse.  I either continue to use linux and apparently dont get to take advantage of the better hardware or I have to use Windows.  And I have yet to see what it will take to get the Waves Maxx Audio 3 working fully.

Someone please tell me that getting nvidia working is not as hard as the last five hours have indicated.

---

### Post by Redblade20XX on 2011-10-22
Hey, I would recommend you to do a fresh install and see if this helps!
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) ;)

- Red

---

### Post by 23dornot23d on 2011-10-22
Interesting read too ..... but a slightly different card Zotac GeForce GTX 550 Ti 

[http://ubuntuforums.org/archive/index.php/t-1833930.html](http://ubuntuforums.org/archive/index.php/t-1833930.html)

---

### Post by SyntheticShield on 2011-10-22
Well I have been sorta working along those lines.  I downloaded the Nvidia driver for linux straight from their website.  I got everything set to run the installer but in order to do that I have to drop out of x.  Well, the command 

sudo /etc/init.d/gdm stop
sudo service gdm stop

dont work.

So I did some searching and found another command

sudo service lightdm stop

That works in that it stop the graphics server.  However, it drops me back to a blank screen and I cannot run any commands.  And heaven forbid if there be an up to date reference guide on how to use the recovery console which I have been unsuccessful in doing.

So two more hours now and Im no further along.  It should not be this difficult Canonical.  Why in Gods name would you make it so difficult to get around the operating system?

So until I find a reliable way to get to a recovery console, tty or stop the x server and still run the nvidia installer Im just plain stuck.  I wanted so bad to use Ubuntu but I am quickly coming to the conclusion that I will have to go back to Linux Mint.  Not that the installation issues will go away with that, but at least I will have EASY access to things like a recovery console where I can SOLVE issues I run into.

---

### Post by SyntheticShield on 2011-10-22
> **23dornot23d said:**
> Interesting read too ..... but a slightly different card Zotac GeForce GTX 550 Ti 

[http://ubuntuforums.org/archive/index.php/t-1833930.html](http://ubuntuforums.org/archive/index.php/t-1833930.html)


Oh, and thanks Red for posting, I appreciate you trying to help.

23dornot23d, I did a fresh install and tried installing the restricted drivers.  Did not work.  I did a new fresh install and tried installing the nvidia-current from the ppa.  All I got out of that was a non booting machine and because Ubuntu has apparently made it so difficult to get tot a recovery console I could  not fix the issue.  I did another fresh install and tried the ppa again after finding some new information.  Yet another non-booting machine.

Ive done a couple more fresh installs so far today trying to work all this out and quite frankly I am just about to the point of just punting and going back to what I know.  As I mentioned above I was REALLY wanting to use Ubuntu but its just not worth all this time to get set up.

And its not that I wont have to invest time in Linux Mint or some other Ubuntu based distro to get up and running with the nvidia video, but at least I will be able to find things, have recovery options, etc.

Im not trying to be a jerk or difficult or anything like that.  Im just really really peeved that Canonical would make things so difficult.  How do they expect common everyday computer users to use their software if they cannot do simple tasks like get a video driver installed?

---

### Post by 23dornot23d on 2011-10-22
To save you re-installing .....

In the grub boot menu .... there should be a second choice for the kernel that you are
using ..... its the recovery mode as such and should go in to a screen that allows safe-graphics selection ....

But I guess you have had enough messing about ...... the 280.13 driver may be the one.

I also had to mess about with mine ..... thing is once its fixed thats it ..... away you go .....

I keep advising people to hang on a month and try again as some things may sort themselves out ...... after all 11.10 as only been out a week ..... the one Mint uses is basically 11.04 ...... so it has had six months to get things sorted out ....... plus there own little tweaks here and there.

X-swat is something to search on ...... but other than that its going to be difficult to help 
you here as you cannot get the safe mode up .......

I actually went into synaptic .... removed everything to do with Nvidia .... 
also removed the 

/etc/X11/xorg.conf 

file ..... too ....... 

then I re-installed Nvidia-Current ........ to get mine working 

But who knows ........ if it will work for yours .....

Mint is good and its only 6 months old anyway ....

---

### Post by SyntheticShield on 2011-10-22
23dornot23d thank you for your reply.  You are correct and it is an important consideration that 11.10 has only been out a short time.  However, the Nvidia issues seem to have persisted before that though.

I will have to see if I can get the grub menu to come up as it normally doesnt when I boot but I will work it from that angle to see what I can do.  Hopefully I can get it working.  I will report back if I do and what I had to do to get it to that point.

---

