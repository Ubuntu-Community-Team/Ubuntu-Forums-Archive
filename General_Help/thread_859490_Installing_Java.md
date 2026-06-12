---
title: "Installing Java"
date: 2008-07-14
forum: General Help
---

### Post by R2D2! on 2008-07-14
I'm trying to install Java. I followed the instructions from [http://www.java.com/en/download/help/5000010500.xml]("http://www.java.com/en/download/help/5000010500.xml"). When I do ```
./jre-6u<version>-linux-i586-rpm.bin
``` and agree the License Terms, it shows this:

```
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u7-linux-i586.rpm  
error: Dependencias fallidas:
	/bin/basename se necesita por jre-1.6.0_07-fcs.i586
	/bin/cat se necesita por jre-1.6.0_07-fcs.i586
	/bin/cp se necesita por jre-1.6.0_07-fcs.i586
	/bin/gawk se necesita por jre-1.6.0_07-fcs.i586
	/bin/grep se necesita por jre-1.6.0_07-fcs.i586
	/bin/ln se necesita por jre-1.6.0_07-fcs.i586
	/bin/ls se necesita por jre-1.6.0_07-fcs.i586
	/bin/mkdir se necesita por jre-1.6.0_07-fcs.i586
	/bin/mv se necesita por jre-1.6.0_07-fcs.i586
	/bin/pwd se necesita por jre-1.6.0_07-fcs.i586
	/bin/rm se necesita por jre-1.6.0_07-fcs.i586
	/bin/sed se necesita por jre-1.6.0_07-fcs.i586
	/bin/sort se necesita por jre-1.6.0_07-fcs.i586
	/bin/touch se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/cut se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/dirname se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/expr se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/find se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/tail se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/tr se necesita por jre-1.6.0_07-fcs.i586
	/usr/bin/wc se necesita por jre-1.6.0_07-fcs.i586
	/bin/sh se necesita por jre-1.6.0_07-fcs.i586
 
Done.

```
Where can I get that files?

—Ilhu&#305;temoc &#948;

---

### Post by kk0sse54 on 2008-07-14
From your first code it looks like you downloaded a rpm package. rpm is for distro's like Red Hat or Fedora. While it probably would be better just to download the correct package you could probably  use Alien to convert the package to the proper format.

---

### Post by Ataris on 2008-07-14
Here is a quick guide.

1. Go to [http://java.com/en/download/manual.jsp]("http://java.com/en/download/manual.jsp")

2. Scroll down and right click on Linux (self-extracting file). Click on Save Target As...

You'll get a .bin file.

Now follow the instructions here: [http://java.com/en/download/help/5000010500.xml#selfextracting]("http://java.com/en/download/help/5000010500.xml#selfextracting")

---

