---
title: "HP Laserjet 1020"
date: 2009-05-28
forum: Hardware
---

### Post by keplerspeed on 2009-05-28
UPDATE: as of Lucid, the HP Laserjet 1020 now works out of the box.

........

Here is a solution to get your HP laserjet (possibly other hp lasers) working.

Firstly, when you plug in (usb) and turn on the printer, ubuntu will auto discover the printer and add it. HOWEVER it doesn't work. The printer will be auto added in system>administration>printing, but does not print.

To fix this:

Go to system>administration>printing and delete the printer that ubuntu auto added (or any laserjet 1020 for that matter)

Open a terminal, from applications>accessories>terminal, and enter this command:

```
sudo hp-setup -i
```

Then just accept all the default options.

A test page should be printed. Now your laserjet should be working fine! If you still have problems, either try rebooting, or turning the printer off and on again.

---

### Post by pous on 2009-06-12
thanks a lot, was having a headache with my 1020...

---

### Post by hirsute bivalve on 2010-02-04
Another thanks for the heads up.  It has me up and running.

---

### Post by ericson578 on 2010-02-12
I have a fresh install of ubuntu 9.04, this worked for me:

in a terminal:
sudo hp-setup -a -i

Hope that helps someone, this got my hp laserjet 1020 working perfectly.

---

### Post by craigrose on 2010-02-20
I have Ubuntu 9.10.  Tried this but get:

"error: No device selected/specified or that supports this functionality."

This occurs after a short pause which follows selecting the USB option.

Anyone have any ideas?

---

### Post by wittich on 2010-02-23
have the same problem

```
Using connection type: usb

[COLOR="Red"]error: No device selected/specified or that supports this functionality.[/COLOR]
```

tried many things without success...  

@**craigrose**: do you have a solution?

---

### Post by craigrose on 2010-02-23
This was solved here [http://ubuntuforums.org/showthread.php?t=1412421](http://ubuntuforums.org/showthread.php?t=1412421) after I did a complete install (probably unecessary - but I am coming from Windows :) ).

---

### Post by wittich on 2010-02-24
Fine, now I have also a solution:

1. Remove all HP-Tools
```
sudo apt-get remove hp*
```
2. Manual install of the new version (see [http://hplipopensource.com/hplip-w,eb/install/install/index.html](http://hplipopensource.com/hplip-w,eb/install/install/index.html))
```
wget http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run
sh hplip-3.9.12.run
```
3. Restart and run the HP-Tool
```
hp-setup
```

I chose the plugin file manually from [http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.12-plugin.run](http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.12-plugin.run)

I hope it helps someone.

---

### Post by Gareon on 2010-03-03
> **wittich said:**
> Fine, now I have also a solution:

1. Remove all HP-Tools
```
sudo apt-get remove hp*
```
2. Manual install of the new version (see [http://hplipopensource.com/hplip-w,eb/install/install/index.html](http://hplipopensource.com/hplip-w,eb/install/install/index.html))
```
wget http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run
sh hplip-3.9.12.run
```
3. Restart and run the HP-Tool
```
hp-setup
```

I chose the plugin file manually from [http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.12-plugin.run](http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.12-plugin.run)

I hope it helps someone.

Thanks much. Been all over the place trying to find a way to get my HP Laser Jet 2430dtn working and this did it. 
Dell Dimension E521 & Ubuntu 9.10

---

### Post by pous on 2010-03-16
.

---

### Post by craigrose on 2010-03-16
Hi pous

Try turning the printer off and then on again, followed by the hp-testpage command.  It appears to me that whenever you change a driver and/or settings then the printer needs to be restarted for compatible firmware to be updated.

---

### Post by bhaverkamp on 2010-05-11
> **wittich said:**
> Fine, now I have also a solution:

1. Remove all HP-Tools
```
sudo apt-get remove hp*
```
2. Manual install of the new version (see [http://hplipopensource.com/hplip-w,eb/install/install/index.html](http://hplipopensource.com/hplip-w,eb/install/install/index.html))
```
wget http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run
sh hplip-3.9.12.run
```
3. Restart and run the HP-Tool
```
hp-setup
```

I chose the plugin file manually from [http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.12-plugin.run](http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.12-plugin.run)

I hope it helps someone.

bernie@sal:~$ sh hplip-3.9.12.run
Creating directory hplip-3.9.12
Verifying archive integrity... All good.
Uncompressing HPLIP 3.9.12 Self Extracting Archivedf: `hplip-3.9.12': Permission denied
df: no file systems processed
test: 365: -lt: unexpected operator
cd: 379: can't cd to hplip-3.9.12
...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................cd: 379: can't cd to hplip-3.9.12
chown: changing ownership of `./.gvfs': Function not implemented
chown: changing ownership of `./nas/downloads/Ubuntu-8.10-desktop-i386.iso': Operation not permitted
^C

Just tried running this script when I saw these message. This script is definitely touching things it has no business touching. I would not run this. Better to just throw the POS HP away!

---

### Post by John Bean on 2010-05-11
> **bhaverkamp said:**
> This script is definitely touching things it has no business touching. I would not run this. Better to just throw the POS HP away!

It's trying to do what it's supposed to do. Your run failed at the first stage of simply extracting to a new directory created in the same place you ran it from, which would normally be somewhere in your home directory. From the look of it you seem to have run it from somewhere that didn't allow it to create a new directory.

---

### Post by knowlittle on 2011-05-11
> **Gareon said:**
> Thanks much. Been all over the place trying to find a way to get my HP Laser Jet 2430dtn working and this did it. 
Dell Dimension E521 & Ubuntu 9.10

------------------------------------------------------------------------------------------------------
Hi, 

sudo apt-get remove hp*
I did the above, Ubuntu 10.04 warned me that I would do some serious damage, if I wish to proceed, I have to confirm by typing that I wish to proceed. I did and it killed my Ubuntu! Silly me! Just a warning to others... Maybe, someone wants to do a practical joke. 

I found this works. [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/). Good luck.

---

### Post by Jetro on 2011-09-28
> **keplerspeed said:**
> UPDATE: as of Lucid, the HP Laserjet 1020 now works out of the box.
........
Does not work.

The same thing happens here as with if you would do it automatically: 
You get the option to find drivers from the HP website or something, and this error occurs: "error: Plug-in file does not match its digital signature. File may have been corrupted or altered. Error code: 2".
Which is exactly the same thing that happens when I do it according to this guide.

HP Laserjet 1020 will still not print in 10.04. 

I am so angry I will bang my head against a chestnut tree until it explodes.

---

### Post by arkanabar on 2011-10-04
I am having this EXACT SAME ISSUE with my 1018.  Nobody in IRC knows a darned thing about it.

I ran sudo hp-setup -i and it seems I'm ok except for one thing:  NOTHING PRINTS.  When I send a test page, the printer doohickey responds:  /usr/lib/cups/filter/hpcups failed

grrrrrrrrrr....

---

### Post by arkanabar on 2011-11-07
my issue apparently was due to openprinting.org being down.  it's now back up, so things may well be better.  Give your HP printers another shot, folks!

---

### Post by amazed1963 on 2011-12-01
I was having a terrible time installing an HP1200 Laserjet on Ubuntu 10.04 Lucid.

The printer was taking about 15 minutes to print the first page.  I probably spent 2 nights trying to scour the forums and get the printer to print without success.

My problem disappeared completely when I decided to use the HP LaserJet 5 driver instead.

I am sure the solution is not optimal though I haven't found any printing issues since then, but if it saves someone buying a new printer or lots of yelling at the computer screen...

---

### Post by rad_sci_guy on 2013-02-23
> **wittich said:**
> fine, now i have also a solution:

1. Remove all hp-tools
```
sudo apt-get remove hp*
```
2. Manual install of the new version (see [http://hplipopensource.com/hplip-w,eb/install/install/index.html](http://hplipopensource.com/hplip-w,eb/install/install/index.html))
```
wget http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run
sh hplip-3.9.12.run
```
3. Restart and run the hp-tool
```
hp-setup
```

i chose the plugin file manually from [http://www.linuxprinting.org/download/printdriver/auxfiles/hp/plugins/hplip-3.9.12-plugin.run](http://www.linuxprinting.org/download/printdriver/auxfiles/hp/plugins/hplip-3.9.12-plugin.run)

i hope it helps someone.

do not type sudo apt-get remove hp*

this will delete and destroy many important files on your ubuntu  install.  I just killed my server thanks to this reckless command. I cannot believe ubuntu forums would keep such a dangerous command in a help forum.  This destroyed my file and web server

this is not a safe command and do not follow instructions in this post.

---

### Post by bragasuporte on 2013-12-01
SOLVED. I installed in 13.10 64 bits using [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

