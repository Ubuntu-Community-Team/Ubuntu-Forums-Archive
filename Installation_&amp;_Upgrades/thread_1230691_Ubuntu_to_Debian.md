---
title: "Ubuntu to Debian"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by techgeek314 on 2009-08-03
I had a wonder about converting an Ubuntu installation into a Debian one...

Could I edit /etc/apt/sources.list to use only Debian repositories and then use a sequence of commands something like

    aptitude update
    aptitude install aptitude apt dpkg
    aptitude full-upgrade

to convert the computer to Debian without rebooting?

---

### Post by ibuclaw on 2009-08-03
> **techgeek314 said:**
> I had a wonder about converting an Ubuntu installation into a Debian one...

Could I edit /etc/apt/sources.list to use only Debian repositories and then use a sequence of commands something like

    aptitude update
    aptitude install aptitude apt dpkg
    aptitude full-upgrade

to convert the computer to Debian without rebooting?

Truthfully ... no.

Infact, apt-get upgrade is not a supported way to switch between **ubuntu** versions either.

Also, bare in mind that Ubuntu has newer version packages, what you will be doing is essentially downgrading your system / doing nothing. And downgrading your system will break it indefinitely.

Not to forget that Debian split packages up different to that of how Ubuntu packages are built. ie: file ABC and DEF are together in the same package in Ubuntu, but are split into separate packages in Debian. This will cause unwanted conflicts.

The only way to switch to Debian Lenny is to install it from scratch.

Regards
Iain

---

### Post by snowpine on 2009-08-03
Why break a perfectly good Ubuntu install? Debian and Ubuntu are 95% the same, there is no real reason to convert... if you are running Ubuntu, you are basically running Debian. :)

Perhaps if you have a more specific goal/reason for converting that you wanted to discus... ?

---

### Post by techgeek314 on 2009-08-03
Not a major reason...  I'm just in the settling faze of distro hopping.  I used (perhaps a little bit out of order) wubied Ubuntu, then UNR, Ubuntu, Kubuntu, Fedora 10 briefly, Mint, Fedora 11 for awhile (stopped becase I didn't really want to be testing a company's software so that they can sell it, maybe isn't entirely true but I wanted deb instead of rpm), then Ubuntu again, Debian, and now I'm at Ubuntu.  I was considering switching again if I could do something like above, but that's probably a bad idea (this netbook can't stand unlimited operating system installs).  I'll probably just stop now.  Thanks for your comments, though.

---

### Post by snowpine on 2009-08-03
You really need to install virtualbox. :)

---

