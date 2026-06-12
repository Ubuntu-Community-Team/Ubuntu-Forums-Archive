---
title: "Newbie needs upgrade Help!"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by lisadob on 2009-03-08
I'm a linux newbie and I'm trying to upgrade from version 6.10 to whatever the latest version is. My OS says the newest version for me available is 7.04 but whenever I go to upgrade the server times out or it says the update could not be completed. This is both running it from the installed version on my computer and directly from the cd I have as well. Any suggestions on how I can easily upgrade?

---

### Post by Neo_The_User on 2009-03-08
Applications > Accesories > Terminal

Type this in

```

gksudo update-manager -d

```

And... Upgrade.

9.04 is the latest you can get.

---

### Post by lisadob on 2009-03-08
thanks, that worked but then I ended up back where I began where it says "Could not download all repository indexes" (?) and it has a huge list of files it could not dl. Any other suggestions? I bought the cd so I wouldn't have to figure out how to dl this online but I may have to buck up and learn how I guess.

---

### Post by Neo_The_User on 2009-03-08
Hmmm... Let me see your sources.list file.

Terminal:

```

gedit /etc/apt/sources.list

```

Copy and paste the whole thing.

My dad has this error a lot when just updating the repos but I personally never experienced this.

[http://ubuntuforums.org/showthread.php?t=1090963](http://ubuntuforums.org/showthread.php?t=1090963) I made a post there. Might wanna check it out.

---

### Post by Partyboi2 on 2009-03-09
> **lisadob said:**
> thanks, that worked but then I ended up back where I began where it says "Could not download all repository indexes" (?) and it has a huge list of files it could not dl. Any other suggestions? I bought the cd so I wouldn't have to figure out how to dl this online but I may have to buck up and learn how I guess.
Feisty (7.04) has reached its end of life. Which means to get to a supported version could be a little difficult. The easier method would be to back up your important stuff to another medium and do a clean install of hardy (8.04) or Intrepid (8.10)

---

### Post by Neo_The_User on 2009-03-09
> **Partyboi2 said:**
> Feisty (7.04) has reached its end of life. Which means to get to a supported version could be a little difficult. The easier method would be to back up your important stuff to another medium and do a clean install of hardy (8.04) or Intrepid (8.10)

Yeah. I never "upgrade" my distros. I always do fresh installs.

---

### Post by vaibhav on 2009-03-09
On a relevant note, can someone suggest me which version to use: LTS or latest? I am currently using 8.04, and would like to know if there are any issues I need to consider before upgrading to Intrepid, so that I can decided whether to stick to LTS or go for latest. I basically want my system to JUST WORK, but having the latest versions also feels good.

---

### Post by Neo_The_User on 2009-03-09
I perfer 9.04 because of the later development odds and ends and XCB, glproto and all those good X11 / Xorg dev packages. If you don't need the latest bleeding edge development tools for everything, 8.10 would be the way to go. I personally dislike 8.04. 8.10 I find to be more stable due to Gnome 2.24, 2.6.27 kernel and some other good improvements you just can't get with 8.04. However, If you are a developer, 9.04 all the way!

---

### Post by Partyboi2 on 2009-03-09
> **vaibhav said:**
> On a relevant note, can someone suggest me which version to use: LTS or latest? I am currently using 8.04, and would like to know if there are any issues I need to consider before upgrading to Intrepid, so that I can decided whether to stick to LTS or go for latest. I basically want my system to JUST WORK, but having the latest versions also feels good.

If you want you system to "JUST WORK" then I would suggest sticking to 8.04 since you know it works + its a long term support version. If you where wanting the "lastest" you could always install a later version using something like virtualbox.

---

### Post by ugm6hr on 2009-03-09
I would strongly suggest you reinstall using either 8.04 (or 8.10 or 9.04 in  2 months).

The reason you get that error, is that 6.10 is not supported, and the repositories 9where the updates come from) have been removed (actually, just moved).

To upgrade, you would have to go 6.10 -> 7.04 -> 7.10 -> 8.04
This would just be a waste of bandwidth.  Save yourself the trouble by backing everything up and installing from scratch.

---

