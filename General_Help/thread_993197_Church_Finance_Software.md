---
title: "Church Finance Software"
date: 2008-11-25
forum: General Help
---

### Post by IanB2 on 2008-11-25
I hope you can help. I'm looking for some advice on finance software packages for a church.

I've been using Linux (Ubuntu) for approx 18 months but we have had to maintain a Windows PC to allow my wife to run some software called 'Cashcall' [http://www.datadevelopments.co.uk/DDCAS1.htm]("http://www.datadevelopments.co.uk/DDCAS1.htm"),which she uses in her role as Church Treasurer.

I've been looking for an alternative for some time, with little success. I'd like to find preferably some open source software (if possible) that will run in Linux (don't mind paying for this). 

While there are many excellent personal finance packages available, my understanding is that it would take some considerable time to configure the reports to meet the requirements of the Charities Act etc. The reason that Cashcall was originally chosen was to meet the requirements of the legislation. Data Developments, the writers of Cashcall, have no plans to produce a Linux compatible version.

Any ideas would be very welcome. Thanks.

---

### Post by __Ryan__ on 2008-11-25
GNUCash is probably your best bet.  It is a good Linux alternative to Quicken I believe. I think it is mainly geared toward personal finance but you might be able to configure it for your uses.

---

### Post by decard_pain on 2008-11-25
have you tried running the windows program in wine?

---

### Post by opscure on 2008-11-25
You can try and run the program through wine.  If it's anything like the demo on their site, it is just a bunch of Adobe director movies compiled into a binary.  This should run fine through wine.

```
sudo apt-get install wine
```
then just copy the .exe from the windows machine, right click it, and run it with the wine windows program loader.

If that doesn't run then maybe spending a little time to configure the reports from another program might not be such a terrible idea, at least this way you won't be stuck with propriatary software.

---

### Post by HermanAB on 2008-11-25
VMware, WinXP, Cendio Seamless RDP and Bob's your Uncle.

---

### Post by IanB2 on 2008-11-27
> **HermanAB said:**
> VMware, WinXP, Cendio Seamless RDP and Bob's your Uncle.

Thanks for the suggestions.

I know that VMware or virtualbox would work but I don't have a WinXP installation CD as it came pre-installed on my desktop PC. I have tried this with Windows 98 but that was very flaky (forgotten how bad 98 was!). Any way around this?

I have also tried WINE in the past with little success, however I know that WINE has come on recently, so maybe I'll try again.

---

### Post by IanB2 on 2008-11-28
> **opscure said:**
> You can try and run the program through wine.  If it's anything like the demo on their site, it is just a bunch of Adobe director movies compiled into a binary.  This should run fine through wine.

```
sudo apt-get install wine
```
then just copy the .exe from the windows machine, right click it, and run it with the wine windows program loader.

If that doesn't run then maybe spending a little time to configure the reports from another program might not be such a terrible idea, at least this way you won't be stuck with propriatary software.

Thanks ..... the Cashcall appears to run under wine with a couple of problems. The main issue is that I've been unable to print from this application in wine (I've got printing working fine with another wine application). I guess taking screen shots is just too messy and there is not much I can do about this as the problem with lie within Cashcall as an application?

---

### Post by IanB2 on 2009-02-22
As an update ...... looks like 'Moneydance' or 'Kmymoney' are the best solutions for us

---

