---
title: "[SOLVED] WINE windows imulater won't/can't install."
date: 2008-10-21
forum: General Help
---

### Post by Austin_Duffy on 2008-10-21
Every time I press it under the "Add/Remove" under applications I get the following error:

[[IMG]http://img519.imageshack.us/img519/139/screenshotof1.png[/IMG]](http://imageshack.us)

I understand how to get to synaptic under system but, after that then what do  I look under?

---

### Post by taqkavar on 2008-10-21
go to synaptics, then search for wine. mark it and click apply. or do "sudo apt-get install wine"

If you want a more recent version of wine, follow this page:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Austin_Duffy on 2008-10-21
> **taqkavar said:**
> go to synaptics, then search for wine. mark it and click apply. or do "sudo apt-get install wine"

If you want a more recent version of wine, follow this page:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Thanks for the quick response I appreciate it, But I got this when ever I tried to install it:
[[IMG]http://img525.imageshack.us/img525/1131/screenshot1nx9.png[/IMG]](http://imageshack.us)

I searched for "libaudio2" in synaptics but could not find it. Any suggestions?

---

### Post by Sycron on 2008-10-21
Go to System-Administration-Software Sources and check everything but Source Codes. Then reload the repositories.

---

### Post by Austin_Duffy on 2008-10-21
> **Sycron said:**
>  Then reload the repositories.

Thanks for the help but where do I find repositories or how do I reload them?
 
Much appreciated.

---

### Post by Sycron on 2008-10-21
Once you will activate all that checkboxes and click close you will be prompted to reload the repositories. Reload them and post back.

---

### Post by Austin_Duffy on 2008-10-21
> **Sycron said:**
> Once you will activate all that checkboxes and click close you will be prompted to reload the repositories. Reload them and post back.

Thanks I installed it and then clicked apply and now it has installed, thanks again for the help!

---

### Post by Sycron on 2008-10-21
If your problem have been solved you may mark your thread as Solved. Go to Thread Tools and choose Mark as Solved.

---

### Post by Titan8990 on 2008-10-21
I have something to add. WINE is not a emulator. In fact, that is what it stands for: **W**ine **I**s **N**ot a **E**mulator.

---

