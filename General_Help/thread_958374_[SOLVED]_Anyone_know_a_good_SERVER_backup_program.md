---
title: "[SOLVED] Anyone know a good SERVER backup program ?"
date: 2008-10-25
forum: General Help
---

### Post by dbyrne on 2008-10-25
I'm looking for a good backup program to run on my Ubuntu file server. This box has terabytes of websites, media and personal files, but no desktop, no console, no X, in other words no way to use any of the prettyboy personal PC type backup suites that need Gnome/KDE/etc. to configure them :)

What I'm looking for:

1. Server config only, via PUTTY;
2. Full backup monthly, incremental every day;
3. Exclude lists for directories, file types and individual files;
4. Ability to store in standard format (tar, gzip)

Any ideas gratefully appreciated, I've been looking without success for months. I don't want to kludge something together with rsync/tar/gzip if I cann possibly help it - I'm sure Ubuntu must have something better to offer.

---

### Post by TyTiger on 2008-10-25
im looking for the same thing you are :) I was using Nero BackitUp to back everytihng up on to DVDRW, but thats Windoez GUI Based. :/

---

### Post by gpsmikey on 2008-10-25
You might want to check out "Image For Linux" from terabyteinc.com -- I have been using the windows version for years and it works very well.  Their linux version can either be run as a program or from a bootable CD.  It is all command line driven.  A bit "geeky" but that should fit right in with the Linux mindset these days :lolflag:

They also have their own support newsgroups that work well.

mikey

---

### Post by dbyrne on 2008-10-25
Looks superb ! Unfortunately (as is usually the case with Ubuntu), the solution usually requires a whole bunch of hard work. The Image for Linux product requires the edd kernel module to be loaded, and on Ubuntu it isn't even built into the kernel, never mind loaded ...

So not having built a unix kernel for 20 years or so, looks like a trek to locate edd soource and figure out how to config and build a Ubuntu kernel first !!!

And they say it's not ready for mass market yet :-D:shock::roll:

---

### Post by gpsmikey on 2008-10-25
While I haven't used it integrated into the kernel, I have used it a lot simply by booting of the CD image and in that mode it works very well (granted, your server is down while you are doing this, but it does give you a good backup).

mikey

---

### Post by afbase on 2008-10-25
Use backup-manager

It is in the synaptic repository.  It is a CLI tool.  By default it can make a tar file of the file contents of a server on a given given time interval (say every 3 days or whatever.).

---

### Post by russlar on 2008-10-25
rsync will satisfy all your needs.

---

### Post by p_quarles on 2008-10-25
If I were in this position, I would be "kludging" together something with rsync, tar, cron and bash. There is no "better" than this -- there's just the faint possibility that someone has already "kludged" together the same thing, which is pretty much the same thing. We're not talking about an incredibly complicated script, here, so I would suggest doing that rather than searching for some pre-written script that may or not do what you want it to.

---

### Post by dbyrne on 2008-10-25
> **russlar]
rsync will satisfy all your needs. 
[/quote]

[QUOTE=p_quarles said:**
> If I were in this position, I would be "kludging" together something with rsync, tar, cron and bash. There is no "better" than this -- there's just the faint possibility that someone has already "kludged" together the same thing, which is pretty much the same thing. We're not talking about an incredibly complicated script, here, so I would suggest doing that rather than searching for some pre-written script that may or not do what you want it to.

Thanks guys, and y'know if I didn't have a life, this is exactly what I'd do :) Heck, I even did it for a living for a couple of decades ... and had a lot of fun doing it.

However these days I prefer to use code that thousands of others have bashed the bugs out of rather than re-invent yet another (yaawwn !) wheel. I have always intensely disliked the *nix competitors - although I guess there's only really MS left - but I hate to admit it: when it comes to it they're peddling boring family saloon cars against our string and baling wire home built soapbox carts. And I know which one I'd grudgingly buy first ...

@afbase: thanks, backup-manager looks like it'll do most of what I want, I'll give it a shot before giving up and backing up my Linux boxes using XP :(

---

### Post by The Cog on 2008-10-25
You might like this one:
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

---

### Post by dbyrne on 2008-10-25
Funny, I actually use backuppc to backup a bunch of PCs on our home network (which it does very nicely). Never thought of using it to backup the server but in principle it sounds viable. Hmmm, thinking hat on :)

Perfect, does everything I need, and incorporated into the overall network backup schedule ... thanks !

---

