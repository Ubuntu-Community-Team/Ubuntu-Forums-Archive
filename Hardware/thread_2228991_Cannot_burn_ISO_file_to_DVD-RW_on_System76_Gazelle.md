---
title: "Cannot burn ISO file to DVD-RW on System76 Gazelle Professional v9"
date: 2014-06-10
forum: Hardware
---

### Post by mintyninja41 on 2014-06-10
Hello-
I'm running Kubuntu 14.04 on a System76 Gazelle Professional  (version 9), and lately it seems that K3B, the native disk burning  application for KDE, refuses to burn ISO files to rewritable DVDs (the  only type of disc I've got).  It's strange, because it was maybe two weeks ago that I was able to burn the images to discs without any problems.  I'd like to install Debian on my old pc (a COMPAQ Presario V2000, not that it matters) as a sort of "testing ground", since I'm trying to learn in more depth how to use the command line in Linux, but I don't want to mess up my main laptop, as I need it for schoolwork- but I digress.  Mind, I hate to be a bother, but I'd very much appreciate any help that anyone could offer.

(The error message that K3b gives me when I try to burn ISOs to DVD is at [http://imgur.com/iKVhdP6](http://imgur.com/iKVhdP6) .)

Thanks so much!
        -Minty

---

### Post by Yellow Pasque on 2014-06-10
Settings -> Configure k3b -> Programs -> User Parameters

Add 'dvd-compat' (no apostrophes) in the field for growisofs. Restart program (just to be sure) and try again.

---

### Post by mintyninja41 on 2014-06-11
No joy-

I followed your instructions, and this happened:

After I specify which image to burn to disc, the second window opens, and K3b prints the following messages:

"Writing DVD-RW in incremental mode."
"Using growisofs 7.1 - Copyright (C) Andy Polyakov <appro@fy.chalmers.se>"
"Starting disc write..."
"Fatal error at startup: Invalid argument"

....no quotes, of course.

        -Minty

---

### Post by Yellow Pasque on 2014-06-11
Perhaps you need a hyphen before dvd-compat (-dvd-compat).

---

### Post by mintyninja41 on 2014-06-11
Oh...my...god.

A hyphen, that's it? Wow, I feel a bit stupid :3

Right-o, thanks for your help!

---

### Post by SeijiSensei on 2014-08-13
Thanks for this fix!  I would never have found it on my own!

---

