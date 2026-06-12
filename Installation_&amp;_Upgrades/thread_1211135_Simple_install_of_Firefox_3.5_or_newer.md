---
title: "Simple install of Firefox 3.5 or newer"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by arranmc182 on 2009-07-12
I found a simple way that will let you simply jump back to the older version if things go wrong.

download the latest version of Firefox from the site then extract the file it will be called firefox rename it to firefox-3.5 then move it to /usr/lib/ directory, Now go to /usr/bin/ directory and look for the file called firefox and as root open it in a text editor and look for this part that looks somthing like this

MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.0.11
APPVER=3.0
META_NAME=firefox
GDB=/usr/bin/gdb
DROPPED=abandoned

you will need to change the LIBDIR & APPVER from your old version to the new one so it should look like this

MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.5
APPVER=3.5
META_NAME=firefox
GDB=/usr/bin/gdb
DROPPED=abandoned

now save the file and open up Firefox it should now be the latest version you can do this with any version from the Firefox site but if anything goes wrong just re edit the file back and you should then be able to reload your old version of Firefox but if you feel happy with the new version of fire fox you can now remove the directory for your old version if you wish.

i have tested this in Ubuntu 9.04 and it works as i am on FF 3.5 right now

---

