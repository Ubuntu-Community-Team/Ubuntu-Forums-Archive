---
title: "Cannot print to hp photosmart C7180"
date: 2010-12-18
forum: Hardware
---

### Post by MaineBud on 2010-12-18
Hi there,
I'm using 10.04 dual booted (installed using Wubi) on an Acer Aspire 5745 w/ Windows 7.  I've been searching these forums for many hours over the last few weeks and have been able to find fixes for several problems (microphone(s), headphones and DVD player not functioning) but have been unable to get printer to work. The printer shows as "connected to localhost", all settings appear correct but every time I attempt to print anything (.txt, .doc, pdf, web page, etc.)  it hangs at "processing".  When I troubleshoot I get   "/usr/lib/cups/backend/dnssd failed" This same printer works fine on Windows 7 "side" and with previous Acer XP laptop using Ubuntu 8.10.  Any thoughts? I really want to eventually abandon Windows all together, but I need to print. Thanx.

---

### Post by Joshimitsu on 2010-12-18
You may need to install hp linux drivers for your model.

Download hplip from the HP website [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and see if it works.

---

### Post by MaineBud on 2010-12-19
> **Joshimitsu said:**
> You may need to install hp linux drivers for your model.

Download hplip from the HP website [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and see if it works.
Thanks for your help.
I downloaded and ran hplip as directed. It seemed to successfully load. However, when I tried to print a short text document it stopped.  I ran the troubleshooter which indicated "There is a missing filter for printer 'HP-Photosmart-C7100-series'". How do I determine and locate this missing filter?

---

### Post by Joshimitsu on 2010-12-20
> **MaineBud said:**
> Thanks for your help.
I downloaded and ran hplip as directed. It seemed to successfully load. However, when I tried to print a short text document it stopped.  I ran the troubleshooter which indicated "There is a missing filter for printer 'HP-Photosmart-C7100-series'". How do I determine and locate this missing filter?

I had a similar problem with my printer on Ubuntu 10.10.  Check out part 2 in post #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=1645102](http://ubuntuforums.org/showthread.php?t=1645102)

and see if that helps.

---

### Post by MaineBud on 2010-12-21
> **Joshimitsu said:**
> I had a similar problem with my printer on Ubuntu 10.10.  Check out part 2 in post #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=1645102](http://ubuntuforums.org/showthread.php?t=1645102)

and see if that helps.
SOLVED! Thank you much. Long story short... I followed the link you provided and followed those directions and now I can print. Yeah!  I'm still unable to understand why I had the problem to begin with and how those commands, in that order, fixed things, but I plan to keep studying and learning what I can about Terminal and command line usage.

---

### Post by Joshimitsu on 2010-12-22
> **MaineBud said:**
> SOLVED! Thank you much. Long story short... I followed the link you provided and followed those directions and now I can print. Yeah!  I'm still unable to understand why I had the problem to begin with and how those commands, in that order, fixed things, but I plan to keep studying and learning what I can about Terminal and command line usage.

Brilliant!  Glad it proved useful.  Perhaps you could mark this thread as solved?

---

### Post by MaineBud on 2010-12-23
> **Joshimitsu said:**
> Brilliant!  Glad it proved useful.  Perhaps you could mark this thread as solved?
Done.
I wasn't sure how to mark it "solved" and after all the time spent completing the task I was, quite frankly, too lazy to do more than a cursory search as to how. Thanks for the subtle kick in the butt and again for your assistance.
Bud

---

