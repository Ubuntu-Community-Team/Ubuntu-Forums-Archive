---
title: "LPR install issues"
date: 2018-04-15
forum: Hardware
---

### Post by MibunoOokami on 2018-04-15
Hi all,

I just got a brand new printer, downloaded all the drivers from their website but have run into the following issue with two of the packages (which look identical in name with the exception of a single letter).

```
 sudo dpkg -i --force-all mfcj4620dwlpr-3.0.1-1a.i386.deb
(Reading database ... 288089 files and directories currently installed.)
Preparing to unpack mfcj4620dwlpr-3.0.1-1a.i386.deb ...
Unpacking mfcj4620dwlpr:i386 (3.0.1-1) over (3.0.1-1) ...
Setting up mfcj4620dwlpr:i386 (3.0.1-1) ...
[COLOR=#0000ff]mkdir: cannot create directory ‘/var/spool/lpd/mfcj4620dw’: No such file or directory
chown: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
chgrp: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
chmod: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory[/COLOR]

```
```
sudo dpkg -i --force-all mfcj4620dwlpr-3.0.1-1.i386.deb
(Reading database ... 288089 files and directories currently installed.)
Preparing to unpack mfcj4620dwlpr-3.0.1-1.i386.deb ...
Unpacking mfcj4620dwlpr:i386 (3.0.1-1) over (3.0.1-1) ...
Setting up mfcj4620dwlpr:i386 (3.0.1-1) ...
[COLOR=#0000ff]mkdir: cannot create directory ‘/var/spool/lpd/mfcj4620dw’: No such file or directory
chown: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
chgrp: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory
chmod: cannot access '/var/spool/lpd/mfcj4620dw': No such file or directory[/COLOR]

```

Should I try making the directory myself? It seems weird to me that it says there's no such file or directory when it's supposed to be making it... 
Any ideas and/or suggestions are welcome, thanks in advance

---

### Post by kerry_s on 2018-04-15
1. did you even try the add printer?
2. are you installing 32bit drivers on a 64bit system?

---

### Post by MibunoOokami on 2018-04-15
> **kerry_s said:**
> 1. did you even try the add printer?
2. are you installing 32bit drivers on a 64bit system?

1) Yes, but drivers weren't there.
2) Honestly, I don't know

Correction to 2), I just checked the website again, they have some pre-requisites for installing on 64bit as listed below. I tried installing lib32stdc++ got an error message, due to held broken packages.
```
Pre-required Procedure (5)
**Related distributions**Debian 64 bit version, Ubuntu 64 bit version**Related products/drivers**printer/PC-FAX drivers**Requirement****ia32-libs** or **lib32stdc++** is required to be installed.

```
```
lib32stdc++6 is already the newest version (5.4.0-6ubuntu1~16.04.9).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lib32stdc++6-4.8-dbg : Conflicts: lib32stdc++6-4.7-dbg but 4.7.4-3ubuntu12 is to be installed
 lib32stdc++6-4.9-dbg : Conflicts: lib32stdc++6-4.7-dbg but 4.7.4-3ubuntu12 is to be installed
                        Conflicts: lib32stdc++6-4.8-dbg but 4.8.5-4ubuntu2 is to be installed
 lib32stdc++6-5-dbg : Conflicts: lib32stdc++6-4.7-dbg but 4.7.4-3ubuntu12 is to be installed
                      Conflicts: lib32stdc++6-4.8-dbg but 4.8.5-4ubuntu2 is to be installed
                      Conflicts: lib32stdc++6-4.9-dbg but 4.9.3-13ubuntu2 is to be installed
 lib32stdc++6-5-dbg-s390x-cross : Conflicts: lib32stdc++6-4.9-dbg-s390x-cross but 4.9.3-13ubuntu2cross1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

If someone could help me rectify this situation it would be much appreciated.

---

### Post by kurt18947 on 2018-04-15
If you used Brother's installer script, it should just work. Don't worry about the "cannot create/cannot access" messages. I get them every time I install a Brother printer but they print perfectly. Ignore the preinstall stuff, that is from earlier days. I haven't had to do the preinstall stuff since perhaps 2012. Are you doing a USB or network install? The printer shouldn't matter, the scanner will. Here's a useful page if you're not aware of it:

```
http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on

```
Another useful bit I find is to install "system-config-printer"if you don't already have it. It's installed by default in Xubuntu & Lubuntu, not sure about MATE. It's much more informative than the printer app found in Ubuntu IMO.  A couple other tricks I find useful are to give networked printers static I.P. addresses and maybe I'm a behind-the-times old fart but I've had really good luck using socket://xxx.xxx.xxx.xxx:9100 where x=the printer's i.p. address for the URI . I haven't had a problem with the printer being found since adopting that. The FAQ pages and examples at the above posted address may prove helpful to you. Good luck and be sure to post back with further questions.

Ah, had one other thought. I had a problem getting the scanner function recognized under 17.10 & 18.04. The solution is in the scanner FAQ but as far as I know the installer script will still mess up and put files in usr/lib64 when they should be in usr/lib. The fix is in the Scanner FAQ under "I cannot find my Brother Scanner".

---

### Post by MibunoOokami on 2018-04-16
I inadvertently left out some information, my bad. When scanning, there is a feature where I should be able to press the scan button on the printer and have it scan direct to pc rather than using simple scan. I can't get that feature to work and figure it must have something to do with said LPR issue.

Thanks

---

### Post by kurt18947 on 2018-04-17
> **MibunoOokami said:**
> I inadvertently left out some information, my bad. When scanning, there is a feature where I should be able to press the scan button on the printer and have it scan direct to pc rather than using simple scan. I can't get that feature to work and figure it must have something to do with said LPR issue.

Thanks
I'm pretty sure that function is provided by br-scan-key or similar name. I haven't used it and don't have time now to dig into it. I think 'scan-key' is the place to look for that service though.

Edit: If you haven't done so, it might be worthwhile to look through these scanner/scan-key questions. There are a couple things to check re scan-key:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00080](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00080)

---

### Post by MibunoOokami on 2018-04-18
> **kurt18947 said:**
> I'm pretty sure that function is provided by br-scan-key or similar name. I haven't used it and don't have time now to dig into it. I think 'scan-key' is the place to look for that service though.

Edit: If you haven't done so, it might be worthwhile to look through these scanner/scan-key questions. There are a couple things to check re scan-key:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00080](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00080)

                        That makes sense, I completely overlooked the little note on Brother’s website that says scankey is for using the scanner button. I do have this installed though but am unsure whether or not I have a firewall. A search online said I can check using the command [FONT=Liberation Serif]iptables -L, the output suggests I don’t have a firewall or if I do it’s not working properly…[/FONT]
 
 ```
iptables -L
 modprobe: ERROR: could not insert 'ip_tables': Operation not permitted
 iptables v1.6.0: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
 Perhaps iptables or your kernel needs to be upgraded.
```
 
 Back to my original post, to make sure I understand correctly, the LPR (whatever that is/does) has nothing to do with the scan button**?** Is actually for 32bit not 64bit**?** And probably isn’t required since everything except the scan button seems to be working fine**?**
 
 Thanks

---

### Post by him610 on 2018-04-18
>  LPR (whatever that is/does)
It is actually lower case, "*lpr*". You can type it on the command line in a terminal followed by the filespecs of the file to be printed.
```
 lpr yourfile.txt 
```
If your multifunction device is set up properly, it will print the file. You can find out more about* lpr* 
```
man lpr
```

---

### Post by MibunoOokami on 2018-04-18
> **him610 said:**
> It is actually lower case, "*lpr*". You can type it on the command line in a terminal followed by the filespecs of the file to be printed.
```
 lpr yourfile.txt 
```
If your multifunction device is set up properly, it will print the file. You can find out more about* lpr* 
```
man lpr
```

I only used capitalised letters in the post and used the tab feature to type in the rest of the command in terminal as per my OP. Thanks anyway.

---

### Post by kurt18947 on 2018-04-20
AFAIK lpr is a sort of printer communication protocol, may be short for** l**ine **pr**inter. Brother says they prefer CUPS (Common Unix Printing System) but seem to still require lpr to be installed. I don't think lpr has anything to do scanning or scan-key but wouldn't bet on it.

---

