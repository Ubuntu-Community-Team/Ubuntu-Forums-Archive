---
title: "problem with HP AIO printer and wireless"
date: 2013-07-18
forum: Hardware
---

### Post by RyanGT on 2013-07-18
I just bought an HP DeskJet 3512 AIO and configured the wireless using my Mac and the HP driver.  The printer is correctly connected to my wireless network.  I am trying to isntall the printer in Ubuntu 12.04 LTS.  When I go to printing and select add printer, the dialog finds the network printer and I accept the defaults.  But when I print a test page, it hangs in the queue indefinitely.  How do I troubleshoot this?

Thanks,

Ryan

---

### Post by RyanGT on 2013-07-18
I guess this is sort of solved.  I was sure that a fairly recent version of hplip was installed (it was).  Not knowing what else to try, I downloaded and installed the software from hp: [http://prdownloads.sourceforge.net/hplip/hplip-3.13.6.run](http://prdownloads.sourceforge.net/hplip/hplip-3.13.6.run)

The script uninstalled the version that came with 12.04LTS and installed a newer version (and quite a few other packages).  

My printer is now working wirelessly in Ubuntu and Mac OSX, so I am happy.  But the HP people had to solve the problem, so I don't know if that makes Ubuntu people happy or not (in some sense it is really nice to have companies do stuff for you - that is why I buy HP).

---

