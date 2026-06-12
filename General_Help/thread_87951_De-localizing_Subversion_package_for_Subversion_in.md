---
title: "De-localizing Subversion package for Subversion integration"
date: 2005-11-09
forum: General Help
---

### Post by ranarion on 2005-11-09
Hello everyone,

I am running a standard Kubuntu (Breezy Badger) installation with a German locale (de_DE:UTF-8 ). I'd like to use Subclipse, an SVN plugin for the Eclipse IDE, but am experiencing problems.

I've read that Subclipse needs English SVN messages to work correctly. So I tried to dpkg-reconfigure locales and added support for en_GB:UTF-8 to my system. This went fine. 

However, trying to export LANG=en prior to starting Eclipse fails, and I have not found a way to persuade the svn command line tool to output English messages. Does anyone here have an idea what I did wrong?

Many thanks in advance!

---

### Post by asimon on 2005-11-09
Does 
```
export LANGUAGE=en_US.UTF-8
```
before starting eclipse help?

---

### Post by ranarion on 2005-11-10
[QUOTE=asimon]Does 
```
export LANGUAGE=en_US.UTF-8
```
before starting eclipse help?[/QUOTE]

Well, at least the command line client does use English messages now, thanks for your hint (btw: what is the difference between the LANG and LANGUAGE variables? I only saw LANG before...).

However, this does not affect the behaviour of the Subclipse plugin. As this is no Ubuntu package, I'll try to ask on their mailing list.

---

