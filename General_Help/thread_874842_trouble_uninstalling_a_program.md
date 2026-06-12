---
title: "trouble uninstalling a program"
date: 2008-07-30
forum: General Help
---

### Post by HarmonicaGoldfish on 2008-07-30
Hello,

A while ago I installed first class on my dell/ubuntu laptop. 

I installed it by following the instructions here:

[http://education.concordia.ca/ClientDownloads/Linux%20Download%20Page](http://education.concordia.ca/ClientDownloads/Linux%20Download%20Page)

I would now like to uninstall it in order to reinstall it. It is acting all wonky.

However I can't figure out how!

My first step was to use add/remove. It didn't show up there.

So, I did a search for it on my system and got this result:
[ATTACH]79467[/ATTACH]

I tried this so far:

> tracy@tracy-laptop:~$ sudo apt-get remove firstclass
[sudo] password for tracy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firstclass
tracy@tracy-laptop:~$ sudo apt-get remove /opt/firstclass
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 
tracy@tracy-laptop:~$ sudo apt-get --purge remove firstclass
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firstclass
tracy@tracy-laptop:~$ 


What can I do?

---

### Post by SunnyRabbiera on 2008-07-30
Did you try to remove it in synaptic?

---

### Post by HarmonicaGoldfish on 2008-07-30
it does not appear when I do a search for 'firstclass' or 'first class' in synaptic.
(I think because I installed it manually?)

---

### Post by derrick81787 on 2008-07-30
> **HarmonicaGoldfish said:**
> it does not appear when I do a search for 'firstclass' or 'first class' in synaptic.
(I think because I installed it manually?)

It is probably because the package name isn't firstclass or anything like that (even though that's the program name).

Can you please paste the results of this command?
```
aptitude search fcc
```

I'm thinking the name of the package is fcc or fcc-*something*.

- Derrick

---

### Post by SunnyRabbiera on 2008-07-30
if its something you compiled then yeh the normal removal doesnt work.
But it looks like that app has a debian binary...

---

### Post by HarmonicaGoldfish on 2008-07-30
tracy@tracy-laptop:~$ aptitude search fcc
i   fcc                             - FirstClass is a communication and collabor
p   libgfccore-2.0-0-dbg            - GTK+ Foundation Classes Core - debug symbo
p   libgfccore-2.0-0c2a             - GTK+ Foundation Classes Core - shared libr
p   libgfccore-dev                  - GTK+ Foundation Classes Core - development
p   libgfccore-doc                  - GTK+ Foundation Classes Core - API referen
tracy@tracy-laptop:~$

---

### Post by geirha on 2008-07-30
If it was installed by a debian package, the following should show you the package name: ```
dpkg -S /opt/firstclass
```

---

### Post by derrick81787 on 2008-07-30
> **HarmonicaGoldfish said:**
> tracy@tracy-laptop:~$ aptitude search fcc
i   fcc                             - FirstClass is a communication and collabor
p   libgfccore-2.0-0-dbg            - GTK+ Foundation Classes Core - debug symbo
p   libgfccore-2.0-0c2a             - GTK+ Foundation Classes Core - shared libr
p   libgfccore-dev                  - GTK+ Foundation Classes Core - development
p   libgfccore-doc                  - GTK+ Foundation Classes Core - API referen
tracy@tracy-laptop:~$

I think this should solve your problem:

```
sudo aptitude remove fcc
```

Let me know if this helps.

- Derrick

*****Edit: ** ```
sudo apt-get remove fcc
``` will also work, but I like aptitude.

---

### Post by HarmonicaGoldfish on 2008-07-30
Thanks Derrick - seems to have done the job.

Mostly...I still have files and folders in my home folder. Do I just move those to trash? Or does more need to be done?

---

### Post by SunnyRabbiera on 2008-07-30
> **HarmonicaGoldfish said:**
> Thanks Derrick - seems to have done the job.

Mostly...I still have files and folders in my home folder. Do I just move those to trash? Or does more need to be done?

if they are not owned by root you can just wipe them out, you can tell if they are root folders if they have locks on them.

---

### Post by HarmonicaGoldfish on 2008-07-30
> **SunnyRabbiera said:**
> if they are not owned by root you can just wipe them out, you can tell if they are root folders if they have locks on them.

But is just trashing them enough to completely remove? The first class folder in opt had no lock on it either but it got removed when I followed Derrick's suggestion:

sudo aptitude remove fcc

---

### Post by derrick81787 on 2008-07-30
> **HarmonicaGoldfish said:**
> But is just trashing them enough to completely remove? The first class folder in opt had no lock on it either but it got removed when I followed Derrick's suggestion:

sudo aptitude remove fcc

You either want to move them to the trash and then empty the trash, or you want to just remove their whole directory with the rm -r command.

The reason that the files in /opt were removed is because they were actually the program installation files, so uninstalling the program removed them.  The files in your home folder are your own personal preferences, and uninstalling the program keeps those files there just in case you want to install the program again later and keep your preferences, or in case another program is using those files (which can happen for things like GNOME or GPG or something like that which are integrated with other programs, but this almost certainly isn't happening in this case).  Just deleting these files is perfectly alright and should get rid of it completely.

Keeping the preferences around in the users home folder can be annoying at times, but it's nice for certain situations.  If you install a program, remove it, and then install it again later, your preferences will be exactly the same is they were when you uninstalled it the first time, as long as you haven't deleted those files.  Also, if you have /home on a different partition, you can re-install Ubuntu from scratch (for example, if you wanted a clean install when upgrading) and even though it's just the default install, all your program preferences (including the GNOME/XFCE panels) will be exactly the same as they were before you reformatted.  That's pretty cool and can come in handy.

Anyway, for the answer to your question, just delete those files and you should be fine.

- Derrick

---

### Post by HarmonicaGoldfish on 2008-07-30
thanks for all of your help.

---

