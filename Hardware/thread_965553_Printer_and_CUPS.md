---
title: "Printer and CUPS"
date: 2008-10-31
forum: Hardware
---

### Post by pyromanic123boom on 2008-10-31
After an upgrade to Intrepid, I lost my printer settings and appearantly, my cups server. I have tried to reinstall the cups sys, sd, etc, but it still isn't running and it won't come up in localhost:631. 

Following the Brother Printer guide, I have installed my MFC7420 before. So now, when I tried to install the cups driver for the printer again, it gives me a bad output. 

```

peter@desktop:~$ cd /home/peter/Downloads/brother
peter@desktop:~/Downloads/brother$ sudo dpkg -i cups.deb
(Reading database ... 277901 files and directories currently installed.)
Preparing to replace cupswrappermfc7420 2.0.1-2 (using cups.deb) ...
lpadmin: Unable to connect to server: Connection refused
/usr/sbin/cupsd: error while loading shared libraries: libcupsmime.so.1: cannot open shared object file: No such file or directory
cups: unable to restart scheduler.
Unpacking replacement cupswrappermfc7420 ...
Setting up cupswrappermfc7420 (2.0.1-2) ...
/usr/sbin/cupsd: error while loading shared libraries: libcupsmime.so.1: cannot open shared object file: No such file or directory
cups: unable to restart scheduler.

lpinfo: Unable to connect to server: Connection refused
lpinfo: Unable to connect to server: Connection refused
lpadmin: Unable to connect to server: Connection refused

```

Does anyone have any ideas on this? I read about a bug in Interpid that causes some of theses issues...  Thanks to anyone who has got some fixes.

---

### Post by hopesdevid on 2008-10-31
i have check your code and i am trying to get more information about this, i will give you reply after getting answer.

---

### Post by pyromanic123boom on 2008-11-01
still not working..

i think that hardy is more secure and they released intrepid too soon..

---

### Post by pyromanic123boom on 2008-11-02
bump.. 

i need some help with this

---

### Post by pyromanic123boom on 2008-11-02
Ok, once again I fix my own problems.  I found this thread mentioning a very similar problem -- [http://ubuntuforums.org/showthread.php?t=926027](http://ubuntuforums.org/showthread.php?t=926027).  So when I read it, I realized that in Intrepid some of the cups packages get changed around.  I compiled Cups 1.38 from source, (I think that 1.38 works well for Intrepid from what I found), and then I browsed my /etc/init.d directory.  All I found was cups there, (no cupsd), so I did a quick sudo /etc/init.d/cups restart and then it told me the scheduler was back.  So my printer and pdf printers are back, and localhost is working again!  If anyone else has this problem (as it appears to be a bug with Intrepid), then try to do something here, or follow what the other guy did in the other thread.  He copied some cups files from the live cd.  Well it's fixed anyway and I'm done.

---

### Post by coalcracker on 2008-11-03
I was having the same problem and compiled Cups 1.3.8 from source and it worked for me. thanks for the suggestion pyromanic123boom.

---

