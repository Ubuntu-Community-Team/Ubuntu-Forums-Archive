---
title: "Argh. Save session warning comes up even when disabled"
date: 2005-11-18
forum: General Help
---

### Post by Pausanias on 2005-11-18
Help! Whenever I log out, even though I have the "Save current setup" box **unchecked**, it still warns me about windows (FireFox, calculator, etc.) that it can't save. I select shut down from the menu, click ok, go get my stuff, come back to my laptop expecting it to be off, and instead there's that silly dialog warning me about FireFox.

This was fine for the first few months. But somehow, rather than my getting slowly used to it, I slowly got more and more aggravated by the dialog box and my computer's failure to shut down immediately on demand, so much so that I just wasted half an hour searching for an answer on the forums and on Google. OK, my searching skills must be severely impeded by lack of sleep. So, here I am taking some of your time and hoping for an answer. How do I turn off that very aggravating dialog (I am getting more and more worked up about it just typing this).

---

### Post by Pausanias on 2005-11-18
Come on, ultra friendly Ubuntu people. Show me your genius!

---

### Post by greenstar on 2005-11-18
I think I have a solution. Go to: System->Preferences->Sessions. In the Sessions window, click the Session Options tab. Then, uncheck (if checked) the "Automatically save changes to session" option.

I hope this fixes your problem.

greenstar

---

### Post by Pausanias on 2005-11-19
[QUOTE=greenstar]I think I have a solution. Go to: System->Preferences->Sessions. In the Sessions window, click the Session Options tab. Then, uncheck (if checked) the "Automatically save changes to session" option.

I hope this fixes your problem.

greenstar[/QUOTE]

Hi greenstar

I tried your suggestion, but the "Automatically save changes to session" check box was already unchecked.

However, I do have more information on the problem. It happens only when logout is activated via a keyboard shortcut.

That is, when I select "Log out" from the GNOME menu, everything works fine.

But when I logout using the keyboard shortcut defined in System->Preferences->Keyboard shortcuts, then I always get the "cannot save" warning, even though all the "save settings" dialog boxes are unchecked.

Very strange. Looks like it's time to head over to bugzilla.

---

### Post by no1wantdthisname on 2005-11-19
Did you remove any sessions that are saved?  There's usually one called Default.

EDIT: ah, after rereading it seems like your problem is that firefox can't be saved and the dialog pops up.  That's strange since I can logout just fine with firefox open.  
You can try using the firefox 1.5 version.

---

