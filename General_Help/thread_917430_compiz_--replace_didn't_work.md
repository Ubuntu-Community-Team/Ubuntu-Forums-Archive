---
title: "compiz --replace didn't work"
date: 2008-09-11
forum: General Help
---

### Post by methodtwo on 2008-09-11
Hi there
I'm running ubuntu 7.10.I understand that all the compiz stuff is supposed to be in by default.However when i do
```
compiz --replace
```
i get:
```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```
What can i do to get the compiz effects working?.I don't understand how to include xgl on 7.10:The only guide i found on this was on 7.04:confused:
Thankx for any help

---

### Post by ezzieyguywuf on 2008-09-11
try running the following

%sudo apt-get install xserver-xgl

then logging into the xgl session. Actually, I think 7.10 defaults to xgl if present, so simply logging back in should do it for you

---

### Post by overdrank on 2008-09-11
> **methodtwo said:**
> Hi there
I'm running ubuntu 7.10.I understand that all the compiz stuff is supposed to be in by default.However when i do
```
compiz --replace
```
i get:
```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```
What can i do to get the compiz effects working?.I don't understand how to include xgl on 7.10:The only guide i found on this was on 7.04:confused:
Thankx for any help

Hi and what is the model of the graphics card. Some do not use xgl.
Edit also look at the compiz-check
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by methodtwo on 2008-09-11
Here is the relevant line from the output of $lspci:
```
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```
Thankx for the replies!

---

### Post by overdrank on 2008-09-11
> **methodtwo said:**
> Here is the relevant line from the output of $lspci:
```
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```
Thankx for the replies!

Hi and the intel graphics do not need the xgl. Try the compiz-check from my previous post.

---

### Post by methodtwo on 2008-09-11
Oh and how do i verify that xgl is being used, as there's no visible difference.

---

### Post by methodtwo on 2008-09-11
Does this mean that i shouldn't use xgl?
How do i remove it?

---

### Post by ezzieyguywuf on 2008-09-11
sudo apt-get remove xserver-xgl

---

