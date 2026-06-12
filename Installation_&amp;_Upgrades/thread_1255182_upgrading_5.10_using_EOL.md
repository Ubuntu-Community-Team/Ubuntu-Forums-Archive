---
title: "upgrading 5.10 using EOL"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by dvdljns on 2009-09-01
I am trying to uprade using the instructions for the EOL.instructions posted here.  [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades). I will try to upload a snapshot of my results but basically it tells me I need to use apt-cd to add my sources but there is nothing in the directions about how to do this.Can someone explain what I need to do.

---

### Post by slakkie on 2009-09-01
What you could do it download the alternate CD for 6.06 and mount it. And perform the upgrade. It should be the same as 

[https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

I have never tried it (as the author of the page). I only focused on network upgrades. I can give it a try, but I won't have anything ready this week (kinda busy).

---

### Post by drs305 on 2009-09-01
I think part of the problem with the wiki is that it is trying to upgrade you to 6.06, which is also now EOL. As I read the wiki, it says the 6.06 will reach it's EOL in June 09, so the 6.06 repositories to upgrade from 5.10 are probably no longer available on the main site.

It looks like the upgrade is trying to reference your Dapper CD. You might be able to remove the CD reference from the CD from the repository but I'm not an expert at how the EOL upgrade works. If you want to try, you can remove it via manual edit of /etc/apt/sources.list (put a # symbol in front of the CD reference near the top of the file), or untick the CD reference in Synaptic.

That being said, and whether or not that is the problem, trying to upgrade from such an old release is bound to be a headache (as you have seen). If I could tell you how to do what you want I would, but I also have to recommend a fresh install of a current release.

If you are trying to save your current settings, a more productive path would probably be to make a separate /home partition and then perform a clean install.

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Good luck with your upgrade, no matte how you attempt it.

---

### Post by slakkie on 2009-09-01
BTW, you could also remove the cdrom entries from your sources.list and then rerun the update/upgrade.

---

### Post by dvdljns on 2009-09-01
> **drs305 said:**
> I think part of the problem with the wiki is that it is trying to upgrade you to 6.06, which is also now EOL. As I read the wiki, it says the 6.06 will reach it's EOL in June 09, so the 6.06 repositories to upgrade from 5.10 are probably no longer available on the main site.

It looks like the upgrade is trying to reference your Dapper CD. You might be able to remove the CD reference from the CD from the repository but I'm not an expert at how the EOL upgrade works. If you want to try, you can remove it via manual edit of /etc/apt/sources.list (put a # symbol in front of the CD reference near the top of the file), or untick the CD reference in Synaptic.

That being said, and whether or not that is the problem, trying to upgrade from such an old release is bound to be a headache (as you have seen). If I could tell you how to do what you want I would, but I also have to recommend a fresh install of a current release.

If you are trying to save your current settings, a more productive path would probably be to make a separate /home partition and then perform a clean install.

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Good luck with your upgrade, no matte how you attempt it.



Thats what the EOL is for. I found out what the problem is just do not know what to do about it. The problem is it is not changing the apt sources list. I need to be root but ubuntu does not let me login as root.:confused:

---

### Post by drs305 on 2009-09-01
> **dvdljns said:**
> Thats what the EOL is for.  ...  I need to be root but ubuntu does not let me login as root.:confused:

You edit /etc/apt/sources.list with:
```

gksudo gedit /etc/apt/sources.list

```

You are correct that there is a procedure for EOL upgrades. That is why I didnt' say not to do it. There are many ways to do things in Ubuntu. 

Having watched these forums I can tell you that I have seen many posts by users trying to upgrade through the various old releases that finally gave up and did a clean install. That's not to say it isn't sometimes successful and I hope yours goes well.

---

### Post by dvdljns on 2009-09-02
> **drs305 said:**
> You edit /etc/apt/sources.list with:
```

gksudo gedit /etc/apt/sources.list

```

You are correct that there is a procedure for EOL upgrades. That is why I didnt' say not to do it. There are many ways to do things in Ubuntu. 

Having watched these forums I can tell you that I have seen many posts by users trying to upgrade through the various old releases that finally gave up and did a clean install. That's not to say it isn't sometimes successful and I hope yours goes well.

```
I did su root gedit
```, then opened the file. It worked but I got a 404 message on that list. I think I will try setting up vi or something. I need to do 
some research. gedit copys the file with save at the end of it. I do not remember vi doing that. I do not have a way to burn a cd. I would love to install a clean copy of ubuntu but I am not buying one. The only reason I have this disk is a freind of mine took courses in linux and gave me this. He is a network security expert for the state of ny and keeps comps with all the major os networked at home. Since there are more flavors of linux he has more linux machines. When he gave me this disk he told me he leans toward ubuntu. now when someone asks about installing linux he advises ubuntu. I do not think those EOL sources are any good anymore. Thanks for the help and if you hear of something that might help, Please let me know.
I guess I will load win2k on it in a couple days and sell it. Thank god for windows.:)

---

### Post by dvdljns on 2009-09-03
> **slakkie said:**
> What you could do it download the alternate CD for 6.06 and mount it. And perform the upgrade. It should be the same as 

[https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

I have never tried it (as the author of the page). I only focused on network upgrades. I can give it a try, but I won't have anything ready this week 
(kinda busy).

Great Thanks for the info. If I run across a way to burn it to cd I could do a clean install. I wonder if I can find storage space a couple hours upload to that. If you wrote the page will you check to see what I am doing wrong or if the EOL sources are still good.

---

### Post by miklcct on 2009-09-03
6.06 is LTS. It will be supported until 2011. Therefore, you can use the main site/mirrors for upgrading to 6.06

---

### Post by slakkie on 2009-09-03
> **dvdljns said:**
> Great Thanks for the info. If I run across a way to burn it to cd I could do a clean install. I wonder if I can find storage space a couple hours upload to that. If you wrote the page will you check to see what I am doing wrong or if the EOL sources are still good.

> **slakkie said:**
> BTW, you could also remove the cdrom entries from your sources.list and then rerun the update/upgrade.

You probably have some kind of cdrom source in your sources.list. Remove them, or.. you could use the following sources.list and try the upgrade.

```

# Uncomment deb-src if you really need them
## Keepers
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

## Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

```

When you have "installed" this sources.list just follow the guide as is. It will convert this sources.list to something that you can use (change archive to old-releases) and then you should get to 6.06. Which is like someone already stated LTS and the repo's haven't been removed from the main servers.

From 6.06  you (probably?) want to upgrade to 8.04. Eventhough 6.06 is LTS the desktop version is not officially supported anymore, and 8.04 is the oldest release which still has both desktop and server support.

---

### Post by dvdljns on 2009-09-03
> **miklcct said:**
> 6.06 is LTS. It will be supported until 2011. Therefore, you can use the main site/mirrors for upgrading to 6.06

Thanks using this info and this site I upraded.

[https://help.ubuntu.com/community/DapperUpgrades#Upgrading%20by%20changing%20sources%20and%20the%20command%20line:D](https://help.ubuntu.com/community/DapperUpgrades#Upgrading%20by%20changing%20sources%20and%20the%20command%20line:D)

---

### Post by dvdljns on 2009-09-04
> **slakkie said:**
> You probably have some kind of cdrom source in your sources.list. Remove them, or.. you could use the following sources.list and try the upgrade.

```

# Uncomment deb-src if you really need them
## Keepers
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

## Optional, but recommended
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

```

When you have "installed" this sources.list just follow the guide as is. It will convert this sources.list to something that you can use (change archive to old-releases) and then you should get to 6.06. Which is like someone already stated LTS and the repo's haven't been removed from the main servers.

From 6.06  you (probably?) want to upgrade to 8.04. Eventhough 6.06 is LTS the desktop version is not officially supported anymore, and 8.04 is the oldest release which still has both desktop and server support.



I need to find out why this comp won't recognize more than 128 mb of memory. It is getting slow now that I have 6.06 LTS on it. I think 8.04 recomends 256 mb. I did a clean install then upgraded from there. Then loaded apache::Asp. Is there a way I can setup a system restore on this thing. Maybe use gzip to make a tarball on a second harddrive then a floppy that will wipe this drive and restore from the second.

---

### Post by dvdljns on 2009-09-06
I did not know how to get solved on the front of it,but I am happy with 6.06. I want to thank every one for their help. Now on to the next comp.

---

### Post by drs305 on 2009-09-06
> **dvdljns said:**
> I did not know how to get solved on the front of it,but I am happy with 6.06. I want to thank every one for their help. Now on to the next comp.

Congratulations. 

You can use the Thread Tools link near the upper right of the original post to mark it solved.

---

