---
title: "[SOLVED] Package Manager Error Help! YIKES!"
date: 2008-09-12
forum: General Help
---

### Post by augoldfinger on 2008-09-12
Help with System error

I tried to install a unsupported wireless printer scanner Brother MFC-665CW. I actually went to the Ubuntu forum & found drivers from another user.

There were two, One did install, the first. The second did not. Now I have a system error with my package manager.

Which says > :An error occurred, please run Package Manager from right click menu or apt-get in a terminal to see what is wrong. The error message was "Unknown Error"<type 'exceptions.system error'> (E:the package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.) 'This usually means that your installed packages have unmet dependencies.

When I run package manager I get an error that says > "E: The package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report." I click close & the window closes

When I double click the package manager icon I get > "Not all updates can be installed"
then is has a selection of a partial upgrade or close. If I select partial upgrade I get Remove package in bad state? Y or N
If I select Y I get > "Package in inconsistent state"
"The package 'mfc665cwcupswrapper' is in a inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system."
Then a box asking me to close. the terminal window will also close at this time.

I am too new at Ubuntu to know where to look or what to do.

If someone would help I would really appreciate. I really don't want to do another system install, just to fix this. I figure that the problem is simple, but I sure don't have the solution.

Thanks Much Brad!!!

---

### Post by knattlhuber on 2008-09-12
Try

```
sudo apt-get remove mfc665cwcupswrapper
```

in a terminal window.

That should remove the package (hopefully).

Did you check below site for more info on installing Brother printers on Linux? There's probably a page for your printer that tells you what other packages to install before installing the printer drivers.

[http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")

---

### Post by augoldfinger on 2008-09-12
Hello,
Thanks for the reply, I really appreciate it!

I did open a terminal & pasted the code you sent. 

I got ```
E: The package mfc665cwcupswrapper needs to be reinstalled,
 but I can't find an archive for it.

```

I'll sure review the link you sent

---

### Post by knattlhuber on 2008-09-12
Try

```
sudo dpkg --force-uninstall-reinstreq mfc665cwcupswrapper
sudo apt-get update
sudo apt-get --fix-broken upgrade
```

---

### Post by augoldfinger on 2008-09-12
Hello,
When I open a terminal & type```
sudo dpkg --force-uninstall-reinstreq mfc665cwcupswrapper

```
I got ```
~$ sudo dpkg --force-uninstall-reinstreq mfc665cwcupswrapper
dpkg: unknown force/refuse option `uninstall-reinstreq'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

When I did the update it worked & took the red package manager icon away, but still had ```
:An error occurred, please run Package Manager from right click menu or apt-get in a terminal to see what is wrong. The error message was "Unknown Error"<type 'exceptions.system error'> (E:the package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.) 'This usually means that your installed packages have unmet dependencies.
```

When I the fix broken update I got ```
 sudo apt-get --fix-broken upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.
```

I really appreciate your help on this.

---

### Post by knattlhuber on 2008-09-12
> **augoldfinger said:**
> Hello,
When I open a terminal & type```
sudo dpkg --force-uninstall-reinstreq mfc665cwcupswrapper

```
I got ```
~$ sudo dpkg --force-uninstall-reinstreq mfc665cwcupswrapper
dpkg: unknown force/refuse option `uninstall-reinstreq'



Oops sorry.. should read

[CODE]sudo dpkg --force-remove-reinstreq mfc665cwcupswrapper
```

---

### Post by augoldfinger on 2008-09-12
Hello,
Everything seemed to work without a hitch until the last line of code. I got```
sudo apt-get --fix-broken upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.

```

Is it possible that I might hap put this in the wrong dir?

---

### Post by knattlhuber on 2008-09-12
Somebody on the German Ubuntuforums had the same problem ([http://forum.ubuntuusers.de/topic/kaputtes-apt-get-ubuntu-6.10]("http://forum.ubuntuusers.de/topic/kaputtes-apt-get-ubuntu-6.10")). Please do

```
cat /var/lib/dpkg/info/mfc665cwcupswrapper.prerm
cat /var/lib/dpkg/info/mfc665cwcupswrapper.postinst

locate *mfc665cw*

```

and we take it from there.

---

### Post by augoldfinger on 2008-09-12
Hello,
Again Thanks Much!

```
joseph@ShopPC:~$ cat /var/lib/dpkg/info/mfc665cwcupswrapper.prerm
#!/bin/sh
# ESP Package Manager v3.7.0
/usr/local/Brother/Printer/"mfc665cw"/cupswrapper/cupswrapper"mfc665cw" -e
joseph@ShopPC:~$ cat /var/lib/dpkg/info/mfc665cwcupswrapper.postinst
#!/bin/sh
# ESP Package Manager v3.7.0
/usr/local/Brother/Printer/"mfc665cw"/cupswrapper/cupswrapper"mfc665cw"
joseph@ShopPC:~$ locate *mfc665cw*
/home/joseph/.local/share/Trash/files/mfc665cwcupswrapper-1.0.0-6.i386.deb
/home/joseph/.local/share/Trash/files/mfc665cwcupswrapper-1.2.0.0-6.i386.deb
/home/joseph/.local/share/Trash/files/mfc665cwlpr-1.0.0-6.i386.deb
/home/joseph/.local/share/Trash/files/mfc665cwlpr-1.2.0.0-6.i386.deb
/home/joseph/.local/share/Trash/info/mfc665cwcupswrapper-1.0.0-6.i386.deb.trashinfo
/home/joseph/.local/share/Trash/info/mfc665cwcupswrapper-1.2.0.0-6.i386.deb.trashinfo
/home/joseph/.local/share/Trash/info/mfc665cwlpr-1.0.0-6.i386.deb.trashinfo
/home/joseph/.local/share/Trash/info/mfc665cwlpr-1.2.0.0-6.i386.deb.trashinfo
/home/joseph/Desktop/mfc665cwcupswrapper-1.0.1-1.i386.deb
/home/joseph/Desktop/mfc665cwlpr-1.0.1-1.i386.deb
/usr/bin/brprintconf_mfc665cw
/usr/local/Brother/Printer/mfc665cw
/usr/local/Brother/Printer/mfc665cw/inf
/usr/local/Brother/Printer/mfc665cw/lpd
/usr/local/Brother/Printer/mfc665cw/inf/brPrintListij2
/usr/local/Brother/Printer/mfc665cw/inf/brio06aa.bcm
/usr/local/Brother/Printer/mfc665cw/inf/brio06ab.bcm
/usr/local/Brother/Printer/mfc665cw/inf/brio06ac.bcm
/usr/local/Brother/Printer/mfc665cw/inf/brio06af.bcm
/usr/local/Brother/Printer/mfc665cw/inf/brio06ag.bcm
/usr/local/Brother/Printer/mfc665cw/inf/brmfc665cwfunc
/usr/local/Brother/Printer/mfc665cw/inf/brmfc665cwrc
/usr/local/Brother/Printer/mfc665cw/inf/paperinfij2
/usr/local/Brother/Printer/mfc665cw/inf/setupPrintcapij
/usr/local/Brother/Printer/mfc665cw/lpd/brmfc665cwfilter
/usr/local/Brother/Printer/mfc665cw/lpd/filtermfc665cw
/usr/local/Brother/Printer/mfc665cw/lpd/psconvertij2
/var/lib/dpkg/info/mfc665cwcupswrapper.conffiles
/var/lib/dpkg/info/mfc665cwcupswrapper.list
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst
/var/lib/dpkg/info/mfc665cwcupswrapper.postrm
/var/lib/dpkg/info/mfc665cwcupswrapper.preinst
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm
/var/lib/dpkg/info/mfc665cwlpr.conffiles
/var/lib/dpkg/info/mfc665cwlpr.list
/var/lib/dpkg/info/mfc665cwlpr.postinst
/var/lib/dpkg/info/mfc665cwlpr.postrm
/var/lib/dpkg/info/mfc665cwlpr.prerm

```

Brad

---

### Post by knattlhuber on 2008-09-12
Try

```
gksudo gedit /var/lib/dpkg/info/mfc665cwcupswrapper.prerm
```

and add a '#' in front of the second line. Save the file. Then do 

```
gksudo gedit /var/lib/dpkg/info/mfc665cwcupswrapper.postinst
```

and add a '#' in front of the second line. Save the file. Now run

```
sudo dpkg -r --force-all mfc665cwcupswrapper
```

---

### Post by augoldfinger on 2008-09-12
Hello,
```
sudo dpkg -r --force-all mfc665cwcupswrapper
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 128566 files and directories currently installed.)
Removing mfc665cwcupswrapper ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc665cwcupswrapper

```

When you say add a #, it already had one on the second line. should it read?```
#!/bin/sh
## ESP Package Manager v3.7.0
/usr/local/Brother/Printer/"mfc665cw"/cupswrapper/cupswrapper"mfc665cw"
```

---

### Post by knattlhuber on 2008-09-12
Sorry, my bad. You should put the '#' in front of the line that starts with 'usr/...' in each of the two files.

This is called commenting out a line. A '#' tells Ubuntu to ignore this line.

If that doesn't work, I give up :)

---

### Post by augoldfinger on 2008-09-12
> **knattlhuber said:**
> 
If that doesn't work, I give up :)

LOL

Thanks it look like that fixed the problem!

I'll let you know Monday...

THANK YOU!!!

---

### Post by augoldfinger on 2008-09-15
That did work!

Thanks much!

---

