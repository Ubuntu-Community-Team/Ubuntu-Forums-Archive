---
title: "how downgrade from 9.04 to 8.10"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by martinsill on 2009-05-24
Hi all!
 
I installed and used 8.10 during 6 months without any problem.... then I decided (really bad day that day) to upgrade to 9.04... and the problems started...
1. The audio stopped (no one of solutions I found was useful)
2. I can't install wine
3. I can't install skype (it seems something is moving now and maybe now it can work)
4. I can't install sop-player
5. I can't install picasa
...
so is there some way to downgrade to the previous, well-working 8.10?
 
best regards,
M.S.

---

### Post by cwsnyder on 2009-05-24
The bad news:  I haven't seen anything that indicates you can automatically down-grade to a previous version.

The good news: If you have your data backed up (not your entire /home, just the data), you can re-install Intrepid from CD/DVD by having it reformat and install.  You will have to re-install all of your applications after removing any vestiges of previous installations from your data manually.  That is why you do not want to backup /home and restore the entire directory structure.

Good luck!

---

### Post by hollowhead on 2009-05-24
I don't think there is without a clean install.  Isn't it possible to resolve these problems?

---

### Post by petterdyrdahl on 2009-06-03
I have been quite disapointed with the Jaunty release aswell, as I have had numerous problems with all kinds of stuff ranging from video to audio to printing, and even if I have been able to find solutions and workaround for most of the problems, there are still some that are basically unsolved, like the video thing (sticky, disrupted video, from a problem from the Intel support in the new software, as it appears...) and I am still wishing I was back in the "good old" Intrepid Ibex days where everything **just worked**.

So, anyway, after using ubuntu for about a year and with all the modifications and setup tweaks done, I am pretty reluctant to just popping in the Ibex cd and formating it all without making a copy of **all the important files first** 

Is it as simple as copying the /home folder, or are there more folders to copy? Someone said /etc? anything more?

Thanks for the feedback guys

---

### Post by Don1500 on 2009-06-03
I have gone back to Intrepid for many of the same reasons. Jaunty just didn't "feel" right. I've been using Ubuntu since Fisty and never had the kinds of problems that Jaunty gave me. I'll stick with Intrepid for now. I will be doing a hardware upgrade (New MB, uP, Video Card) in a few weeks and I have a spare Drive sitting around, I may try Jaunty then and convert completely if it works. I do have Jaunty working on my Laptop, but I keep the requirements pretty low on that.

---

### Post by 440roadrunner on 2009-06-03
I, too, upgraded, and was instantly sorry.   I've run Intrepid now for months on this Dell 9100 with few issues.   So I get this message that jaunty is available.  

Taskbar audio controls have no effect

Firefox  has frozen computer to point of requireing manual shut down 4 times in last two days

Firefox IS  slower.  various "button" activations are markedly slower.

I hate to start over,  (clean install)  but at this point it looks like the only way out

---

### Post by topher-t-mill on 2009-06-03
I was happy with jaunty till a recent upgrade which, has completely knocked out the boot up, I have tried various ways of reconnecting the kernel, to no avail, I tried to copy files using the live disk but would not let me so I have resorted to using a very helpfull Slax, Which at least allows me to extract important data and still use system, I have only been using Linux for 6 months, so whilst I like it, this is a major set back.
 During the upgrade I was asked for the latest Debian release, which I had and so used but this Kernel is somewhere in the system but can't be accessed either, so effectively I have swapped to Slax but would like to get Ubuntu back with out doing a disk backup and reinstall which by the sound of it need to be 8.10

---

### Post by kkempke on 2009-06-04
All, I too have tried 9.04 2 x on my Netvista, once as a clean install and my first attempt, then through 8.10 upgrades.. both complete failures.  I had to do a clean partition install to start over.  I was lucky that not much was installed so it was not a loss in time.   perhaps will be Jaunty in the future, but staying Intrepid right now.:D

---

### Post by Don1500 on 2009-06-05
One good thing about doing a complete re-install is you know how you want it set up now. You can put your partitions where you really want them and not "where they have to go". I made the W-XP partition the complete "C:/" drive (250 gig), then added a 1/2 terabite drive for the exclusive use of Intrepid. I might go back and devide the Intrepid drive into: 100 gig for Root, 395 gig for /home, 5 gig for swap, or some division like that.

---

### Post by ronparent on 2009-06-05
I did the downgrade yesterday. To retain most of my settings, before the downgrade I backed up my /home (to /bu-home). I then started the 8.10 live cd, did a manual install to the partition 9.04 resided in without formatting (to overwrite 9.04 with 8.10), and, for good measure took space out of the / partition to create a separate /home partition. Then without quitting the live session copied the contents of /bu-home to the new /home partition (overwritting it). I then rebooted to the new install. One unwitting bonus is that the new kernel from 9.04 was still present as the default booting option. It is working fine and seems to be superior to the older 8.11 kernel! Because of degraded functionally of 9.04 in handling of raid drives I am happier with the reinstalled 8.10.

---

### Post by LepeKaname on 2009-06-06
There is a way to downgrade without reinstalling the system. I did once and It worked:

Just in case backup your home and /etc/ directory as well any other place like databases websites, etc...

You need aptitude and synaptic and modify your apt/sources.lst

Change "jaunty" for "intrepid" in your repositories. Then, enter synaptic and select all your installed packages and use "Force version..." and select "intrepid". ... then try proceed.

After all, it may have some dependency problems (normally). Kill your X11 or go to console (but close synaptic). Run aptitude and proceed to fix your dependencies...  

It is not the best way nor the cleanest one, but I did it once and worked fine. Also take a lot of time, so I think the faster ans safer is to install it again.

I can not warranty this will work for you, so only do it if there is no other way.

---

