---
title: "connecting prexisting users (other than the primary user) to a new install"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by w.g.hanna on 2009-05-30
just a tip - not a question - so somebody looking for an easy solution to a problem i encountered can find it on a search

i have my home and my os on seperate partitions.  when you have this, you can do a fresh install of any distro and keep your home folder intact.  

to make a seperate home partition from scratch is simple - all you have to do is install ubuntu, select the third option at the partition manager (the one that lets you choose your own partition), make a partition with about 20gigs, specify it as /, choose to format the partition, leave the swap partition alone, and specify the remainder as /home, and choose to format that partition too.  just remember - your starting clean so have your data backed up in something external.  

if you already have a home partition, psychocats has a tutorial on how to repartition without data loss - but it didn't work for me - so that's why i did the totally clean install and just moved my data over from an external hard drive.  

if you already have a seperate home partition, you can do a fresh install by using the partition manager to select the third option, selectthe os partition, designate it as /, choose to format it,  and then you must also select the partition that has your data on it, designate it as /home, but DO NOT choose to format it.  when you start up, your os system will interact seamlessly with your home folder without any need for terminal work or mounting.  

the problem i had was getting the os to recoginize my other users.  it let me log on, presumably because it created a username and password for me during the installation process, but my fiance didn't have a user name or password anymore.  what a drag!

so i tried to create one - but the user administration tool wouldn't let me.  it was a catch 22.  it wouldn't let me add a new user to attach a user name to her existing home folder, and it didn't present me with an obvious way make her homeflder accessible through the login.

but lucky for me, i installed kubuntu and xubuntu in addition to my regular ubuntu.  i like gnome for every day purposes - but when i move files around i like kde.  it gives me more information about seemingly duplicate files and gives me more options on what to do about it.  sometimes they're not really duplicates - sometimes they are.  gnome doesn't give me enough information to tell the difference, and kde both gives me detailed info and let me easily rename the file or folder.  and all it takes is a simple log out and selecting kde under the session menu on the login screen.  

so before i give up and cry for help on the forums, i decided to try to attach my fiance's account to a user name with the other desktops' tools.  i couldn't even figure out xfce - and sometimes i wonder why i ever let it take up the space - maybe one day it will earn its keep.  but kde did the job.  it was a little hard to find the right application - its not where i thought it would be in the control panel you can pick under the computer tab, but . . . there was an easy to use tool i found by selecting 'system administration' in the applications tab. 

and therein lies the beauty of linux.  i switched almost a year ago today - hardy was my first distro - out of necessity.  while some people like macs because they're easy and some people like windows because you have more options - i get the best of all worlds.  when i just want to get my work done and not worry about the computer, i roll with gnome becuase it always does the most sensible thing without even asking.  but sometimes i want my computer to what i want - sensible or not - and i'm willing to do a little work for it.  that's when i turn to kde.  so forget the debates over which one is better - with linux you can have it all.

anyway, thats my rant/ tip for the day!

---

