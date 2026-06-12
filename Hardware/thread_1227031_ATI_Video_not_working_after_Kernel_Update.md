---
title: "ATI Video not working after Kernel Update"
date: 2009-07-30
forum: Hardware
---

### Post by wrwarwick on 2009-07-30
Yesterday after I installed the kernel update my ATI video was no longer functioning. At first I could get into ubuntu and gnome would load but I did not have any composite effects. I tried to reinstall the ATI driver from the ati.com website to no effect. Then I installed envyng and attempted to use that and now when I load ubuntu all I get in garbled and blurry screen. 

I'm afraid I may have corrupted something along the way but do not know how to correct the issue. 

Any help would be great!

---

### Post by automaton26 on 2009-07-30
Yes, my ATI Catalyst 9.6 configuration was broken by a kernel update too (wish they'd warn new users about that).

Try uninstalling first, then make sure default GNOME support is OK, then try installing again:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

---

### Post by wrwarwick on 2009-07-30
> **automaton26 said:**
> Yes, my ATI Catalyst 9.6 configuration was broken by a kernel update too (wish they'd warn new users about that).

Try uninstalling first, then make sure default GNOME support is OK, then try installing again:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

Thanks for the help - now I am back in ubuntu and gnome has loaded successfully. 

One question - I have envy installed and it still reports that the driver is installed and enabled. Should I not worry about envy and just reinstall the driver that I downloaded? Should I uninstall envy first?

---

### Post by wrwarwick on 2009-07-30
Well I went ahead and reinstalled the drivers that I downloaded and it is working now. Thanks for all the help!

---

### Post by ZaHACKieL on 2009-07-30
> **wrwarwick said:**
> Well I went ahead and reinstalled the drivers that I downloaded and it is working now. Thanks for all the help!

Hi. Well, everytime you make a kernel update you have to reinstall the ATI drivers. I don't know if it's the same with NVIDIA but what I usually do is, after a kernel update I restart the system and boot from the previous kernel. I reinstall the ATI drivers after that and go back to the new kernel =]

---

