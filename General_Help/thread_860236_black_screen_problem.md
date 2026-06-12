---
title: "black screen problem"
date: 2008-07-15
forum: General Help
---

### Post by marc raes on 2008-07-15
I have hardy installed on Asus A7M laptop. When I leave my desktop on, it is supposed to put the computer on black screen after 30 minutes. It does, but at the same time it puts the laptop to sleep. So that to get to my desktop I have to type alt+ctrl+backspace. But this brings the login-screen back. This didn't happen with former releases. So something must have gone wrong. Is this a bug or an asus-hardware problem? I upgraded the hardy, starting from a beta-release and remember having had some problems with the /etc/apt/sources.list file. I solved it by putting the power-manager-preferences to "never put on black screen". But I'd like to see it work properly. Someone out there had the same problem? (and solved it)

---

### Post by wpshooter on 2008-07-15
There are 2 sliders in power management section of Ubuntu.

The top one is for setting sleep timing.

The bottom one is for setting screen/display/monitor blanking/power saving mode/timing.

Do you have the TOP slider set to NEVER ?

---

### Post by marc raes on 2008-07-15
Top sliders are set to NEVER.
I consider reinstall, but want to know first if anybody else has the problem with asus notebooks.

---

### Post by wpshooter on 2008-07-15
> **marc raes said:**
> Top sliders are set to NEVER.
I consider reinstall, but want to know first if anybody else has the problem with asus notebooks.

My "guess" would be that it is yet another bug in Hardy.

That's why I am sticking with Gutsy until perhaps Intrepid is released.

---

### Post by marc raes on 2008-07-16
> **wpshooter said:**
> My "guess" would be that it is yet another bug in Hardy.

That's why I am sticking with Gutsy until perhaps Intrepid is released.
I do not think it is a bug because everything is fine on a dell c640 laptop.
If it is a hardware thing with asus A7M, reinstall has no meaning. That's what I'm waiting for to hear from an other A7M user who has hardy installed. So far no news.

---

### Post by marc raes on 2008-07-17
On the other hand: putting the notebook to black screen, that's meant for saving power isn't it. My technical knowledge is minimal. But I can see it must be a power-manager defect. What it actually does is logging everybody out. I don't know if this can be called 'putting the computer to sleep'. When I start it up and stay with the logging screen, because something else needs my attention, finding it on black screen after half an hour, logging screen must be called back by alt+ctrl+backspace.
Could there be something wrong with the configuration files of the gnome-power-manager, some mistake in some script? What have I to look for and how should they look to work right?
Somebody told me that it must be a driver problem. What driver? Can I install it?

---

