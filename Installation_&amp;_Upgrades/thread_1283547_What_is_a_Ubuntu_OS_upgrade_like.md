---
title: "What is a Ubuntu OS upgrade like?"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by garnold on 2009-10-05
I brand new to Ubuntu and loving it. I never thought there was something this good to goto and thought I would be stuck in windows forever. With the new release coming around the corner what should I get ready for? I have never been through and upgrade before so how does it work? Is it just a simple download or is there more involved?

---

### Post by Nburnes on 2009-10-05
It will show as a simple update in Update Manager I do believe. The update should be rather painless.

---

### Post by garnold on 2009-10-05
> **Nburnes said:**
> It will show as a simple update in Update Manager I do believe. The update should be rather painless.

Wow that is great :)

---

### Post by slakkie on 2009-10-05
Upgrading is very easy. Just don't upgrade on the day it is released. I normally wait one month before I do upgrade. Although I am running Karmic already this time around.. 

You could upgrade via a GUI (which is a method I don't prefer) and you can upgrade via the command line (which I prefer).

Just have a look here: [https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

It is for upgrading from 8.10 to 9.04, but the principle is exactly the same.

If you want to you could install 8.10 inside a virtual machine (install virtualbox) and try the upgrade to 9.04 there. It is very easy.

---

### Post by cguy on 2009-10-05
> **Nburnes said:**
> 1)It will show as a simple update in Update Manager I do believe.
2)The update should be rather painless.

1) Not really, but it isn't more complicated.
2) My previous upgrades were painless.

After the upgrade from Intrepid to Jaunty I couldn't enjoy the advertised fast boot times, so a clean install was due. I imagine something similar to happen with Jaunty-to-Karmic.

Also, if you upgrade to Karmic you won't get GRUB 2.


Before any upgrade it's recommended that you back up your data; if you do that, why not proceed with a clean install and avoid any headaches?

But also do the upgrade to satisfy the curiosity. :D

---

### Post by garnold on 2009-10-05
> **cguy said:**
> 1) Not really, but it isn't more complicated.
2) My previous upgrades were painless.

After the upgrade from Intrepid to Jaunty I couldn't enjoy the advertised fast boot times, so a clean install was due. I imagine something similar to happen with Jaunty-to-Karmic.

Also, if you upgrade to Karmic you won't get GRUB 2.


Before any upgrade it's recommended that you back up your data; if you do that, why not proceed with a clean install and avoid any headaches?

But also do the upgrade to satisfy the curiosity. :D

What is GRUB2 and why would I not get it?

---

### Post by garnold on 2009-10-05
> **slakkie said:**
> Upgrading is very easy. Just don't upgrade on the day it is released. I normally wait one month before I do upgrade. Although I am running Karmic already this time around.. 

You could upgrade via a GUI (which is a method I don't prefer) and you can upgrade via the command line (which I prefer).

Just have a look here: [https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

It is for upgrading from 8.10 to 9.04, but the principle is exactly the same.

If you want to you could install 8.10 inside a virtual machine (install virtualbox) and try the upgrade to 9.04 there. It is very easy.

Why do you prefer the command line approach?

---

### Post by cguy on 2009-10-05
> **garnold said:**
> What is GRUB2 and why would I not get it?
Grub 2 is the bootloader. Make a search on google to find out more.

See
[http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta) (scroll down)

---

### Post by slakkie on 2009-10-05
> **garnold said:**
> Why do you prefer the command line approach?

Because I maintain all my machines via the command line (sys admin as a profession). I run a Debian and Ubuntu server and have an Ubuntu desktop. By running cli only upgrades I can script the most common things and I don't need to think about it.

```

functions.deb:apt_update() {
functions.deb:rmkernel() {
functions.deb:purge_build_deps() {
functions.deb:purge_pkg() {
functions.deb:pkg2repo() {
functions.deb:repo2pkg() {
functions.deb:pkg_update() {
functions.deb:rel2pin() {
functions.deb:pkg2pin() {
functions.deb:dpkg2pin() {
functions.debian:safe_upgrade() {
functions.debian:release_upgrade() {
functions.ubuntu:safe_upgrade() {
functions.ubuntu:release_upgrade() {

```

This is what I have automated on both Ubuntu and Debian, the function list is slowly growing. I find it easier and by running cli commands, I can help someone on a forum much easier. I don't need to explain, click here, make sure you tick that, etc etc. I just type in the command and it works. It is also easier because cli statements don't change so much as GUI interfaces do per release.

And regarding grub2, it is true that grub will not be upgraded to grub2 when you do a release-upgrade. But once you are in Karmic you can install grub2 and remove grub. There is an excelent howto somewhere on this forum.

---

### Post by oldos2er on 2009-10-05
Before you upgrade, make sure you backup any sensitive data.

---

