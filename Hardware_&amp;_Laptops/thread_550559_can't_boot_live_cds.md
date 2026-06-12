---
title: "can't boot live cds"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by ice109 on 2007-09-14
i can't boot any of the *buntu live cds. i've tried ku/u/xu and they get to the initial menu where it ask what you want to do, boot, safe graphic mode etc and i select boot or install and then a blank screen. this is on a dell latitude c400. any ideas?

---

### Post by rivalarrival on 2007-09-14
Are you waiting long enough?  LiveCDs are notoriously slow...

I had a similar problem - I was trying to setup a desktop edition as a server (I wanted some sort of GUI as a crutch - recent Redmond Refuge) but the installer wouldn't work for some reason or another...  I ended up using the server version and using ```
apt-get ubuntu-desktop
``` to install the GNOME gui later.

---

### Post by abhilash82 on 2007-09-14
Did you try the safe graphics mode option?

---

### Post by ice109 on 2007-09-14
> **abhilash82 said:**
> Did you try the safe graphics mode option?

yup the disk just stops spinning eventually with either menu selection

in fact i think none of the options work, probably only boot from main hard disk

---

### Post by ice109 on 2007-09-14
bump, now i've tried burning another copy of one of the distros to make sure it wasn't a scratched disk and it still doesn't work.

---

### Post by abhilash82 on 2007-09-15
Sometimes 256MB of RAM is not sufficient to run the Live CD. Did you try the Memtest option in the boot menu? Did you find any errors in the RAM?

Another way is to download the alternate version of ubuntu iso which can be customized for lesser memory PCs.

Info about downloading and installing using an alternate ubuntu iso can be fond in the links given below.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate)

---

### Post by Sef on 2007-09-15
1. Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the downloads?

2. Did you burn the iso at 4x or less?

---

