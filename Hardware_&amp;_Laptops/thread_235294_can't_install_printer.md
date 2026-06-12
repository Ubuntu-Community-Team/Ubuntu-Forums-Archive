---
title: "can't install printer"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by JohnJSal on 2006-08-12
Hi guys. This isn't really a laptop-specific question, but none of the other Hardware forums applied to me any better than this (Inspiron 8600).

So I have a Dell 720 printer, and when I go through the steps of adding it, Ubuntu detects it just fine during the first step, but when I get to the next step of choosing the manufacturer and model, there are only two options for Dell, neither of which is my model.

So according to Ubuntu Hacks, I chose a couple of different drivers under the "Generic" category, but when I try to print nothing happens. Is there some way for me to get my printer working despite the fact that it doesn't show up in the list?

Thanks.

---

### Post by skale on 2006-08-13
Dell is a rebranded Lexmark. Lexmark and Linux aren't very friendly, but there are some third-party drivers available. I have a 720, and I believe it is equivalent to a Lexmark z615.
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&searchLang=en&os_group=Redhat&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&searchLang=en&os_group=Redhat&target=)

use alien to install the RPM.

If it doesn't workMake sure you have updated Tcl libraries (>8.4, I think)

---

### Post by JohnJSal on 2006-08-14
Thanks. I didn't see this printer listed either though.

---

### Post by franny on 2007-08-14
I have Dell Inspiron E1705 and am trying to get my HP psc 2110 all in one (print,copy, scan) printer to work. I cannot even get it recognized. I searched for a solution,though it was not a Dell specific solution which was probably my first mistake, and installed an HPLIP toolbox (and it was real complicated - so probably that was probably my second mistake) and of course, there were no results. Any suggestions?
When I try to print the printer box says there is a generic printer and then nothing happens. I did check my cables.
There must be a simpler and workable solution...

Thanks to anyone with info

  :KS   By the way, this is obviously not really a reply - I am finding a hard time figuring out how/where to post this on its own. I am not very good with the forum yet, but most willing to learn. If you can direct me to the right way to post this, I would appreciate it.
I want to post it on a Dell Ubuntu forum.

---

### Post by Uncle_Grombor on 2007-08-24
I have a Dell 720 (lexmark) Inkjet.  I did everything I know to do so far.  I downloaded the redhat driver as stated above, I downloaded alien and the tcl libraries greater then 8.4 and I can't get the program to install.  I tried using alien but it told me it was an unknown or wrong filetype. (sudo alien "file").  I also tried sh "file", since the file was a .sh and this is what it did ....

grombor@grombor-desktop:~/Desktop$ ls
CJLZ600LE-CUPS-1.0-1.TAR.gz  COPYING  README  z600cups-1.0-1.gz.sh
grombor@grombor-desktop:~/Desktop$ sh z600cups-1.0-1.gz.sh
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
OK
Uncompressing Lexmark Printer Drivertrap: 125: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap

Thanks

---

### Post by Uncle_Grombor on 2007-08-31
I've discovered how to get the drivers installed and the 720 Dell Inkjet running.  If anyone out there has this same issue go to this website and it should tell you all that you need to know.  [http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600)  Everyone have a wonderful holiday weekend.

---

### Post by vintendo on 2007-09-01
Hi, I have a Lexmark P6520 Printer/Scanner and I need to use it for work but cannot find Linux drivers for it :( is there any at all?

---

### Post by franny on 2007-09-02
Hello vintendo

The post right above your's has a link [http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600) you should try. I do not have a lexmark. I have an HP which I got working at last. Try that link, it looks like the right one for you. 
Good luck.

franny

---

### Post by Wesseli on 2007-09-25
> **franny said:**
> Hello vintendo

The post right above your's has a link [http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600) you should try. I do not have a lexmark. I have an HP which I got working at last. Try that link, it looks like the right one for you. 
Good luck.

franny

THANK YOU FOR THAT LINK!!!!

I just installed my Lexmark Z-515 printer with those instructions! FINALLY!

I noticed that the created .deb file names were actually a little different than in the guide. I put ls in the terminal and copied the changed filename and it installed perfectly and works perfectly!

My system is Debian Lenny (GNOME)  and I installed program called Alien trough repositories before messing around with the terminal, as it is needed to convert the packages to .deb files. Also, after install, I selected the Z600 driver from the list in the administration-> printing ->add printer. What is funny that the printing output is much better than with the native lexmark drivers in my wife's XP :guitar:

This really saved my say, I buy you a virtual beer. I almost bought a new printer but I still got back to these awesome forums to dig some more information. Hope this helps someone!

Cheers!

---

