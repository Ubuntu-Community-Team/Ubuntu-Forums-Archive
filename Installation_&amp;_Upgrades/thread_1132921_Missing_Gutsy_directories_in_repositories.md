---
title: "Missing Gutsy directories in repositories"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by nbr on 2009-04-22
Does anybody know why there are no Gutsy directories in any Ubuntu repository anymore?
I tried to install a package today and found out that gutsy is no longer in repos!
I googled for some info, but found nothing.

These are the contents of 
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
as of today, April 22nd, 10:55 am CST

Index of /ubuntu/dists
[ICO]	Name	Last modified	Size
[DIR]	Parent Directory	 	- 	 
[DIR]	dapper-backports/	12-Nov-2008 07:00 	- 	 
[DIR]	dapper-proposed/	12-Nov-2008 07:00 	- 	 
[DIR]	dapper-security/	12-Nov-2008 07:00 	- 	 
[DIR]	dapper-updates/	12-Nov-2008 07:00 	- 	 
[DIR]	dapper/	16-Dec-2008 16:19 	- 	 
[DIR]	hardy-backports/	12-Nov-2008 07:00 	- 	 
[DIR]	hardy-proposed/	12-Nov-2008 07:00 	- 	 
[DIR]	hardy-security/	10-Feb-2009 05:34 	- 	 
[DIR]	hardy-updates/	29-Jan-2009 05:38 	- 	 
[DIR]	hardy/	12-Nov-2008 07:00 	- 	 
[DIR]	intrepid-backports/	21-Feb-2009 05:35 	- 	 
[DIR]	intrepid-proposed/	22-Nov-2008 05:17 	- 	 
[DIR]	intrepid-security/	26-Nov-2008 05:15 	- 	 
[DIR]	intrepid-updates/	13-Nov-2008 05:32 	- 	 
[DIR]	intrepid/	12-Nov-2008 07:00 	- 	 
[DIR]	jaunty-backports/	12-Nov-2008 07:00 	- 	 
[DIR]	jaunty-proposed/	12-Nov-2008 07:00 	- 	 
[DIR]	jaunty-security/	12-Nov-2008 07:00 	- 	 
[DIR]	jaunty-updates/	12-Nov-2008 07:00 	- 	 
[DIR]	jaunty/	12-Nov-2008 05:13 	-

---

### Post by mistaquade on 2009-04-22
Yeah, I was trying to do the samething to no avail.  I know its out there somewhere just have to find it.  Can we use the ones for dapper or fiesty?

---

### Post by Partyboi2 on 2009-04-22
Gusty had reached its end of life (EOL) that is why the repos have been removed.

---

### Post by FredB on 2009-04-23
Gutsy is dead. You should move at least on Hardy Heron or to Jaunty Jackalope.

---

### Post by luvinit on 2009-04-23
This a shame because most of the people that I have introduced Ubuntu to use Gutsy on my recommendation, because my experience is that it was the last version to work really well. It is ok to move on, but a bad idea to take away the option for people to go back when they encounter problems that don't get fixed in the new version, or if they are subject to bloat with their old low ram machine. Not supporting it with updates is one thing, but keeping the repositories open is a good idea. There are some repositories on the DVD version which is probably still downloadable via bittorrent and other means, but it isn't the same thing as the full set.

---

### Post by Partyboi2 on 2009-04-23
> **luvinit said:**
> This a shame because most of the people that I have introduced Ubuntu to use Gutsy on my recommendation, because my experience is that it was the last version to work really well. It is ok to move on, but a bad idea to take away the option for people to go back when they encounter problems that don't get fixed in the new version, or if they are subject to bloat with their old low ram machine. Not supporting it with updates is one thing, but keeping the repositories open is a good idea. There are some repositories on the DVD version which is probably still downloadable via bittorrent and other means, but it isn't the same thing as the full set.
Eventually you should be able to use the deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) repos.

---

### Post by FredB on 2009-04-23
Gutsy, the last working version ? So, I've not using my computer with both hardy and jaunty (since alpha4) ? 

- Sigh -

---

### Post by aatheus on 2009-04-27
What puzzles me is that Dapper is still available in the main Ubuntu dists tree, while Edgy, Feisty and Gutsy are not. Someone asleep at the switch, or is it being kept there for personal/historical reasons?

Upgrading my machine at work to Hardy. Grumble.

---

### Post by oldos2er on 2009-04-27
Dapper's an LTS (long term support) release, so it has a longer life cycle.

---

### Post by jecompton on 2009-04-28
In case it's useful to someone, to upgrade from gutsy (7.10) to hardy (8.04) comment out all the lines in your /etc/apt/sources.list and then add the following lines:

```
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```

After that, do an apt-get update, apt-get dist-upgrade then uncomment the lines you commented before. You can remove the 'old-releases' lines I just listed.

Finally, do another apt-get update and apt-get upgrade.

I had an error with the human-theme on doing the apt-get upgrade. It stopped the whole upgrade. Fortunately you can just do dpkg --purge gnome-screensaver and then do the upgrade (if you need gnome-screensaver you can install again after the upgrade). Thanks to Mateo figuring it out and posting here ([http://ubuntuforums.org/showthread.php?t=767906](http://ubuntuforums.org/showthread.php?t=767906)).

Someone more knowledgeable should correct me since I just saw that if you're doing this through the cl, you should apt-get update-manager-core...

---

### Post by nbr on 2009-04-29
Thanks for the replies.
I agree with luvinit that not supporting updates is fine, but the repos should still be there.
In any case, I just found that the packages are still available at (as in jecompton's post):

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

---

### Post by luvinit on 2009-05-24
You might be interested to know that it appears that you can make your own dvd set of Gutsy repositories from the location listed below. Most people are probably ok with just disks one and two, but if you want more here it is:

[ftp://tuma.ui.edu/pub/ubuntu-repository/gutsy/](ftp://tuma.ui.edu/pub/ubuntu-repository/gutsy/)

---

