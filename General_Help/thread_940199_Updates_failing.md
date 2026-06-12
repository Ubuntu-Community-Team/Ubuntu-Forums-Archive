---
title: "Updates failing"
date: 2008-10-06
forum: General Help
---

### Post by SpaceMaster on 2008-10-06
Okay, I'm at a loss.  Using the update manager, I can't install updates.  I just noticed it with the most recent security update.  the error I get is: 
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-2ubuntu0.1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```
O_o.  I'm at a loss for words.  For one, why, to get updates, is it looping back to my own machine?  Secondly, if this was a network issue, why haven't web browsing, file sharing, ftp, etc. been affected?  

Currently, I'm running Hardy Heron on a Dell Inspiron 9100.  I tried shutting down the Firestarter firewall on a hunch, but that certainly wasn't it.  I'm not using proxies, either.

---

### Post by jerome1232 on 2008-10-06
Did you check System->Preferences->Network proxy to make sure? It sure looks like it thinks there's a proxy.

---

### Post by SpaceMaster on 2008-10-06
It's set to "Direct Internet Connection."
I did briefly set up a proxy, but because of a few issues reverted my system to how it had previously been.

I also checked to ensure that I removed all components of "anon-proxy"

It also says "Failed to download the list of changes.  Please check your Internet connection."  As I'm posting this, my internet connection is obviously working properly

---

