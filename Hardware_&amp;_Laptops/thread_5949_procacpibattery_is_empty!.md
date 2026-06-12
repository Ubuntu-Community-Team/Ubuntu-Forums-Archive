---
title: "/proc/acpi/battery is empty!"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by snop on 2004-11-23
Hi,

I've just purchased an Acer Travelmate 4001WLMi. Ubuntu did a great job on configuring my system (Suse 9.1 didn't detected wireless card and was a pain to configure and Yoper failed at first boot).

There are two major things that annoy me:
1. Some fonts look "thin" (gnome terminal ones, for instance).
2. Battery can't be read (gnome applet says N/A and /proc/acpi/battery shows no dirs inside where there should be BAT1 or something).

Any solutions ?

Thanks in advance.

SnOp

---

### Post by snop on 2004-11-26
I've found that my laptop uses a "smart battery" that is not *yet* supported by Linux. 

Check this:
[http://sourceforge.net/mailarchive/forum.php?thread_id=6021008&forum_id=6102](http://sourceforge.net/mailarchive/forum.php?thread_id=6021008&forum_id=6102)

I own an Acer Travelmate 4001 WLMi and there seem to be other models using this kind of batteries:

-Travelmate 4001WLMi (being phased out, they won"t let us have it)
-Travelmate 8005LMi (supposedly the same as above)
-Travelmate 4501WCi
-Travelmate 292 (Extensa 2920) (AFAIK phased out)
-Extensa 3001 (N/A)
-Probably others (specialy different flavors of Travelmate 4000, 8000 etc...)

I don't know if support would be soon implemented. Let's hope so.

Bye

SnOp

---

### Post by fromtheflames on 2004-12-09
Ouch!!!

My laptop's battery isn't supported too!
Acer TM3200

Thank you for the infos about smart battery!
Hoping in a soon support!

---

### Post by fromtheflames on 2005-01-21
Found this page: [http://linuca.org/body.phtml?nIdNoticia=315](http://linuca.org/body.phtml?nIdNoticia=315)

The most important link, is the last one: [http://shayol.bartol.udel.edu/~rhdt/download/acpi_sbs-20050120.tar.gz](http://shayol.bartol.udel.edu/~rhdt/download/acpi_sbs-20050120.tar.gz)

This is a driver written by Rich Townsend; here an extract from the acpi-devel newsgroup: [http://article.gmane.org/gmane.linux.acpi.devel/11733](http://article.gmane.org/gmane.linux.acpi.devel/11733)

Need to include a patch into the kernel first... I'm having problem doing that: I want to obtain a kernel like the current one (hoary for me) plus the patch included in the package... not much time for trying this...

Hoping someone could test this driver and report here.

Good luck!

---

### Post by snop on 2005-01-21
Hi,

These are great news for smart battery users! I also read acpi mailing lists from time to time. There are some other links in one of my recents posts regarding smart batteries:

[http://ubuntuforums.org/showpost.php?p=52245&postcount=19](http://ubuntuforums.org/showpost.php?p=52245&postcount=19)

Some people using travelmate 400x has reported that the driver works.

Now I wonder what stable kernel will be the first to get the patches in. I guess it will be 2.6.12.

Bye

PD: I don't want to recompile my kernel as I did many times when using slackware. But I think I'll have to is I want to get rid of my buggy dsdt.

---

### Post by huron7014 on 2007-05-15
> **fromtheflames said:**
> Ouch!!!

My laptop's battery isn't supported too!
Acer TM3200

Thank you for the infos about smart battery!
Hoping in a soon support!


[generator insects Mortgages Mortgages photosynthesis](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

