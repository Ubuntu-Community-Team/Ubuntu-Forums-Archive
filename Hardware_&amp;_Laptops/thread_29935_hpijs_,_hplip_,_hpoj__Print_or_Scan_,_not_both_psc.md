---
title: "hpijs , hplip , hpoj : Print or Scan , not both psc 1350"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by wbeck85 on 2005-04-26
I am trying to set up my HP psc 1350. It prints very well using the hplip driver. However, when I try to start up xsane, I get an error stating "no devices available" I would really like my scanner to work, that's why I bought this printer, so I tried using the hpoj driver, following the instructions from [here](http://www.ubuntulinux.org/wiki/HpPsc1200series). Using the hpoj driver, I was able to use xsane nicely. However, when I tried to add my printer, using the Add printer wizard found in System>Administration>Printing>New Printer, I could not find my printer model (Usually I have to choose the PSC 1310 option with the hplip driver). A lot of laser printers are listed, but not one PSC model. So I picked one of the only non-laser printers (i do not remeber which I picked) but when I tried to print a test page, my PSC 1350 responded by blinking its lights rapidly. I had to unplug it. So, will I have to uninstall/install a different driver everytime that I want to go from printing to scanning or vice-versa? That seems impractical.

Is there anyone who has successfully configured their PSC 1350 (or similar model) to work comepletely?
I would love to hear from you.

Thank you very much

---

### Post by Jvaldezjr on 2005-05-01
Unfortunatley I have a PSC 1350, and I can get one part of it to work, but not both together.  I can either scan with Ubuntu, or Print with Ubuntu, and none of the methods I have found for PSC printers work with mine.  So the short anwser is no.

---

### Post by Stefan Koopmanschap on 2005-05-30
I used to have it all working fine when running Warty, using the hpijs/hpoj drivers with ptal-init. However, after upgrading to Hoary, things are not working well anymore. I can scan without a problem using xsane, but printing goes wrong. Weird thing is, it lists the correct printer, I can print a test page, however, when I do so, it will say 'job-printing' but nothing happens. the printer isn't printing, even though the system says it is.

Anyone have any idea? This is a PSC 1350 I'm talking about here.

---

### Post by wbeck85 on 2005-06-04
[QUOTE=Stefan Koopmanschap]I used to have it all working fine when running Warty, using the hpijs/hpoj drivers with ptal-init. However, after upgrading to Hoary, things are not working well anymore. I can scan without a problem using xsane, but printing goes wrong. Weird thing is, it lists the correct printer, I can print a test page, however, when I do so, it will say 'job-printing' but nothing happens. the printer isn't printing, even though the system says it is.

Anyone have any idea? This is a PSC 1350 I'm talking about here.[/QUOTE]
 Well, this is a shame then, if we can't get it to work properly :(

---

### Post by Jvaldezjr on 2005-06-29
There, i found a solution and now its working 100%
[Solution](http://www.ubuntuforums.org/showthread.php?t=33424&page=2)

---

### Post by Sweezel on 2005-06-29
Ubuntu HPOJ is broken for the T45 Parallel port OfficeJet.

When you run ptal-init setup, no parallel devices are found.




I can install another version of HPOJ and everything works fine. The Ubuntu version is broken.

dpkg -i --force-depends hpoj_0.91-4_i386.deb makes it work with a downloaded version.


From syslog:
Jun 30 22:52:29 localhost ptal-mlcd: FATAL ERROR at ParPort.cpp:48, dev=<mlc:par:OfficeJet_T_Series>, pid=6804, e=1, t=1120189949         Access denied to parallel port! 
Jun 30 22:52:29 localhost ptal-printd: ptal-printd(mlc:par:OfficeJet_T_Series) successfully initialized using /var/run/ptal-printd/mlc_par_OfficeJet_T_Series*. 



Maybe developers are listening?

---

### Post by Sweezel on 2005-07-25
I see that the Ubuntu HPOJ version is still not detecting my parallel port printer.

Are there any plans to update this to the new version of HPOJ?


TIA

---

