---
title: "Canon LBP 660 and 460 HOWTO on Ubuntu"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by stedevil on 2007-11-12
The Canon LBP-660 (and LBP-460) GDI/Win printers unfortunately dont work out of the box with Ubuntu linux.

To make it work in Ubuntu (tested on 7.04 with CUPS 1.2.8, if anybody tries in 7.10 or other versions/dists, please report your experience).

1) apt-get install build-essential (to make sure you have the minimum required packages to compile & install the driver)
2) Download lbp660-0.3.1.tar.gz from [http://www.boichat.ch/nicolas/lbp660/](http://www.boichat.ch/nicolas/lbp660/) and extract it
3) cd into the unpacked folder in a terminal window
4) sudo -s (to make you root)
5) make
6) make install
7) The restartcups.sh file is broken, so REPLACE what is in it with the below (if you are using another dist you might need another line for the CUPS restart)

#!/bin/sh
cp /usr/share/cups/model/Canon-LBP-* /usr/share/ppd/
/etc/init.d/cupsys restart
echo "Waiting 5 seconds..."
sleep 5

8) install your printer by using one of the following lines
make cups-install-660-a4
make cups-install-660-letter
make cups-install-460-a4
make cups-install-460-letter

9) In a browsers address field enter localhost:631, click the [Printers]-tab and then on the [Print Test Page]-button to verify it works.

---

### Post by jis on 2007-11-16
In [another thread]("http://ubuntuforums.org/showthread.php?p=3778222") it is reported that printing did not succeed, when the driver is used in ubuntu 7.10.

Why do you need the 
```
cp /usr/share/cups/model/Canon-LBP-* /usr/share/ppd/
```
line in restartcups.sh?

---

### Post by stedevil on 2007-11-16
> **jis said:**
> In [another thread]("http://ubuntuforums.org/showthread.php?p=3778222") it is reported that printing did not succeed, when the driver is used in ubuntu 7.10.


Why do you need the 
```
cp /usr/share/cups/model/Canon-LBP-* /usr/share/ppd/
```
line in restartcups.sh?


Hmm, printer stopped working for me as well when I updated all my comps to 7.10 and I decided to revert back to 7.04 on the one that my 660 was connected to (only 1 with an printer port). Once back in 7.04 I decided to not just manually hack my way through installation, but see if I could fix the install script (a lot of people on the net seems to have big problems with getting the LBP-x60 working at all).

The reason I do the cp /usr/share/cups/model/Canon-LBP-* /usr/share/ppd/ is because it looks like the CUPS program the install script calls fails because it is no longer looking for ppd's in /usr/share/cups/model/ but in /usr/share/ppd/ instead. I assume it's a change that has been made in CUPS since 2005 (when Boichat made his last driver release). Since the restartcups.sh is FUBARed in any case (again outdated?) I just decided to put all the changes in 1 place instead of having people weed through the much larger scriptfile to make this change. Additionally doing it this way wont break backwards compability (though thinking about it right now I guess an ln -s would do the job equally well as a cp).

As for why it isnt working on 7.10, I dont know. Maybe 7.10 is doing something weird or CUPS itself have become incompatible with the old Boichat driver (last updated in 2005). Would be interesting to know if eg installing CUPS 1.3.2 on Ubuntu 7.04 would work. Then again, perhaps just a bug report and letting the pros (that knows what is going on in CUPS development and not just guessing like me) handle it would be the best solution. 

Would you care to file a bug report in Ubuntu, since it is now been determined to be a  regression from 7.04 -> 7.10? They should be able to figure out if this is an upstream or Ubuntu problem and hopefully fix it with a specific install package or service update. :)

---

### Post by jis on 2007-11-16
Well, I don't get any (visible) error message when running (sudo) make cups-install-660-a4, even if I haven't copied or symlinked the Canon-LBP-* files to /usr/share/ppd/. In contrary, I see a message that tells that restarting Common Unix Printing System cupsd was ok.

---

### Post by jis on 2007-11-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/163148](https://bugs.launchpad.net/ubuntu/+bug/163148) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just filed a bug report about this.

---

### Post by stedevil on 2007-11-16
That line has nothing what so ever to do with if CUPS will be restartable or not, it "only" matter for if the printer will actually work or not.

With that line
```

> sudo make cups-install-660-a4
install -s -m a=rxs lbp660 /usr/bin
install -s -m a=rxs lbp460 /usr/bin
echo "Installing foomatic..."
Installing foomatic...
install -m a=rx foomatic-rip /usr/bin
install -m a=rx foomatic-gswrapper /usr/bin
rm -f /usr/lib/cups/filter/foomatic-rip
ln -s /usr/bin/foomatic-rip /usr/lib/cups/filter/foomatic-rip
echo "Foomatic installed."
Foomatic installed.
install -m a=rxs ppd/Canon-LBP-660-lbp660.ppd /usr/share/cups/model
install -m a=rxs ppd/Canon-LBP-460-lbp460.ppd /usr/share/cups/model
echo "Restarting CUPS..."
Restarting CUPS...
./restartcups.sh
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Waiting 5 seconds...
echo "CUPS restarted."
CUPS restarted.
/usr/sbin/lpadmin -x LBP-660 | /bin/true
/usr/sbin/lpadmin -p LBP-660 -E -m Canon-LBP-660-lbp660.ppd -v file:/dev/null
lpoptions -p LBP-660 -o PageSize=A4
lpoptions -p LBP-660 -o LeftSkip=70
lpoptions -p LBP-660 -o Topskip=100
lpoptions -p LBP-660 -o AlwaysReset=True

```

Without it
```

> sudo make cups-install-660-a4
install -s -m a=rxs lbp660 /usr/bin
install -s -m a=rxs lbp460 /usr/bin
echo "Installing foomatic..."
Installing foomatic...
install -m a=rx foomatic-rip /usr/bin
install -m a=rx foomatic-gswrapper /usr/bin
rm -f /usr/lib/cups/filter/foomatic-rip
ln -s /usr/bin/foomatic-rip /usr/lib/cups/filter/foomatic-rip
echo "Foomatic installed."
Foomatic installed.
install -m a=rxs ppd/Canon-LBP-660-lbp660.ppd /usr/share/cups/model
install -m a=rxs ppd/Canon-LBP-460-lbp460.ppd /usr/share/cups/model
echo "Restarting CUPS..."
Restarting CUPS...
./restartcups.sh
 * Restarting Common Unix Printing System: cupsd                              [ OK ] 
Waiting 5 seconds...
echo "CUPS restarted."
CUPS restarted.
/usr/sbin/lpadmin -x LBP-660 | /bin/true
/usr/sbin/lpadmin -p LBP-660 -E -m Canon-LBP-660-lbp660.ppd -v file:/dev/null
[color=red]lpadmin: Unable to copy PPD file!
make: *** [cups-install-660] Error 1[/color]

```

---

### Post by jis on 2007-11-16
But I get the output that you get with the line also without the line.

---

### Post by stedevil on 2007-11-16
> **jis said:**
> But I get the output that you get with the line also without the line.

Before trying without the line, do you first manually remove the files from the ppd directory that a previous run with the line already copied there?

Ie, first do 
sudo rm /usr/share/ppd/Canon-*
and then try the install without the 
cp ...
in restartcups.sh

---

### Post by jis on 2007-11-17
Actually I removed the respective symlinks and didn't add the line to create ones in the script. Did you try it in 7.10?

---

### Post by stedevil on 2007-11-17
> **jis said:**
> Actually I removed the respective symlinks and didn't add the line to create ones in the script. Did you try it in 7.10?

I tried it on my 7.10 Laptop now, and it works fine without the cp 
So, with 7.10, feel free to skip that line.

BTW any progress in getting any actual printing to work on 7.10?

---

### Post by mirkuma on 2007-12-01
>  BTW any progress in getting any actual printing to work on 7.10?
Nope, here also. All installes ok, but won't print...

---

### Post by jis on 2007-12-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/163148](https://bugs.launchpad.net/ubuntu/+bug/163148) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, after I removed apparmor package.

---

### Post by mirkuma on 2007-12-04
Thanks! Works now. I use script to stop apparmor when i need to print.

---

### Post by stedevil on 2007-12-13
There was a bunch of suggested patches coming down the pipe a few days ago that supposedly fixes a lot of these issues on many hardware setups. This fix apparently was to not set restrictions for eg third party printer drivers since you cannot predict if they will need root access or not (the lbp660 driver needs it eg)

I've yet to try it myself, but this should mean that printing again is possible even with Ubuntu 7.10 without modifying apparmour behaviour manually.

PS: Here is a related sisterbug affecting another printer with the details for the fixes implemented
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537)

---

### Post by nicktns on 2008-04-26
In Ubuntu 8.04 - Hardy Heron ,before instaling you're printer with "make cups-install-460-a4"(for my printer) you must delete the model file from: "/usr/share/cups" then make a folder with name "model" (sudo /mkdir/usr/share/cups/model) and copy the ppd files from unpacked folder (ex: cp /home/nick/download/lbp660-0.3.1/ppd/Canon-LBP-* /usr/share/cups/model/). That's all.

---

