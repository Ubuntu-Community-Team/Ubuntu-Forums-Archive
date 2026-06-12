---
title: "how to: Epson Perfection 4490"
date: 2009-03-29
forum: Hardware
---

### Post by Anfanglir on 2009-03-29
Hi,
I searched the forums and found some no longer valid advice on how to install an Epson Perfection Photo 4490 scanner on Ubuntu. I tried em all ;) with no luck. In the end it turned out to be quite simple.

Ubuntu 8.10 
0. Go to the Sane homepage ([http://www.sane-project.org/cgi-bin/driver.pl](http://www.sane-project.org/cgi-bin/driver.pl)) and do a search for the Espon 4490. This gives you a link to avasys from where you can download Iscan.

1. Download Iscan and Iscan-plugin from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
(Fill in the form, choosing Perfection 4490, Ubuntu, Local scanner etc. to come to the download page, I download the DEB 32 packages:
iscan_2.18.0-2_i386.deb
iscan-plugin-gt-x750_2.1.0-4_i386.deb)

2. Iscan requires libltdl3 not present on 8.10. I downloaded and installed this from the hardy repos:
[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

3. Intstall Iscan and Iscan-plugin (cf. 1).

4. Add your login as user to the scanner group

5. login/logout

6. start Image Scan! (or Xsane) and scan away


The steps on my Ubuntu 8.04lts notebook was the same as far as I can tell, though I didnt have to download libltdl3. "As far as I can tell" - since I first tried to follow advice in old threads - installing conflicting software as libsane-extras, converting rpms to debs using Alien and what-not. Once I got the procedure figured out as above, I just removed each newly installed package that conflicted with Iscan. Then it worked.

/ Anfanglir

---

### Post by boliston on 2009-04-05
I'm thinking of getting the 4490 and I have heard quite a lot of mixed reports about people getting it up and running on Ubuntu (and other types of linux).

I would be mainly getting it so that I can scan my 120 size (medium format) negatives so it would be interesting to know if the negative scanning function works well under Ubuntu.

It's good to hear that you have managed to get the scanner up and running with out too much bother.

---

### Post by Anfanglir on 2009-04-13
sorry, but I havent scanned any negatives so I cant advice you on this point.

One thing I noticed though is that the colours dont look as good when scanning in Linux with the 4490, as compared to XP/Epson Scan (I have dual boot). It may be that this can be tweaked by someone with more knowledge than me. I'm experimenting with lpof to get the scanner calibrated. No luck so far but I'm a scan-newbie. :\

/ Anfanglir

---

### Post by boliston on 2009-04-13
The 4490 is now on order so I'm hoping it will all work OK in Ubuntu.   I don't really want to have to go to the bother of setting up a windows xp partition just for scanning if at all possible.

---

### Post by mickbuntu on 2009-04-18
The closest to a "recent model stll being sold" linux scanner is: [http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=G3110&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=G3110&bus=any&v=&p=)  It seems that we are at mercy of manufacturers. At least "HP" is friendly enough but even that it " sort of works" "Basic" but says it works for the more recent model. I may get that model to support HP as "HP" printers work too for most part. Cannon is on my blacklist of being anti-linux. When linux does pick up pace I wish that they do not survive it. They made no attempt to support an alternative OS.  Running Vista / XP here so I conform to the "standards."

---

### Post by Pollywoggy on 2009-04-28
I had the 4490 scanner working under Hardy but I can't get it working in Jaunty.

$ sane-find-scanner | grep 0x04b8
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:001:004


iscan, which I had to compile from source (the debs from Avansys did not install), says it cannot find the scanner.

---

### Post by boliston on 2009-04-28
I have now had my Epson 4490 for a couple of weeks and am starting to get the hang of it a bit more.

At first I had some difficulties getting it running on Ubuntu Intrepid as the .deb file refused to install, so I resorted to downloading the .rpm file instead and then using alien to convert to to a .deb and this seemed to work fine and the scanner worked with the Epson Iscan driver for Linux.

Initially I quite liked using Iscan but I cannot find any way to turn off auto-exposure and this has started to annoy me as I would rather do my image adjustments manually in GIMP.

Auto exposure is fine when starting but I'd rather have the option of doing everything manually and Epson Scan (the windows driver) lets me switch off all auto functions altogether.   

I tried scanning using Sane, and the Epson 4490 works fine with Sane under Ubuntu Intrepid for FLATBED scanning but Sane does not seem to have any way to use the transparency unit.   As I only ever scan negatives & slides then this is a major problem!

I also tried using "Scanimage" which is command line driven, but again it will only work with FLATBED and not the transparency unit.

The only other linux option for the 4490 seems to be vuescan, but I do not want to have to pay for software when Epson Scan seems to work for me, even if it means that I have to resort to dual booting until such time as Epson can provide a button to disable autoexposure in Iscan for Linux.

---

### Post by Pollywoggy on 2009-04-28
> **boliston said:**
> I have now had my Epson 4490 for a couple of weeks and am starting to get the hang of it a bit more.

At first I had some difficulties getting it running on Ubuntu Intrepid as the .deb file refused to install, so I resorted to downloading the .rpm file instead and then using alien to convert to to a .deb and this seemed to work fine and the scanner worked with the Epson Iscan driver for Linux.

Initially I quite liked using Iscan but I cannot find any way to turn off auto-exposure and this has started to annoy me as I would rather do my image adjustments manually in GIMP.

Auto exposure is fine when starting but I'd rather have the option of doing everything manually and Epson Scan (the windows driver) lets me switch off all auto functions altogether.   

I tried scanning using Sane, and the Epson 4490 works fine with Sane under Ubuntu Intrepid for FLATBED scanning but Sane does not seem to have any way to use the transparency unit.   As I only ever scan negatives & slides then this is a major problem!

I also tried using "Scanimage" which is command line driven, but again it will only work with FLATBED and not the transparency unit.

The only other linux option for the 4490 seems to be vuescan, but I do not want to have to pay for software when Epson Scan seems to work for me, even if it means that I have to resort to dual booting until such time as Epson can provide a button to disable autoexposure in Iscan for Linux.

I will try alien.  That is how I got it working in Hardy but I have not tried it in Jaunty yet since the company provides source for the driver on its website.

thanks

---

### Post by Tux Aubrey on 2009-04-29
Pollywoggy - any success?

I have tried all the methods (.deb, source and rpm) with no success in Jaunty (I had it working in gutsy via the rpm).

I have installed libltdl3 (from Debian testing).

I'm still getting "no scanner found" with xsane.

---

### Post by Pollywoggy on 2009-04-29
> **Tux Aubrey said:**
> Pollywoggy - any success?

I have tried all the methods (.deb, source and rpm) with no success in Jaunty (I had it working in gutsy via the rpm).

I have installed libltdl3 (from Debian testing).

I'm still getting "no scanner found" with xsane.

No success.  I even tried making debs from the rpm's and that did not work either.  I get the same result from xsane.  I had it working in Hardy before I installed Jaunty.  Tomorrow I will try the same method I used to get it to work in Hardy if I can locate the rpm's I used.

---

### Post by boliston on 2009-04-30
> **Pollywoggy said:**
> No success.  I even tried making debs from the rpm's and that did not work either.  I get the same result from xsane.  I had it working in Hardy before I installed Jaunty.  Tomorrow I will try the same method I used to get it to work in Hardy if I can locate the rpm's I used.

Presumably you have used the "scripts" command with alien.   I seem to remember I forgot this bit the first time I ran alien and it did not work.

The command I used was:
**sudo alien --scripts iscan-2.19.0-4.c2.i386.rpm iscan-plugin-gt-x750-2.1.0-4.c2.i386.rpm**

I can't think what else could stop it working, presumably you have also added your username to the "scanner" group?

---

### Post by Pollywoggy on 2009-04-30
> **boliston said:**
> Presumably you have used the "scripts" command with alien.   I seem to remember I forgot this bit the first time I ran alien and it did not work.

The command I used was:
**sudo alien --scripts iscan-2.19.0-4.c2.i386.rpm iscan-plugin-gt-x750-2.1.0-4.c2.i386.rpm**

I can't think what else could stop it working, presumably you have also added your username to the "scanner" group?

I do not have a "scanner" group and it appears the scanner is not being detected.  I will add my username to "saned" but I do not expect this will help.

---

### Post by Pollywoggy on 2009-04-30
> **Pollywoggy said:**
> I do not have a "scanner" group and it appears the scanner is not being detected.  I will add my username to "saned" but I do not expect this will help.

xsane is detecting the scanner and scanning.  iscan says the scanner is not supported.
Thanks for reminding me to add my username to the scanner group, which is "saned" on my machine.  I think that is probably what is now allowing the scanner to be detected.

---

### Post by Pollywoggy on 2009-04-30
> **Pollywoggy said:**
> xsane is detecting the scanner and scanning.  iscan says the scanner is not supported.
Thanks for reminding me to add my username to the scanner group, which is "saned" on my machine.  I think that is probably what is now allowing the scanner to be detected.


I converted the 2.10 rpm package to a deb and that one works.  The deb package on the website that has the drivers for the scanner is broken and will not install.

iscan is now working.

This is what scanimage -L says:

device `epkowa:libusb:001:013' is a Epson Perfection 4490 flatbed scanner

I had earlier added epkowa to the "saned" configuration.
It appears the newer drivers do not work on Jaunty systems.

---

### Post by Tux Aubrey on 2009-05-01
Many thnx to Pollywoggy and boliston - my 4490 is now working.

---

### Post by boliston on 2009-05-03
I have just installed Jaunty and the Epson Drivers seem to install OK but with the same problem as with Intrepid in that I have to use the .rpm rather than the .deb packages (and convert them to .deb with alien).

I'm wondering if anyone has managed to get the Transparency Unit running with Sane.   It's not vital as it works fine with the Iscan software but it would be handy to be able to use Sane directly.

---

