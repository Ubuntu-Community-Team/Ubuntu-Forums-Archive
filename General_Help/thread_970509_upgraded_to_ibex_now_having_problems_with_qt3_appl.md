---
title: "upgraded to ibex: now having problems with qt3 applications..."
date: 2008-11-04
forum: General Help
---

### Post by axa1001 on 2008-11-04
Hi All, 

This one is causing me a bit of a headache. I upgraded to Intrepid Ibex via the dist-upgrade route. 

However I then noticed a strange thing when launching Open Office (2.4, installed on Hardy prior to upgrade to Ibex). None of the UI controls contained any text, just icons on those entries that normally had them. This affected all menus and dialogs etc... I removed and reinstalled OOO 2.4, to no effect. I then removed OOO 2.4, downloaded OOO 3.0 from the OOO website, installed it, and found the same problem...

I then discovered that Scribus also had the same problem, and therefore identified that the common element was qt3. It turns out the the qt3 configuration utility also had the problem, whereas the qt4 configuration utility works ok.

I have since removed all of qt3/4 and applications that relied on them. Once that was done, I reinstalled the qt3 basics, and Scribus. And the problem still exists in Scribus and the qt3 configuration utility.

here is a screenshot of the qt3 configuration utility as an example:

[IMG]http://i247.photobucket.com/albums/gg139/axa1001/qt3-config-missing-text.png[/IMG]

and a more dramatic example from Scribus (very similar to that in OOO before i uninstalled it)

[IMG]http://i247.photobucket.com/albums/gg139/axa1001/Scribus-qt3-missing-text.png[/IMG]

So what am I missing here? any ideas or similar experiences... any suggestions would be appreciated.

Thanks.

---

### Post by axa1001 on 2008-11-04
Ok, in the end my solution has been to download 8.10 desktop iso image, burn a cd, and install from scratch.

I never found out what the cause of the qt3 issue was...

I won't mention the incredibly stupid thing i managed to do to all of the files in /etc while attempting to remove all possible traces of qt... needless to say that lobotomizing your Ubuntu install is "A Bad Thing" ](*,):biggrin:

---

### Post by ronniet on 2008-11-23
The problem there is that you probably have Desktop Effects enabled in Ubuntu?

I did the same thing, but when I DISable the Desktop Effects both Scribus and OOo are fine. I'm not sure what causes it, but that's the solution I used...  :(

---

### Post by carlosalvatore on 2008-12-27
there must be a reason for this to happens, is there a way to fix it without disabling desktop effects?

---

