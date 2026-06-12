---
title: "Canon MP210/MP220 on 64 bit hardy"
date: 2008-06-23
forum: Hardware
---

### Post by Fatfool on 2008-06-23
Good day 

I have this particular AIO printer:

[IMG]http://www.canon.com.au/images/big_products/mp220%20web.jpg[/IMG]
an MP220 (mine is labeled as an MP228 but its obviously just a relabeled MP220)
[http://www.canon.com.au/images/big_products/mp220%20web.jpg](http://www.canon.com.au/images/big_products/mp220%20web.jpg)

I understand that there are no Linux drivers for this particular model but its predecessor, the MP210 has such drivers. However, as seen in this thread, the drivers don't work for the 64 bit version of linux:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=556980&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=556980&page=2)

now the issue here is that I've gotten the printer portion to work by randomly clicking on the CUPS drivers and using an MP180's driver which seems to work perfectly well. but XSANE cannot detect this particular model and will not start. I was wondering that as XSANE does support the MP180, perhaps I could force it to use the MP180's driver? any suggestions? thanks :D

(P.S. the 64 bit version seems to kick me in the balls at every turn. Kilz managed to fix a big one with the lack of 64 bit java with his firefox32 script but I haven't found a solution for this scanner problem in 64 bit yet)


edit:
the MP220 does seem to be supported but by a different backend?!?!!

[http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=MP220&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=MP220&bus=any&v=&p=)

odd. how does this work out?

---

### Post by Fatfool on 2008-06-24
erm, can there be some input here from the community members?

---

### Post by Fatfool on 2008-06-24
erm perhpas I could get some help on how to install that backend or somthing?

---

### Post by Hampster on 2008-06-26
Help.... I've got the same problem.  Thought I would be fine with a brand new printer Scanner but.....   Got the print side going with MP 150 etc driver but no sign of the scanner working.  ZSane  Darn message no devices available.  Anyone?  Please take pity on Fat and the ham.

Edit I am using gutsy)

---

### Post by Fatfool on 2008-06-30
> **Hampster said:**
> Help.... I've got the same problem.  Thought I would be fine with a brand new printer Scanner but.....   Got the print side going with MP 150 etc driver but no sign of the scanner working.  ZSane  Darn message no devices available.  Anyone?  Please take pity on Fat and the ham.

Edit I am using gutsy)
oh darn. 64 bit too right?

---

### Post by Hampster on 2008-06-30
Thanks for you reply fatfool.  64 bit?  don't know I a a real apprentice when it comes to tech stuff.  No sign of help yet but at least the thread is alive and maybe just maybe someone might see the need and help is on its way.  looks like the problem may be with Xsane I just dont know. Fingers crossed.

---

### Post by Fatfool on 2008-06-30
> **Hampster said:**
> Thanks for you reply fatfool.  64 bit?  don't know I a a real apprentice when it comes to tech stuff.  No sign of help yet but at least the thread is alive and maybe just maybe someone might see the need and help is on its way.  looks like the problem may be with Xsane I just dont know. Fingers crossed.
hmm... well cos the 32 bit version of Ubuntu does have a sort of workaround by using the .deb of the MP210 drivers. it won't work for the 64 bit version on Ubuntu though.

---

### Post by Fatfool on 2008-07-06
i'm gonna bump this as I still haven't found a solution...

---

### Post by Fatfool on 2008-07-11
well, Vuescan doesn't work either as it apparently requires the Scangear software from Canon to be installed..

some help? :(

---

### Post by mad_prince on 2009-01-19
Hello, did someone solved the problem with mp220 on 64bit?

---

### Post by Fatfool on 2009-03-08
> **mad_prince said:**
> Hello, did someone solved the problem with mp220 on 64bit?
erm, I solved it by using the backends back then.
[http://ubuntuforums.org/showthread.php?t=856996](http://ubuntuforums.org/showthread.php?t=856996)

the solution is no longer needed in Intrepid 8.10 as the backends are installed by default. just start up Xsane and it works. for the printer portion, use the MP180 CUPS driver

---

### Post by easyease on 2009-04-01
> **Fatfool said:**
> hmm... well cos the 32 bit version of Ubuntu does have a sort of workaround by using the .deb of the MP210 drivers. it won't work for the 64 bit version on Ubuntu though.

just download this tarball : [http://software.canon-europe.com/software/0030808.asp](http://software.canon-europe.com/software/0030808.asp) and then used the --force-architecture command.

extract the tar, venture inside the driver folder and issued these commands,
Code:

sudo dpkg -i --force-architecture ./cnijfilter-common_2.80-1_i386.deb 
sudo dpkg -i --force-architecture ./cnijfilter-mp210series_2.80-1_i386.deb

Then all you need to do was set the printer up on CUPS

---

