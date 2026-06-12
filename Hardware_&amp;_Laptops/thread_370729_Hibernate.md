---
title: "Hibernate"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by sagyvolkov on 2007-02-26
Hi,

Running Edgy on Dell D620 for last week.
could never got hibernate to work and the noticed that hibernate destroyed my swap file system.
Read suggestions from []("https://launchpad.net/ubuntu/+bug/66637") to fix my swap which worked nice.
Since Hibernate still didn't continue, i've searched for alternatives.
Some nice summaries from [http://www.linux.com/article.pl?sid=07/02/02/2117209]("http://www.linux.com/article.pl?sid=07/02/02/2117209")

but i could not make s2disk to work...

when i installed uswsusp, i did not get any question about where is my resume file/device.
When i run s2disk i get:
suspend: Could not stat the resume device file


where are the config files for s2disk? I coulnd find on computer or web refs for this info.
Any help will be greatly appriciate as this step is one the last thing i need to setup on this laptop so i can start work with ubuntu on a day to day basis.

Thanks,

---

### Post by Mischa on 2007-03-13
add the swap device as parameter to the  s2disk commmand.

s2disk `cat /etc/fstab|grep sw |awk '{print $1}'` 

hope it helps. in my case it did suspend, but not resume :confused:

---

