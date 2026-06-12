---
title: "Kontact crashes when opening settings"
date: 2008-11-11
forum: General Help
---

### Post by rousselm on 2008-11-11
Hello,

I've installed Kontact (version 1.3) on the new Ubuntu intrepid. At first it was working fine and I changed some of the setting like categories, calendar ressource and so on. I also disabled Kmail as I thought I wouldn't need it. But in fact I do need it.
The problem now is that each time I try to open Kontact settings (in "configure Kontact") Kontact crashes. It gives me this message 
"A Fatal Error Occurred
The application Kontact (kontact) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc."
I don't know why. I could go around it by opening each application settings I need to change one by one but the problem is to enable Kmail again. Any ideas?

Thanks in advance for any help...

Marie

---

### Post by Proshka on 2009-01-30
> **rousselm said:**
> Hello,

I've installed Kontact (version 1.3) on the new Ubuntu intrepid. At first it was working fine and I changed some of the setting like categories, calendar ressource and so on. I also disabled Kmail as I thought I wouldn't need it. But in fact I do need it.
The problem now is that each time I try to open Kontact settings (in "configure Kontact") Kontact crashes. It gives me this message 
"A Fatal Error Occurred
The application Kontact (kontact) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc."
I don't know why. I could go around it by opening each application settings I need to change one by one but the problem is to enable Kmail again. Any ideas?

Thanks in advance for any help...

Marie

Marie,

I found a solution here: 

[https://bugs.kde.org/show_bug.cgi?id=167625]("https://bugs.kde.org/show_bug.cgi?id=167625")

I deleted .kde/share/config/kontactrc and now it seems to work. After that I could use Kmail again without any crashes.

---

