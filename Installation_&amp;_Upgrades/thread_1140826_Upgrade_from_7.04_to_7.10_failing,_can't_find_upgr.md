---
title: "Upgrade from 7.04 to 7.10 failing, can't find upgrade tool or sig?"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by jpatokal on 2009-04-28
So I'm trying to upgrade a totally obsolete Ubuntu 7.04 (Feisty) to a mildly less obsolete 7.10 (Gutsy).  Patching up 7.04 to the final packages as per [this]("https://help.ubuntu.com/community/GutsyUpgrades") was no problem, but 7.10 seems to have hit End-of-Life just last week and now I get this:

# do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool

Basically, it can't even find the tool or its GPG signature.  What to do? :confused:  Here's my /etc/apt/sources.list:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

### Post by tommcd on 2009-04-28
Because 7.10 has reached end of life, upgrading to 7.10 is no longer an option. At least that is how I understand it. Anyway, you would not want to upgrade to a version that is no longer supported.

You options are to do a clean install of 8.04, 8.10, or 9.04. I would recommend 9.04 since it has been working very well for me.
You could also go with 8.04 if you wanted a long term support version that will be supported for a few years.

And welcome to the Ubuntu forums!

---

### Post by jpatokal on 2009-04-28
> **tommcd said:**
> You options are to do a clean install of 8.04, 8.10, or 9.04. I would recommend 9.04 since it has been working very well for me.
Unfortunately doing a clean install is not really an option, since the server in question has a very fiddly LaTeX install that would be exceedingly painful to rebuild from scratch...

> You could also go with 8.04 if you wanted a long term support version that will be supported for a few years.
Yes, my target is 8.04, but I need to get to 7.10 first before I can upgrade to it. ](*,)

---

### Post by magicfab on 2009-04-28
Perhaps try adding a 7.10 CD or DVD to the sources, remove all online sources, then retry.

7.04 and 7.10 EOL has been announced in many ways, many times. May I ask how you missed it ? Just trying to understand, not trolling.

Tx.

---

### Post by jpatokal on 2009-04-28
> **magicfab said:**
> Perhaps try adding a 7.10 CD or DVD to the sources, remove all online sources, then retry.
So you're telling me -- and this time it's me who's not trolling -- that, because 7.10 is now EOLed, Ubuntu has actually gone out of their way to remove all their online sources for upgrades?  Why on earth!?

> 7.04 and 7.10 EOL has been announced in many ways, many times. May I ask how you missed it ? Just trying to understand, not trolling.
"How did I miss it?"  How did you expect me to get notified?  I don't follow any Ubuntu news sites -- it's an operating system, for chrissake, the only thing it's supposed to do is work and keep on working, and on that count 7.04 has served me fine.  And until now I was under the apparently mistaken impression that "EOL" just meant "no more patches", it never occurred to me that it could possibly be so painful to upgrade your way out... ](*,)

---

### Post by jecompton on 2009-04-28
> **jpatokal said:**
> 
"How did I miss it?"  How did you expect me to get notified?  I don't follow any Ubuntu news sites


I agree completely. I have an old testing computer that I need to upgrade from 7.10 and I had no idea that they would shut off the sources for gutsy. If the EOL is announced only in sites ubuntu OS enthusiasts visit, it will alienate the sort of baseline average computer user ubuntu is trying harder to reach.

At the very least, there should be a notification when you apt-get or aptitude something that says ```
***** Warning! You must upgrade from
gutsy 7.10 soon (around Apr. 09) or you will
be unable to upgrade and will need to do a fresh install or
a lengthy forum jaunt to get things working again ****
```

If I, as someone who loves and uses Ubuntu as his primary OS hits a brick wall like this with an old machine, users who are ignorant of the latest computer trends will be lost.

---

### Post by Synchro on 2009-04-28
> **jpatokal said:**
> Until now I was under the apparently mistaken impression that "EOL" just meant "no more patches"

I quite agree. I don't know of any other project in which EOL means 'deleted'. It certainly adds a sense of urgency that was not apparent in any notes I saw. It seems a bit bizarre given that the old-releases repo works fine for an even older release! Is it just that gutsy has not made it into old-releases yet?

---

### Post by Synchro on 2009-04-28
Panic over: upgrading from the gutsy alternative installer CD works fine.

---

### Post by tommcd on 2009-04-28
Ubuntu has always supported the regular versions for 18 months; and the LTS versions for 3-5 years. This is clearly stated on the download page for all versions of Ubuntu. For example:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
The EOL is announced in the news section of the Ubuntu.com site also:
[http://www.ubuntu.com/news/pressreleasearchive](http://www.ubuntu.com/news/pressreleasearchive)
I agree that they should probably state that the repos will be taken down when a version reaches EOL though. I suppose maintaining servers for obsolete versions of Ubuntu is not cost effective. And the maintainers probably expect that people will upgrade before support ends.

---

### Post by jpatokal on 2009-04-28
> **Synchro said:**
> Panic over: upgrading from the gutsy alternative installer CD works fine.

So I need to download and burn this --

[http://old-releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso](http://old-releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso)

Then follow the instructions here?

[https://help.ubuntu.com/community/GutsyUpgrades#Upgrading%20using%20the%20alternate%20CD/DVD](https://help.ubuntu.com/community/GutsyUpgrades#Upgrading%20using%20the%20alternate%20CD/DVD)

Fine, let's give it a shot then...

---

### Post by jpatokal on 2009-04-29
Still no dice.  Upgrader starts up, but soon aborts with:

2009-04-29 12:20:27,794 DEBUG demoted: 'binfmt-support feisty-session-splashes gcj-4.1-base gij-4.1 gnome-cups-manager libdb3 libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a liblzo1 libportaudio0 libslab0 libstlport5.1 openoffice.org-filter-mobiledev ttf-baekmuk vnc-common xvncviewer'
2009-04-29 12:20:38,109 DEBUG Installing 'language-support-ja' (Distro KeepInstalledSection rule: translations)
2009-04-29 12:20:46,491 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'[FONT=monospace]

[/FONT]Needless to say, there are no packages on hold:

# dpkg --get-selections | grep hold | wc -l[FONT=monospace]
[/FONT]0

But apt.log lists broken deps out the wazoo, including this for language-support-ja:

Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Investigating openoffice.org-help-ja
Package openoffice.org-help-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to openoffice.org-help-ja 1
  Removing openoffice.org-help-ja rather than change openoffice.org-l10n-ja
Investigating language-support-ja
Package language-support-ja has broken dep on openoffice.org-help-ja
  Considering openoffice.org-help-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-help-ja
Package language-support-ja has broken dep on openoffice.org-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Package language-support-ja has broken dep on openoffice.org2-l10n-ja
  Considering openoffice.org-l10n-ja 10000 as a solution to language-support-ja 10000
Done

So how?  Remove it?  :confused:

---

### Post by magicfab on 2009-04-29
I normally ignore request for help that include trolls. Let's keep this constructive.

The assumption here is that if you trust an OS to drive a server or desktop, you would at least follow one resource about official news or announcements.

Clearly that assumption is wrong, I get it. Let's focus on getting you out of that situation, and improving it for other users.

Synaptic or apt could/should warn about this further. I am trying to determine where to file an appropriate bug and relaying this to some other colleagues internally.

@Syncro, you mention "upgrading from the gutsy alternative installer CD works fine." Could you detail what steps you took ? I'd suggest you upgrade to 8.04 ASAP, otherwise you risk the same problem in a few months.

jpatokal, language-support-ja may be removed by:

sudo apt-get remove --purge language-support-ja

If you get further errors, relay them here, I'll happily review them as time permits.

Regarding keeping all past versions of Ubuntu available, the only logical explanation I have for removing a version at EOL time is the costs involved in bandwidth and storage, not only at Canonical but also at all the mirrors. I'll inquire more about this precise corner case, though.

Good luck and let us know what happens.

---

### Post by slakkie on 2009-04-29
See my sig, it should help you :)

---

### Post by jpatokal on 2009-04-29
> **magicfab said:**
> jpatokal, language-support-ja may be removed by:
sudo apt-get remove --purge language-support-ja
If you get further errors, relay them here, I'll happily review them as time permits.
Thanks for the offer, but I've decided to give up on the upgrading.   The uncertain benefits do not outweigh the certain costs of stabbing wildly at it with a butcher knife and hoping I can repair the damage somewhere down the road.

> Regarding keeping all past versions of Ubuntu available, the only logical explanation I have for removing a version at EOL time is the costs involved in bandwidth and storage, not only at Canonical but also at all the mirrors. I'll inquire more about this precise corner case, though.
That's the weirdest thing of all -- you're already paying the bandwidth and storage costs for maintaining [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/), which has versions back to 4.10, including both 7.04 and 7.10.  The only thing that you're kneecapping is the installer :shock:

---

### Post by radixor on 2009-05-10
The issue is that Ubuntu is not upgrading its [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) file correctly.

If you notice, this is pointing to 'archive' vs. old-releases for some of the old releases. This is breaking on download.

The fix to this is to write a python script that uses a custom meta-release file to launch the upgrade, this worked on my system.

Please see attached python file and meta-release file.

Don't forget to follow the steps ( [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) ) post launching do-custom-release-upgrade!!!

---

