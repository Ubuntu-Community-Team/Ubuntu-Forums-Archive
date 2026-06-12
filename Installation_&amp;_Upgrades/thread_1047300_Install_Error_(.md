---
title: "Install Error :("
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by BrandonBan6 on 2009-01-22
Hello,

So I was installing a VirtualBox upgrade via GUI package when my machine froze up, I manually shut it down. Restarted it, and now when double click the package I get the attached error. I can't find a process running for Synaptic, Aptget or Update Manager. Any thoughts?

---

### Post by BrandonBan6 on 2009-01-22
New clue here, when I try an install from the terminal, I get an error that say:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

So I run the suggested code, and I get this:
```

:~$ sudo dpkg --configure -a
dpkg: error processing virtualbox-2.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 virtualbox-2.1

```

Where should I go from here, or how should I reinstall this?

---

### Post by BrandonBan6 on 2009-01-22
Sweet...........actually, I was able to somehow use dpkg --force and got it to remove the "broken" package. Honestly, I'm not sure what I did, but it works!

---

### Post by dabl on 2009-01-22
> **BrandonBan6 said:**
> 

when my machine froze up, I manually shut it down.


 Any thoughts?


That's tough on your filesystem and running processes, and usually not necessary.  Next time you think it is frozen, try holding down Alt-SysRQ and then press slowly, in sequence, R  S  E  I  U  B

Probably you will be amazed to see your "fozen" system do a graceful shutdown/restart.  And stuff won't be broken (or at least not any _more_ broken) when it comes back up.  ;)

---

### Post by BrandonBan6 on 2009-01-22
Thanks dabl,

That is a bit elaborate to remember eh? 

Is there another "ctrl+alt+del" like command, that would allow you kill a hung up process? 

thanks for your help.

---

### Post by boof1988 on 2009-01-22
> **dabl said:**
> Next time you think it is frozen, try holding down Alt-SysRQ and then press slowly, in sequence, R  S  E  I  U  B

Where is the <SysRQ> button?  -Or-  What other name/label would the <SysRQ> button have?

---

### Post by BrandonBan6 on 2009-01-22
> **boof1988 said:**
> Where is the <SysRQ> button?  -Or-  What other name/label would the <SysRQ> button have?

It is the same as your "print screen" button. Right next to the scroll lock and pause buttons, above the insert/home/page up buttons :)

---

### Post by dabl on 2009-01-22
_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring.


:D

---

### Post by BrandonBan6 on 2009-01-22
haha! that works.........thanks a lot!

---

### Post by boof1988 on 2009-01-22
> **dabl said:**
> _R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring.


:D

Or...  from [TechPatterns](http://techpatterns.com/forums/about911.html)

> _R_eboot _S_ystem _E_ven _I_f _U_tterly _B_roken

---

