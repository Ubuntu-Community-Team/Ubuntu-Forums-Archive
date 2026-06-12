---
title: "problem downloading updates"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by vijay karthik on 2009-01-26
hello 
i am unable to download any updates. i am connected to the internet though. the error msg goes like this

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

and so on for many other packages. i am connecting to the net using wireless. could anyone help me on this.

---

### Post by taurus on 2009-01-26
So into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and try another server.  Pick the Main Server to see if that works.

---

### Post by vijay karthik on 2009-01-28
i did try it...but hard luck it wasnt working still..when i clicked on find the best server it siad "no best server" , check network connection. and some of the error msgs say "proxy authentication required" wat do i do.?

---

### Post by avtolle on 2009-01-28
Open Synaptic; click on Settings; from drop-down, select Preferences; then click on the Network tab to be sure the radio button for Direct connection is selected (unless you are using a proxy, and if this is the case, be sure the proxy is correctly configured).

---

