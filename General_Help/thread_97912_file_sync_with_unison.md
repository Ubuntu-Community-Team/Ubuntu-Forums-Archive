---
title: "file sync with unison"
date: 2005-12-01
forum: General Help
---

### Post by capaci on 2005-12-01
hey, i'm new to ubuntu and would like to know how i can install a newer version of a package than the one in the repository? right now the latest version of unison in the repository is 2.10. however, all of my other machines have 2.13 installed on them and the program is complaining about it. thanks.

---

### Post by David Valentine on 2006-01-19
I'm a newbie looking for the same info.  I downloaded the 2.13 version, extracted the binaries to /usr/bin, and then used the application menu editor to change where the unison link pointed.  That is a totally kludged setup, but it does the job.  I'd prefer to do it via apt-get, and keep my system clean, but I can't find a repository with the later versions in it.

[edit]

Ok, here's how

1.  add the backports repository (see the backports forum)
2.  run 'sudo apt-get update'
3.  open synaptic package manager, and voila!

---

### Post by tikey on 2008-03-11
I have a similar problem now. The current version of unison is 2.27.57 which supports the mountpoint option. The version in the repository is 2.13. I can't find a newer version in the backport repositories either.
Am I overlooking something or is there no newer package of unison?
Does anyone know when the new version will be available?

Thanks
   Thomas

Sorry, I found a much newer thread about this:

[http://ubuntuforums.org/showthread.php?t=687830](http://ubuntuforums.org/showthread.php?t=687830)

So don't worry about my post here.

---

