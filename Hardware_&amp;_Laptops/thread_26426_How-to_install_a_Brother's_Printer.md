---
title: "How-to install a Brother's Printer"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by rbarth on 2005-04-12
If your new at this like I am, then hopefully this will help. Between the new terminology and the things that proficient Linux users take for granted, I wasted an entire weekend just trying to get my mfc210c printer working.

	First you must go to the “Unofficial Ubuntu 5.04 Starter Guide” located at > [http://ubuntuguide.org/](http://ubuntuguide.org/)  Now look for “How to add extra repositories?” and accomplish steps 1 trough 6.  I suggest that you copy and paste the extra lines that are needed.

	Second now you can use “Synaptic Package Manager”, found under > System > Administration >  Synaptic Package Manager Select search and locate the file “tcsh” , mark for install and hit continue. This apparently installs the “C” shell which will be needed later on, the little something that all the notes fail to explain.

	Third step is to go to the Brother solution center at > [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)  and select “LPR Printer Driver,” click and then select your model which must be located under the Debian files. Save the file to disk, use your home directory, this is the default starting place for the root terminal, this way you can learn about changing paths to different folders later on. Do not extract these files at this time.

	Now go back to the  Brother solution center and select CUPS wrapper driver and do the same as you did above.

	Enter into the root terminal via > Application > System tools > root terminal and type>  apt-get install libstdc++2.10-glibc2.2 and wait till it is done. Next you will type>  apt-get install libqt3c102  and wait till it is done.

	Once the files are installed you will type > ln -s /usr/lib/libqt.so.3 /usr/lib/libqt.so.2  and wait till it is done. Next you will type>  ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.2-2.so.3 again wait till it is done. You have now successfully linked these files.

	Now to install the LPR drivers, type in>  dpkg -i –force-overwrite mfc210clpr-1.0.0-1.i386.deb  again wait till it is done.

	Finally type in >  dpkg -i –force-overwrite cupswrappermfc210c_1.0.0-1_i386.deb when it's done go to > System > Administration >  Printers. Double click and you should now see an icon with your Brother's printer name. Right click on the printer icon and select properties.Try the test print to be sure it is working.

	The instructions from step three to the end can be found on the Brothers web site. I hope that this is useful to someone.

Bob

---

### Post by lignito on 2005-12-12
Thank a lot for this input, it did help me . Did you make the scanner to work and how?Would like the input of this please...

---

