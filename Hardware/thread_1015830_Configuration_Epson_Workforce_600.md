---
title: "Configuration Epson Workforce 600"
date: 2008-12-19
forum: Hardware
---

### Post by lmonast on 2008-12-19
I've just installed a Epson Workforce 600. I've managed to get it working (as a printer) using the Epson Stylus Scan 2500 settings. But it is printing veeeery slowly and with bad quality. BTW, printing is my main concern (scanning it is not that important for me).
Is there any other option? I am quite a ubuntu newbie, so I would like to ask you to treat me kindly.
Thank you very much!

---

### Post by w4gn0r on 2008-12-23
This is what I did to get it to work in Intrepid Ibex: (first time using a ubuntu distribution, so I dont know if previous ones are the same, and I speak in VERY non-technical terms, so some linux nerds may not like me.).

 I looked up "workforce 600 linux driver" in google and found this site: 

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-WorkForce_600](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-WorkForce_600)

So I downloaded this driver (Link 1) and selected to open it with GDebi Package Installer. It did its thing, I think it even downloaded more packages, but when it got around to installing them it sorta stopped, so I notice there was a little drop down triangle thingie for terminal and in the terminal, turns out it was asking me something about a mail server or something all this time, i guess mail server stuff is in this download too, but one of the options was to leave the setting the same, so i did by clicking into the terminal and pressing one and enter, afterwards the installation completed. Then I went into system/administration/printing and did all that stuff but the driver was not listed, so then i went back and downloaded the other driver (Link 2) did the same thing before, used GDebi to open it and it added some more drivers. I go back into system/administration/printing and voila! Its in there under the drivers. I think after you download link 1 and 2 and have GDebi install them, you can literally click add new printer and then click "next" or "forward" or whatever the whole way through the printer setup and it will work. I tried to get the Workforce 600 to work under OpenSuse 11 but it didnt work at all. If you have a Workforce 600, I know for sure if you switch to Ubuntu 8.10, it will work. I am not sure if you really *have* to download and install Link 1 first but it couldnt hurt, so do it anyway. The printing quality is pretty dang good I will have to say.

Link 1 x86 32 bit (DEB for LSB 3.1)
[http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.1/main/binary-i386/gutenprint_5.0.1-1lsb3.1_i386.deb](http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.1/main/binary-i386/gutenprint_5.0.1-1lsb3.1_i386.deb)

Link 2 x86 32 bit (DEB for LSB 3.2)
[http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb](http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb)

---

### Post by wbeck85 on 2009-01-11
> (first time using a ubuntu distribution, so I dont know if previous ones are the same, and I speak in VERY non-technical terms, so some linux nerds may not like me.).
Not true!  "VERY non-technical terms" are what makes this distro great. Remeber: Ubuntu is linux for HUMANS! Your post was very informative and straight forward, expressing insight that a casual user benefits from. Good job.

BTW, thanks for the links :-)

---

### Post by rothenmr on 2009-01-18
[QUOTE=w4gn0r;6421740]This is what I did to get it to work in Intrepid Ibex: (first time using a ubuntu distribution, so I dont know if previous ones are the same, and I speak in VERY non-technical terms, so some linux nerds may not like me.).

This was an excellent post. I think you underestimate yourself. The links were exactly what I needed.  I downloaded and installed the DEB packages from Link 1 and 2. After installing the DEB package from Link 2 I configured my Workforce 600 with no issue.  And the test page was quick.

For the DEB package at Link 1 I selected #1 option for the mail configuration.  Basically option 1 was No Configuration. Then the package proceeded to install automatically after this single manual step.

Thanks much.  And I agree the print quality is excellent.

Mark

---

### Post by dmj99 on 2009-01-19
I second the motion.  I followed your instructions and my WorkForce 600 is working perfectly.

Thank you so much.

Don

---

### Post by inkisbetter on 2009-02-03
w4gn0r, 

Just wanted to add that this worked perfectly in KDE 4.2.  I don't know how much the windows manager matters but for anyone using KDE you should be good.  Thank you very much!  

Side note, I have not tested the ability to scan/fax with this driver but the printing is brilliant.  Also, it is working wireless (other forums talked about success only when wired).

---

### Post by lmonast on 2009-02-12
Thank you very much, w4gn0r,
It works like a charm!
Excellent printer, BTW.

---

### Post by cdaringe on 2009-02-13
Thanks!

I only needed to use the newer .2 driver.

For those who run a **64 bit system** and want the WorkForce 600 to kick into gear right away, your driver is here:

[http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.2-1lsb3.2_amd64.deb](http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.2-1lsb3.2_amd64.deb)

---

### Post by frilock on 2009-02-15
:KS Worked perfect up and runig thanks :guitar:

---

### Post by stbub on 2009-02-19
Just a note for those who google about this all-in-one and find people saying "it works great"... it ain't so...

I'm using the printer via USB on Ubuntu 8.10.

I installed gutenprint 5.2.2 (found on LinuxPrinting).

I can now print

2-sided printing is NOT available.

xsane finds NO scanner.

---

### Post by IcarusR on 2009-02-20
Not listed as supported by xsane so can not be expected to work !!
[http://www.sane-project.org/sane-backends.html#S-EPSON]("http://www.sane-project.org/sane-backends.html#S-EPSON")

---

### Post by fdevelasco on 2009-03-02
Hello, thank you for your initial posting. Driver 2 did just fine. Now, I don't know if this is already on the post or somewhere else but it is possible to use the printer wireless if one selects the jetdirect option and just enter the ip of the device, then select the driver from the list and let it be. Works just fine.

---

### Post by josaphat on 2009-05-01
Yeah guys, I just got a WorkForce 500, and it works in Jaunty just fine without installing any extra drivers :P
Unfortunately, I got the machine mostly for the scanner ability and it will be far too cumbersome to connect it to my Vista Laptop just to get it to scan. I'd like to be able to scan from my Ubuntu desktop machine so if anyone could help me out I would greatly appreciate it!

So far I've tried xsane :(
I've tried "scanner utility" :(
and I've tried Skanlite. :(

None of these programs finds a scanner available. It prints like a charm, and though I know I have a workforce 500 not 600, I think they are similar enough that I'm in the right thread.
Thanks in advance for help!

---

### Post by CyberAgeVoodoo on 2009-05-07
> **josaphat said:**
> ...scanner ability and it will be far too cumbersome to connect it to my Vista Laptop just to get it to scan. I'd like to be able to scan from my Ubuntu desktop machine so if anyone could help me out I would greatly appreciate it!


what he said Pretty much sums up my problem at the moment. Any help would be greatly appreciated.

Thanks

---

### Post by mastapat11 on 2009-06-08
links for the x32 & x64 of the LSB2 don't work anymore.
In case anyone else started to freak out like i did a first,
just go to the site below directly and get them from there:

[B]
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-WorkForce_600]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-WorkForce_600")[/B]

---

### Post by sockmoney on 2009-08-14
Great post.  I ended up installing both version of the driver and got my printer working.  Since my printer is networked, I had to "find" it first... but once I did that it loaded the drivers and prints great.

Thanks!

---

### Post by newagelink on 2009-08-27
I came here also looking for instruction about the scanning feature of this Epson device. I suppose, if I find it, I'll update this post.

Attempts: [LIST]
[*]Found the Epson WorkForce 600 [Quick Reference Guide]("http://files.support.epson.com/pdf/wf600_/wf600_qr.pdf") (Windows/Mac only)
[*]```
daniel@daniel-laptop:~$ xsane&
[1] 4401
daniel@daniel-laptop:~$ [epson2] Cannot send this command to a networked scanner

[1]+  Done                    xsane
daniel@daniel-laptop:~$ gksudo xsane
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:255: error: invalid identifier `selected_fg_color', expected valid identifier
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSdaniel@daniel-laptop:~$
``` (It told me trying to run it as root was a huge mistake so I clicked "Cancel".) And, since I do have a networked scanner, apparently I'll have to try something else.
[*]Found [the HTML User's Guide]("http://files.support.epson.com/htmldocs/wf600_/wf600_ug/index.html") (Windows/Mac only)
[*]Performed the job using a Windows Vista laptop with the provided Epson software.
[/LIST]

---

### Post by tns09 on 2009-08-31
I just got a Work Force 600 too and it prints great in Ubuntu 9.04. It is networked and not able to scan. I am hoping someone will come up with a solution.

---

### Post by sandwormblues on 2009-09-16
this works on hardy heron!  thats a great link and these are some mighty precious debs.  i'm hanging on to these.  thanks!

---

### Post by suavecu on 2009-09-26
This printer (haven't tried the scanner) works automatically with Ubuntu 9.04+ No need to install anything.

---

### Post by MaquinaX on 2009-11-05
Hey Guys,
          I have a WorkForce 500, and was able to get both printing and Scanner to work on 8.10. I recently upgraded to Kubuntu 9.10, and printer works out of the box, but now I'm having issues installing iScan. For everyone else, here is the iScan link. Enjoy-

[HTML]http://linux.avasys.jp/drivers/iscan/2.22.1/iscan_2.22.1-2_i386.deb[/HTML]

p.s. If anybody can help me out with 9.10 install, please send me a message, or reply on my own post.Thnx :D

---

### Post by MaquinaX on 2009-11-05
> **MaquinaX said:**
> Hey Guys,
          I have a WorkForce 500, and was able to get both printing and Scanner to work on 8.10. I recently upgraded to Kubuntu 9.10, and printer works out of the box, but now I'm having issues installing iScan. For everyone else, here is the iScan link. Enjoy-

[HTML]http://linux.avasys.jp/drivers/iscan/2.22.1/iscan_2.22.1-2_i386.deb[/HTML]

p.s. If anybody can help me out with 9.10 install, please send me a message, or reply on my own post.Thnx :D

... Wait a minute everyone..., GREAT NEWS! Finally able to get the newer release of iScan (after endless searching). Installed newer .deb package, and then ran sane find scanner utility. Once scanner was detected, (of course, after installing iScan), I then rebooted system, and WAHLA!!! I have Karmic Koala running with working WorkForce 500 printer and scanner.
Good luck to everyone, and working together is how we move foward...;)

Newer iScan .deb

[HTML]http://linux.avasys.jp/drivers/iscan/2.22.1/iscan_2.22.1-2.ltdl7_i386.deb[/HTML]

Find Scanner Command
```
 sane-find-scanner | grep 0x04b8 
```

---

### Post by timbuktoo on 2010-09-09
you only need link 2.  I went to the first link in the post instead of the link to the download portals and I downloaded one that I later saw had the same name as the second link because I didnt scroll down and see the links (or fully read the post).

---

### Post by timbuktoo on 2010-09-09
sorry I think I posted that in the wrong thread how do I delete them?

---

### Post by timbuktoo on 2010-09-09
wait ya it is the right thread it is just page 3 sorry everyone... who ever can delete these 2 accidental posts please do

---

