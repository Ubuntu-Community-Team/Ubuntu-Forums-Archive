---
title: "Advice on upgrading/installing to Jaunty; /home on separate partition"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by cyberfin on 2009-05-04
Hi folks,

I would just like some advice as I'm going to do something I've never done before.

My /home is on a separate partition because I followed everyones advice when I installed Intrepid. It made sense. My HD looks like this:

[IMG]http://lh4.ggpht.com/_S2vmic2YFXc/Sf8C0DnExTI/AAAAAAAAAY0/cm7MSBhCDgk/ScreenshotGParted.png[/IMG]

Now, I'm looking to make the jump to Jaunty 64 bit, but I don't like the idea of upgrading directly mainly because I've configured and messed around with quite a few things and settings and would like a more or less clean start.

I've looked for tips on how to do this but I'm unable to find a guide to lean on to do it while having /home on a separate partition.

Can anyone give me an explanation of what to do or a quick guide? (or point me to one)

Cheers.

---

### Post by tgyorgyi on 2009-05-04
Do you mean that you want to leave the /home partition untouched when you do the clean install, or do you want to wipe the whole hard drive and have a new /home as well?

---

### Post by cyberfin on 2009-05-04
Thanks for the reply.

Yes, I would like to leave the /home partition untouched as it is my understanding that there are many perks to having /home on a separate partition (simplicity of a fresh install being one of them).

If it was a simple wipe everything and install I'd be more than capable of doing it (I count 7 full ubuntu installs/reinstalls so far).

What I'm looking for is for pointers on what I should be doing (or not doing) when installing Jaunty from scratch and how I would either during the install process or after, assign the /home partition as ... well, the home partition :); so I don't loose all my info and keep some configs.

Thanks for any input.

---

### Post by mikezila on 2009-05-04
When you do your install, just let it do it's thing on your root parition and once everything is up and running, mount your /home/ partition at /home/ on your root partition.  It's how I've always done it.

There's also options to do this in the partitioner if memory serves, but nothing is stopping you from just doing it after the fact save for having to set permissions on a few things.  You gotta make sure you set the owner and stuff of your old home folder to your new username on the fresh installation.

Just make sure you decline to format the /home/ partition, as by default it'll probably want to wipe it clean.

---

### Post by cyberfin on 2009-05-04
Thanks for the reply.

Ok well that's basically what I had in mind; just wanted to check it actually was that simple :P.

Anyway, I also thought on doing the following. To make sure that I won't have any compatibility problems and so on, I'm going to reduce the size of "/" and leave about 8 Gb free. On that space I'll then install Jaunty and let it configure grub as it normally would.

Once I've checked the installation, I'll mount /home as mentioned and configure/install stuff as I require.

After finishing everything, I'll just format the intrepid root partition and add it to the new Jaunty partition.

This way, should something go horribly wrong during the installation/setup process, I can always fall back on the Intrepid install. (I really don't wanna risk loosing anything)

Does this make any sense or am I just making things complicated?

Comments?

---

### Post by dabl on 2009-05-04
Your plan will work -- the caveat is, unless you carefully hunt them down and remove or rename them, the old hidden settings files (.mozilla, .xinitrc, .audacity, etc.) whatever they are, will still be there and the settings for those packages will remain the same.

For this reason, I stopped mounting /home as a separate partition, and just go ahead and put it in with the rest of the OS.  Then I symlink my actual data folders in from separate data partition(s), the real data folders being appropriately named "MUSIC", "PIX", "DOCS", etc. etc.  This way, the settings stay in /home and don't pollute my data, and in the event of a new installation, it starts with clean settings.

---

### Post by mikezila on 2009-05-04
I always hate the file system shuffle that fresh installs cause.

You could do that, for sure, but I'm not sure how the bootloader would handle it.  Sounds like it will work, but I've never tried that exact approach.

Looks good, but I'm not sure.

---

### Post by mikezila on 2009-05-04
> **dabl said:**
> Your plan will work -- the caveat is, unless you carefully hunt them down and remove or rename them, the old hidden settings files (.mozilla, .xinitrc, .audacity, etc.) whatever they are, will still be there and the settings for those packages will remain the same.

I believe this is his goal.

---

### Post by cyberfin on 2009-05-04
> I believe this is his goal.

Precisely. Well thank you all for your input. It's given me the reassurance that I needed.

I'll post the outcome. Tomorrow. I'm too tired to start now :).

Thanks again!

---

### Post by Bruce M. on 2009-05-04
I've kept my /home partition for 4 installs of newer versions of Ubuntu / Xubuntu, with no problems.

1. Backup your /home partition first.
2. in gparted:
-  create: / in old / partition - **and format it**
-  create: /home in old /home partition - **[COLOR="Red"]DO NOT FORMAT[/COLOR]**
-  reuse: the same swap partition

If all goes well, your system will all be there. If something messed up you can restore your /home from the backup.

I have yet to loose a single byte of info. Well, that's not true, I think my wifes "flash" games store game info in one of the root directories, (/var possibly?) but she just starts from scratch.

Have a nice day.
Bruce

---

### Post by Mr_Knuckles on 2009-05-09
Would there be any problems from using a separate /home partition with multiple linux installs? 

Different distros? same distro? 

I'll probably use Ubuntu as the main distro, but I'd like to use others.

---

### Post by mikezila on 2009-05-09
Eh, you could have some minor problems with old config files, but you won't have any showstoppers.  Most nonessential apps (like desktop apps, music players, webbrowsers, etc) store their preferences in your home folder in hidden folders.

But everything important is going to be in /etc/, which sharing your home folder has nothing to do with.

You shouldn't have any real problems, and actually it'll probably make it so that most apps use persistant settings accross any distrobutions you use!

---

### Post by cyberfin on 2009-05-10
> Would there be any problems from using a separate /home partition with multiple linux installs? 

Interesting thoughts; I could suggest trying to create a different user name for each distro but symlinking the folders that would share info across distros. That way distro-specific settings in certain programs won't be affected (of course you would have to hunt these down and make a list).

Anyway, I have news! :o

I finally got around to executing my plan. It failed. :( Not due to the idea, but due to the fact I already had 4 primary partitions on the HD, therefore not being able to create a 5th one for the new install.

I suppose this would have worked brilliantly if I had /home on a separate drive altogether.

In the end I just backed up certain things from / and did a fresh install and mounted /home in fstab.

Much better than I expected and all the settings are untouched (Compiz for example which I've spent a lifetime tweaking, started up like always after installing it fresh).

Thanks to everyone for all of your help. :D

---

