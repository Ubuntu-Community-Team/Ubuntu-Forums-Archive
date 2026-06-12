---
title: "onboard sound not active"
date: 2009-03-25
forum: Hardware
---

### Post by cfmunster on 2009-03-25
I am running Ubuntu 8.10 on an AMD X2-based system with an Nvidia motherboard. I have a Bose Companion 3 system for general sound output. I setup my system to use the onboard sound hardware with Skype, but in the last week my system has started losing the connection to the onboard audio. It looks like it started happening after one of the software updates in the last week, though I don't have an exact day when it started. 

If I do "lshw" as superuser, I get this:


 *-multimedia UNCLAIMED
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: latency=0 maxlatency=5 mingnt=2


So the system sees it, but lists it as "UNCLAIMED". Anything I can do to get the onboard audio active again?

---

