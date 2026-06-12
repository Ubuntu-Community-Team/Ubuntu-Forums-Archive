---
title: "Reinstalling 9.04"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2009-07-11
Ok I screwed up my xserver and thats taking way too much time to figure out, so I want to just reinstall 9.04.  

How do I keep from losing things such as emails, various desktop settings, ect ect?

Thanks

---

### Post by earthpigg on 2009-07-12
boot from the live cd

go to places -> computer

find your hard drive with ubuntu installed

go to the /home/yourusernamehere on that hard drive

go to view -> show hidden files

all of those folders starting with a period (.) are hidden folders that contain settings and whatnot for specific programs.

copy everything you see to a thumb drive or something similar -> _*look at them and make sure you can find the stuff you backed up*_ that you dont want to lose. clicking around in .evolution, for example, and you should be able to find your emails and whatnot.

reinstall 9.04

copy the stuff from your backed up /home over onto your new and mostly empty /home.

---

### Post by merlinus on 2009-07-12
And to save yourself from having to do this next time you need to reinstall, or want a newer version, create a separate /home partition.

---

### Post by Daremo_06 on 2009-07-12
> **merlinus said:**
> And to save yourself from having to do this next time you need to reinstall, or want a newer version, create a separate /home partition.

How big is a large enough partition?

Also other than the contents of my home folder should I have to copy anything else over?  I have a 500GB drive that I use as my main storage drive so putting the /home/user folders is simple enough

---

### Post by earthpigg on 2009-07-12
> **Daremo_06 said:**
> How big is a large enough partition?

Also other than the contents of my home folder should I have to copy anything else over?  I have a 500GB drive that I use as my main storage drive so putting the /home/user folders is simple enough

you will still need to reinstall all the software and programs.... but once you do, they will use the settings from your /home instead of the default ones.

if you want to save yourself from having to download them all again, a lot of them should be stored at /var/cache/apt/archives as .deb files. a .deb file is the same as a setup.exe file in windows. back them up to your external hard drive, if you like.

as far as a seperate /home partition: it really depends.

some programs take up a lot of space in /home, some take up a lot of space in /. i have a 150 gig hard drive. my / partition is 35 gb and /home is 112 gb.... /home is 50% full, / is 16% full.

but i keep music and pictures and whatnot in my /home, so that accounts for about 35 of that 52 gb of stuff in my /home.

next time i reinstall/repartition this computer, i plan to do 15 gigs at / and the rest at /home.

```
df -h
```

on an existing ubuntu install will give you an idea of how big you should make each partition:

```
ep@ep-9:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
_/dev/sda2              35G  5.2G   28G  16% /_
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  240K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  164K  2.0G   1% /dev
tmpfs                 2.0G  964K  2.0G   1% /dev/shm
lrm                   2.0G  2.5M  1.9G   1% /lib/modules/2.6.28-13-generic/volatile
_/dev/sda1             111G   52G   54G  50% /home_
/dev/sdb1             259G  204G   56G  79% /media/disk
ep@ep-9:/$ 
```

i underlined the important stuff.

---

### Post by raymondh on 2009-07-12
For carrying apps/programs over (or with you wherever you go)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Daremo_06 on 2009-07-12
Heheh i like to cause pain apparently...

I decided to switch to 32bit version because of the hassles I have had with certain 64bit things like flash ect ect.

I assume I will lose some things right? or are all the preferences the same between various 32/64 programs?

Thanks for the help.. I'm getting there with this stuff, its just frustrating to not know it off the top of my head though i shouldnt expect that having worked with dos/windows since the early 90s

---

### Post by Daremo_06 on 2009-07-12
Ok here is what I have done so far.

Resized my 80g drive to give me an 8G partition.  I took this partion and installed it as ./ for my new 9.04 32b install.  I also set the original ./ partition to being my /home partion.  It still has the 64b 9.04 kernel and all my settings (as screwed up as some of them got yest).  

I also had copied my 3 user account home folders over to another storage drive.

Whats the best way to try to get everything back to where I was yesturday?  Mainly I am concerned about evolution emails, firefox favorites and pidgin settings/saved conversations.  The rest of my documents are all on my storage drive so nothing else really to worry about.

I had games and other things installed that arent part of the distro, but I can always re-install those.

Lastly, once I get everything back to how I want it, is this guide here still relevant for 9.04?  

[http://ubuntuforums.org/showthread.php?t=35087&highlight=partion]("http://ubuntuforums.org/showthread.php?t=35087&highlight=partion")

or is there a better way for 9.04?

Thanks for all the help and eventually I'll learn to not screw with things without having them backed up 1st :)

---

### Post by earthpigg on 2009-07-12
go ahead and pop the CD in and install.

manually partition.

ensure you set the mount point of the 8 gig / partition to / and format it -> ext3/ext4 (whichever you prefer).

set the mount point of your /home to /home. select 'do not format this partition.' you may have to move things around on that partition so as not to have duplicate /home directories over there. time will tell.

as far as backup and restore, search for 'backup' in add/remove applications.... plenty of easier ways to do it than the link you provided, if ease of use is your priority.

if exactetude is your priority, the KISS (keep it simple, stupid) command line way to get a backup is by using dd.

> man dd

if you use dd, ensure you do _*not not not*_ get the 'if' and 'of' parts of the command backwards.


(lol, ubuntu spell checker isn't correcting me... i guess _*exactetude*_ is a real word!)

---

### Post by Daremo_06 on 2009-07-12
Ok now i am up and running on that machine, but I havent done anything yet as far as copying over old /home/user folders.  do i just replace the entire home/user folder or do i do it one folder at a time?  What about applications that i did not get through synaptic?

thanks

---

### Post by earthpigg on 2009-07-12
> **Daremo_06 said:**
> Ok now i am up and running on that machine, but I havent done anything yet as far as copying over old /home/user folders.  do i just replace the entire home/user folder or do i do it one folder at a time?  What about applications that i did not get through synaptic?

thanks

it shouldn't matter where you got the applications from -- once the app is installed, it will see the settings in /home/username/ and use them.

keep in mind, however, that using settings from different versions of programs can sometimes cause troubles.... nothing that can't simply be solved by deleting /home/myusername/.appname, however.

i usually do it one folder at a time for specific apps i want, but you can copy the entire /home/myusername/ over if you want. its not something that can break your system. worst case, as i said, delete and it will simply resort to defaults.

---

