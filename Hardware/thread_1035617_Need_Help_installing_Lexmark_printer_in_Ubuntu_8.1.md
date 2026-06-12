---
title: "Need Help installing Lexmark printer in Ubuntu 8.1"
date: 2009-01-09
forum: Hardware
---

### Post by hoekstbj on 2009-01-09
I've been trying everything to install my Lexmark Z25 printer. I've been using the directions given at [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

I'm still new to Ubuntu so I don't understand everything yet. Here's what it looks like in the terminal.

Not sure if this should go in the Beginner Talk form

Any help would be greatly appreciated since it's been frustrating. 
Thanks 

brandon@inspiron:~$ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists
brandon@inspiron:~$ cd /home/brandon/lexmark
brandon@inspiron:~/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
COPYING
README
z600cups-1.0-1.gz.sh
brandon@inspiron:~/lexmark$ tail -n +143 z600cups -1.0-1.gz.sh >install.tar.gz
tail: option used in invalid context -- 1
brandon@inspiron:~/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh >install.tar.gz
brandon@inspiron:~/lexmark$ tar -xvzf install.tar.gz
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
brandon@inspiron:~/lexmark$ alien -t z600cups-1.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
brandon@inspiron:~/lexmark$ sudo alien -t z600cups-1.0-1.i386.rpm
[sudo] password for brandon: 
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
brandon@inspiron:~/lexmark$ sudo alien -t z600llpddk-2.0-1.i386.prm
File "z600llpddk-2.0-1.i386.prm" not found.
brandon@inspiron:~/lexmark$ sudo alien -t z600llpddk-2.0-1.i386.rpm
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated
brandon@inspiron:~/lexmark$ sudo tar xvzf z600llpddk-2.0.tgz -C /
./
./usr/
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/cartridgemanager.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/printjobmanager.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/printerdevice.h
./usr/lib/
./usr/lib/liblexprinter.a
./usr/lib/liblexprintjob.la
./usr/lib/liblexz600core.so.0.0.0
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexprinter.la
./usr/lib/liblexz600core.la
./usr/lib/liblexprintjob.a
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexz600core.a
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/lxbccln.out
./usr/local/z600llpddk/utility/bnsi3.lut
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/bnsi2.lut
brandon@inspiron:~/lexmark$ sudo tar xvzf z600cups -1.0.tgz -C /
tar: Options `-[0-7][lmh]' not supported by *this* tar
Try `tar --help' or `tar --usage' for more information.
brandon@inspiron:~/lexmark$ sudo tar xvzf z600cups-1.0 tgz -C /
tar: z600cups-1.0: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: tgz: Not found in archive
tar: Error exit delayed from previous errors

---

