---
title: "Ubuntu 12.10 no longer boot after driver installation"
date: 2013-01-11
forum: Hardware
---

### Post by Hyper Tails on 2013-01-11
Hey guys, I have Ubuntu 12.10 installed, I have a ATI Radeon HD 5770 graphics card installed.

I wanted to install the drivers because I recently install steam for Linux, and I wanted to make use of my graphics card's performance.

However, I installed the drivers (Downloaded from their website) and I can no longer boot into Ubuntu; I get a blank screen.

Any help will be thank on restoring and fixing this issue.

---

### Post by iponeverything on 2013-01-11
use ctrl-alt-f2 to get terminal.

from there login and get a super-user prompt with sudo -i.

get package name of package that borked your graphics with:

```

cd ~root/.synaptic/log/
cat `ls -tr |tail -1`

```

uninstall it with (where <package> is what was found above):

```
dpkg -e --purge <package> 
```

reboot with:

```
shutdown -r now
```

---

### Post by Yellow Pasque on 2013-01-12
@ipon: the OP probably didn't even create a package (assuming s/he installed directly from the .run file).

@OP: You don't need to download the driver from AMD's site, and if you go that route, you have to make sure certain packages are installed, or else you have the borkage.

Do this:
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

Then, if you want to install the Catalyst driver, simply grab it from the repo:
```
sudo apt-get install linux-source fglrx fglrx-amdcccle
```

---

