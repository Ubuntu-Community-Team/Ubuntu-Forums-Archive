---
title: "ath9k help"
date: 2010-08-21
forum: Hardware
---

### Post by CStryker on 2010-08-21
Trying to get the wireless working on my new laptop. 

lspci yields AR928X Wireless Network Adapter

I've been googling for days trying to figure this out, but despite numerous success stories, none of it works for me. 

I've tried both ndiswrapper and madwifi, but they didn't work. From what I understand though, that may be because mine is a b/g/n card instead of just b/g, so I tried ath9k.

Ath9k doesn't seem to be working either though, even though I installed the backports as suggested on the ath9k page.

Thoughts? Could it have something to do with mine being on a PCI-E bus instead of PCI?

---

### Post by dino99 on 2010-08-21
maybe follow this post:

[http://ubuntuforums.org/showpost.php?p=9146713&postcount=129](http://ubuntuforums.org/showpost.php?p=9146713&postcount=129)

---

### Post by moore.bryan on 2010-08-21
Which Ubuntu are you using? I didn't have to install anything extra for wireless to work when I did before.

---

### Post by CStryker on 2010-08-22
Ubuntu 10.04 LTS. I've tried both the 32- and 64-bit versions with the same results. It shows up and everything looks good, but won't turn on using fnc+f3. If I do a manual ifconfig wlan0 up, it shows up on ifconfig, but I still can't associate with anything.

---

