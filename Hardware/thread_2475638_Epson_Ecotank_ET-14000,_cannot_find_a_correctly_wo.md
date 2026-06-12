---
title: "Epson Ecotank ET-14000, cannot find a correctly working driver or color profile"
date: 2022-06-02
forum: Hardware
---

### Post by ffrr on 2022-06-02
Hi all,

Two years ago my ET-14000 suddenly started to print pictures with an excessive amount of black, so that the machine became unusable for printing pictures. The other day I hooked it up to a Windows machine and it printed beautifully. So the culprit must be a mismatched piece of software between some lower-level output and the printer. Some time ago I downloaded Epson's own driver for explicitly the ET-14000. That didn't help. The driver currently available is still the same. It would have been fixed by now, had it had a flaw. Remains cups. The one I have installed is still the newest version (2.2.7-1ubuntu2.7). There are supposed to be color profiles somewhere. I don't know where they are. The printer test-prints the pure colors cyan, magenta, yellow, red, green and blue without black contamination, which indicates that it's the control of the black jets that's off. Gimp is off the hook. Printing from the command line with 'lp' produces the same ghastly results.

A second likely unrelated problem I noticed one day, when accidentally the magenta and yellow jets were clogged and only cyan printed. All was white except, as it should be, 100% cyan in the locations of the cyan and the green patten. Out of place was an estimated 50% cyan where the magenta pattern would be. Cyan has no business in the magenta pattern. With all jets working, the magenta pattern indeed looks distinctly too dark and purplish.

Gratefull for any suggestion. Surely I am not the only one with malfunctions as severe and as persistent.

Frederic

Ubuntu 18.04 LTS
Epson ET-14000 Ecotank
cups 2.2.7-1ubuntu2.7

---

### Post by ffrr on 2022-06-19
Reporting back after two weeks of no reponse, I wonder if I am on the right forum. I use an Epson Ecotank printer set up in a standard way (Epson's Ecotank driver for Linux and the latest version of cups). There must be quite a number of users out there set up the same way. It is absolutely impossible that I should experience a serious malfunction and no one else would, set up in the same standard way. True, I don't seem to be striking an issue, current or past. Odd, isn't it. So, I reiterate my appeal, pointing out that I identified the pre-print data processing train as the culprit. That would be either Epson's driver or cups. Anyone with a well performing Ecotank printer would be most obliging, if she or he would share his or her installation skills. 

Frederic

---

