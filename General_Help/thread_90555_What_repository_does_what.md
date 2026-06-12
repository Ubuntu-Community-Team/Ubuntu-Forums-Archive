---
title: "What repository does what?"
date: 2005-11-15
forum: General Help
---

### Post by Randy Sparks on 2005-11-15
Can somebody spare a few minutes to explain to me what the various Ubuntu repositories contain? 

As far as I can tell, there are four:

main (officlaly supported)
restricted (restricted copyright)
Multiverse (non-free)
Universe (Community maintained)

I assume "main" is, well, the main repository. All free software goes into here. 

But my questions are:

- what's the difference between "restricted" and "multiverse"? Isn't restricted copyright effectively non-free? 
- what's the point of "universe (community maintained)" if the whole point of main is that it's community maintained?
- what's the "backports" repository all about and who maintains it?

Many thanks in advance for help.

---

### Post by adwait on 2005-11-15
The rest of the stuff I don't know, but the backports repository consists of new versions of packages which are not included in the older version but are present in the next version of Ubuntu. So that allows you install the latest packages without having to upgrade Ubuntu to a version which may not be stable yet.

---

### Post by linux?? on 2006-01-01
This is the exact question I'm trying to find out as well, thanks Randy... although there don't seem to be any replies to it.

One of the things i'm concerned about is installing something which is not 'free'.  I see a number of sites (from searching sround) explaining what to put in the reps; which is all well and great - it's of help and no doubt solves many issues.  However, I want to find out the meaning of what they mean.  Kinda like teaching one to catch fish instead of just giving the fish. :)   I don't wanna end up installing something which is 'illegal' to have without a license or purchasing it.  (I don't know if my last sentence was from a MS world only, but it is something I'm used to, being someone who has grown up with windows.)

---

### Post by s_spiff on 2006-01-01
I wanted to know what all Reps should be there by default? I have three of them, but everytime I start SPM, it gives me some error, I have sported that error on another thread. Someone please help.

---

### Post by az on 2006-01-01
[QUOTE=Randy Sparks]
main (officlaly supported)
restricted (restricted copyright)
Multiverse (non-free)
Universe (Community maintained)

- what's the difference between "restricted" and "multiverse"? Isn't restricted copyright effectively non-free? 
- what's the point of "universe (community maintained)" if the whole point of main is that it's community maintained?
- what's the "backports" repository all about and who maintains it?
[/QUOTE]

Debian packages all have a package maintainer.  There are something like 14000 packages in debian.  There are 1000 or so debian developers.  To get all the packages working perfectly together and most of the developers on the same page is difficult, which is why Debian does not release often.

Ubuntu only officialy supports a small subset of theose packages.  That is why they can realse every six months.  All of those packages that are GPL-compatible are what "main" is about.

Some software is free to distribute, but not free to use the source code and change and redistribute.  This is restricted.

Some software is free to distribute (or redistribute) in some countries, but not in others.  It can be open source, but proprietary, it can be closed-source (binary-only) and proprietary, it can be distributed under a number of licences.  This is multiverse.

All of the other packages that are in debian, but not officially supported by the Canonical ubuntu team go into universe.  These packages are maintained by a crack group of packaging ninjas called MOTU (Masters of the universe)  They have a lot of work.

You make a backport by taking the latest version of a debian package (unreleased) and compiling it with the current stable toolchain - This is a backport.  JDong runs the packports project for Ubuntu.

---

