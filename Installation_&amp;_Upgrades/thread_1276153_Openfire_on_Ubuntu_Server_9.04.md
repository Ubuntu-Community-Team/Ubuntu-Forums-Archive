---
title: "Openfire on Ubuntu Server 9.04"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by newbeen on 2009-09-26
Hay gang, Newbeen here, and trust me I'm a noob in all things.  :) 
 
I'm having an issue getting to Openfire through a browser.  It seems to me that the problem is Shorewall.  When I disable Shorewall, I have no issues accessing the login screen for Openfire, but when it enabled I have no access.  Pretty smart of me eh? lol..
  
Anyway, this is the problem, obviously I need shorewall to be enabled but can't figure out what I need the rules to state so that I can have it working.  Any help here would be greatly appreciated.  Thanks in advance.

---

### Post by pwebguy on 2009-12-13
Check the Server Manager/Server Information page in the Openfire admin console. It will give you a list of the ports openfire uses. 

These need to be available (allowed) in shorewall. Depending on what your shorewall policies are, you may need to create both inbound and outbound rules.

---

