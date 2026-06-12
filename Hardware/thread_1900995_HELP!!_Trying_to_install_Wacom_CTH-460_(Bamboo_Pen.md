---
title: "HELP!! Trying to install Wacom CTH-460 (Bamboo Pen and Touch) in Lucid!!"
date: 2011-12-27
forum: Hardware
---

### Post by Dalian on 2011-12-27
Can anyone tell me what the best way to install a Wacom CTH-460 using Ubuntu 10.4?

---

### Post by lukeiamyourfather on 2011-12-27
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by Favux on 2011-12-27
Hi Dalian,

Lucid's default wacom.ko does not support your BambooPT tablet nor does the default Wacom X driver.  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") for instructions.

---

### Post by Dalian on 2011-12-28
Luke: Thank you for providing the link, although I have already investigated it.

Favux: I have already investigated that link as well. I fear that given my Ubuntu infancy, it would NOT be in my best interest to go mucking around in the terminal.

---

### Post by Favux on 2011-12-28
lol

You're letting yourself be unnecessarily intimidated.  Part I. and II. of the HOW TO are set up to be just Cut & Paste of the commands.  You don't need to understand them.  Just read through those sections a couple of times to get the general idea and go for it.  Easy to restore the non-working defaults through Synaptic Package Manager.  You need to compile a newer wacom.ko and xf86-input-wacom to get your tablet working.  Heck to get all the latest gesture improvements you need to clone xf86-input-wacom which is b) and c) of part II.

Your other option is to use Martin Ownen's PPA which is in the Note just above part I.  But that may have a problem with the 10-wacom.conf, which is the file that configures the tablet and you need that.  Plus it installs a DKMS implementation of the wacom.ko so read the caution on that.

---

### Post by Dalian on 2012-01-03
Thanks to everyone's kind contributions. I resolved the issue (so far) by simply upgrading to Ubuntu 11.04. After doing so my Wacom Bamboo Pen & Touch (CTH-460) works out of the box. Thanks again to everyone.

---

