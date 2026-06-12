---
title: "Remove all extra language support?"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by floborg on 2009-01-20
My Dellbuntu machine came with support for many extra languages.  The update manager recently showed 520 updates available - most of which were language-related packages for languages I do not speak.

So far, I have used the [COLOR="Blue"]Language Support app (under System => Administration)[/COLOR] to disable support for everything except English.  That brought the list of available updates down from 520 to 39.

There are still a number of dictionaries and other language packages left on the system that are not needed.  I've run [COLOR="Blue"]"dpkg-reconfigure locales"[/COLOR] and it did **not** help.

[COLOR="Blue"]How can I clear out all these extra language packages for good without manually searching for them in Synaptic?[/COLOR]

Thanks in advance.

---

### Post by floborg on 2009-01-23
bump

---

### Post by floborg on 2009-01-27
bump

---

### Post by lime4x4 on 2009-01-27
this is probably what u want

Tip #3 - Getting rid of unnecessary locale data - For this tip, you need to download the "localepurge" package found in Synaptic Package Manager. "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the Sections button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the Search button. In the search window, key in the following text :

Quote:
localepurge
Did the "localepurge" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "localepurge" package name. Click on Mark for Installation. Now click the Apply button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish. Once it is done, a new window should popup that has a bunch of abbreviations on it. for example:

Quote:
en
fr
po
sp
ka
etc...
You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones. For example, I speak english, so I would select the "en" abbreviation. A french speaker would select the "fr" abbreviation. So on and so forth... Then click next. All done!

---

### Post by floborg on 2009-01-27
Thanks, but I did learn about localepurge while searching for answers.  Here's why I didn't use it:

> Please note, that this tool is a hack which is *not* integrated with
Debian's package management system and therefore is not for the faint
of heart. This program interferes with the Debian package management
and does provoke strange, but usually harmless, behaviour of programs
related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
Responsibility for its usage and possible breakage of your system
therefore lies in the sysadmin's (your) hands.

Please definitely do abstain from reporting any such bugs blaming
localepurge if you break your system by using it. If you don't know
what you are doing and can't handle any resulting breakage on your own
then please simply don't use this package.

This was in the package description.  It makes it sound like I'd be better off without it.

---

