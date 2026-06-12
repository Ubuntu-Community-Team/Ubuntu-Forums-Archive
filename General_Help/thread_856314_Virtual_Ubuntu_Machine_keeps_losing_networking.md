---
title: "Virtual Ubuntu Machine keeps losing networking"
date: 2008-07-11
forum: General Help
---

### Post by seeker1458 on 2008-07-11
Hey guys Im running VMware Server Version 1.0.6 build-19891 (XP Pro SP2 host). I've got a Hardy install that I got from the Virtual Appliances page that keeps losing networking. I unpackaged the compressed file, and then booted it up and set up the static ip(being used as a syslog server) and everything works fine...for about a week. After about a week I cannot get any network activity (no internet, no ping response...nothing). I have two NICs, on two separate subnets. I am also using VMware Server to run a LeftHand FailOver Manager for our two SANs. Could VMServer be trying to resolve an address of 172.16.1.X from the NIC configured as 172.16.10.X? What do I need to check? Fairly experienced with Linux, and feel confident that all the network settings are proper, but can any of you tell me something I should check? Thanks in advance!

---

