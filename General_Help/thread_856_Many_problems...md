---
title: "Many problems.."
date: 2004-10-16
forum: General Help
---

### Post by Homer on 2004-10-16
Hi,

I use Ubuntu Preview for a week now.  All was OK before right now.  When I tried to start Firefox, nothing happened.  Ok.. I closed my session and I tried to relog again.

First problem, when I type my password, I see a square with alphanumerical number in it (normally, it's * or dot). 

Second problem, login was not possible.  GDM complains about .ICEauthority.  I logged in TERM and I see that this file was owned by root (!?).  I sudo chown to my user and I login.  Second problem is resolved.

Third problem.  Firefox still doesn't start.  Thunderbird too!  I tried to start it in a terminal:

```
fd@duff&#58;~ $ mozilla-firefox
Error&#58; No running window found
auto selected locale&#58; fr-FR
Erreur de segmentation
fd@duff&#58;~ $ mozilla-thunderbird
selected locale&#58; fr-FR
DOUBLE-CLICK&#58; 400 --&gt; -1 THRESHOLD&#58; 8 --&gt; -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh&#58; line 451&#58;  5403 Erreur de segmentation  &quot;$prog&quot; $&#123;1+&quot;$@&quot;&#125;
fd@duff&#58;~ $
```

Segmentation fault!  Why!?


I checked for update.  Only a base-config update was available.  I installed it and I reinstalled Firefox and Thunderbird.. with still no luck.

All of my others applications seem to work (Gnome terminal, Gaim, X-Chat 2.4.0, Synaptic, Konqueror...)

What is my problem(s) ?

Thanks for your help and sorry for my bad English.

EDIT: If I sudo mozilla-firefox or sudo mozilla-thunderbird, it works!  Another rights problems?  Then If I start Firefox, it still doesn't start, but Thunderbird starts... with an empty profile (over of 300mo of mail lost..)  Wtf about this thing ?

---

### Post by borris.morris on 2006-12-30
i had the firefox problem. What worked for me is to go to your home folder and remove ".mozilla" folder. It's got a bug with the session or something.

---

