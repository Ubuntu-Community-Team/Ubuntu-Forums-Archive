---
title: "System won't shutdown cleanly; 9.04 post-install restart also failed"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Rulls on 2009-04-26
I need assistance with how to resolve shutdown problem.  When I shut down the system, it freezes at a text screen (appears to be well into the shutdown process), and the only way to get out is to force a power down.

In case it might be related, the shutdown-restart sequence that occurs at the end of the installation process also failed with similar behavior.

Thank you in advance for any assistance you can provide.

---

### Post by Latito on 2009-04-28
I'm having the same issue, any idea on what could be causing this?

---

### Post by lisati on 2009-04-28
I had 9.04 briefly on one of my laptops and had the exact same problem: hanging on shutdown. I read elsewhere in the forums that it sometimes appears to be connected with the wireless card, and one person suggested turning off your wifi card before shutdown.

---

### Post by Rulls on 2009-04-28
Thanks for the reply and the suggestion, Lisati.  Update on symptoms on my machine - shutdown problem is intermittent.  Sometimes I get a clean shutdown, and sometimes the same lockup.  I had not yet tried turning off wi-fi.

So it appears that this is not an uncommon problem, but what I'm not hearing about is a focus on a solution (an actual solution, not an awkward workaround).  Is this being addressed?  Is a general symptom like this an appropriate subject for bug reporting?

---

### Post by Monsieur Gonzalez on 2009-04-28
What are your system specs? (video card, ram, swap partition size).

---

### Post by Rulls on 2009-04-28
My system specs are:
Make and Model - Toshiba Satellite A105 Notebook
Processor - Intel Core 2 Duo, 1.6 GHz
Video - Intel GMA 950
Wireless - Intel PRO/Wireless 3945ABG
RAM - 1.5 Gb
Swap - 3 Gb

---

### Post by Monsieur Gonzalez on 2009-04-28
Just a little test: 

1- Save all your work and close any open programs.
2- Change to a terminal (Control+Alt+F1)
3- log as your user
4- enter "sudo shutdown -h now" and watch the shutdown sequence for any errors that might give a clue about the problem

---

### Post by Rulls on 2009-04-28
> **Monsieur Gonzalez said:**
> Just a little test: 

1- Save all your work and close any open programs.
2- Change to a terminal (Control+Alt+F1)
3- log as your user
4- enter "sudo shutdown -h now" and watch the shutdown sequence for any errors that might give a clue about the problem

Thanks for the suggestion.  I'll shutdown shortly and try that.

I'm thinking there must be a log where any messages from all recent shutdowns would have been recorded.  Do you know if that's the case, and where I might find that log?

---

### Post by Monsieur Gonzalez on 2009-04-28
Logs are kept in /var/log/ . There are many files, you might want to take a look at messages, kmesg, syslog

---

### Post by l-x-l on 2009-04-28
I had a problem with my wireless card shutting down & found a work around from this site & it works for me:

**[Workaround]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes")**

```
sudo gedit /etc/init.d/alsa-utils

Search for "stop)" and add immediately below: 
ifconfig eth0 down
ifconfig wlan0 down
```

---

### Post by fotis_utmost on 2009-04-30
> **l-x-l said:**
> I had a problem with my wireless card shutting down & found a work around from this site & it works for me:

**[Workaround]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes")**

```
sudo gedit /etc/init.d/alsa-utils

Search for "stop)" and add immediately below: 
ifconfig eth0 down
ifconfig wlan0 down
```

It worked for me too! Thanks man!

---

### Post by l-x-l on 2009-05-03
Update: If you're laptop won't shutdown due to wireless not shutting down, a proper fix was posted by hesapotman **[HERE.]("http://ubuntuforums.org/showpost.php?p=7149271&postcount=22")** I'm now using his solution instead of the one I posted earlier.

---

