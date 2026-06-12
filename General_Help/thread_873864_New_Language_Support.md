---
title: "New Language Support"
date: 2008-07-29
forum: General Help
---

### Post by dublinus on 2008-07-29
Hi,
I'm running Xubuntu 8.04 on my computer. When Xubuntu was installing, I chose English as my primary language. I thought I could add more supported languages, but can't find that here. My question is: How can I add Arabic support on Xubuntu? I don't need everything to be Arabic, just one of the input languages. Also, can i switch the actual language with the "Keyboard Layout Switcher"? Finally, do you think it would be better or easier if I install just the ordinary Ubuntu, or maybe Kubuntu?
Thanks,
Dublinus

---

### Post by Bruce M. on 2008-08-05
> **dublinus said:**
> Hi,
I'm running Xubuntu 8.04 on my computer. When Xubuntu was installing, I chose English as my primary language. I thought I could add more supported languages, but can't find that here. My question is: How can I add Arabic support on Xubuntu? I don't need everything to be Arabic, just one of the input languages. Also, can i switch the actual language with the "Keyboard Layout Switcher"? Finally, do you think it would be better or easier if I install just the ordinary Ubuntu, or maybe Kubuntu?
Thanks,
Dublinus

In Synaptic Package Manager, have you tried:
```
language-pack-ar
```
> translation updates for language Arabic 
Translation data updates for all supported packages for:
Arabic

language-pack-ar-base provides the bulk of translation data
and is updated only seldom. This package provides frequent translation
updates.

Please note that you should install language-support-ar
to get full support for this language.

It will also load "language-pack-ar-base"
> Translation data for all supported packages for:
Arabic

This package provides the bulk of translation data and is updated
only seldom. language-pack-ar provides frequent
translation updates, so you should install this as well.

Please note that you should install language-support-ar
to get full support for this language (spell checkers, OpenOffice
locale packages, etc.).


As well you'll need:
```
language-support-ar
```
> This metapackage depends on all packages that provide native language
support for applications. (like spell checkers,
dictionaries, OpenOffice and Mozilla locale packages, etc.).

If you also want your applications and the desktop to be translated,
please additionally install language-pack-ar.

Language: Arabic

Hope this helps.
Bruce

---

### Post by ibrahim.shakra on 2010-12-09
thanks man that was helpful

---

### Post by heron92 on 2012-08-05
How can I make my Ubuntu  supports the Arabic language

Please help

---

### Post by wildmanne39 on 2012-08-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

