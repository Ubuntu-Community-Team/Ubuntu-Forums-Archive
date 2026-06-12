---
title: "All Acer laptops delivered with active backdoor (in Windows)!!"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by janmartin on 2007-01-09
Hi all,

just read this disturbing news at German IT news site [http://www.heise.de](http://www.heise.de).

It seems all Acer Notebooks have been delivered for years with a dangerous backdoor in Windows. Another reason to install Ubuntu.

This is the translation by google, fixed a bit by me: 

**Dangerous back door in Acer Notebooks**

Many Acer Notebooks have a dangerous back door, over which web pages can remote control the Notebook completely. Cause is the factory-installed ActiveX control named *LunchApp.APlunch*, which has been found on all examined Acer Notebooks by heise Security. Among them was also a brand-new TravelMate, which was by chance for a test at the c't editorial office. Visiting a test page set up for this case started the Windows pocket calculator for the demonstration of the problem on these systems without asking the user first.

The control with the Class ID D9998BD0-7957-11D2-8FED-00606730D3AA was marked by the manufacturer as Safe for Scripting, so that any web page can call it via Javascript remote control. Using the method *run *it can even start system programs with parameters. So for example it could load and install a Keylogger. This functioned with Internet Explorer 6 without involving the user at all, only Internet Explorer 7 prevents the automatic start and asks the user first. However if allowed once in Internet Explorer 7 no more warnings will be delivered. With this [test page]("http://www.heise.de/security/dienste/browsercheck/demos/ie/acer.html") you can examine whether your Acer Notebook (running Windows) is susceptible. If the call of the side starts the Windows pocket calculator (C:\windows\system32\calc.exe), your system is susceptible; if nothing happens, the demo did not function.

Since the associated file *LunchApp.ocx* has the date 1998, it is to be accepted that it has been delivered for some time with Acer Notebooks. Which task it once had originally, cannot be reconstructed any longer, however the LaunchManager still works. Even a representative of Acer admitted to heise Security that it works, and must have been forgotten. The removal of the file does not cause any function loss at the examined system.

If the control is installed, the above Class-ID-String is in the Registry. Starting from Windows XP Service Pack 2 one finds it also as LunchApp.APlunch under &#8220;extras/Internet options/programs/ADD Ons administers&#8221; and can deactivate it. Alternatively one can prevent the start from the Internet Explorer also with a [Killbit]("http://support.microsoft.com/default.aspx/kb/240797") and remove and/or rename the file C:\windows\system\LunchApp.ocx.

The safety problem was first documented in November by Tan Chew Keong. Acer confirmed to heise Security that they are already working on a patch and in the second half of December 2006 production has been changed. So systems available in shops can still be affected. In the next days Acer wants to publish an official statement and make a patch accessible to its customers.

See in addition also:

    * [About Acer Notebook LunchApp.APlunch ActiveX control of Tan Chew Keong]("http://vuln.sg/acerlunchapp-en.html")

Original German language posting:
[http://www.heise.de/newsticker/meldung/83381](http://www.heise.de/newsticker/meldung/83381)

Copyright © 2007 Heise Zeitschriften Verlag

---

