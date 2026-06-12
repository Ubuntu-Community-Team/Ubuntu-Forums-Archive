---
title: "turning add/remove applications program into a script generator"
date: 2008-08-31
forum: General Help
---

### Post by armandli on 2008-08-31
everytime i reinstall Ubuntu (not that I do that often, but just in case), I must use the add/remove applications program to select all the programs I have installed in other ubuntu before.

I was wondering, instead of doing the selection every fresh install, can i find the apt-get commands for all those programs? I have tried some entries in the application, such as 7zip by "apt-get install 7zip" but it says 7zip is not found. there are other programs like this, how can i find the apt-get name for all the applications I have selected? any way to turn add/remove application program into a automatic script generating program? (instead of me going around all the websites of programs I've installed to find its source library names)

---

### Post by tjwoosta on 2008-08-31
you can find the correct names for apt-get in synaptic package manager
(system-administration-synaptic package manager)

just use the search feature to find your programs (apt-get uses the same names as the synaptic package manager)



but.. if you are talking about doing this alot i think your best bet is to just make a custom install cd with all of the desired applications included

that way you could just install and already have everything you want, without the need for adding every single program ever time you do an install

here is a good link
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

---

