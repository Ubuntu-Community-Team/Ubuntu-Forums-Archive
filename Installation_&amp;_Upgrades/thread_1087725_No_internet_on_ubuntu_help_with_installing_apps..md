---
title: "No internet on ubuntu help with installing apps."
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Adam25 on 2009-03-05
Hi, i cant get ubuntu to see my onboard NIC, so as of now i cant get it online. Is there a way to install packages or ubuntu updates without haveing the system online>? I downloaded a few things directly from the repos on my windows pc and burned them to disk. After putting the files on my ubuntu pc they install the packages and add the files to the system. But when i goto add programs they say the list is outdated and i must go online. Needless to say nothing is working this way. What can i do?

---

### Post by sarath_it on 2009-03-05
Its not very easy that way. apt solves much more complex dependency graphs et al. IF you have downloaded the .deb files, 

run the 
dpkg -i theoneuwanttoinstall.deb

and it will show you all the dependencies. IF all dependencies are already installed it will proceed to install.

If they are not installed you may have to download all those debs. Install each of them. Follow recursively. Well, thats what is made easy by just apt-get install :)

Easier way: Make your own local repository.
Look at [http://ubuntuforums.org/archive/index.php/t-7455.html](http://ubuntuforums.org/archive/index.php/t-7455.html)

---

### Post by Therion on 2009-03-05
Is there some reason you can't connect using a cable; even if just long enough to get the updates and then see if your NIC is recognized properly?

---

