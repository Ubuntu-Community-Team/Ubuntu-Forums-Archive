---
title: "can't enable effects after installing jaunty on laptop"
date: 2009-04-23
forum: Hardware
---

### Post by Hyper Tails on 2009-04-23
hi my laptop runs vista and jaunty and I installed jaunty just then but back in intrepid and hardy the graphics card could have compiz fusion and it worked out of the box but when I installed jaunty it doesen't.

please help 
thank you

Graphics card:Mobile Intel(R) 965 Express Chipset Family

---

### Post by MSalivar on 2009-04-23
I'm having the same problem on my Thinkpad X61s, which has the same graphics.  I assumed it was because I was using UXA, but that's not the case as I just switched back to EXA.

I installed from either the last beta or the RC (sorry, I can't remember, trashed the ISO, and didn't label the CD... I'll have to check when I get to a machine with an optical drive), and it worked for at least a couple of days in both EXA and UXA.

I just get a generic error 'desktop effects could not be enabled'

xorg.0.log (attached) shows that AIGLX loaded, has no errors, but does have a few warnings

Sorry, I had to gzip my log since it was 2.5kb over the forums limit for text files...

---

### Post by MSalivar on 2009-04-23
I decided to include a log for UXA in addition to EXA.  They both look the same to me, but maybe someone will catch a difference.  Both, labeled accordingly, are in this tarball.

---

### Post by Hyper Tails on 2009-04-24
thanks i'll do it soon but i can't do it now because i'm in school and i'l download it and install it but if something goes wrong i can't reply you instantly because i'l be at my cabin until sunday and It looks confusing so how do I install it?

---

### Post by MSalivar on 2009-04-24
It's... not a solution.

---

### Post by Hyper Tails on 2009-04-26
oh but do you have a solution?

---

### Post by Hyper Tails on 2009-04-27
..............................................................................

---

### Post by Hyper Tails on 2009-04-28
..............................please?:confused:

---

### Post by VladNistor on 2009-04-28
Compiz had blacklisted 965 because of bug [https://bugs.launchpad.net/bugs/359392](https://bugs.launchpad.net/bugs/359392). the Ubuntu community is working on a fix. Read the report for more info.

---

### Post by Hyper Tails on 2009-05-10
Hi I found a driver for it and how do I install it?

It's tar.gz's and I hate tar.gz's

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2800&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2800&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

---

### Post by Hyper Tails on 2009-05-12
anyone?

---

### Post by Dynaflow on 2009-05-12
Just try this: [http://ubuntuforums.org/showpost.php?p=7132843&postcount=5](http://ubuntuforums.org/showpost.php?p=7132843&postcount=5)

---

