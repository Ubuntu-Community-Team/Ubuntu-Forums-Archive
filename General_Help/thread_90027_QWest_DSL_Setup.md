---
title: "QWest DSL Setup???"
date: 2005-11-14
forum: General Help
---

### Post by graphfixpunk on 2005-11-14
Before I begin here is my setup.

PC Rhine II Fast Ethernet Adapter
             |
             |
LinkSys Dsl Router Model #BEFSR41
                   |
                   |
Qwest Action Tech DSL Modem

for some strange reason i seem to be able to get to the forums and post this but nowhere else on the internet my modem is configured proparly and i can ping various web pages but i cant get things like GAIM and Firefox to work proparly.

In posting this from my crash prone laggy windows side ugh any help would be appreciated.

thanks

---

### Post by Remmelas on 2005-11-14
cat /etc/resolve.conf and see if the ip of your Actiontec is listed as a dns server, if it is, remove it.  For some reason, if the Actiontec is anywhere in the dsn resolution chain(whether in your router, or your machine) dns resolution gets messy, and hit or miss.

---

### Post by jeffdano on 2005-11-14
[QUOTE=graphfixpunk]Before I begin here is my setup.

PC Rhine II Fast Ethernet Adapter
             |
             |
LinkSys Dsl Router Model #BEFSR41
                   |
                   |
Qwest Action Tech DSL Modem

for some strange reason i seem to be able to get to the forums and post this but nowhere else on the internet my modem is configured proparly and i can ping various web pages but i cant get things like GAIM and Firefox to work proparly.

In posting this from my crash prone laggy windows side ugh any help would be appreciated.

thanks[/QUOTE]

I had the same issues... answer... PORT Forwarding on that damned Actiontec. You need to allow port 1863 for GAIM (good luck getting any settings on this router to stick!), I had to download KMess, which worked marvelously, and load it first, then quit to get GAIM to work at all, don't know why, just works. As for Firefox, depending on the system it may or may not work. I am able to use Firefox on my computer, but on my wife's laptop only Konqueror works without issue. I blame the Actiontec router for my problems. I even, GASP, tried a different distro and it had the same issues, so it's definitely not Ubuntu specific. Hope this helped.

---

### Post by graphfixpunk on 2005-11-14
ill try both ideas and see what works but its a start thanks guys

---

### Post by Cashel on 2006-01-28
Very helpful, thanks folks.

I'm considering buying a cisco switch, it's gonna be fun to see if I can use this crappy dsl modem then :)

---

### Post by mips on 2006-02-03
[http://ubuntuforums.org/showthread.php?t=95350](http://ubuntuforums.org/showthread.php?t=95350)

Look at post #26 and follow the link to the LinuxQuestions site.

It should solve your problem.

---

### Post by Djartklom on 2006-02-07
Interesting problem.  I have Qwest DSL and the same DSL modem, but a different NIC.  Ubuntu gave me absolutely no problems with this setup, but these days, that seems to be the rule rather than the exception with Linux.  

What was interesting about my particular hardware configuration is that I had great difficulty getting it to work with Windows XP.  The tech support person had me attempt to configure the Actiontec router through Internet Explorer--their usual procedure.  It didn't work.  In fact, the configuration menu wouldn't even open in the browser.  On a whim, I suggested we use Firefox to accomplish the task.  It worked.  No word on whether they put the information from my success story into the tech support database.

---

