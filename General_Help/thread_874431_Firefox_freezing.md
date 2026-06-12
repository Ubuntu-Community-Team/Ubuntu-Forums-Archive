---
title: "Firefox freezing"
date: 2008-07-29
forum: General Help
---

### Post by jkid on 2008-07-29
when i try to type something firefox it froze and when i try to open a pic does to and it just froze with everything i do ...its a virus ....cuz me and my friend were watching [COLOR="Red"]P0rn[/COLOR]:confused::confused:

---

### Post by kool_kat_os on 2008-07-29
ubuntu will not get viruses....(ok...its possible...but you would have to directly excecute the file)


but...what are the specs of your computer...although i think its a software problem

---

### Post by tuxxy on 2008-07-29
lol restart firefox clearing all stored data firstly, cookies, cache etc and try again.  Re-install firefox is another option.

---

### Post by jkid on 2008-07-29
DID ALL THAT AND STILL DOES FROZE ....AND I HAVE A hp PAVILLION DV6000 WTIH 120HD AND 1 gIG RAM

---

### Post by Sef on 2008-07-30
> when i try to type something firefox it froze and when i try to open a pic does to and it just froze with everything i do ...its a virus ....cuz me and my friend were watching P0rn

Does it happen with any site or just a particular site?

---

### Post by jkid on 2008-07-30
any site and now my whole PC freezing

---

### Post by gjoellee on 2008-07-30
try this tweak: 
1.Type “about:config” into the address bar and hit return. Scroll down and look for the following entries:
 network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests
 Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.
 2. Alter the entries as follows:
 Set “network.http.pipelining” to “true”
 Set “network.http.proxy.pipelining” to “true”
 Set “network.http.pipelining.maxrequests” to some number like 30. This means it will make 30 requests at once.
 3. Lastly right-click anywhere and select New-> Integer. Name it “nglayout.initialpaint.delay” and set its value to “0&#8243;. This value is the amount of time the browser waits before it acts on information it receives.


if this doesn't help you out see id this happens with other web browsers

---

### Post by jkid on 2008-07-30
the things it frozen when ever i try to type something in the address bar

---

