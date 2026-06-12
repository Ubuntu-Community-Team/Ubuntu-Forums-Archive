---
title: "installing tar.gz file"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by jayanramesh on 2009-11-07
Dear buddies,
Whenever I install tar.gz or tar.bz on karmic everything goes right till-./configure then it gives the output after giving the code-make-as"_No target specified and no make file found_".How can I fix the target to set it right?.

---

### Post by shababhsiddique on 2009-11-10
> **jayanramesh said:**
> Dear buddies,
Whenever I install tar.gz or tar.bz on karmic everything goes right till-./configure then it gives the output after giving the code-make-as"_No target specified and no make file found_".How can I fix the target to set it right?.

Did you tried?

./configure
make
sudo make install
I hope you are in the directory where you extracted .tar.gz . You can jump to the directory using cd commands.
cd /
cd your directory

---

### Post by lswb on 2009-11-10
There is no standard method for installing something from a .tar.gz file. While true that the sequence ```
./configure
make
make install
``` is very common, it is not universal by any means. The .tar.gz file can include precompiled executable binaries that are istalled by a shell script for instance, or many other installation methods.

After you untar the .tar.gz, look in the newly created directory for a README or INSTALL or other likely named file for instructions. Often there is a website for the software with instructions. If you still have no success, post again naming the specific software you are trying to install and the source where you obtained it.

---

### Post by zhaxnti on 2009-11-10
> **lswb said:**
> There is no standard method for installing something from a .tar.gz file. While true that the sequence ```
./configure
make
make install
``` is very common, it is not universal by any means. The .tar.gz file can include precompiled executable binaries that are istalled by a shell script for instance, or many other installation methods.

After you untar the .tar.gz, look in the newly created directory for a README or INSTALL or other likely named file for instructions. Often there is a website for the software with instructions. If you still have no success, post again naming the specific software you are trying to install and the source where you obtained it.
I agree with Mr.Iswb, you must read the README or INSTALL file,maybe you can find the answer... or you must be install autoconf and automake before you run the configuration...

---

### Post by jayanramesh on 2009-11-11
Thanks to everyone who took pain to furnish me with precious and precise answers.But I tried all without the fruits.I tried installing VLC 1.0.3, tar.gz & audacious-plugins-2.1.tgz and they gave me the  warning as "[COLOR="Red"]No target specified and no make file found[/COLOR]" so how can I proceed further?.

---

