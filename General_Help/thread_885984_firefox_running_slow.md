---
title: "firefox running slow"
date: 2008-08-10
forum: General Help
---

### Post by fkabir on 2008-08-10
Firefox is running slow despite several tweaks.

Okay the output is attached.

---

### Post by gjoellee on 2008-08-10
try this tweak:

**1.Type “about:config” into the address bar and hit return. Scroll down and look for the following entries:**
 network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests
 Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.
 **2. Alter the entries as follows:**
 Set “network.http.pipelining” to “true”
 Set “network.http.proxy.pipelining” to “true”
 Set “network.http.pipelining.maxrequests” to some number like 30. This means it will make 30 requests at once.
 **3.** Lastly right-click anywhere and select New-> Integer. Name it “nglayout.initialpaint.delay” and set its value to “0&#8243;. This value is the amount of time the browser waits before it acts on information it receives.

---

### Post by fkabir on 2008-08-10
okay i already had the first two tweaks set to the same as yours. the third tweak network.http.pipelining.maxrequests i had set to 8 so i changed it to 30.

and the last tweak nglayout.initialpaint.delay i added

thanks

---

### Post by gjoellee on 2008-08-10
no problem:)

you should add the addon called "AdBlock" and block annoying ads as well, this may have an effect on the performence as well!

---

