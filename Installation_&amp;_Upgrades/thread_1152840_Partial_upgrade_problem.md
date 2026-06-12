---
title: "Partial upgrade problem"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by achristoffersen on 2009-05-08
After updating to jaunty I get a "not all updates can be installed" message asking me to run a partial upgrade. The partial upgrade however does not work. The messagesbox tells me that " 1 packages is going to be removed, 2 new pavkages are going to be installed. 2 package is going to be upgraded"

the details list
* Remove libdb4.5-java
* install libdb4.6-java
* Install libdv4.6-java-gcj
* Upgrade liblucene2-java

Since updata manager can't do this - how can I do it manually? (I have not yet tried apt-get --purge remove as I am both timid and understands that this is basically what the update manger would do.

help much appreciated

---

### Post by abn91c on 2009-05-08
> **achristoffersen said:**
> After updating to jaunty I get a "not all updates can be installed" message asking me to run a partial upgrade. The partial upgrade however does not work. The messagesbox tells me that " 1 packages is going to be removed, 2 new pavkages are going to be installed. 2 package is going to be upgraded"

the details list
* Remove libdb4.5-java
* install libdb4.6-java
* Install libdv4.6-java-gcj
* Upgrade liblucene2-java

Since updata manager can't do this - how can I do it manually? (I have not yet tried apt-get --purge remove as I am both timid and understands that this is basically what the update manger would do.

help much appreciated
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Dazed_75 on 2009-05-08
> **abn91c said:**
> sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

Thank you abn91c,

I have been trying to solve exactly the same problem as achristoffersen for a couple of days.  Your solution worked for me!

I still am not sure why update manager was not able to do this.  I had previously noticed my free disk space was down to 3GB which might have caused the problem originally (especially since it was reported during the dist-upgrade that 3.6 GB would be needed).  But I had then cleaned out 13GB and the update manager still failed with 16GB free.  So I still don't know what happened.

In any case, Thanks.  Seems like there used to be a button somewhere here to specificly thank a poster, but I don't see it anymore.

---

### Post by gandalf458 on 2009-05-08
And a thanks for me too!

---

### Post by abn91c on 2009-05-08
you are welcome :popcorn:

---

### Post by vewert on 2009-05-08
That worked for me as well.  I'm a relative Linux newbie.  What was the actual problem, and how does the fix work. (Just trying to learn a thing or two)

Thanks!

-----------------------------------
Victor Ewert
[http://www.ewert-technologies.ca]("http://www.ewert-technologies.ca/")

---

### Post by achristoffersen on 2009-05-09
THANKS a bunch. Incidentally all of a sudden update manager worked. therefore I am also curious as to why dpgk could/should solve the problem. Its always nice to learn :-)

---

