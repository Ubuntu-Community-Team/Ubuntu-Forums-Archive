---
title: "Evolution fails start -- segmentation fault"
date: 2008-10-31
forum: General Help
---

### Post by Unterseeboot_234 on 2008-10-31
Because of a glowing article in "Linux Magazine" on the virtues of Evolution email program, I decided to try to configure Evolution 2.+. In the past, starting Evolution would get the Wizard to set up the mail server. Now, all I get is a silent fail from a desktop launch. In terminal I get

```
user-desktop:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
Segmentation fault (core dumped)
```

sudo apt-get purge evolution
sudo apt-get remove evolution
sudo apt-get install evolution

does nothing. Is there anything else I can look at? Any configuration file? Should I suspect the repos have the 32-bit Evolution for AMD64 users? Or, do I need to link Evolution through ia32?? Baffling to me because Evolution has always just worked. It's part of Gnome. 

Ideas? anyone?

---

### Post by dcstar on 2008-10-31
> **Unterseeboot_234 said:**
> Because of a glowing article in "Linux Magazine" on the virtues of Evolution email program, I decided to try to configure Evolution 2.+. In the past, starting Evolution would get the Wizard to set up the mail server. Now, all I get is a silent fail from a desktop launch. In terminal I get

```
user-desktop:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
Segmentation fault (core dumped)
```

sudo apt-get purge evolution
sudo apt-get remove evolution
sudo apt-get install evolution

does nothing. Is there anything else I can look at? Any configuration file? Should I suspect the repos have the 32-bit Evolution for AMD64 users? Or, do I need to link Evolution through ia32?? Baffling to me because Evolution has always just worked. It's part of Gnome. 

Ideas? anyone?

Rename the hidden .evolution folder and try again.

---

### Post by dryan775 on 2008-12-13
> **dcstar said:**
> Rename the hidden .evolution folder and try again.

I have the same problem with evo on load (7.10).  I have renamed the .evolution folder, the system works fine.  I replaced folders one by one to isolate the problem.  The address book and calendar went back in without a problem.  I can get it running with my calendar info and address fine. When I try to put the email back, I get the segmentation fault again.  
I was just using it earlier to day.  I got an email from my mother, checked the calendar and closed it without an issue. Camee back later, it crashes.  Any ideas?   I'm thinking something in the email is corrupting the file.  I tried to gedit that message out of the file, but it still faults.

---

