---
title: "Canon Printers in Breezy 550i"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by jerrykenny on 2005-11-17
Installing Canon Printers on any Debian Distro using the Drivers from Canon Japan ?

You need libpng and libtiff, (newest versions) then in /usr/lib/ created symbolic links from libpng2 to the new version (repeat for libtiff)
 
1/ For the above do   [COLOR="Blue"]<apt-cache search libpng>[/COLOR] to see what versions are available, same for libtiff . . . . . 

2/ Get your rpms here . . . .[COLOR="Blue"]ftp://download.canon.jp/pub/driver/bj/linux/[/COLOR] you'll need the cups interface + the corresponding rpm for your specific printer.

3/ Next, create .debs from the two rpm's (you need the 2.2.1 version for the 550i) [COLOR="blue"]<apt-get install alien>[/COLOR] 
  [COLOR="blue"]<alien whatever.rpm>[/COLOR]

4/ manually install the .debs  <dpkg -i whatever.deb>
 
5/ Restart the cups server  /etc/init.d/cupsys restart

6/ Check the installation of the above debs from a console by typing [COLOR="blue"]<bjfilterpixus550i>[/COLOR]  you should get the following output (but dont worry at this stage if you dont . . : )

BJLSTART
ControlMode=Common
SetTime=20061125192711
BJLEND

7/ In fact at this stage you'll probably get an error message telling you libpng2 cant be found . . . I get round this by manually creating a symlink to my version of libpng (its in /usr/lib/) and calling my symlink libpng2

8 / Do the same for libtiff, keep trying  [COLOR="blue"]<bjfilterpixus550i>[/COLOR] untill you finally get the desired output above

9/ reinstall your .debs (step 4)

10/ switch off, and connect the dratted thing on the Printer-Port (I wonder if that requires a reboot) : )
 
11/ start up, and Access the cups admin on [http://localhost:631](http://localhost:631)
 
12/ IGNORE the option to install the "detected" printer these are all RED HERRINGS !!!. . .instead go to "add printer" . . . . and go thru the details . . . you MUST specify the LPT Port !!!!!!!!!!!!! 
 
13/ In my case I had to specify a ppd file, they're in /usr/share/cups/model
 
 
 Good Luck
 
 
Remember, once you've installed your .debs, you have to check to see if you created your symbolic links OK. . . . if your symlinks are not to the correct libraries, it'll let you know. . . . (unusually helpfull)

---

