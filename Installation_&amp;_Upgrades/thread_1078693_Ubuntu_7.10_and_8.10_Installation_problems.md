---
title: "Ubuntu 7.10 and 8.10 Installation problems"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by rhddallas on 2009-02-23
Okay. i am having two problems right now.
I will start with 7.10. i know it is old but it is reliable for me.
my graphics card on my laptop (Toshiba Tecra A8 ) was not fully configured when i plugged it into a projector. hence my screen size and many other things basically failing altogether. i was lucky and had about 1/4th visibility and was able to retrieve my files before i tried to reinstall. turns out my disk might be scratched / burned too fast. oh well. let me burn a new one
go thru the install again and the SAME thing happens and i remember correctly burning at 15x on my optical drive works correctly. that is how i installed it the first time (and it worked)
so now that drive is locked up (lucky i have a spare)
i still have info on that drive b/c i was duel booting with windows vista ultimate. i can retrieve the information by putting in a live disk but i cannot run it without the live disk. the vista partition is un-bootable. i can only retrieve files because the grub is still partially installed but still messed up. 
any suggestions? should i nuke the drive and reinstall everything? should i get a new drive?
if needed i can get screenshots.

i decide to forget 7.10 and my friends say 8.10 is completely reliable. okay might as well try.
get the install off the internet. nothing goes wrong of my knowledge. burn the disk and put it in. go thru the install. when i get to the partition manager, the live session basically crashes and wont let me go any farther. the message is along the lines of 'Partman has crashed.' and then 3 choices. 'continue' 'go back' 'quit'
i hit continue. install crashes and shoots me back 3 steps.
i hit go back. sends me back (as it states it would.)
i hit quit. hit kills the install and moves into the live session

any ideas on whats going wrong for 8.10? is it possible the crash is caused on possibly the same lines of 7.10?

(yes i tried to install on the same drive.) currently i am using my back up drive and i am NOT messing with the settings because it is nice at least having a working hard drive back up. haha

PLEASE HELP

---

### Post by zwygart on 2009-02-23
For boot problems, please post the Result.txt file of [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

For partition problems, it is the output of fdisk -lu. But this is also contained in the boot_info_script.

---

### Post by rhddallas on 2009-02-23
i dont think its much of a partition problem.
its more of an installation problem involving the partition manager.

---

### Post by zwygart on 2009-02-23
Try to make partition with gnome partition, leaving empty the sapce where you want to install ubuntu. In the install set it to Guided - Using teh biggest empty space (or something). 

If that crashes, post any indices. 
What do you mean by "basically crashes"

---

### Post by Therion on 2009-02-23
> **rhddallas said:**
> ... when i get to the partition manager, the live session basically crashes and wont let me go any farther. the message is along the lines of 'Partman has crashed.' and then 3 choices. 'continue' 'go back' 'quit'
i hit continue. install crashes and shoots me back 3 steps.
i hit go back. sends me back (as it states it would.)
i hit quit. hit kills the install and moves into the live session
I am sooooo feeling your pain right now.  I know EXACTLY what you're talking about and it about drove me nuts.  You're trying to set up your partitions and everything looks like it's ticking along just fine and then... BOOM!  For what appears to be no good reason you get an error-message saying partitioning has failed and you get looped right back to the partitioning tool.  And round and round you go, right?  Been there, seen that so many times it's a miracle I have a hair left on my head.

You want the bad news now, now, or now?  How about now?  The immediate "solution" was to install 8.04 and then do a dist-upgrade.

The long term solution was replacing my WD Raptor hard drive.  No clue why the Raptor was being problematic but once I switched it out, Intrepid partitioned it just like it should have.

Oh, and someone is going to come along and suggest you try using gPartEd to pre-partition your drive and THEN install Intrepid.  It didn't work for me.  

I'd suggest you try installing Ubuntu 8.04 and see how you like it.  Then, if you want, maybe consider doing a dist-upgrade to 8.10 but I'd give that serious consideration if 8.04 is as solid for you as it was for me.  Right now I'm vacillating between Ubuntu 8.04 (Hardy Heron) and Debian 5.0 (Lenny) and mainly** because **of Intrepid.

---

