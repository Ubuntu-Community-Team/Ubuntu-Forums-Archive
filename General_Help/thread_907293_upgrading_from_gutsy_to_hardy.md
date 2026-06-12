---
title: "upgrading from gutsy to hardy"
date: 2008-09-01
forum: General Help
---

### Post by madubuntuer on 2008-09-01
About ubuntu says am running hardy but the locales package refused to install which is what caused the upgrade from gutsy to fail.

When ever I try apt-get install -f or apt-get install locales I get this
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up locales (2.7.9-4) ...
Generating locales...
 'ror: Bad entry '
Error: Bad entry '--- '
 'ror: Bad entry '---
Error: Bad entry '{ '
Error: Bad entry '} '
 'ror: Bad entry '
  0.April 12, 2007... Try `localedef --help' or `localedef --usage' for more information.
failed
  0.- March 13, 2007... 

why??? I didn't change anything.  It was complaining about not being able to find no definition file but after I executed locale-gen en_GB it disappeared

---

### Post by tjwoosta on 2008-09-01
there have been countless threads on this forum about people trying to upgrade via terminal and it fails

upgrading through the terminal is kinda like a one way upgrade  
(if it works, it works, but if not then you are stuck with a broken ubuntu)

the real (best ) way to upgrade ubuntu is to just shrink your existing parttiton and install the new ubuntu beside the old one
(use gparted partition manager)

(its kinda like dual booting the old ubuntu with the new one)

that way you can simply drag and drop all of your important stuff from one partiion to the other

also you dont have to worry about the upgrade failing because it is really just a fresh install beside the old one

there would be some minor setup required for the new install, but it shold be familiar by now, also you have the benefit of being able to copy system config files like xorg and even hardware drivers over to the new install

now after everything is all setup and the new ubuntu is working, you can simply delete the old partition and expand the good one

(if you were unhappy with the new install, you could always delete the partition and expand the old one back to normal size without making any changes at all)

it is the safest way of upgrading

---

