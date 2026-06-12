---
title: "Canon imageClass (i-sensys) MF4700 series scanner"
date: 2014-08-15
forum: Hardware
---

### Post by youknowit on 2014-08-15
Ubuntu 14.04 currently ships with sane-backends 1.0.23 which somehow does not support my Canon i-SENSYS MF 4780w all-in-one printer/scanner/fax. 
I compiled sane-backends from source and modified a couple of symbolic links, and now I can use the scanner. Here is what I did. 

First of all, follow this instruction to compile and install the latest sane-backends: [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource) 
Make sure to configure the source with "./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var" before compiling.

After installing, try "scanimage -V". You will see a sort of version mismatch such as "scanimage (sane-backends) 1.0.25git; backend version 1.0.22". You need to make sure that the newest sane-backend libraries are 'actually' used by your newest scanimage. This can be done by fixing the symbolic links. I followed this instruction to get it right: [http://ubuntuforums.org/archive/index.php/t-2072162.html](http://ubuntuforums.org/archive/index.php/t-2072162.html) 

Basically, /usr/lib/sane/ will hold the newest libraries after you install sane-backends from the latest source. However, /usr/lib/i386-linux-gnu/sane still holds the older sane-backends libraries. You need to change the symlink /usr/lib/i386-linux-gnu/sane/libsane-pixma.so and /usr/lib/i386-linux-gnu/sane/libsane-pixma.so.1 to point to /usr/lib/sane/libsane-pixma.so.1.0.25 (the latest sane-pixma library which properly supports i-SENSYS 4700 scanner).

So, do something like this:
```
$ sudo ln -i -s /usr/lib/sane/libsane-pixma.so.1.0.25 /usr/lib/i386-linux-gnu/sane/libsane-pixma.so
$ sudo ln -i -s /usr/lib/sane/libsane-pixma.so.1.0.25 /usr/lib/i386-linux-gnu/sane/libsane-pixma.so.1
```

Then, try "scanimage -L" . Your scanner should now be detected. If not, make sure that you edit /etc/sane.d/pixma.conf to add "bjnp://192.168.123.10" (assuming this is your scanner's ip address)

In order to actually 'scan' a document, you need to choose "Remote Scan" from the scanner itself. If you do not do this, your scanner software (xsane, for example) will complain that the scanner is busy.

---

