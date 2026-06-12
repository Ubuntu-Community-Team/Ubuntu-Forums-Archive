---
title: "[SOLVED] Epson AcuLaser CX11NF on Ubuntu 8.04 (Hardy Heron)"
date: 2008-08-19
forum: Hardware
---

### Post by Greg K on 2008-08-19
Hi, I'm posting this because I couldn't reply to another thread detailing this printer.

[http://ubuntuforums.org/showthread.php?t=156631](http://ubuntuforums.org/showthread.php?t=156631)

This is to install this printer when it's setup as a network printer. This does not detail adding this printer locally - though I suspect it's similar, you'll still need to install the driver.

To summarize:

[LIST=1]
[*] Download [Epson-ALCX11-filter-1.1.tar.gz]("http://www.avasys.jp/lx-bin2/linux_e/mfp/DL1.do") by selecting 'Other' and 'Other' for the distribution and version drop down boxes. It's at the bottom of the section title 'Download for AcuLaser CX11 for CUPS'.

[*] Once downloaded, do the following to compile and install the driver (commands in square brackets are optional, if you're not sure if something is installed, perform the command):
```
sudo apt-get install libcupsys2-dev build-essential
tar -zxvf Epson-ALCX11-filter-1.1.tar.gz
cd Epson-ALCX11-filter-1.1/
./configure
sudo make install
[ sudo apt-get install bc ] # this should already be installed on Heron
sudo apt-get install libstdc++5
```
[*] Now go to System -> Administration -> Printing
[*] Go to Edit -> New Printer (your Epson CX11NF should be in the list on the left)
[*] Click Forward and follow the install Wizard prompts, you should see the driver you just installed listed. Select that and print a test page - voila!
[*] If you see the job enter the queue briefly and then disappear, with no output from your Epson, try this command to help offer pointers to missing dependencies:
```
/usr/local/bin/pstoalcx11.sh PageSize=lt XY600=5100×6600 MediaType=normal TonerSave=false InputSlot=cassette1 Collate=on Copies=1 Color=color Resolution=600dpi XY600=5100×6600
```
[/LIST]

Hope this helps!

---

### Post by lsilver on 2008-10-27
Hello.

Using your instructions I have my CX11nf printer working perfectly on several Hardy x86 systems.  However, I can't get it working on a Hardy AMD64 system.  Do you know of any variations required for this version?

Thanks, Leo.

---

### Post by ab0032 on 2011-03-29
I am using karmic, but the problem seems to be that a 32 bit libstdc++5 is required. Maybe this will solve the problem for amd64 too.

I followed the instructions here[INDENT] [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)
[/INDENT]which solved my problems with the epson cx11nf.

Actually I purged the 64 bit libstdc++5, then I did as told to install the 32 bit version, moved it to the right place and then reinstalled the 64 bit version.

The first hint that something was wrong with the libstdc++5 even though it was installed came when I tried to create a printer on the commandline:[INDENT]/usr/local/bin/pstoalcx11.sh PageSize=lt XY600=5100×6600 MediaType=normal TonerSave=false InputSlot=cassette1 Collate=on Copies=1 Color=color Resolution=600dpi XY600=5100×6600
[/INDENT]After installing the 32 bit version the errors were gone, but I deleted the printer thus created and used the cups web interface on[INDENT][http://localhost:631](http://localhost:631)
[/INDENT]to create a new fresh printer and now its working for me and I hope this will help others solve their problems with the cx11 faster.

---

### Post by byte-wrangler on 2011-04-06
I have the same problem, but went through the steps outlined above and had no luck.  Thoughts?

---

