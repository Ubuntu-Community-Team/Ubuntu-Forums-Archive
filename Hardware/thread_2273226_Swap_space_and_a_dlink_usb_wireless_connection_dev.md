---
title: "Swap space? and a dlink usb wireless connection device is not functional."
date: 2015-04-11
forum: Hardware
---

### Post by ian83 on 2015-04-11
I am struggling to find a swap space method of partitioning, and im willing to commit 100/600gb to the ubuntu install and up to 10gb more for swap space. should i just install it to see if it works without swap space for now and then somehow change the partition in future? i have 4gb physical memory on it. any help will be much appreciated. i also have a dlink wireless device thru usb and appears to be nonfuctional in ubuntu as is.
Thank you

---

### Post by dino99 on 2015-04-11
start the installation from the iso
when partitionning comes, select 'something else' choice to do a custom installation. You may already know about the hdd config to choose where the installation can be done: load a partitionning tool, like gparted, or else, to avoid confusion/error and possible overwriting of existing partition(s).
The usual need for the installation is:
- / about 10/12 gb to install the OS (root partition, need the 'boot' flag set)
- swap about 4 gb
- /home for your settings & data (rest of the free disk space)

note: you may prefer to create the partitions before installation  [http://gparted.org/index.php](http://gparted.org/index.php)

at some point you'll be asked about the 'grub' bootloader, install it on /dev/sda
indeed, later, if your needs have changed, you can resize the partitions (if they are not mounted of course)

note2: to get help about dlink, tell us wich model is used please

---

### Post by ian83 on 2015-04-11
ok ill look at the i have dlink, i also now have anew issue, i was attempting to install without the use of that software which makes more reliable partitions as you say, and it seems to have disabled w7, so i can only run ubuntu by choosing it from the esc menu on hp. im looking at it now ive ran sys restore twice and still doesnt work. i think its booted by now and will go look at it

---

### Post by ian83 on 2015-04-11
its a DWA 130

---

### Post by ian83 on 2015-04-11
the dlink thing is now functioning with no installs made, but w7 is still not functional, is there any solution to actually roll back to a previous date?

---

### Post by ian83 on 2015-04-11
I ended up just taking the thing to a comp store and hes gonna nuke it and reinstall w7 using the serial on the underside sticker for a reasonable price

---

