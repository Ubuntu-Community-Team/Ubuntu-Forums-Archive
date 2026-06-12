---
title: "Problem installing Murrine Engine"
date: 2008-10-14
forum: General Help
---

### Post by NCarlson on 2008-10-14
Is this the right forum?

As the title suggests, I have a problem installing the gtk2-engines-murrine package from the hardy section of the repo.  I get the "dependency not satisfiable: libpango1.0-0" error message.  Next I donloaded that package from the repo, and I still get the error.

(FYI the computer that has these problems CAN NOT connect to the internet, so if you'd refrain from apt-get commands much appreciated)

Thanks in advance

-NCarlson-

---

### Post by NCarlson on 2008-10-15
bump

---

### Post by shawnrgr on 2008-10-15
Can you please paste all cl output ?

---

### Post by NCarlson on 2008-10-17
I didn't use the command line to install the package.  the error is just as the computer threw out.  Is there a way to cd to the package and use the terminal to install it?

---

### Post by oldos2er on 2008-10-18
To install a package already on the hard disk, use the command "sudo dpkg -i packagename" where "packagename" is libpango1.0-0 or whatever. This assumes you're already in the directory where the package file is.

---

### Post by NCarlson on 2008-10-20
Thanks dude.  I'll try that then see what the command line spits out.

EDIT:  I presume that the -i flag means "install" and do I also include the .deb extension?

---

### Post by shawnrgr on 2008-10-20
yes, just use tab to auto complete the file name. in a terminal the TAB key will auto-complete any command/file/folder just start typing (i think at 3+ chars before it will complete) then hit tab. if nothing happens double tap TAB for a list of matches... ;)

---

### Post by NCarlson on 2008-10-21
All right!  Got the command line output:

```

localhost@ubuntu:~/Desktop$ sudo dpkg -i gtk2-engines-murrine_0.60-0ubuntu1~ppa3_i386.deb
(Reading database ... 97767 files and directories currently installed.)
Preparing to replace gtk2-engines-murrine 0.53.1-1ubuntu1 (using gtk2-engines-murrine_0.60-0ubuntu1~ppa3_i386.deb) ...
Unpacking replacement gtk2-engines-murrine ...
dpkg: dependency problems prevent configuration of gtk2-engines-murrine:
 gtk2-engines-murrine depends on libpango1.0-0 (>= 1.20.5); however:
  Version of libpango1.0-0 on system is 1.20.1-1.
dpkg: error processing gtk2-engines-murrine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtk2-engines-murrine
localhost@ubuntu:~/Desktop$

```

---

### Post by shawnrgr on 2008-10-21
I don't understand why your installing a downloaded deb... the murrine engine is in the repositories. The version your trying to install is different from the one currently available with ubuntu. The one in the repositories will work just fine...

```
sudo apt-get install gtk2-engines-murrine
```

---

