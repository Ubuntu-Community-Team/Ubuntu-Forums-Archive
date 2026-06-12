---
title: "Hp 6500 scanner not detected"
date: 2011-09-05
forum: Hardware
---

### Post by houndhen on 2011-09-05
I am running Ubuntu 10.10 32 bit and trying to use the HP 6500 all-in-one scanner. It is connected to my computer by USB and seems to work while in Windows XP. I have read thread 1669486 and tried to follow it. I downloaded the latest hplip 3.11.1 from sourceforge. Then I found the help at hp located here:[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne). That had dependency errors so it didn't help. 

I went back to system/administration/printing and was able to get the printer and fax to be recognized. But no scanner.

Questions:
1. How do I run the 'hplip-3.11.7.run' file that I downloaded?

2. Should I uninstall the hplip 3.10.6-1ubuntu10.2 before running the 'hplip-3.11.7.run'?

I mostly work from the gui but can use CL some.

Thanks,
Harold

---

### Post by houndhen on 2011-09-11
Anybody have any kind of answer? Is my problem something that I should have figured out by myself? Is it a problem that has not solution as yet?

---

### Post by foresthill on 2011-09-11
HP scanners were not very well supported a couple of years back when I tried to get one to work. Hopefully that has changed.

What I would do is go into Synaptics and remove the old HPLIP program. Then go put the 'hplip-3.11.7.run' file on your desktop.

Then navigate to it from the terminal. Do this by typing 

cd (path to the file on the desktop)

In my case, that would be

cd /home/foresthill/Desktop

Then type or copy and paste this command and hit enter:

sudo hplip-3.11.7.run

You will be asked for your password and then you should see the file get extracted and installed in the terminal.

Then run:

sudo hp-check -r

I'm not gonna walk you through the rest of the troubleshooting process, the Wiki you linked to explains it pretty well. 

I just noticed that you printer/scanner is not listed in the supported models, so good luck. Hopefully you'll get at least partial functionality from that driver.

---

### Post by houndhen on 2011-09-11
Thanks, foresthill.

after edit
Got it working. Found a really good howto at [[URL="http://www.hplipopensource.com/hplip-web/install/install/index.html"]http://www.hplipopensource.com/hplip-web/install/install/index.html]("http://www.hplipopensource.com/hplip-web/install/install/index.html")[/URL]

---

### Post by houndhen on 2011-09-14
A day or so after I got my scanner recoginized along with the printer and fax, update manager tells me I have 15 updates involving CUPS. Most of them are updating from 1.4.4-6ubuntu 2.3 to 2.4.

I got my scanner working by installing hplip from the HP website. Does anyone know if the update of CUPS will undo what I have done with hplip?

If I don't need to install the updates, how do I keep from being reminded of them?

Thanks,
Harold

---

### Post by pembertonq on 2012-07-18
For anyone coming here, as I did, looking for a solution, when installing the printer using the standard System Settings>Printing>Add a printer, when it finds the printer as a network printer, ensure you install it as an HPLIP printer, and not one of the other options. If you use the other options it will still print, but not scan.

---

