---
title: "How to remove &quot;dpkg was interrupted&quot; state"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by paulocr on 2009-05-18
Hello,

I was upgrading from Intrepid to Jaunty and for some reason (I left my pc upgrading during the weekend and was not here) when I came on Monday it was frozen. So I don't know where in the process it failed or locked and I had to manually reboot and now it's in a broken state.

I am trying to recover from this by reinstall the udev package however when I try to run any apt-get or aptitude commands it gives me the error "dpkg was interrupted you must manually run, etc". I already tried this but the error persists so I am wondering if there is some kind of lock that can be removed from dpkg which will allow me to reinstall a package and then run the dpkg --configure -a at the end.

Thanks,

Paulo

---

### Post by paulocr on 2009-05-18
I think I managed to fix it by running dpkg -forget-old-unavail

I'll let you all know in a second :D

---

