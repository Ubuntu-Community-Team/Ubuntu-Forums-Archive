---
title: "Help me, which distro?"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by fela on 2009-09-03
OK, so I've been using Ubuntu for the last 3 years and consider myself a Linux 'power user' - I know alot about Linux, not afraid of the CLI, etc etc etc.

I'm looking for a distro that supports KDE (as that's my DE of choice), is stable (important), runs reasonably fast (not as important), doesn't require you to compile packages (not because I can't but because I don't want to have to leave my computer on for days on end compiling stuff) - and has alot of packages in the respositories. Also - I don't need or want any 'newbie' junk - one of the reasons I'm switching from Ubuntu. No need for any glamour, just want a nice working, speedy and stable system.

Right now I'm torn between Debian and OpenSuSE. Here is the info I've gathered about each distro:

Pros about Debian:
Rock solid stable;
Tonnes of readily available software;
Very configurable and good for 'power users';
Excellent package manager

Pros about OpenSuSE:
More bleeding edge software;
Actively supports KDE

Cons about Debian:
Not so much bleeding edge software;
Supports all desktop environments, so I gather that it can't give so much time on developing new KDE features, fixing KDE bugs, etc.
Don't know if it supports KDE 4.3 - anyone know this?

Cons about OpenSuSE:
Not such a good package manager, although don't know (I've only ever used apt);
Not as stable;
Has lots of newbie junk such as Yast (I prefer to configure stuff through text files myself);
Not so configurable;
Not as fast (goes without saying)

So, which distro do you think, out of these two, would be best for a Linux junkie who loves the command line and needs a good, stable KDE4 environment to work in?

I'm switching from Ubuntu mainly because it seems centred around GNOME rather than KDE.

And, please tell me if it's possible to get KDE 4.3 running on Debian  5.0.

Thanks ;)

PS. I voted debian, just because that's what I'm leaning towards right now.

EDIT: if I choose debian, should I go with the 'stable' or 'testing' release? I want fairly new software, but I also want good stability. Thanks.

---

### Post by SuperSonic4 on 2009-09-03
From those I would pick OpenSUSE because it's more cutting edge and reasonably stable (debian will be more stable but it's much older - I feel honoured to have seen a new version of debian in my lifetime!) although it's been a while since I used either. Plus you don't have to use yast ;)
Have you thought about giving Mandriva a try though? Also I highly recommend **Arora** as a web browser :D


edit: Here is a list of kde distros from distrowatch: [http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=KDE&architecture=All&status=Active](http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=KDE&architecture=All&status=Active) 
You might want to be more specific if you search yourself

---

### Post by snowpine on 2009-09-03
Hi Fela, you are going to have to make a decision between "stable" and "KDE 4.3". :)

The "stable" branch of Debian (Lenny/5.0) uses KDE 3.5. KDE 4 is in the "unstable" branch, which will become next year's stable (Squeeze/6.0). If you are willing to use KDE 3.5, Debian Stable is an excellent distro otherwise.

I've never used OpenSuse, so I won't comment on that.

Because KDE 4.3 is brand new, by definition you will only find it in newer releases.

---

### Post by SnowRider on 2009-09-03
Have you tried kubuntu?

---

### Post by Simian Man on 2009-09-03
I personally can't imagine using Debian for a personal desktop system.  If you want reasonably up to date software, you will have to either use the experimental repos  or install stuff manually which defeats the point of having big repos.

Definitely go with OpenSuse or Mandriva.

---

### Post by snowpine on 2009-09-03
> **Simian Man said:**
> I personally can't imagine using Debian for a personal desktop system.  If you want reasonably up to date software, you will have to either use the experimental repos  or install stuff manually which defeats the point of having big repos.

Definitely go with OpenSuse or Mandriva.

Hi Simian Man, I agree that Debian Stable is ultra-conservative (like using Ubuntu LTS), and Experimental is ultra-bleeding-edge. However, in betwen those two extremes there are two other options:

"Testing" aka "Squeeze" is the testing ground for the next release (6.0). It is my #1 recommendation for most desktop users. The packages are a good compromise between stability and newness. Debian Testing is roughly the same as using a current Ubuntu release. 

"Unstable" aka "Sid" falls between testing and experimental. It is very up-to-date but also not quite as dangerous as people sometimes think. Ubuntu is based on a snapshot of Sid.

Two other compromise options are "mixed" testing/unstable and sidux (an independent project, based on Sid but with some stabilized packages).

In other words, Debian is an infinitely flexible distro, able to satisfy the needs of most users. It is not just the "super stable, outdated" distro that a lot of people mistakenly believe.

---

### Post by fela on 2009-09-03
Thanks for the replies.

Right now I'm downloading a netinstall image of Debian testing (squeeze) to a USB stick, I'm gonna install it and play with it for a week. I see that it includes KDE 4.2, I'm fine with that and that's the version I'm running right now (I could always install 4.3 via SVN I suppose if I really want it). If it really is too old for me I'll reinstall OpenSuSE (or something else) over it.

I might try OpenSuSE in a VM or in a different partition, but I want to get a running Debian testing OS first. I have 2 linux partitions, one for stable and one for bleeding edge.

---

### Post by fela on 2009-09-04
I installed Debian yesterday and today - I installed the base system through a netinstall, and then (once the system got up and running) installed kde4.2, pulseaudio, etc etc.

I much prefer it to Ubuntu, I just love its flexibility and complete support for any choices you might make - such as which kind of install, what programs, which architecture (debian supports what, 11 different CPU architectures? I forget ;)).

Initially I had some problems installing it, it didn't seem to recognize that I wanted a separate boot partition as grub doesn't like XFS. In the end I just stuck it all on one ext4 partition (fine for me ;)). It might have something to do with the USB installation media/setup though. But now it's up and running and I'm lovin' it! I'm so glad I chose it over opensuse actually, it just seems much more 'community driven' - I did do some research about opensuse and I found out that:

1) Novell seem to like making deals with Microsoft...me no like :(

and 2) it seems pretty much the same as Ubuntu in terms of the goal of the distro, whereas Debian seems just about right for anyone.

Now I've just got to get KDE 4.3 from the subversion...

Or does anyone know of an easier/quicker (repo) method for installing KDE 4.3 on Debian Squeeze (testing)? D'you reckon I could just download all the required debs from the unstable debian repo? I doubt it somehow - and I don't want to break my OS before I've even set it up!

Cheers :)

---

