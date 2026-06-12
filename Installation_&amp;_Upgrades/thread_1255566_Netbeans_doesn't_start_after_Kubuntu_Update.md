---
title: "Netbeans doesn't start after Kubuntu Update"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by ig0r89 on 2009-09-01
Hello!
Yesterday I've updated my kubuntu 9.04 through 
apt-get update
apt-get upgrade
A lot of features where installed. 

After that my Netbeans doesn't start.  It appears at my task manager. But then it just disappears =(
I think that is because  Java libraries where updated?

How can I fix this? 
How can I trace  errors? Netbeans doesn't show them to me at startup.


Thanks!

---

### Post by ig0r89 on 2009-09-01
OK guys, I've got this problem solved!

After Java upgrade - it renamed it's main folder from 
old:  /usr/lib/jvm/java-6-sun-1.6.0.14/jre   to
new:/usr/lib/jvm/java-6-sun/jre

So if you run into this - just edit the netbeans/etc/netbeans.conf and change the jdkhome param.

Thank you!

---

### Post by Albert Cabre on 2010-02-05
I had a very similar problem once I upgraded to Ubuntu 10.0.4. My Netbeans didn't start.

I had to install JDK (through Synaptic) and then I had to change the jdkhome path to the new one in netbeans.conf like this: 

netbeans_jdkhome="/usr/lib/jvm/default-java"

At the moment it works!

---

