---
title: "Printing/scanning on Brother DCP-115C"
date: 2010-10-10
forum: Hardware
---

### Post by peejay1977 on 2010-10-10
Hi all,

I'm still fairly new to the forums so apologies if this has been covered or if I fundamentally missed something with regards to my solution.

I have been an I.T. Engineer for 15 years but always Windows based stuff so learning the Linux way has been a challenge and I'm still what I would consider a beginner.

I had a lot of problems (on Ubuntu 10.04) getting my Brother printer working but after alot of Googling and messing around I finally found a way but it's not quite how Brothers documentation tells you. This also works with Ubuntu 10.10 which I have just installed from scratch. It also may work for other Brother printers but I cant be sure of that.

Brothers own solution is to use the driver for the MFC-210C. It instructs you to opt for the CUPS driver instead of the LPR one but upon trying their suggest command of :

```
sudo dpkg -i -force-all (name of package)
```

This fails with the following screenshot :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall1.png[/IMG]

I found removing the -force-all remark worked but produced this error :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall2.png[/IMG]

I then installed csh using :

```
sudo apt-get install csh
```

Then I ran the install again and got :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall3.png[/IMG]

This was because I missed off installing the LPR driver, this was mentioned on the install instructions but on a previous screen it said if CUPS is available then use that, I took it literally.

On running the install of the LPR package I got this error :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall4.png[/IMG]

This wasn't mentioned in the instructions on the Brother site or on other Ubuntu forum posts I had stumbled across so I did some looking about and found that under /var/spool the lpd folder mentioned didn't exist, and obviously neither did the MFC210C folder obviously. I manually created these from a Terminal window using sudo rights and then ran the package again :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall5.png[/IMG]

I then ran the CUPS package again as previously mentioned and it failed again, but this time due to folders being unable to be opened as per the LPR package so I had to create the following folder /usr/share/cups/model. Ran the package yet again and all OK :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall6.png[/IMG]

Opened the Printing window under System/Administration and it's there :

[IMG]http://www.pjitsolutions.co.uk/pics/printerinstall7.png[/IMG]

Ran a test print and everything is fine. Onto the scanning. Simply you download the brscan2 driver for this model and run it using :

```
sudo dpkg -i (scanner package)
```

Everything should work according to the Brother site, but it doesn't and the scanner still wont function. A reboot didn't solve this but there are extra instructions on a file you need to edit to allow non-superusers to be able to scan. I found even though I am an administrator of this machine this file needed to be modified and a reboot performed before the scanner would operate, the file is :

```
/etc/udev/rules.d/60-libsane.rules
```

I found running :

```
sudo gedit /etc/udev/rules.d/60-libsane.rules
```

Was best for doing this as otherwise you won't be able to save the file.

I hope this has helped someone, I've probably not done something very basic at the beginning of this which hampered my entire effort so if the moderators feel this post is useless please remove and accept my apologies. I just thought it might be useful to someone like me who is a Windows person, moving over to Linux.

All the links I used to get to this conclusion are below :

Ubuntu Forum reference to previous fix :
[http://ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc](http://ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc)

Driver Download Page :
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

LPR Driver : 
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr)

CUPS Driver :
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperMFC210C-1.0.2-3.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperMFC210C-1.0.2-3.i386.deb&lang=English_gpl)

LPR Install Instructions :
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

CUPS Install Instructions :
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Scanner Download Page :
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

BRSCAN2 Download Page :
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan2-0.2.5-1.i386.deb&lang=English_sane](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan2-0.2.5-1.i386.deb&lang=English_sane)

Scanner Install Instructions :
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)

Scanner for Normal User mode :
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

Thanks

Paul.

---

### Post by plucky on 2010-10-10
Welcome to the forum.

Thanks for the info,but to make life easier some of the Brother drivers are packaged in Synaptic Package Manager.

See [Here](https://wiki.ubuntu.com/BrotherDriverPackaging)

If you had opened SPM and searched for **mfc-210c** it would show ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
```

If you select the cup-wrapper-extra and install,it would have installed both drivers for you.This doesn't apply to all Brother printers,just the ones on the WIki list.

You still have to use the Brother Website to install the scanner drivers.

Good Luck

p.s. I use the Brother DCP-120C which also uses the MFC-210C driver.

---

### Post by peejay1977 on 2010-10-11
Thanks Plucky, I knew someone would show me a quicker way! :)

Ah well, at least I tried, I didnt even give SPM a thought.... :oops:

---

