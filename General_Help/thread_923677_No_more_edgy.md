---
title: "No more edgy?"
date: 2008-09-18
forum: General Help
---

### Post by spibou on 2008-09-18
I just went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and I no longer see edgy listed. Under "News" it says "Removed edgy". So where do I download edgy packages from now?

And some related questions: what are the differences between different "distributions" like gutsy, hardy etc.? Will packages for one of them work on the others? What is the right word to refer to them instead of distributions, is it "editions"?

---

### Post by -Zeus- on 2008-09-18
you can't get edgy stuff anymore, it's past it's life-cycle.  7.04, 8.10, etc are usually referred to as "versions".  I would recommend updating to Hardy 8.04.

---

### Post by spibou on 2008-09-18
Hmmmm , I don't like what I'm hearing. If I update will I have to load all over again all the packages I already have? What happens when Hardy 8.04 also gets obsolete? Does Ubuntu force you to continually update to newer and newer versions? How often do you have to do that?

---

### Post by oilchangeguy on 2008-09-18
> **spibou said:**
> Hmmmm , I don't like what I'm hearing. If I update will I have to load all over again all the packages I already have? What happens when Hardy 8.04 also gets obsolete? Does Ubuntu force you to continually update to newer and newer versions? How often do you have to do that?

no ubuntu does not "force" you to do anything. you have a choice. no operating system forces you to upgrade. there's still people out there who for whatever reason are using windows 95.

---

### Post by spibou on 2008-09-18
> **oilchangeguy said:**
> no ubuntu does not "force" you to do anything. you have a choice. no operating system forces you to upgrade. there's still people out there who for whatever reason are using windows 95.

But what do I do if I need a new package? For example I was thinking of downloading VLC after I've sorted out some other issues. Is my only option to go to the homepage of the utility (VLC in this case) download the source and compile?

---

### Post by oilchangeguy on 2008-09-18
> **spibou said:**
> But what do I do if I need a new package? For example I was thinking of downloading VLC after I've sorted out some other issues. Is my only option to go to the homepage of the utility (VLC in this case) download the source and compile?

that's just the way it is. operating systems and other software continue to evolve. you can keep using what you've got, or upgrade. you can always run 8.04 as a vm inside of 6.10.

---

### Post by mb_webguy on 2008-09-18
As oilchangeguy said, you don't *have* to upgrade, but a particular release is only supported with updates for a set period of time -- 18 months for a regular release, or 3 years for the desktop version of an LTS release.  

Also, upgrading is relatively painless.  All of the packages you currently have installed will remain, though some (or quite a few, in your case) of them may be updated to newer versions.  You can upgrade directly from one LTS release to another (i.e. from 6.06 Dapper Drake to 8.04 Hardy Heron), but otherwise I think you have to upgrade sequentially (i.e. from 6.10 to 7.04 to 7.10 to 8.04).

Unlike in the Windows world, one release of Ubuntu is not a completely different operating system from another.  It's somewhat more like a Service Pack.  Ubuntu is Ubuntu.  Ubuntu 8.04 is simply a more recent version of Ubuntu than 7.10, with more recent versions of software available in the repositories.

---

### Post by spibou on 2008-09-18
> **mb_webguy said:**
> As oilchangeguy said, you don't *have* to upgrade, but a particular release is only supported with updates for a set period of time -- 18 months for a regular release, or 3 years for the desktop version of an LTS release.  

Also, upgrading is relatively painless.  All of the packages you currently have installed will remain, though some (or quite a few, in your case) of them may be updated to newer versions.

If I decide to upgrade how do I go about doing it? Note that I bought my computer with Ubuntu preinstalled so I've never had to install Ubuntu (or any other distribution for that matter).

Will all the files under /home remain as they are or do I need to back-up everything and restore it from back-up after the new installation?

Will all the packages I already have be reinstalled automatically? For every package that gets reinstalled the corresponding man pages will get overwritten, yes? The reason this last issue is of importance to me is that in a number of man pages I have made modifications like added additional information.

And a final question which is academic but still important to me: why don't the Ubuntu people keep package repositories for older versions? Would it be hard for them to keep for example the repositories for edgy?

---

### Post by oilchangeguy on 2008-09-18
you can't upgrade from 6.10 to 8.04. it would be best if you can back up all of your data, and do a fresh install.

---

### Post by mb_webguy on 2008-09-18
Last things first.  Repositories must be maintained.  That takes effort and time that could be spent on developing and maintaining more recent versions of the operating systems, and Ubuntu has a limited staff available.  Older versions of Ubuntu (or of any software, realistically) simply can't be maintained indefinitely.  The LTS (Long Term Support) releases, which are supported for 3 years (for the desktop version, or 5 years for the server version), exist precisely for those people who don't want to upgrade frequently (with frequently being more often than every 18 months).

[This page]("https://help.ubuntu.com/community/UpgradeNotes") should explain a few things about upgrading Ubuntu.

You can upgrade from one LTS to another easily, and you can upgrade from one release to the next easily.  Unfortunately for you, the LTS releases are 6.06 and 8.04, so if you want to upgrade to the more recent LTS release, since you have 6.10 you'll either have to upgrade to 7.04, then 7.10, then 8.04, or you'll have to do a clean install of 8.04.  Personally, I'd go with the second option, since it's much less hassle and there's less likelihood of package breakages.

It's easy enough to back up your home directory, but you're unfortunately likely to lose those man pages.  You could back them up and restore them as well, but it's possible -- even likely -- that those man pages are out-of-date, so you'd benefit from getting the newer versions.

Installing Ubuntu is easy.  If Ubuntu came pre-installed on your computer, then it was probably installed to a single partition.  To make future upgrades easier, you probably want to change that so that your home directory is on a separate partition.

However, before you do anything else, you'll want to backup all of your files, including the configuration files in your home directory.  If you have Apache and MySQL installed, you'll want to backup your web files and databases as well.  You should probably also make a list of any software you currently have installed that you use regularly, so that you can reinstall them later.  On the bright side, there's considerably more software available in the repositories of the new releases, so it's possible that any software you might have had to install from source previously is now available in the repositories.

---

### Post by spibou on 2008-09-19
> **mb_webguy said:**
> Last things first.  Repositories must be maintained.  That takes effort and time that could be spent on developing and maintaining more recent versions of the operating systems, and Ubuntu has a limited staff available.  Older versions of Ubuntu (or of any software, realistically) simply can't be maintained indefinitely.

They could still keep the repositories for older versions unmaintained. Better unmaintained than nothing at all. In my case it would make my life much easier.

Anyway I've given it some thought and a fresh install is definitely out of the question. It's not just the man pages but changes in /etc/alternatives links, fixes of small bugs in various packages, changes in configuration files of various packages, various utilities of my own which I have put on /usr/bin etc. Trying to keep track of what will get overwritten with an install and what will not and then which parts of the new install can or cannot be overwritten by restoring my own stuff from back-ups would be a nightmare.

Thankfully I already have most of the packages I need and for anything new I guess I will have to resort to the traditional method of configure, make, make install ;)

Thanks for the help everyone and especially to mb_webguy for his detailed reply.

---

