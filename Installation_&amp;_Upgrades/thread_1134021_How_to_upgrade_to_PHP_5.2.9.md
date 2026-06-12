---
title: "How to upgrade to PHP 5.2.9?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by z33k3r on 2009-04-23
Hello everybody. I am trying to update PHP from 5.2.6 to 5.2.9. There are some major bug fixes that I need implemented. The problem is that apt-get is not installing any PHP version higher than 5.2.6! The install of Ubuntu was 8.04 and then was upgraded to 8.10 due to the PHP limits of the 8.04 release... but I am not getting PHP 5.2.9? Any help would be appreciated!

---

### Post by z33k3r on 2009-04-23
Has nobody really run into this? I am astounded that I haven't been able to find anything on these forums or Google!:confused:

---

### Post by z33k3r on 2009-04-23
Does any body have a clue?

---

### Post by z33k3r on 2009-04-23
I ended up adding a new repository location to my list that had the package (dotdeb.org)...

---

### Post by ubuntuforums on 2009-04-23
I was wondering about this as well. Glad you found a way to get 5.2.9. Thanks.

---

### Post by z33k3r on 2009-04-24
I added :
> deb [http://packages.dotdeb.org/](http://packages.dotdeb.org/) oldstable all

Then ran :
> apt-get update
apt-get install php5-cli

Hope this helps somebody like me when I was looking for it. :)

---

### Post by alexlittle on 2009-06-06
Thanks for this - exactly what I needed to know :-)

---

### Post by z33k3r on 2009-06-06
Just to follow up; if you start using third-party application distros, make sure to read their forums and comments on their site. For example, there were some naming inconsistency which stopped me from installing a progress bar module.

---

### Post by rojakcoder on 2009-06-17
> **z33k3r said:**
> I added :


Then ran :


Hope this helps somebody like me when I was looking for it. :)

Thanks for the tip! It sure helped.

---

### Post by jumbo-jet on 2010-02-14
hi,

plz folks. help me and others share you success by telling us step-by-step how you managed to upgrade to php-5.2.9.

i have managed to down oad the .gx & bz2 and unpacked it. BUT i have some questions...

q1. WHICH FOLDER DO THESE X unzipped FILES GO IN

q2. PLZ show us how to configure them for apache ie. with ds support

q3. How to compile them

q4. How can we finally make it all work as a proper lamp.


thanks. your HELP  URGENTLY  NEEDED - sure, others will also benefit.

( shame ubuntu system can't do this by the synaptic manager..!? )

BIG THANK YOU !

jumbo-

---

### Post by conner_bw on 2010-02-22
Hi,

This no longer works... Seems dotdeb moved 'oldstable' to [http://archives.dotdeb.org/](http://archives.dotdeb.org/)

To add insult to injury, 'oldstable' is no longer used as a naming convention. I now have to choose from: etch, lenny, sarge, woody.

Which is the correct repo for Ubuntu 8.04?

Thanks.

---

