---
title: "Cannot enable desktop effects in 10.10 under virtual box"
date: 2010-12-31
forum: Hardware
---

### Post by langer123 on 2010-12-31
Hi All

I have Ubuntu 10.10 installed on my Dell xps studio 16' laptop.
It's installed under the latest version of Virtual Box (3.2.10) as a guest OS.

I'm having a problem enabling 'Visual Effects' under the appearances preferences.

I cant set it to 'Normal' or 'Extra'.
Both return the message:
"Desktop effects could not be enabled."

Has anyone any ideas on this? Maybe not recognizing my graphics card?
I do have 3d acceleration enabled in the virtual box setting and have given it 64mb of video ram.

Looking forward to a dazzling shiny interface for the new year! :)

Thanks

---

### Post by langer123 on 2011-01-14
Nobody? :(

---

### Post by wangsuda on 2011-01-14
Many graphics are disabled under VB. I run Windows 7 in VB and cannot get the fancy pop-up windows - too memory intensive. Perhaps the same is true for desktop effects - very memory intensive. You can try to up the amount of RAM memory given to the VM. Additionally, up the amount of video memory given to the VM.

---

### Post by sarim on 2011-01-14
you need to install virtualbox guest addition in the guest os(Ubuntu).

---

### Post by wangsuda on 2011-01-14
> **sarim said:**
> you need to install virtualbox guest addition in the guest os(Ubuntu).
I knew there  was something I forgot to mention. thanks!

---

### Post by langer123 on 2011-01-14
Appreciate the tips guys but unfortunately I've tried upping the memory to 1.6G and video memory to 128mb with no luck.

I have virtualbox guest edition (autorun.sh) installed on Ubuntu already, as I am able to use it in full screen mode.

---

### Post by Yellow Pasque on 2011-01-14
What is the output of:
```
compiz --replace
```

---

### Post by langer123 on 2011-01-14
```
thomas@thomas-VirtualBox:~$ compiz --replace
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

Launching fallback window manager
```

---

### Post by sarim on 2011-01-14
There definitely any problem with virtualbox installation of guest addition installation, bcz i have run compiz many times inside vbox with only 2MB Video ram.

---

