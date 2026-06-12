---
title: "Firefox issues."
date: 2008-09-14
forum: General Help
---

### Post by _Corsair_ on 2008-09-14
Hello! (**TL;DR read bold**)

First of all, I'd like to say thank you to everyone here.  I've been running Ubuntu for about a month (my first foray into Linux), and so far the archives here (and occasionally some other websites) have helped me solve all of the problems and questions I've had without me having to register.  That is, until now.

[B]Firefox is not working properly.  When I open it, it asks me the "your last session did not end normally.... restore tabs?" question, and no matter what I pick, it then just opens up with a white screen and nothing in the location bar.  (see image below)
[[IMG]http://img525.imageshack.us/img525/4213/firefoxfailedlk3.th.png[/IMG]](http://img525.imageshack.us/my.php?image=firefoxfailedlk3.png)
It gets even more weird because I can enter URLs in the location bar and visit those websites, clicking around and even opening multiple tabs, but the text in the location bar stays the same unless I change it myself, and then it changes for all tabs.  Also strange is that my bookmars seem to be missing (couldn't find the bookmarks.html file when searching my computer, just old backups), and yet my addons (personal menu, AdBlock Plus) are working fine.

I have unistalled and reinstalled firefox (sudo aptitude remove firefox ;  sudo apt-get install firefox)  and restarted, but nothing has improved.  Also, since my launcher actually goes to "firefox-3.0", I have tried uninstalling that, but got a rather unsettling warning which caused me to abort:

[[IMG]http://img411.imageshack.us/img411/6334/remvoalqy8.th.png[/IMG]](http://img411.imageshack.us/my.php?image=remvoalqy8.png)

removing "ubuntu-desktop" doesn't sound good to me...[/B]

All my other browsers are working fine, and I have run update manager since this problem developed, but nothing has changed.

_Tech specs:_
Thinkpad T61
Intel Duo Core 2.0 Ghz
200GB Seagate 7200rpm HDD
2GB RAM (I think...)

Firefox version 3.0.1

Any ideas would be very much appreciated, and please let me know if you'd like me to provide more information about anything.

---

### Post by Tanker Bob on 2008-09-14
The usual problems with Firefox are caused by bad extensions or conflicts between them. First thing would be to start Firefox in [safe mode](http://kb.mozillazine.org/Safe_Mode):

```
firefox -safe-mode
```

Then see if the problem reoccurs. That's something quick and easy to try. 

However, it sounds like your profile has become corrupted. Try moving your profile directoy somewhere else and then starting Firefox clean. If that works, then put your extensions back one by one, restarting Firefox after each addition.

---

### Post by _Corsair_ on 2008-09-14
Thanks!  moving the profiles file to a different directory fixed the problem, although now I must rebuild all my customizations.  I wonder what caused the corruption.

---

### Post by Tanker Bob on 2008-09-14
I'm glad it worked for you. Since almost all the extensions and plug-ins are developed independently, any developer who even inadvertantly wanders outside of reservation can cause havoc. I love Firefox and wouldn't trade it for anything out there. Extension are one of its greatest strengths but at the same time its Achilles Heal.

---

### Post by jenelle on 2008-09-15
firefox prevented this page from automatically redirection to another page

i am getting this message on some forums i got to when i log in or out or post something , my sister pressed something [ don't ask me what but i can ot stop it from doing what it is doing  .

now i have on my computer 2 other users and i can go into them if need be and it does not do it on them i checked the page info button in tools and went to where it said allow cookies etc etc and checked that against all the other pages [ user pagers ] and all the same ?

has me stumped if anything i will create another user page just to stop the problem and delete the one i am using if anything but thought i would see if any of you can help me before i try that

---

### Post by Tanker Bob on 2008-09-15
Do you have the Redirector extension installed? That strips the redirection from links. I use this but haven't generally had the problem that you describe.

---

### Post by dayanandasaraswati on 2008-09-15
I too had almost similar if not much worse issues with firefox 3. I manually downloaded firefox 2 and installed it separately and was using it. Now few weeks before my firefox updated itself to firefox 3.0.1 and now the beauty of firefox 3 has restored. Now firefox seems to work flawlessly. Infact the previous crash firefox 3 happened only after installing too many addons. So you better update your firefox to the latest version and try working. That could help you around.

---

### Post by jenelle on 2008-09-16
> **Tanker Bob said:**
> Do you have the Redirector extension installed? That strips the redirection from links. I use this but haven't generally had the problem that you describe.

to be honest i don't know , it has been upgraded to 8.04LTS just recently , it was not doing it till my sister did something which i don't know what the page that comes up allow cookies images etc etc in it is the same on all user pages but am lost on all other stuff i know bits that is it , i am not happy with my sister for doing what she did :(

> **dayanandasaraswati said:**
> I too had almost similar if not much worse issues with firefox 3. I manually downloaded firefox 2 and installed it separately and was using it. Now few weeks before my firefox updated itself to firefox 3.0.1 and now the beauty of firefox 3 has restored. Now firefox seems to work flawlessly. Infact the previous crash firefox 3 happened only after installing too many addons. So you better update your firefox to the latest version and try working. That could help you around.
i think it did when it got up graded [firefox upgrading ] what ever happened was cause of my sister and now i am left to try and fix it and as i don't like fiddling too much in this sort of thing as i am always afraid of stuffing it up i have not yet till i let my sister use it !

---

