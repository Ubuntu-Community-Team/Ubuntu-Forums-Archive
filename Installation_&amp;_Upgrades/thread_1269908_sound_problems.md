---
title: "sound problems"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by gt8ost4l on 2009-09-18
i really need help after i tried to upgrading alsa using the commands in this website [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/) now i get no sound at all

---

### Post by skatinjj on 2009-09-18
Just as a quick suggestion before I go dive into this, how you checked the sound settings and made sure it was not turned down or muted.

I have seen that a lot lately and thought I would throw it out there.

---

### Post by gt8ost4l on 2009-09-18
> **skatinjj said:**
> Just as a quick suggestion before I go dive into this, how you checked the sound settings and made sure it was not turned down or muted.

I have seen that a lot lately and thought I would throw it out there.

yea its not muted

---

### Post by skatinjj on 2009-09-18
Can you post ur sound card specs?

---

### Post by gt8ost4l on 2009-09-18
> **skatinjj said:**
> Can you post ur sound card specs?

intel corporation 82801BA/BAM AC'97 Audio Controller

---

### Post by skatinjj on 2009-09-18
I don't see your card listed on their project site.

[ALSA Project Site]("http://www.alsa-project.org/main/index.php/Main_Page")

You can look there and see.

Sorry I can't be of more assistance.

---

### Post by gt8ost4l on 2009-09-18
> **skatinjj said:**
> I don't see your card listed on their project site.

[ALSA Project Site]("http://www.alsa-project.org/main/index.php/Main_Page")

You can look there and see.

Sorry I can't be of more assistance.

isent there a way to reinstall to my defaults

---

### Post by skatinjj on 2009-09-18
You should be able to download an earlier version ( like the version you upgraded from) and install it.

---

### Post by gt8ost4l on 2009-09-18
> **skatinjj said:**
> You should be able to download an earlier version ( like the version you upgraded from) and install it.yea but what you mean from the live cd

---

### Post by skatinjj on 2009-09-18
Using the live cd would be the best way to

---

### Post by gt8ost4l on 2009-09-18
> **skatinjj said:**
> Using the live cd would be the best way to

ok im on it right now give me the step by step process

---

### Post by skatinjj on 2009-09-19
Boot to your hard drive and insert the live cd.

**If you have adept:**

run adept and select manage repositores from the adept menu up top.

go to the third-party software tab and check the box for cd-rom and uncheck all other boxes

do a search for alas and mark it for install (check version to be sure it is earlier)

apply changes

go back to third-party software tab and recheck the boxes you unchecked earlier
[B]

if you have synaptic:[/B]

go to the settings menu and select repositories

check the box for cd-rom

uncheck all other boxes

search for alsa

mark for install

apply changes

recheck the boxes you unchecked earlier

---

