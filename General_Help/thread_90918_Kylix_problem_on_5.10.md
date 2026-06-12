---
title: "Kylix problem on 5.10"
date: 2005-11-16
forum: General Help
---

### Post by shultz on 2005-11-16
Hi All,
I try to ./startdelphi but I get error:
./startdelphi
/home/shultz/kylix3/bin/delphi: relocation error: /home/shultz/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

Whats may be wrong?
Installation is ok. Bordertest:
/home/shultz/downloads/kylix3_open/borpretest# ./testsystem
Borland Kylix System Compatibility Test

Checking loader....OK
Checking kernel >= 2.2....OK
Checking libc >= 2.1.2....OK
Checking libjpeg >= 6.2.0....OK

Looks GOOD !!!
This system should be able to run Borland Kylix!

Thanks.

---

### Post by lucasvasconcelos on 2005-11-17
see this link [http://www.jsk.com.br/kylix-ubuntu.html](http://www.jsk.com.br/kylix-ubuntu.html)

---

### Post by vinx on 2006-04-26
I tried all to get Kylix running and these are the things that have to be done to get it up and running op Dapper Drake:

As said in the Brazilian link:
[INDENT]$ sudo apt-get install gcc libgtk1.2 libxaw6[/INDENT]
and
[INDENT]$ sudo ln -s /usr/X11R6/lib/libx11.so.6 /usr/X11R6/lib/libx11.so[/INDENT]
Install as root and do not change any of the settings! Keep the program your friend by not adjust the things it says you should do (when I ignored it, it did not want to register). So, just press enter a lot of times. You can skip the readings by pressing 'q' instead of page-down.

Just to be clear, installing as root:
[INDENT]$ sudo sh setup.sh[/INDENT]
installing as user:
[INDENT]$ sh setup.sh[/INDENT]
(yeah, newbie-proof! :) )

If it kind of locks (strange names and it takes a lot of times), try to uninstall or reinstall and then uninstall. After that delete the directory with rm -Rf, because it has made a mess then. 

Now the little trick, as said by ouw Brazilian friends, the beginning of 'startdelphi' (find it with 'locate -i startdelphi', newbies) has to look like:

[INDENT]#!/bin/bash

# BEGIN STRING TABLE
export LD_ASSUME_KERNEL=2.4
LANG=en_US.ISO8859-1
KYDEF_LOCALE="en_US"
LC_ALL_IS_C1="The LC_ALL environment variable is set to C.  Kylix cannot start with this setting."
LC_ALL_IS_C2="Defaulting LC_ALL to"

# END STRING TABLE[/INDENT]

After that the program will stop screaming about the GLIB_C-blahblah and it will show pas-files correctly.

If it fails on registration, try to copy the file to /root too, or reinstall it as user and then as root again. Also try to delete ~/.borland (why not? except if you have more Borland-products).

This worked for me. Please add comments.
english version of the great JSK-tutorial:
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.jsk.com.br%2Fkylix-ubuntu.html&langpair=pt%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http%3A%2F%2Fwww.jsk.com.br%2Fkylix-ubuntu.html&langpair=pt%7Cen&hl=en&ie=UTF8)
('to tar' should be 'tar')

groetjes,
Vincent

PS: I like it that more and more good tools are available on Linux. Even better news is that Borland transfers all it's IDE's to Eclipse, but till then we have Kylix3... (just search on 'borland ide eclipse' if this is new to you).

---

