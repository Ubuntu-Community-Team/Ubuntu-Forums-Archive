---
title: "Brother mfc5460cn -can't install scanner drivers"
date: 2013-03-18
forum: Hardware
---

### Post by haya on 2013-03-18
I have a Sony Viao. I am using Ubuntu 12.10. The printer is Brother mfc5460cn.  Using the Linux brprinter installer program from Brother, I was able to install the printer drivers.  However, the program doesn't work for the scanner. The instructions from  Brother for installation are not working.  dpkg -i | Brother  tells me that the driver wasn't installed as  "install needs at least one package archive file argument".  I have already installed tcsh and csh.  I  have tried editing files, I have enen asked a friend who works with Linux.  No one seems to know what the missing argument is and how to either install it or get around it so that the drivers will be installed.

Any help would be  gratefully accepted

---

### Post by gifford on 2013-03-18
It would help to know what version of 12.10 you are using, 64 bit or 32. Also, is this for a USB install or network?

---

### Post by pdc on 2013-03-18
> However, the program doesn't work for the scanner.

I wonder if you installed the scanner files;

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

your MFD uses the brscan2 files; ............each different depending as gifford points out, on whether you are using 32bit or 64bit

clicking on the install link gives you the instruction page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html)

and 3 different links, 2 depending on USB or network

....and the final crucial one

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

needs an edit of the file so your system knows to recognise your scanner

> [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR] ........if gedit is on your system

then 2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 

by copy and paste

> [COLOR="#0000FF"]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR]

---

### Post by haya on 2013-03-19
I have tried to install brscan2-0.2.5-1.i386.deb  and brscan-skey-0.2.4-0.i386.deb  (The printer is also 32 bit).   I have already edited the rules.  The problem is that I can't install because a "package archive file argument" either isn't there or it can't be found.  I have no idea what thls argument is nor how to either add it or find it.

---

### Post by pdc on 2013-03-19
gifford asked you if you were using usb or networking; can you tell us that please, so the information is available here please

Brother traditionally advise

> dpkg  -i  --force-all  (scanner-drivername)

I assume that 

> [COLOR="#FF0000"]dpkg  -l  |  grep  Brother[/COLOR]

does not show any entries?

if you re-ran the install command without the force-all option, do you get a printout in the terminal that you can copy and paste to the forum please?

---

### Post by haya on 2013-03-20
I tried to reinstall both with and without --force-all the results are the same.  

sudo dpkg -i | grep Brother
dpkg: error: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

What stumps me is what is the file argument.  I hope that this helps.  If I can install, I can deal with the other issues. I tried installing both USB and network.  Neither resolved the problem.

---

### Post by plucky on 2013-03-20
> sudo dpkg -i | grep Brother
dpkg: error: --install needs at least one package archive file argument

dpkg -l (lowercase L not an I) 

Try ```
sudo dpkg -l | grep -i brother
```

The character after grep is lowercase I

Copy and paste the line into a terminal window and post the output.

Good Luck

---

### Post by pdc on 2013-03-20
if we go over what one should do to install the scanner driver for the MFC5460CN; 

from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

we identify it is brscan2 and if we assume you have a 32bit system, you would download [COLOR="#008000"]brscan2-0.2.5-1.i386.deb[/COLOR] into your Downloads directory;

from a terminal the command that Brother recommend would be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]....hit enter .......and then ...........

>  [COLOR="#FF0000"]sudo dpkg  -i  --force-all brscan2-0.2.5-1.i386.deb[/COLOR]

**[COLOR="#EE82EE"]Can we just confirm you are doing the above please?[/COLOR]**

______________________________________________________________________________________________________________________---

one can then also install the 32bit scan key, that allows you to use the scan button the MFD: brscan-skey-0.2.4-0.i386.deb

and install with the command

> [COLOR="#FF0000"]sudo dpkg  -i  --force-all brscan-skey-0.2.4-0.i386.deb[/COLOR]

---

### Post by haya on 2013-03-28
Thank you for all your help,especially for the one who saw my typo.  Once that was clear, I was able to find the other problem.  I had another printer, a wifi, that was interfering.  Once I removed the wifi printer, the mfc5460cn showed as active.  

The only remaining problem is to get xsane to find the machine.  It looks in the wrong place.  chmod doesn't make any change in where xsane looks.

---

