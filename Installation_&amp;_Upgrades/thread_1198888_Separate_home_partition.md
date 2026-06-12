---
title: "Separate /home partition"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by Kevbert on 2009-06-28
I plan to re-install a number of versions of Ubuntu and Kubuntu on my PC. Are there likely to be any problems with having a single shared /home partition which will be used by all instances (installations) of Ubuntu and Kubuntu ?

---

### Post by ridgeland on 2009-06-28
Hi Kevbert,

I hit problems sharing .files when the new Linux used a different package version than the old.  It just didn't work, for most it worked.

My view is /home is for OS settings nothing more.  I use /Data for all my music, photos etc and share that with our local home network with NFS.  I link to Firefox bookmarks (places.sqlite) so all the distros on my PC can share the same bookmarks file.  But only if they are all Firefox 3.x and not 2.x.  An example where a common /home doesn't work.  I also link to Thunderbird so any Linux partition can get new email and see old email.  For some simple settings like ~/.bashrc I copy it to /etc/skel before I create my user ID.  For some other settings I use a script that modifies some ~/.files but I need to move more of from the script and into etc/skel.

I like distro hopping and seeing what the new interface looks like by default.  I still clone in some must have items like .bashrc.

What is your reason for wanting to share /home?

---

### Post by presence1960 on 2009-06-28
I can tell you from experience that sharing a /home partition among different distros is not a good idea. The reason being your KDE config files and your gnome will be all in the same /home. If you do not have exactly the same packages installed on each distro there may be problems. Example I had some  panel applets installed in my Ubuntu but not in Kubuntu. When I would boot Kubuntu those applets would create error messages because they were not installed on Kubuntu. Then they would leave a different colored space where they would have been in the panel.

I would not share /home among distros. What you can do is create an ext 3 partition for your data to be shared among the distros and leave /home for each distro in /, don't create a separate home. These individual /homes in root of each distro will contain ONLY the setting & config files for that partitcular distro.

---

### Post by Kevbert on 2009-06-30
Thanks folks. I'll just use a separate /home for my main Ubuntu distro.

---

