---
title: "Photo printing with Brother MFC-J875DW and Ubuntu 14.04"
date: 2015-07-29
forum: Hardware
---

### Post by rbmoler on 2015-07-29
Two days ago I installed the latest update to Ubuntu 14.04 LTS.  The next day I tried to print a 4x6 photo on my Brother MFC-J875DW printer.  I had been doing such printing for the year that I've owned the printer (just after I upgraded to 14.04 from 12.04).

This time the printing failed with a paper jam report from the printer and a crash report from Ubuntu.  I should have copied the crash report so I could paste it here, but being a bit senile I didn't think about than in my zeal to get the paper jam fixed.  The crash happened twice and I reported it twice. The paper jam happened multiple times as I struggled to determine what the problem might be.  The jam issue only occurs with 4.6 photo paper.  8.5x11 prints correctly.

This evening I actually had a rational thought.  I decided to try to copy a 4x6 photo onto 4x6 photo paper.  That worked without a hitch.  So I am led to believe that the printer is working just fine and that the problem is the last update of Ubuntu 14.04 that I received

Another (small?) thing that happens is that after an attempt to print, I get the notification that Ubunu is waiting for the job to complete.  That will not go away until and unless I reboot the system.

The crash report says that BASH has crashed.  I have gotten this message _only_ when I've been trying to print photos on 4x6 photo paper.

Here is the crash report:

Executable Path:  /bin/dash
Package:             dash 0.5.7 - 4ubuntu1
Problem Type:      crash
Title:                    Dash Crashed with SIGSEOV
Apport Version:     2.14.1-Oubunta3.11
Architecture:         AMD64.

I have uninstalled the printer drivers and re-installed them from the brother website using their install tool.  The problem persisted.

Also I copied a picture to a thumbdrive and used that with the printer's USB picture input and it printed perfectly, so I think the printer is fine.  The glitch must be in Ubuntu.

Any ideas?

Well, I guess that there's no answer to the problem unless Brother  rewrites the code for the driver or Ubuntu fixes whatever it was that  was modified and made it incompatible with the printer driver.  I  haven't tried but I would not b surprised if I cannot print on a CD/DVD  either.  Fortunately I can boot up to Win7 and everything works.  I'll close this thread.

---

