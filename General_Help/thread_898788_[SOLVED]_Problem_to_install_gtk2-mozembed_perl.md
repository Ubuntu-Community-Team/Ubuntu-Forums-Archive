---
title: "[SOLVED] Problem to install gtk2-mozembed perl"
date: 2008-08-23
forum: General Help
---

### Post by jjgomera on 2008-08-23
Hello

I'm trying to install [gtk2-mozembed perl]("http://sourceforge.net/project/showfiles.php?group_id=64773&package_id=127248"), but i have problem to install:

i've installed the building dependences, i think:
libextutils-pkgconfig-perl, libextutils-depends-perl, libgtk2.0-dev, libxul-dev

but when i try to built i have this error:

```
jjgomera@ordenata:~/mozembed/Gtk2-MozEmbed-0.07$ perl Makefile.PL 
Glib version 1.180 required--this is only version 1.161 at /usr/share/perl/5.8/Exporter/Heavy.pm line 107.
BEGIN failed--compilation aborted at (eval 9) line 1.

Checking if your kit is complete...
Looks good
Warning: Guessing NAME [Gtk2-MozEmbed] from current directory name.
Can't locate object method "postamble_clean" via package "Glib::MakeHelper" (perhaps you forgot to load "Glib::MakeHelper"?) at Makefile.PL line 111.
jjgomera@ordenata:~/mozembed/Gtk2-MozEmbed-0.07$ 

```

really, i dont know how fix that problem

Any help would be appreciate, thanks

---

### Post by jjgomera on 2008-08-25
anyone?

---

### Post by jjgomera on 2008-08-31
nobody?

---

### Post by jjgomera on 2008-09-07
nobody? :(

---

### Post by robwoj44 on 2008-10-04
I have exactly the same problem. I wanted compile it for gmusicbrowser. Did you solve this problem?

---

### Post by robwoj44 on 2008-10-06
You must take the version 0.06 and you will compile it without problem:-)
[http://sourceforge.net/project/showfiles.php?group_id=64773&package_id=127248](http://sourceforge.net/project/showfiles.php?group_id=64773&package_id=127248)

---

### Post by jjgomera on 2008-11-04
Hi
thanks for answer, really for me dont work:

```
jjgomera@ordenata:~/mozembed/Gtk2-MozEmbed-0.06$ perl Makefile.PL
Mozilla::DOM >= 0.01 not found.
Including ApiDoc pod...
Loaded 3 type definitions from maps
    2 GFlags
    1 GtkObject
Found Gtk2 in /usr/lib/perl5/Gtk2/Install
Found Glib in /usr/lib/perl5/Glib/Install
Found Cairo in /usr/lib/perl5/Cairo/Install
Writing build/IFiles.pm
Checking if your kit is complete...
Looks good
Unrecognized argument in LIBS ignored: '-pthread'
Writing Makefile for Gtk2::MozEmbed

```

but with make:

```
Compilation failed in require.
BEGIN failed--compilation aborted.
make: *** [build/podindex] Error 2

```

PD: i want it for gmusicbrowser too :p

---

### Post by robwoj44 on 2008-11-11
Try it - it works:-) I consulted it with the author of gmusicbrowser.
sudo apt-get install libextutils-pkgconfig-perl libextutils-depends-perl libgtk2.0-dev libxul-dev
mkdir ~/mozembed_sandbox
wget [http://search.cpan.org/CPAN/authors/id/T/TS/TSCH/Gtk2-MozEmbed-0.06.tar.gz](http://search.cpan.org/CPAN/authors/id/T/TS/TSCH/Gtk2-MozEmbed-0.06.tar.gz)
tar xvf Gtk2-MozEmbed-0.06.tar.gz
cd Gtk2-MozEmbed-0.06
perl Makefile.PL PREFIX=~/mozembed_sandbox && make && make install
echo 'export PERL5LIB=~/mozembed_sandbox/lib/perl/:$PERL5LIB' >> ~/.bashrc
Last instruction need log off for taking effect.

---

### Post by squentin on 2008-11-14
If you are using intrepid, you should install 0.08 instead of 0.06, and xulrunner-1.9-dev instead of libxul-dev.
So the instructions would be :

```
sudo apt-get install libextutils-pkgconfig-perl libextutils-depends-perl libgtk2.0-dev xulrunner-1.9-dev
rm -rf ~/mozembed_sandbox
mkdir ~/mozembed_sandbox
wget http://search.cpan.org/CPAN/authors/id/T/TS/TSCH/Gtk2-MozEmbed-0.08.tar.gz
tar xvf Gtk2-MozEmbed-0.08.tar.gz
cd Gtk2-MozEmbed-0.08
perl Makefile.PL PREFIX=~/mozembed_sandbox && make && make install
echo 'export PERL5LIB=~/mozembed_sandbox/lib/perl/:$PERL5LIB' >> ~/.bashrc
```
Last instruction need log off for taking effect.
(I added the "rm -rf ~/mozembed_sandbox" to make sure it's clean)

---

### Post by jjgomera on 2008-11-15
> **robwoj44 said:**
> Try it - it works:-) I consulted it with the author of gmusicbrowser.
sudo apt-get install libextutils-pkgconfig-perl libextutils-depends-perl libgtk2.0-dev libxul-dev
mkdir ~/mozembed_sandbox
wget [http://search.cpan.org/CPAN/authors/id/T/TS/TSCH/Gtk2-MozEmbed-0.06.tar.gz](http://search.cpan.org/CPAN/authors/id/T/TS/TSCH/Gtk2-MozEmbed-0.06.tar.gz)
tar xvf Gtk2-MozEmbed-0.06.tar.gz
cd Gtk2-MozEmbed-0.06
perl Makefile.PL PREFIX=~/mozembed_sandbox && make && make install
echo 'export PERL5LIB=~/mozembed_sandbox/lib/perl/:$PERL5LIB' >> ~/.bashrc
Last instruction need log off for taking effect.

Thanks, it works perfect :)

@squentin: Thanks, i yet use hardy, and im glad to see you here :lolflag:

---

### Post by jjgomera on 2008-11-16
well, i thought it's solved, but no totally.

If i start gmusicbrowser in a terminal all is ok, show tab with last.fm,...

but if i launch gmusicbrowser from menu, dont work, dont locate mozembed and this plugins dont work.

I already boot with new configuration

---

### Post by robwoj44 on 2008-11-18
Make a script. In hardy:
 
#!/bin/sh
  export PERL5LIB=~/sandbox/lib/perl/:$PERL5LIB
  exec gmusicbrowser

save this script, for example in ~/gmusicbrowser.sh, make it executable :
chmod +x gmusicbrowser.sh
and change the command in the launcher's properties with: ~/gmusicbrowser.sh

In intrepid  instead of
export PERL5LIB=~/sandbox/lib/perl/:$PERL5LIB
you must specify more the path for perl libraries, by using
export PERL5LIB=~/sandbox/lib/perl/5.8.8/:$PERL5LIB


> **jjgomera said:**
> well, i thought it's solved, but no totally.

If i start gmusicbrowser in a terminal all is ok, show tab with last.fm,...

but if i launch gmusicbrowser from menu, dont work, dont locate mozembed and this plugins dont work.

I already boot with new configuration

---

### Post by jjgomera on 2008-11-18
thanks for answer

it doesnt work, but finally I find the error,

with export PERL5LIB=~/sandbox/lib/perl/:$PERL5LIB it doesnt work
with export PERL5LIB=/home/user/sandbox/lib/perl/:$PERL5LIB it works :confused:

well, finally solved :)

---

