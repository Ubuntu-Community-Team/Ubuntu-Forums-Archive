---
title: "Unable to download upgrades via package manager"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by mbwmex on 2009-04-03
Last week pkg. manager worked fine, this week does not.

I get the following msg. for all of the software sources.  Internet connection is working fine.

I have disabled software sources, enabled, reboot etc.  No change.

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Help appreciated.

---

### Post by Lunx on 2009-04-03
> **mbwmex said:**
> Last week pkg. manager worked fine, this week does not.

I get the following msg. for all of the software sources.  Internet connection is working fine.

I have disabled software sources, enabled, reboot etc.  No change.

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Help appreciated.

Been happening to a few people. Try changing the server you're dowloading from and refresh then see how you go

Seems odd that local host ???

---

### Post by mbwmex on 2009-04-03
Have changed servers...no change, live in Mexico so tried the one server, no change.

Prior to this week I could get pkgs. from any US server.

Also contacted ISP provider to see if there had been some kind of hardware/software change on his servers that could be a cause...waiting for a response.

Thx.

---

### Post by mbwmex on 2009-04-03
I had downloaded and thought I had removed 3 different proxy programs as could not any installed, apparently I installed one of them at least to the point where it interfered with package updates.
Went back through the history log on the pkg. mgr., very good tool, found the proxy programs I had downloaded, found one still in place, did a complete removal of the program.
Back in business!
Thanks.

---

