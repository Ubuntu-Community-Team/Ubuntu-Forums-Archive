---
title: "Adding multiverse repositories problem in (Finnish) Ubuntu"
date: 2005-11-16
forum: General Help
---

### Post by olavi on 2005-11-16
I'm trying to install faac and Sun JDK as described in [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) and [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto). However, Synaptic can't find anything 'faad' or 'java-package'.

I have enabled everything I could find in Synaptic. These include:
[http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) - breezy-backports - main restricted universe multiverse - binary
[http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) - breezy-backports - main restricted universe multiverse - source

Is this correct? Or does the Finnish localisation of Ubuntu lack multiverse repositories?

It's weird because there are no software patents in Finland and I'm able to install mp3 and mpeg-2 support just fine.

---

### Post by mcduck on 2005-11-16
You could try using .se-repos instead, I had some problems with finnish repos and that fixed it. Anyway, they are even faster as they are closer to Finland, I believe that .fi-repos are in England but .se is in Sweden..

If that doesn't work, post your sources-list here, so I can have a look at it..

---

### Post by olavi on 2005-11-16
Sorry everyone, this was a lot easier to solve than I thought. You have to add the multiverse repository, instead of just enabling it as it says in the AddingRepositoriesHowto. Synaptic -> Repositories -> Add -> Check "universe" and "multiverse" -> Press OK. :) 

OMG n00b. :rolleyes: 

If I ask ubuntuforums.org a newbie question, I seem to find the solution myself. :)

---

