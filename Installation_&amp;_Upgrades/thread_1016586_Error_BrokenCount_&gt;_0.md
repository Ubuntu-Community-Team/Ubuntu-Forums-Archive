---
title: "Error: BrokenCount &gt; 0"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2008-12-20
Hi all, 
 Sorry in advance because this is going to be a long post. 

I had errors in my filesystem today. Hence put up a live CD and ran fsck on that partition. 

$ sudo fsck -y /dev/sdb5

It took some time and removed some stuff but was able to log in. 

Now I'm stuck with a particular issue. My update-manager shows Error: BrokenCount > 0

Looking at [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

I tried 

```
$ sudo apt-get check
```

 and got 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-app-install: Depends:  but it is not installed
                     Depends:  but it is not installed
  onboard: Depends:  but it is not installed
  penguintv: Depends:  but it is not installed
  python-gnome2: Depends:  but it is not installed
  update-manager: Depends:  but it is not installed
E: Unmet dependencies. Try using -f.

```

Then tried both synaptic as well as the CLI and here's the output of the same :-

```

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
    
Suggested packages:
  python-gconf-dbg python-gnome2-extras-doc
The following NEW packages will be installed:
    
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/99.9kB of archives.
After this operation, 406kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 227, in <module>
    main()
  File "/usr/bin/apt-listchanges", line 48, in main
    debs = apt_listchanges.read_apt_pipeline(config)
  File "/usr/share/apt-listchanges/apt_listchanges.py", line 64, in read_apt_pipeline
    (pkgname, oldversion, compare, newversion, filename) = pkgline.split()
ValueError: need more than 4 values to unpack


(Reading database ... 127778 files and directories currently installed.)
Preparing to replace python-gconf 2.22.3-0ubuntu1 (using .../_2.22.3-0ubuntu1_i386.deb) ...
Unpacking replacement python-gconf ...
Preparing to replace python-gtkhtml2 2.19.1-0ubuntu11 (using .../_2.19.1-0ubuntu11_i386.deb) ...
Unpacking replacement python-gtkhtml2 ...
Processing triggers for python-support ...
Package  listed more than once, only processing once.
dpkg: error processing  (--configure):
 no package named `' is installed, cannot configure
Errors were encountered while processing:
 
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now can somebody tell me how can I fix this?

---

### Post by ShirishAg75 on 2008-12-20
bumping it up for answers :(

---

