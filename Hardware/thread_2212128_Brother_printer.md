---
title: "Brother printer"
date: 2014-03-19
forum: Hardware
---

### Post by gary21 on 2014-03-19
Can some one please help me get my Brother Printer/all in one to work.  Since I have install Ubuntu 13.10 it will do nothing.  It is a Brother MFC-295cn printer.  I don't know how many times I have asked for help but have never had anyone to even answer...

---

### Post by SuperFreak on 2014-03-19
I have a Brother MFC-5490CN and found directions at the Brother site on installing print and scanner drivers [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html"). Basically you need to find your printer at the Brother site at the link I provided(first click on printer driver under download) and download the appropriate drivers. Use deb files not rpm files and follow the instructions provided. If you have difficulty I will try and help

---

### Post by pdc on 2014-03-19
and Brother supply an installer

[http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

if you download this and run it, it should identify your printer and download the needed files and do all the work for you;

_____________________________

this link

[http://ubuntuforums.org/showthread.php?p=12342527#post12342527](http://ubuntuforums.org/showthread.php?p=12342527#post12342527)

..............post #5 tells you what to do and how to use it

____________________________________

if you have a 64bit ubuntu, Brother comment

"    Requirement
    ia32-libs or lib32stdc++ is required to be installed."

so if you use synaptic or package manager to install those first before you run the Brother installer;

______________________

if you like the manual way, 

this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

gives you the instructions: lpr first and then cupswrapper

---

### Post by gifford on 2014-03-19
It is a good idea when asking for help to post a separate thread instead of posting in someone else's that is really not the topic of what you want answered.
And your previous post was answered by SuperFreak just as he did above.

---

### Post by SuperFreak on 2014-03-19
Hopefully it work either by the manual instructions I directed you to or by the installer mentioned above. I tried the installer on my system and found it identified the wrong brother printer and the drivers did not work for me. It did work manually though

---

