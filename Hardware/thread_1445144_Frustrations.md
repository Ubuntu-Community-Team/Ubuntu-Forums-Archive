---
title: "Frustrations"
date: 2010-04-02
forum: Hardware
---

### Post by hartz on 2010-04-02
Lately I'm getting more and more frustrated with Ubuntu.  Instability, unsupported hardware, general weirdness.

I'm a long time Ubuntu user - I used to Dual-boot Debian and Windows until I discovered Ubuntu circa 5.04.  Since then I've not had a single Windows file on my work PCs (I still keep a Windows-only gaming system around, though I don't have time to play so I don't know whether it can boot any more).

Ubuntu treated me well for these past 5 or 6 years, but now I'm starting to look elsewhere .... Debian, Mandriva, Fedora, openSuse, Mint, and more .... all vying for my attention.

My laptop (With Ubuntu 10.09) locks up hard sometimes when transferring lots of data on the Lan.  Gnome acts weirdly, sometimes Alt-F4 stops working, sometimes a subset of the running applications will seize to respond to mouse-clicks (but not to scroll-wheel events), sometimes the entire desktop stops responding to mouse-events (and sometimes Alt-F4 too)... though the keyboard still continues to give input to the application with focus.  On my GFs new Acer Aspire One, Ubuntu netbook remix (4.10) sometimes just don't respond to the mouse (can't even move the cursor), sometimes it locks up hard the moment you try to open any application, or even on boot-up.  Some 3G modems work and some doesn't (Mine works on her netbook, hers doesn't, though both of them works on my laptop.

The USB mouse on my laptop only works when plugged into one specific port, though everything else works on any port, and when booted from a live-CD, the same mouse works on any port.

There's more but I can't remember it all now.

My main concerns are the weirdness with the Gnome GUI, randomly stopping to respond to some events, effectively forcing a reboot.  The hard-hangs happens less often, but is still a big concern.  Overall I'm not happy with Ubuntu's stability.

My question is: Should I continue to lurk and search, hoping to find a solution, or should I switch to another Distro?  Which Distros works well on the Aspire One (Note:  It is the N214 / ZG8 distributed by Telkom in South Africa, not the more common N250 which, apparently, plays quite nicely with most distro's)

Have anybody had similar experiences?  Managed to solve them?

Regarding my Laptop; I've already decided:  I will buy a new hard drive and try OpenSolaris once the new release ships (hopefully in the next few weeks).  I know already that I will struggle with Codecs, VPN and Suspend/Resume, but those are not critical requirements for my laptop - access to Dtrace, ZFS, and Crossbow functionality is much more critical for my work.  For VPN I will use another OS (Ubuntu, most likely) as a guest under Virtualbox.

Thank you all for your thoughts, experiences and suggestions.

---

### Post by ronnielsen1 on 2010-04-02
Understand. I was a long time KDE user, didn't like the bloatness of the upcoming kde4, switched to gnome and recently switched to openbox. Once I figured out openbox - it works fast, great and you can make a beautiful desktop.

---

### Post by ronnielsen1 on 2010-04-02
[http://www.katonda.com/blog/944/call-to-save-opensolaris-fork-it](http://www.katonda.com/blog/944/call-to-save-opensolaris-fork-it)

> Call it a tragedy, or call it history repeating itself, but yet another UNIX-like operating system has been encumbered by a company with purely commercial interests. The OpenSolaris operating system, the last and only remaining Open Source variant of the original System V Release 4 operating system, has seemingly been sentenced to death by its patron Sun Microsystems, after being taken over by Oracle.

This had happened in the past, again with another UNIX variant, the original Berkeley Software Distribution, due to licensing issues with AT&T. The community had replied by preserving the open source part of the software and re-writing the encumbered parts. The result was 4.4BSD Lite, which although unusable, proved to be the bases of two of the most phenomenally robust and successful UNIX-like operating systems ever built, FreeBSD and NetBSD.

History repeats itself, as Oracle has more or less closed down OpenSolaris development. Their proprietary offering, Oracle Solaris, will be available in a 90-day trial version, after which one will have to pay for a license. Oracle has also made it clear that code for all the top-level enhancements in OpenSolaris may not be available, and thus may not be backported to OpenSolaris.

---

### Post by hartz on 2010-04-02
> **ronnielsen1 said:**
> [http://www.katonda.com/blog/944/call-to-save-opensolaris-fork-it](http://www.katonda.com/blog/944/call-to-save-opensolaris-fork-it)

Neither Sun nor Oracle have stopped or even slowed down work on OpenSolaris.

What has happened is that information about releases, schedules, etc must now follow Oracle processes and policies.  These are new to us, so news may be a bit slower to come out for a little while, releases may be delayed while getting settled into the Oracle way of doing things, etc - nothing unusual or unexpected about that as far as one big company buying out another big company is concerned.

Regardless, the whole idea of forking of projects and sharing and re-using of source-code is exactly what Open Source is all about - hooray to this project!  I hope it delivers some good results, and I hope that the fork(s) continue in the Solaris spirit of binary compatibility, stability and general greatness.

  _Hartz

---

