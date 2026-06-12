---
title: "ubuntu package installer dependency problems"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ota_king on 2009-04-10
The main thing I need is build-essentials but I need all these other packages to upgrade it.
I'm a complete noob with ubuntu/linux and all that so bear with me.

Ubuntu details
Release 8.10(intrepid)
Kernel Linux 2.6.27-7-generic

processo: AMD Athlon(tm) 64 Processor 3000 +

from packages.ubuntu.com

Ubuntu  >> Packages  >> intrepid >> devel >> build-essential 

I went in there and downloaded build-essentials

but then it said 
"Dependency is not satisfiable: g++"

I'm guessing I need g++ for that and so I downloaded g++

>> Ubuntu  >> Packages  >> intrepid >> devel >> g++ 

and then it said
"Dependency is not satisfiable: g++-4.3"

so I thought I needed g++-4.3 as well so

>>Ubuntu  >> Packages  >> intrepid >> devel >> g++-4.3 

and then, "Dependency is not satisfiable: libstdc++6-4.3-dev"

and so...

>> Ubuntu  >> Packages  >> intrepid >> libdevel >> libstdc++6-4.3-dev 

but now it says

"Dependency is not satisfiable: g++-4.3"

I think i'm doing something wrong here since g++-4.3 needs libstdc++6-4.3-dev and vice versa

I'm a complete noob with linux and I was wondering whether there was an easier way to just download everything as well as fixing my dependency problem.

Also I need to learn how to do it on terminal as well.

I'm so sorry but I NEED HELP!!! AHHHHHH AAAAAAHHHHHHHHH!!!!!!!!!
Thank you!

---

### Post by coffeecat on 2009-04-10
Don't download deb packages by hand - that way you run into dependency problems. Oh! You've discovered that already. :wink:

Go to System > Adminstration > Synaptic. Once it's open, click on the 'Reload' button for it to refresh the package metadata. (You need an internet connection open.) Now search for build-essential, mark it for installation and click on 'Apply'. All dependencies will be dealt with automatically, and you can sit back and enjoy while everything is downloaded and installed for you.

---

