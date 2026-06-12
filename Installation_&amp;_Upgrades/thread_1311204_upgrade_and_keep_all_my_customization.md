---
title: "upgrade and keep all my customization??"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by ronewolf on 2009-11-02
well, this should be a simple question with a simple answer, but after mucho research guess that is not the case.

as most do, i have not only changed from the default (in my case netbook remix) package list (for instance removing most games and adding some useful apps....), but i have also made various config changes (such as the hack to disable the touchpad when keying). now on 8.04 but want to get to 9.10 (don't i?).

so seem to be two paths to do this. one is to do 4(!) updates 8.04->8.10->9.04-.9.10. ugg, seems like a risky and time consuming path. also, i have poulsboro drivers to bring along.

so maybe better to do a fresh install. in that case, what i'd like to do is to create a fresh 9.10 system on a usb device, apply all of my changes to that stick (packages, configs, ...), try it out for bit, and then bring all of that back onto my hard drive as my standard boot. isn't this what 99% of end users would want?

so i am able to create the 9.10 usb install and bring over my package list (mostly), but what about the configs and other files that are in various system folders? how do i get those to the new system? right, i don't have a list of those changes made over the past year.... and then, once happy with the new system, how to get it back to my hard drive.

am i right that this procedure doesn't exist? i hear linux guys talk about doing something like this, but don't find the tools or clear instructions anywhere.

---

### Post by fancypiper on 2009-11-02
Would you have a separate partition for /home or other storage?

---

### Post by ronewolf on 2009-11-02
> **fancypiper said:**
> Would you have a separate partition for /home or other storage?

my hard drive seems to be a single partition. i'm gathering from reading other threads and from your question that this is not the best setup. so, implying that it would be better to have /home in a separate partition, can i do partition an in use drivce without wiping my disk? maybe a better question for another thread? and likely answers elsewhere - i didn't research yet.

on the other hand, i could copy my /home to a usb drive and then copy it back. so maybe not a big issue.

however, to my original question, i am pretty sure that there are config and other changes that i've made that are not in /home but are scattered around in various system and app folders.

---

### Post by fancypiper on 2009-11-02
Most config files for the system in the /etc directories with a few scattered around in /usr/share/<appname>/etc directories.  To see exactly what config files you have, use this command:

locate /etc | less

I have heard there are problems with using nautilus to copy the files so you might try tar

# Copy Directories using tar
# [http://www.linuxdevcenter.com/pub/a/linux/lpt/18_16.html](http://www.linuxdevcenter.com/pub/a/linux/lpt/18_16.html)
# Both source and destination directories must pre-exist
cd /source/directory

Good luck!
tar cf - . | (cd /destination && tar xBfp -)

---

### Post by ronewolf on 2009-11-02
> **fancypiper said:**
> To see exactly what config files you have, use this command:

locate /etc | less



thx for the quick replies.

locate is not an command on my ubutnu, but i find 'locate' in syntapics (not installed) described as 

"maintain and query an index of a directory tree
updatedb generates an index of files and directories. GNU locate can be used to quickly query this index."

if helpful, i'll install and run it, but my /etc has over 2,000 files. how does having a list of those help me bring whatever i've changed forward to a new OS? are you implying that, using tar, i copy my existing /etc over that of the new system? i'd be surprised if that worked. but i really don't know.

---

### Post by fancypiper on 2009-11-02
I would use it more carefully when moving files in your old /etc over to your new installation as there are loads of changes from Ubuntu 8.04 to Ubuntu 9.10, so lots of those settings will be outdated or replaced. Unless you have done a lot of tweaking of the operating system, you will find that the vast majority of configuration files will be found in your /home/<username> folder.

If you are very comfortable in the command line, you might consider it, but only as a learning experience.  I still recommend keeping the settings and data you have in /home and leaving /etc alone and change only by using the configuring tools.  If the GUI things mess up, you can always get the results you want in the command line (eventually, once a new user can follow directions and understand them.

A good man is easy to find and good info isn't much harder.

---

### Post by ronewolf on 2010-01-02
i'm getting more comfortable with the idea of moving forward by going with a fresh install of Karmic and then copying my home directory over it. indeed i get the following clear advice in a private conversation...

[quote=nanotube] ... doing a clean install is a better deal anyway. back up your docs, do a clean install, stick your docs back in. i've done this myself many times, since i tend not to do an upgrade with every release.....[/quote]

i'm still hazy tho on how this could work? i mean, doesn't the new install come with its own new and updated . this and . that stuff for the home directory too??

well, maybe not, so i'm up for giving it a try. but i'd still be curious as to how this can work??

so any advice or reassurance would be welcome. in the meantime, i'll probably be back in a couple of days with the results. yes, i'll do this all on a stick first...

---

### Post by mikodo on 2010-01-13
I'm not sure how copying /home to the new clean install will bring everything you mentioned with it, but if you want to try it without having your subdirectory /home on it's own partition, maybe follow the advice in the thread I started here  [http://ubuntuforums.org/showthread.php?t=1371094](http://ubuntuforums.org/showthread.php?t=1371094) by following the part on copying and pasting /home contents to the new  install.

Also, jbrown96 (the first poster after me) uses another way to bring /home forward to the new install, I'm not sure if he is discussing having his /home on it's own partition first or not though. It is further explained by yet another poster further down in the thread. 

Good luck!

---

