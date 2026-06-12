---
title: "lack of dependencies"
date: 2005-11-07
forum: General Help
---

### Post by nitrofurano on 2005-11-07
hi!

i'm trying to install FontForge - Ubuntu default distribution lacks libungif4g library (maybe lacks more stuff)

i'm trying to install sdlBasic - Ubuntu default distribution lacks SDL libraries

the Ubuntu i have installed is not connected online (and i'm completelly not interested on online updates) - what must i do?  which library packages must i download (i love the 'out-of-home' download procedures, specially when here in Portugal the online connections are so crappy) and install offline?

thanks?

---

### Post by nagilum on 2005-11-07
There's a rather easy way if you let apt-get find out all the dependency stuff. You don't need to be online for that, just proceed as normal and try to install the wanted packages with 'apt-get --print-uris install <packages>' (with fontforge as <packages> for example). Instead of fetching and installing the files apt-get will print a list of URIs of the .debs you need.

The list contains file sizes and md5sums but a little parsing will give you the pure URIs. To save the URIs in uri_list.txt use:

sudo apt-get --print-uris --yes install <packages> | grep "http://" | sed -e "s/^'\(http.*\)'.*/\1/" > uri_list.txt

The files can then be downloaded with

'wget -i uri_list.txt'

---

