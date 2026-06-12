---
title: "Understanding Update Manager"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by ed bear on 2009-11-11
KEY ISSUES:
-What is the apt-get or update manager procedure for updating?
-Can it be configured to only download packages NOT already installed?
-Can packages be saved for re-installation?

I've been testing and learning about Ubuntu since my first Feisty Fox setup nearly two years ago.  My primary goal is to have a computer that isn't web-dependent - one that can work and be managed even if the whole web dies or decides it hates me.

Finally, in August, I set up dial-up service to try to go a but further than I could with only the CD (mailed snail-mail from Canonical - thanks!) and research at the library's terminals.

I'm on my third build of Ubuntu 8.04 Hardy.  Not yet having discovered a way to do a full, restorable backup (Drive Image won't handle Linux partitions at all), I just started over when things got messy.  I do like to experiment.

Unfortunately, dial-up download is quite slow, and update manager seems to want to do its thing in one big go.  I have to download larger (over a meg or so) updates one at a time and let them install, as there's no provision for interrupt/resume.  And as far as I can tell, it doesn't check to see if a particular update has already been installed BEFORE downloading it again!

My last installation spent 23 hours tying up my phone, but got caught up.  Then I ran update manager again, and it wanted to download it ALL over again!  Synaptic seems to use the same procedure. SO...

1. Is there any way to download ONLY things one hasn't downloaded before?
2. Is there any way to save and then re-install previously-downloaded updates for future rebuilds?

I'm already worried I won't be able to re-download Firefox 3.0.13 when they want to force us to 3.5x and I'm not comfortable with it yet.

BONUS QUESTION: is there anything that provides Drive-Image capability to ext3 partitions?  That is, the ability to save a partition so that it can be restored to a completely blank drive.  Drive Image does it by being a DOS floppy-based program, and I like that - you can restore even if the target machine has no operating system working at all.

Thanks for listening and, to those who take the time, trying to help.

ED BEAR

"Pity the poor in bandwidth, for they inherit the scorn of the profligate."

---

### Post by earthpigg on 2009-11-11
> 1. Is there any way to download ONLY things one hasn't downloaded before?
it does that by default -- when there is a new version of a package, it needs to download it.

> 2. Is there any way to save and then re-install previously-downloaded updates for future rebuilds?

yup! look in /var/cache/apt/archives. whenever it download's a .deb, it goes there. in your case, if you have the hard drive space, i would never type 'sudo apt-get clean' or 'sudo apt-get autoclean'.
> 
BONUS QUESTION: is there anything that provides Drive-Image capability to ext3 partitions?

dd - [http://en.wikipedia.org/wiki/Dd_%28unix%29](http://en.wikipedia.org/wiki/Dd_%28unix%29)




here are a few thing's ill point you towards:

[remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") (doesn't work with 9.10 yet, but works with prev releases)
[apt on cd]("http://aptoncd.sourceforge.net/") - name says it all :D
[Debian Stable]("http://www.debian.org/CD/http-ftp/#stable") - downloading all five DVD's will include damn near any package you could ever want... though it wont be the most up to date stuff. because the stuff is so "tried and true", though, security patches/updates will be minimal. Debian Testing is another option - what we call "Ubuntu" is actually built on a snapshot of Debian Testing taken every six months. Debian isn't as easy to install, but is otherwise very similar. You can either use someone elses broadband to download all five dvd .isos, or you can pay to have them mailed to you.

from there, you can install new stuff using the DVD's as your repository.

one more thing to consider: limit your updates to security patches only, or dont update at all. system -> admin -> software sources -> 'updates' tab -> uncheck stuff

there is a security concern with not even taking security updates.... but this concern is very minimal with debian stable, imo. the stuff in debian stable has been around a while.

---

### Post by ed bear on 2009-11-13
Well, thank you, earthpigg! That does cover a lot - most valuably, the caching site for downloaded packages.  I'd been searching for it.  I'll check out that restore link after leaving the Forum.

I did find a good answer to my primary question before logging back on: using Synaptic instead of Update Manager.  I hadn't realized Synaptic could cover all the same packages as UM, and it clearly shows what's in, what's not, and what's upgradeable. AND it has better explanation of what each package does, which is very useful.

But Upgrade Manager dos NOT seem to be selective - whenever I started it, it would download things that had already been downloaded.  It seemed to depend entirely on what I'd check-boxed, and not check what had come before.  While it's vaguely possible that EVERYTHING I tested was pdated before my next try, it's unlikely.

SO - am I misunderstanding UM's operation,
AND - is there any reason (other than auto-notices) to bother with UM at all rather than Synaptic?


ED BEAR
Second full incarnation of Hardy Heron 8.04 on AMD Athlon 850
(and Suzuki Bandit 1200S)

---

### Post by wojox on 2009-11-13
Synaptic is used for installing packages and it's dependencies.

Update Manager is used to update you when security updates and software upgrades are available.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by winotree on 2009-11-13
Remastersys now works for 9.10 -- I made a working iso this past weekend.  Information can be found at their forum [http://geekconnection.org/remastersys/forums/index.php?PHPSESSID=cd4fccc3c2a965320aaa04858f560275&](http://geekconnection.org/remastersys/forums/index.php?PHPSESSID=cd4fccc3c2a965320aaa04858f560275&)

EDIT - Just thought to mention that I used that iso to re-install my system to verify it's ability *to do what it does so well.*  :)

---

### Post by earthpigg on 2009-11-13
> is there any reason (other than auto-notices) to bother with UM at all rather than Synaptic?

not really. i never use update manager.

---

