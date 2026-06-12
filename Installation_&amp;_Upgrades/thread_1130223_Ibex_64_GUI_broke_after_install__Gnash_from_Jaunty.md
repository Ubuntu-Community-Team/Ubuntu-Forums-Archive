---
title: "Ibex 64 GUI broke after install  Gnash from Jaunty Repos"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Rising Eagle on 2009-04-19
A little knowledge . . .

I'm at a loss. I'm running Ibex 64. Resisted installing any Flash player till now because web pages become too frantic. Installed Gnash 0.8.4 from Ibex repos. It displays only a small rectangular piece of video frame (buggy?). Got too smart for myself and set up Jaunty repos in my Ibex 64 synaptic utility and installed Gnash 0.8.5. During install, it did actually ask for permission to upgrade two quick things during the process. I said yes without paying attention (although it had never asked questions during a synaptic based install before). Now my GUI is hosed and I can't fix it.

Specifically, I boot up and get to blank tan screen and a moveable (but useless) cursor. Can't get network in recovery mode and so trying to reinstall xserver-xorg with root command line won't work because it can't resolve repos urls. I've tried to solve network issue with no luck.

I am now using the live CD to communicate online because my system is useless.

New tactic: Can someone tell me how to manually remove Gnash completely and then restore any changes that the install of Gnash 0.8.5 has made to my GUI?

---

### Post by utnubuuser on 2009-04-19
You can probably figure out what was changed by having a look at the dpkg.log in /var/log/dpkg.log

You might also be able to copy the appropriate files from a live CD to your hd to fix whatever you changed.

You should definitely go into /etc/apt/sources.list and comment out the entries for jaunty so they wont be used again.

Are you saying you have no access to internet if you're not in a gui environment?   Apt-get is not an option?

To get rid of gnash --  sudo apt-get remove gnash --purge

And you could try to restore your desktop with > cd /home/username
rm -rf .gnome2 .gconf .gconfd .metacity  -- this will restore a desktop to it's original state by removing user specific configuration files.
Though I'm guessing you'll have to re-install a lib** something or other that got updated when you added jaunty to the sources.list

You can also add the live CD to your sources.list - should just be a matter of uncommenting in /etc/apt/sources.list, then maybe re-install your desktop through apt-get with > sudo apt-get install --reinstall ubuntu-desktop

---

### Post by Rising Eagle on 2009-04-19
Thx Ubuntuusr,

I'm beginning to take some baby steps. I located the upgrade in the dpkg.log (this is a huge file!). There are 197 lines of gnash 0.8.5 related stuff. I'm not exactly sure what I am looking at, but I copied it into a separate text file so I can look at it easier. I'll get back to that. Although if anybody wants to look at it and give me advice, I'll post it. I'm not sure how to determine how each line might refer to a file on the install CD that I could copy over to replace the bad file on my HDD.

Good call on commenting out the Jaunty repos reference. I was wondering how to keep apt-get from going there. DONE!

You are correct about apt-get not being an option (at least for network downloading). I use root command line in recovery mode to access my system and it is a documented bug that Ibex has no network in recovery mode(Ironically, it's fixed in Jaunty). I tried to configure it, but can't get it working.

To try your other suggestions, I have to reboot into recovery mode and try it out. I do have a customized Desktop. Is there a way to restore it after I reinstall. Also, is there a utility that can read the 197 lines from dpkg.log and reverse out the process?

I do have another idea, I could upgrade to Jaunty. I have the alternate install image on my HDD which I can mount from recovery command line. Problem is, it keeps looking for network access instead of just using what's on the CD. Any suggestions for that approach?

---

### Post by Rising Eagle on 2009-04-19
I started reviewing the dpkg.log listing from the Gnash 0.8.5 install. Removing all lines except those that initiate a package upgrade, I am left with the following 14 software module upgrade references:

2009-04-18 01:07:17 startup archives unpack

2009-04-18 01:07:31 upgrade libc6-i386 2.8~20080505-0ubuntu9 2.9-4ubuntu6
2009-04-18 01:07:32 upgrade libc6-dev 2.8~20080505-0ubuntu9 2.9-4ubuntu6
2009-04-18 01:07:34 upgrade libc6 2.8~20080505-0ubuntu9 2.9-4ubuntu6
2009-04-18 01:08:12 upgrade libpcre3 7.6-2.1ubuntu1 7.8-2ubuntu1
2009-04-18 01:08:15 upgrade libglib2.0-0 2.18.2-0ubuntu2.1 2.20.1-0ubuntu2
2009-04-18 01:08:15 upgrade libxi6 2:1.1.3-2build1 2:1.2.0-1ubuntu1
2009-04-18 01:08:16 upgrade mozilla-plugin-gnash 0.8.4-0ubuntu1 0.8.5-0ubuntu1
2009-04-18 01:08:17 upgrade libltdl7 2.2.4-0ubuntu4 2.2.6a-1ubuntu1
2009-04-18 01:08:18 upgrade gnash 0.8.4-0ubuntu1 0.8.5-0ubuntu1
2009-04-18 01:08:18 upgrade gnash-common 0.8.4-0ubuntu1 0.8.5-0ubuntu1
2009-04-18 01:08:19 upgrade libxrandr2 2:1.2.3-1 2:1.3.0-1build1
2009-04-18 01:08:19 upgrade gtk2-engines-pixbuf 2.14.4-0ubuntu2 2.16.1-0ubuntu2
2009-04-18 01:08:19 upgrade libgtk2.0-0 2.14.4-0ubuntu2 2.16.1-0ubuntu2
2009-04-18 01:08:20 upgrade gnash-cygnal 0.8.4-0ubuntu1 0.8.5-0ubuntu1

Maybe it is only necessary to restore the config files associated with these files to restore my GUI. Can anybody shed light on that? Can anybody help me identify which config files are associated with these 14 modules and how to find/restore them?

---

