---
title: "install desktop on server ubuntu"
date: 2008-08-07
forum: General Help
---

### Post by Wulf_Hntr on 2008-08-07
Ok, I'm lame. I inherited a computer that has Ubuntu server loaded on it but am not adept enough yet to navigate through command lines. I would like to install the desktop version on it and gradually learn more about the server version. Is there a way to do this?  Can I set the computer upon booting up to boot to either server or desktop version?  i will go sit in the corner with my dunce cap on until someone is kind and can help me out of my predicament.

Also apparently when Ubuntu was install all traces of Windows OS was removed.

---

### Post by prshah on 2008-08-07
> **Wulf_Hntr said:**
> 
I would like to install the desktop version on it and gradually learn more about the server version. 


Short answer; yes. ```
sudo apt-get install ubuntu-desktop
```

Long answer: 

a. You really should post more specs; a desktop version will require at least 256Mb RAM.

b. What version of ubuntu is running on it?

c. Rather than use the Internet to download so many packages, it's better if you get the live/alternate CD/DVD, add it to the package manager (post back for commands help) and let the system install ubuntu-desktop from the CD/DVD. Again, one needs to know what version of ubuntu you're running: ```
lsb_release -a
```

> **Wulf_Hntr said:**
> Also apparently when Ubuntu was install all traces of Windows OS was removed All to the good; you can do without it.

---

### Post by Wulf_Hntr on 2008-08-07
Thank you so much for your help.  This is going to sound really strange but i just booted it up so get some of the information you needed to help me get this problem resolved and it opened to the Hardy Heron desktop (I have probably rebooted a couple of dozen times and that has never happened).

Now if it does will continue to do this until i get done with Linux 101 I may be able to take off the dunce cap and put on a beanie.

Thanks again for taking the time help me get started.  It is very much appreciated

---

