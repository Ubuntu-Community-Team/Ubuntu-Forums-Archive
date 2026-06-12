---
title: "Upgrading Hoary to Breezy with dist-upgrade"
date: 2005-11-04
forum: General Help
---

### Post by patsissons on 2005-11-04
Recently it has come to my attention that Kubuntu Breezy is now considered stable and I have been thinking about doing an upgrade from Hoary in the recent days.  I am however feeling a little threatened by the upgrade because of a bad incident when I tried to upgrade to an unstable breezy several months ago.  I learnt my lesson, that being, to wait until the Breezy repos are ready for production.  But even still, I am a little worried and I wish to make sure that a dist-upgrade goes smoothly on my system, as I do not wish to re-install Breezy from scratch like I did with Hoary a few months back.

So, as a precaution, I decided run a test.  A test to see what WOULD a dist-upgrade actually do?  My plan of action was the following:
[list=1]
[*]First acquire a DVD of the latest distribution of Kubuntu.
[indent]**not a problem, grabbed the torrent and the ISO was downloaded within an hour or two.**[/indent]

[*]Next was to burn the disc to a DVD so I had a (safeguard) hardcopy in case the unthinkable happens; and also because I would like to have a hard copy to possibly install on other computers.
[indent]**Unfortunately, my K3b is currently broken (or at least it would not burn the DVD), so instead i just mounted it locally to /mnt/breezy  and proceded to verify that it was properly mounted (which it was).**[/indent]

[*]Now that I had the Breezy disk mounted, I headed over to Synaptic and added the local directory as a breezy repository (deb /mnt/breezy breezy main restricted).  Unchecked my 3rd party / UBP / Uni/Multiverse repos.  And finally asked Synaptic to do a smart upgrade.
[indent]**I know I know, a smart upgrade isn't a dist upgrade.  Don't worry, this step was only to check if Synaptic reported any broken packages (which it did not).**[/indent]

[*]Now I'm ready to test out the dist-upgrade.  So I open a terminal and sudo su.  Do an apt-get update to reload my (temporarily) updated sources.list.  Then finish up with the big one: apt-get -qsu dist-upgrade > breezy.log
[indent]**Well it appears my test completed successfully.  However, the results were a little bit unsettling.  The results may be nothing to worry about, I am unsure, that is why I am posting this thread.  For confirmation, suggestions, and recommendations**[/indent]
[/list]

[size=+2]**_The Results_**[/size]
Well as you can expect the log is quite rotund and I don't think it belongs in this thread in its entirety.  So instead I will post my observations and more importantly my concerns.
[list]
[*]The first thing I notice is that a lot of the KDE apps are being removed.  I figure this is possibly because some of these apps are perhaps deprecated or no longer compatible with the new KDE.
[*]The next thing I notice is that some apps that I commonly use are being removed.  Just curious why a dist-upgrade would remove the xchat package.  Should it not be upgraded or replaced?
[*]One thing that really worried me is that the kubuntu-desktop package is being removed and **NOT** replaced or upgraded.  Now unless Kubuntu has renamed their packages, I was under the impression that this package was the base package for the Kubuntu desktop.  Removing it completely sounds to me like a very bad thing to do.
[*]Finally, this is not really an observation of the dist-upgrade log, but I am currently using the fglrx ati drivers.  I know that these drivers can be finicky and I'm a little worried that after the upgrade I will be *sans* X server.  Just wondering if any fellow fglrx users can give me a success story of a dual head setup working after an upgrade?
[/list]

Well thanks for your time for reading this (what now seems quite long) post.  Any and all answers, pointers, suggestions, and recommendations are welcomed and encouraged.  I hope that this post can be helpful to others in my position.


Pat

---

### Post by beefsprocket on 2005-11-04
> 
[LIST]
[*]One thing that really worried me is that the kubuntu-desktop package is being removed and **NOT** replaced or upgraded. Now unless Kubuntu has renamed their packages, I was under the impression that this package was the base package for the Kubuntu desktop. Removing it completely sounds to me like a very bad thing to do.
[*]Finally, this is not really an observation of the dist-upgrade log, but I am currently using the fglrx ati drivers. I know that these drivers can be finicky and I'm a little worried that after the upgrade I will be *sans* X server. Just wondering if any fellow fglrx users can give me a success story of a dual head setup working after an upgrade? [/LIST] You should be able to apt-get kubuntu-desktop and have most of your apps from before back and working with their old configs (since they are stored in your ~.kde folder).

As for fglrx, get everything upgraded and working first. Once you've done that, then upgrade the driver using mlomker's excellent how-to found here:
[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

---

