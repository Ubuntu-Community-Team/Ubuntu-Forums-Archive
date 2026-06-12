---
title: "Sun Java  browser plugin on amd64"
date: 2008-08-20
forum: General Help
---

### Post by Naatan on 2008-08-20
Hi, I am trying to get Java working on my Gutsy running on AMD64, however when I click on "Sun Java 6.0 Plugin" in add/remove programs (it doesn't appear in synaptic) it says "Sun Java 6.0 Plugin cannot be installed on your computer type (amd64)"

Can anyone tell me how to get Sun Java running in Firefox?

---

### Post by LUS93 on 2008-08-20
Install 32bit.

Sadly, that's Sun's offical answer unless something has changed. They have had a feature request in for years to provide a 64bit plugin, and there still isn't one in sight.

---

### Post by Naatan on 2008-08-20
Sadly that's not really an option.. 

It's dumb how some software developers continue to ignore 64bit, it's like ignoring the fact that you get older or something..

---

### Post by LUS93 on 2008-08-20
Here's the bug ID (submitted in 2003 :P ) [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695)

It looks like the openJDK people have fixed the issue according to this comment:
> 
Submitted On 14-AUG-2008
jcastle

The wait is over... OpenJDK 6b11 went out on Ubuntu linux updates yesterday, and now gcjwebplugin runs signed applets on x86_64 just fine. Woot!


I guess we should be happy it was only 5 years ;)

---

### Post by Naatan on 2008-08-20
I actually had the openjdk installed but it seems unable to run runescape

---

### Post by jespdj on 2008-08-20
> **LUS93 said:**
> Install 32bit.

Sadly, that's Sun's offical answer unless something has changed. They have had a feature request in for years to provide a 64bit plugin, and there still isn't one in sight.
There is certainly one in sight, in the [OpenJDK]("http://openjdk.java.net/") project, which is Sun's effort to make Java 100% open source.

In fact, the OpenJDK Java that's available for 64-bit Ubuntu 8.04 does include a 64-bit Java plug-in, but unfortunately it isn't good enough yet; it doesn't work well with a lot of applets.

Be patient for future versions...

---

### Post by Nepherte on 2008-08-20
On hardy, the openjdk web plugin is called icedtea-webplugin. I guess it's the same on gutsy.

---

