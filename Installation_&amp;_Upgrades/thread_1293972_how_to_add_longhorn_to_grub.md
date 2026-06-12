---
title: "how to add longhorn to grub"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by BigCityCat on 2009-10-17
I just installed Karmic with the alt install cd. It installed fine, but it did not install longhorn. The vista partition is there. I mounted it and moved some files over to Karmic. I don't no why it didn't install an option to login into vista. The cd I have to install Vista is a system recovery cd from the manufacturer, so it won't let me use it to repair the system.

---

### Post by bulldog on 2009-10-17
You have to add some lines to the bottom of your menu.lst,and they look similar like this,which I copied from my menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista (loader)
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

You must find out on which partition and/or hdd your vista partition is located,and change that to your liking.
As you can see is my Vista on the third hdd in the first partition.
Don't forget the mapping lines,windows wants to be on the first partition on the first hdd,and with mapping we can make windows think it is.

---

### Post by BigCityCat on 2009-10-17
I'm not sure I can do it. I was thinking I would just use parted magic to delete the ubuntu partition. Then re install with a karmic disc that is not the alternate install disc. Do you think that would work?

---

### Post by oldfred on 2009-10-17
If you did a new install of karmic you have grub2 not grub legacy (.97)
There is no menu.lst. It should find all other operating systems.

Use osprober to find other systems to boot:
[http://ubuntuforums.org/showpost.php?p=8008800&postcount=3](http://ubuntuforums.org/showpost.php?p=8008800&postcount=3)

Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

---

### Post by BigCityCat on 2009-10-17
> **oldfred said:**
> If you did a new install of karmic you have grub2 not grub legacy (.97)
There is no menu.lst. It should find all other operating systems.

Use osprober to find other systems to boot:
[http://ubuntuforums.org/showpost.php?p=8008800&postcount=3](http://ubuntuforums.org/showpost.php?p=8008800&postcount=3)

Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

Thats awesome. Thank you so much. Did that just add longhorn to grub.

---

### Post by BigCityCat on 2009-10-17
Yup that was it. I had a feeling it was something simple.

---

