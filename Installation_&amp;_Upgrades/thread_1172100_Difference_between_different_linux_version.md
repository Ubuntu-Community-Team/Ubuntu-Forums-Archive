---
title: "Difference between different linux version"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by calvinlyp on 2009-05-28
hi all,

i am relatively new to linux platform.

i am currently using ubuntu 8.10 and also xubuntu 8.10.

i was trying to install some software to my both platform.

from the README.txt of the software provided:

Operating System Compatibility(2): 
   Linux 2.2-2.4 glibc2 based
   Sun Solaris
   Windows NT with Cygnus tools ([Cygnus is now accesso!]("http://www.cygnus.com"))
   Other versions of UNIX using the GCC compiler (untested)

so what is Linux2.2-2.4?
how to differentiate all the different version?
how do i know the current platform i am using is compatible to the above stated OS?

thanks alot.

---

### Post by theozzlives on 2009-05-28
That's your kernel version you can check during boot if you hit esc. The top one in the menu is probably the one your using.

---

### Post by glotz on 2009-05-28
You're on a modern 2.6 kernel.```
uname -r
```

---

### Post by netJackDaw on 2009-05-28
What software are you trying to install? If you are looking in the right place you might find a newer version or a modern alternative... But I (we) have to know to be able to direct you...

---

### Post by jerrrys on 2009-05-28
download 'Ubuntu Tweak', it will give you all the specs plus much more. great app for starting out...

[http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak)

---

### Post by calvinlyp on 2009-05-28
> **netJackDaw said:**
> What software are you trying to install? If you are looking in the right place you might find a newer version or a modern alternative... But I (we) have to know to be able to direct you...

[FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]i was trying to install a software called sharc from [http://sourceforge.net/projects/sharc](http://sourceforge.net/projects/sharc)

[/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]after the command: 
 
./configure 
make 
 
it generate an error: 
cd . && autoconf 
/bin/bash: autoconf: command not found 
make: *** [configure] Error 127 


i have attached 3 files.
all i added the extension of zip.

pls help. 
[/COLOR][/FONT][/COLOR][/FONT]

---

### Post by netJackDaw on 2009-05-28
First of all you shold try to install the missing applications/commands that are specified. Try:

sudo apt-get install autoconf

...to install autoconf

If you after that get more errors try to resolve them in the same manner as above. You can search for packages by using:

apt-cache search package_name_or_description

You might also need to install:

sudo apt-get install build-essential

...but still I strongly recommend that you try to find software through supported channels. In that way you get a more stable system with all dependancies resolved.

If you dont like using the command line to search for packages try searching the online package repo at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Try searching for GPS there and see if you find anything useful.. Maybe the package gpsbabel is something for you. Haven't tried it myself though...

---

### Post by calvinlyp on 2009-05-29
Hi netJackDaw,

actually i did:

apt-get install build-essential

but it stil cant work.

next i tried:
sudo apt-get install autoconf

i got an error of :
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

how do i go about to solve this?

thanks

---

### Post by netJackDaw on 2009-05-29
Did you run the suggested dpkg command? I am sorry but I dont think I can help you any further. If you still have problems try to contact the developer and/or the developers forums.

---

