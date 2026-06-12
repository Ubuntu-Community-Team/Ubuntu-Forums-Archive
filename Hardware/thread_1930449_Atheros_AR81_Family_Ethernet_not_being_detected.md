---
title: "Atheros AR81 Family Ethernet not being detected"
date: 2012-02-23
forum: Hardware
---

### Post by raykodrg on 2012-02-23
Greetings everyone, I'm sorry to post this again, and I hope it's the right place for it.

I've been dealing with the issue of this board since yesterday, and I can't find any solution that works for me. The Ethernet board works well, the problem is that Ubuntu is not recognizing it. I have a fresh install of Ubuntu Server 10.04 LTS, and looking up solutions, most people refer to the board as a Wi-Fi, but mine is only wired.

The lspci shows the board as Atheros Communications Device 1083 (rev c0).

I've tried to compile an AR81 Family driver, the module loads with modprobe, but I still see no eth0 after running ifconfig -a.

I'm getting confused a bit with some things. Some people says that the module needed is atl1e and others atl1c. I also tried some copact-wirless package wich has the sources of both of it, but still the same. The atl1c can't be compiled due to errors. The other one compiles just fine.

The modules are there, both atl1e and atl1c after a the installation. Are those the correct modules? or those are just empty files wating the proper module?

I know this issue has been treated already, but for some reason, I can't get make it work. I'm missing something I guess.

By the way, the 11.10 version of Ubuntu Server, does it solve the issue?

I'll apretiate any tips and I'll keep searching anyways. I'll post any info needed if that helps.

EDIT: Well, after giving up the Ubuntu LST version, I just installed the 11.10 and it was packed with recent modules for the board. Glad the problem is over. Thanks anyway.

---

