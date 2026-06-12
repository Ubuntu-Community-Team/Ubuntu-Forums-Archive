---
title: "Setting up a RAID array"
date: 2008-06-18
forum: Hardware
---

### Post by magicplayr2000 on 2008-06-18
Hi, I'm going to be setting up a new server shortly, and I was wondering how to set up the 2 500gb hard drives I ordered in RAID 0.  Do I need to do anything special when I install ubuntu? (I'm sure I do)

---

### Post by Abu_Dayya on 2008-06-18
use the 'ubuntu alternate disk' for installation. there is a very helpful video tutorial on how to do this in screencasts.ubuntu.com

---

### Post by magicplayr2000 on 2008-06-18
Is that for a software RAID setup?  My motherboard supports a hardware RAID 0/1 setup.  I guess the question I should've asked was whether or not I needed to do anything in Ubuntu for a hardware raid.

---

### Post by Abu_Dayya on 2008-06-18
I think its hardware raid, since its done before the accual installation of the os

hope that helps

---

### Post by JVJB on 2008-06-18
Hardware raid would have to be configured via your raid controller. look for documentation on your motherboard manufacturers website about setting it up.  Using the Alternate disk is for setting up software raid.

On a side note, I setup Raid 1 last week using the normal Ubuntu 8.04 Hardy DVD just by going to text installer instead of the gui.

---

### Post by magicplayr2000 on 2008-06-19
If I set up a hardware raid 0, would I need a seperate hard for the ubuntu install?  I saw on the server forum where someone said that you can't boot from a raid array.

---

### Post by magicplayr2000 on 2008-06-19
bumping

---

