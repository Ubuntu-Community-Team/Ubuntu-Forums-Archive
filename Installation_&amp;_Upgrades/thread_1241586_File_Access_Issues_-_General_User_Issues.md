---
title: "File Access Issues - General User Issues"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by d-pearson on 2009-08-16
Hi there, I am a complete newby to Linux and have been trying to setup a media centre server, through my searching I decided to install Mythbuntu 9.04.

To work out the bugs and to learn how to use Mythbuntu I have installed it on my Mac through Parallels 4 (I know there are a host of other issues with this but so far so good :lol:)

In preparation for my setup I am in the process of using Handbrake to place video files on my external HDD and have been successful in setting mythtv in seeing the External HDD but I am having trouble with two areas:

1. I have a black box appearing in the centre of the screen when I manage my video's which states 'Enter IMDB No Manually' this box restricts the view. - Searching this forum I have found the fix for this in the video-ui.xml file but I cannot amend this file due to file permissions...this brings me to the second point

2. File Access and permissions - I cannot amend or alter file permissions. I'm sure there is a simple way around this but I cannot work out why as 'Administrator' I do not have access to all files and folders.

The main reason I have troubleshooted to this point is as when I add the metadata to the video files there is no artwork as the folder cannot be written to to store the artwork.

I hope this gives a fairly comprehensive overview of my issue and please bear in mind that I am not confident with Linux yet so any steps to resolve anything please treat me as a 1 year old :KS

Thanks you in advance for your help.
Dan

---

### Post by Partyboi2 on 2009-08-16
> Searching this forum I have found the fix for this in the video-ui.xml file but I cannot amend this file due to file permissions...this brings me to the second pointTo gain the ability to write to some files, you will need to use sudo to temporary give you admin rights. For more on sudo have a look at:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Can you provide a link to the fix?

---

### Post by d-pearson on 2009-08-18
> Can you provide a link to the fix?

Sorry for the delay in responding the link for the imdb box fix is here:
[http://ubuntuforums.org/showthread.php?p=7807194#post7807194](http://ubuntuforums.org/showthread.php?p=7807194#post7807194)

It links you to the page where it was reported as a bug and explains the fix:
[https://bugs.launchpad.net/mythbuntu/+bug/339880](https://bugs.launchpad.net/mythbuntu/+bug/339880)

Im going to give the sudo a try and report back! :P

---

