---
title: "EDID Error - Ubuntu Server 10.04"
date: 2011-04-17
forum: Hardware
---

### Post by dakotadave on 2011-04-17
I am running ubuntu server 10.04 server edition and do not plan to use a gui interface. I am getting constant drm_edid_block_valid errors EDID checksum is invalid, remainder is 107 in the console window. Everything else works, but all the errors make typing commands into the console a pain. How can I get rid of these error messages?

David

---

### Post by gaothfanai on 2011-07-19
I'm having the same problem, except mine is with 10.10.  This is a fresh install on top of 10.04 (complete disk wipe), with no problems whatsoever with the previous 10.04 installation.

---

### Post by rdratlos on 2011-11-04
Please post the complete dmesg log from boot start until the first EDID checksum failure entries and in addition the output of lspci -v.

---

