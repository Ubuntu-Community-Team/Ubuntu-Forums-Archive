---
title: "Apt-get Error"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by terazen on 2009-10-06
I logged in to my home computer today and saw that I had some updates to Wesnoth, Spring, Nexuiz etc but when I clicked install it wouldn't download the updates.  I tried to run apt-get upgrade and got this error:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Also, when I run `ps -eaf | grep apt` I saw this: > root      3806  3713  0 19:39 ?        00:00:00 apt-get -qq -d dist-upgrade

What's the deal?

---

### Post by rob2uk on 2009-10-06
something, somewhere, seems to have locked APT.

Do you have GDEBI or Synaptic, etc running?

---

### Post by terazen on 2009-10-06
No, I just turned my desktop on and logged in.  It started dist-upgrade on it's own for some reason, but it's not showing now.  I just ran apt-get update and upgrade and it finally worked, but now it's telling me all of the package updates it asked me about a few minutes ago are being held back.  Dwah?

---

