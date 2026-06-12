---
title: "HP printer problems"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by harelb on 2007-01-05
Hi, my first time here, found it via google. I posted the following question last night but I might have
put it in the wrong place (it's at [http://ubuntuforums.org/showthread.php?t=251334](http://ubuntuforums.org/showthread.php?t=251334) as a reply but that thread's been idle since July..) Here's what I posted there about 
problems with OfficeJet 4315 but the solution to the missing cups-devel support given in that old thread doesn't work for me, per below. Many thanks for any leads! HB

Hello..the above doesn't seem to work for me..

I'm very new to ubuntu (my sweetie installed it for me, she's been
using it about a year) and just got an HP officeJet 4315..the installation disc for MSFT/Mac only, but she found the hplip file for me to install..tried ```
sudo sh ./hplip-1.6.12.run
```
and got 8 missing pieces...finally was able to get it down to 1, namely

"warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common
Unix Printing System development files)"

that's when a google found this thread...however when I typed
```
sudo apt-get install libcupsys2-dev
``` I got the following:
```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcupsys2-dev: Depends: libcupsys2 (= 1.2.0-0ubuntu5) but 1.2.2-0ubuntu0.6.06 is to be installed
E: Broken packages
```

I just want a working printer...it's been a bit ](*,)  ...would appreciate help :)  Many thanks,

Harel

---

### Post by harelb on 2007-01-10
well we fixed this by installing (with Synaptic) something instead of hplip..
something called  hpoj  (oj for OfficeJet)...and then telling it "4100" even though our
printer is a 4315 HP OfficeJet (because the highlighted or put as default 4100) in this case
"we" means my sweetie, she of more ubuntu experience..good for her...so
I finally have a working printer (the old printer didn't need/use usb) but
still curious why the above (the hand install) which others
suggested on this board, which we tried earlier, didn't work...

anyway just posting this so some other poor soul in the same or similar
situation can maybe gain from our experience...
Harel

---

### Post by 11hjpphty76lkjj on 2007-01-12
It's not recommended that anyone use HPOJ.  HPOJ is very old and very outdated.

Most likely the problem you are having is because you have a problem with apt.

You could try running:

```
 sudo apt-get install -f 
```Which may help correct your apt problem.  and you should be able to install libcupsys2-dev.

Hope this helps.

A

---

