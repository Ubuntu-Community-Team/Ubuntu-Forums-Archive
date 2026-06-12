---
title: "[SOLVED] Urgent install help needed"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by igor056 on 2009-01-06
I recently downloaded the ubuntu 8.10 iso image and burnt it onto a CD for installation.  Before trying this install on my main Linux machine I have tried it on an older machine.  My question is, I am certain the first time I tried the install, converting from Windows 2000 to ubuntu, I was offered the choice of what I wanted the machine to be cofigured to do.  ie, desktop machine, development, server etc.  This choice obviously affected the packages which were installed.
I have since then tried the install again, this time from Linux Fedora Core 5 to ubuntu and I do not get this choice at all.  I get a 7 step installation procedure.
Am I missing something or is there a different installer for each situation.  How do I get to choose the configuration during the install if I do not get the options?  This has always be an installation choice before on previous Linux versions. I want such development items as the c++ packages that are not installed with the general installation.

---

### Post by tuxxy on 2009-01-06
The Ubuntu desktop ISO doesn't allow package selection at installation I don't think, it installs its own set of general purpose packages and then you can just use apt-get to download your required development items after installation.

---

### Post by oilchangeguy on 2009-01-06
> **igor056 said:**
> I recently downloaded the ubuntu 8.10 iso image and burnt it onto a CD for installation.  Before trying this install on my main Linux machine I have tried it on an older machine.  My question is, I am certain the first time I tried the install, converting from Windows 2000 to ubuntu, I was offered the choice of what I wanted the machine to be cofigured to do.  ie, desktop machine, development, server etc.  This choice obviously affected the packages which were installed.
I have since then tried the install again, this time from Linux Fedora Core 5 to ubuntu and I do not get this choice at all.  I get a 7 step installation procedure.
Am I missing something or is there a different installer for each situation.  How do I get to choose the configuration during the install if I do not get the options?  This has always be an installation choice before on previous Linux versions. I want such development items as the c++ packages that are not installed with the general installation.

no there is no choice to pick your poison, during the install. that's why different versions are available for download. but have a look in synaptic package manager. make sure the multi universe repos are enabled.

---

### Post by abn91c on 2009-01-06
the main thing is all your hardware working in live cd mode. if it runs OK just install, remember it is **[COLOR="Red"]Linux[/COLOR]**, windows XP does **not** give you a choice for desktop/laptop mode either. Ubuntu will auto detect what your computer is. It comes with Openoffice.org by default among other programs. Anything else you want you will find it in Synaptic. If its a particular program you need search these forums, there might be a free Linux version here that some other person uses.

---

### Post by igor056 on 2009-01-07
> **abn91c said:**
> the main thing is all your hardware working in live cd mode. if it runs OK just install, remember it is **[COLOR="Red"]Linux[/COLOR]**, windows XP does **not** give you a choice for desktop/laptop mode either. Ubuntu will auto detect what your computer is. It comes with Openoffice.org by default among other programs. Anything else you want you will find it in Synaptic. If its a particular program you need search these forums, there might be a free Linux version here that some other person uses.

Thanks guys, I am not too surprised by the replies.  Guess I will just have to get used to the new flavour.

---

### Post by sanil on 2009-01-07
thanks for the information. thanks for the post. Am I missing something or is there a different installer for each situation. How do I get to choose the configuration during the install if I do not get the options? This has always be an installation choice before on previous Linux versions. I want such development items as the c++ packages that are not installed with the general installation.

---

