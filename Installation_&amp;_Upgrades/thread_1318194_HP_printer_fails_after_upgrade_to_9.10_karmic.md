---
title: "HP printer fails after upgrade to 9.10 karmic"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by klaasvg on 2009-11-07
I am a confident user of Ubuntu but have little experience with trouble shooting. After upgrade to 9.10, my HP D6160 printer fails completely and is not recognized anymore. I can still use the printer on my 9.04 machine.
The packages hplip 3.9.8-1ubuntu2 is installed, I also installed hplip-cups but this does not solve the problem. When I want to print, I can only choose to print to file, the HP printer is simply not present anymore!
I consider this as a nasty bug. Is there a solution?
REgards, Klaas

---

### Post by coffeecat on 2009-11-07
Have you tried reinstalling it through System > Administration > Printing?

---

### Post by klaasvg on 2009-11-07
> **coffeecat said:**
> Have you tried reinstalling it through System > Administration > Printing?

I tries, but this option offers no possibility to install a printer. The menu-item Server-New-Printer is greyed out. Previously I did not need to install the printer explicitly.

---

### Post by coffeecat on 2009-11-07
> **klaasvg said:**
> The menu-item Server-New-Printer is greyed out.

Puzzling. That does suggest a system problem, although quite what I can't imagine at the moment.

> **klaasvg said:**
> Previously I did not need to install the printer explicitly.

Yes, indeed. Normally Ubuntu is first-class in detecting and installing printers almost before you can draw breath. I was hoping that this might have been some sort of fail-safe procedure in the dist-upgrade to prevent conflict between different CUPS and driver versions. A faint hope - I was wrong.

There's one other thing you can try. In firefox, type "localhost:631" in the address bar (no quotes) and press return. That takes you to the CUPS configuration page. It's a bit more feature-full than the Printing utility. Click on the administration tab. Are you able to add a printer there?

---

### Post by klaasvg on 2009-11-07
I tried, but... no server is running here!

Unable to connect
Firefox can't establish a connection to the server at localhost:631.
:mad::mad::mad:

I consider a fresh install of 9.10, because I always have trouble with upgrades... I first wait for more suggestions.

---

### Post by coffeecat on 2009-11-07
> **klaasvg said:**
> Firefox can't establish a connection to the server at localhost:631.

...indicates a serious problem with CUPS. CUPS (common unix printing system), by the way, uses a client-server model.

> **klaasvg said:**
> I consider a fresh install of 9.10, because I always have trouble with upgrades... I first wait for more suggestions.

You're probably wise, but before you do, open Synaptic, look for all the installed packages cups-something and mark them all for reinstallation. It's just possible that something went wrong with upgrading cups-common or cups itself during the dist-upgrade.

If that fails and you decide to do a fresh install, while you're running the live 9.10 CD, plug the printer in, switch it on and see whether it gets detected. A vanilla install comes with the hplip package which provides drivers for many/most HP printers - so the live CD may be able to drive your printer without having to install any extra drivers. You may not need the hplip-cups package. My HP OfficeJet 6310 prints just fine in Karmic without the hplip-cups package.

Good luck!

---

### Post by Irony on 2009-11-07
Try deleting .hplip file in your home folder.

---

### Post by klaasvg on 2009-11-07
After I started cups using the buut-up manager, I can access localhost:631, so I will try a bit further to install the printer... 
But strange that this service is disabled by default!!??

---

### Post by coffeecat on 2009-11-07
> **klaasvg said:**
> But strange that this service is disabled by default!!??

Ah! Startup services. *facepalm*. I should have thought of that. :(

It seems as though cups is not being started during the bootup sequence. I'm afraid it's years since I rummaged around in startup scripts, so I'm very rusty. Have a look at this page:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Now have a look in /etc/rc2.d . Do you have a symlink in there called S50cups? Does it link to /etc/init.d/cups ?

---

### Post by klaasvg on 2009-11-07
OK after reinstalling the CUPS packages AND starting the CUPS server my printer is recognized and I can print again!!!
I keep finding it strange that the CUPS server was not running initially. Also my Apache webserver was not running anymore after upgrading... and the Administration-Services menu-item had dissappeared after upgrading!

I installed the Bootup-Manager tool after another tip to start it again, I wonder what has happened this upgrade that so many things have changed... I heared it has to do with runlevels....
But anyway my printer works again :) Thx.

---

### Post by klaasvg on 2009-11-07
Oh and is the ~/hplip.conf file still in use? And the hplip packages? Or can they be removed?
This is the content of the hplip.conf file:
[last_used]
printer_name = Photosmart-D6100-series
device_uri = hp:/usb/Photosmart_D6100_series?serial=MY68MD81C004SH

[installation]
date_time = 06/22/2009 11:23:02
version = 3.9.6

---

### Post by klaasvg on 2009-11-07
> **coffeecat said:**
> 
Now have a look in /etc/rc2.d . Do you have a symlink in there called S50cups? Does it link to /etc/init.d/cups ?

Yes it is there now, but only after starting the service using the bootup-manager! After stopping the service, the symlink dissapears! So the bootupmanager indeed controls this directory and the hyperlinks in it!
:D:D:D

---

### Post by coffeecat on 2009-11-07
> **klaasvg said:**
> After stopping the service, the symlink dissapears!

:shock:

Well - I think we're getting somewhere. I've looked in three different clean installs of Karmic I have here, and that symlink is in all three, and I don't use bootupmanager. Furthermore, one of the three installations I haven't yet installed any printers. So it seems as though that symlink *ought* to be there all the time. If it was there, cups would be started on bootup and you wouldn't have to use bootupmanager.

Perhaps if you create the symlink yourself that will solve the problem - unless you are going to do a clean install. And it sounds as though it was the dist-upgrade that's responsible for this cups problem and the problems with the other services you mentioned.

For which I thank you for starting this thread - I've learned something useful. A few months ago I introduced a relative to Ubuntu by installing Jaunty as a dual-boot with Windows. :cool: She very quickly stopped using Windows. :) She was talking about an upgrade to Karmic, but after your experience (and others I have read about) I'm going to tell her that it will be far better to do a clean install.

---

### Post by klaasvg on 2009-11-07
I still consider doing a clean install, but the problem is you need to install all apps again, though there are not so many so it is probably a good idea. The bootupmanager is a third-party tool I installed because I am always afraid of manually editing config files.... ;)
Though I will definiately continue using Ubuntu, i am pretty disappointed in this upgrade procedure. MY webserver Apache also ceased working after the upgrade, therefore I installed the bootupmanager. I guess this has to do with the transition to the new runlevel system???
I got into this because the Services application was gone after the upgrade without any explanation about how to start and stop services in 9.10

There are other strange issues, like keyboard indicator lights that go on and off when typing specific letters!!!

---

### Post by coffeecat on 2009-11-07
> **klaasvg said:**
> i am pretty disappointed in this upgrade procedure.

I think a lot of people are. The only consolation is that it's far, far worse doing a Windows version upgrade. I would never, **ever** think of doing that although, to be fair, I rarely boot into Windows these days. And that's only to remind myself why I use Linux. :lol:

When I upgraded from Tiger to Leopard on my Mac Mini, I chose an Archive and Install rather than a version upgrade because even Apple isn't immune to major borks when the OS is upgraded. But when I bought Snow Leopard, it was an upgrade or nothing - no archive and install. So far it's been OK, but for Ubuntu I think I'll stick with clean installs. After all...

> **klaasvg said:**
> the problem is you need to install all apps again

... but at least they're free. :p

---

### Post by BlackBuffalo on 2010-05-05
I had this same exact problem upgrading from 9.10 karmic to 10.4 lucid.  The gnome print server wouldn't start and all my printers disappeared.  Reinstalling all the cups packages and restarting the system worked marvelously.  All my printers are back.  There must have been some problem upgrading the cups server that reinstalling fixed.  Thanks for the idea to reinstall the cups packages.

---

### Post by Amzer zo on 2010-05-05
Same here.  I did a clean install of 10.04 and had the printer disappear on me twice already (never been a problem with 9.10).  Each time I reinstalled cups and got the printer to show up again.  If it keeps on happening I will need a better solution than the cups re-install method...

---

### Post by klaasvg on 2010-05-06
The moral of this story: never use the distribution upgrade function, but always do a clean install when you want to upgrade to a new distribution. I had onther problems which were only solved after a clean install. Also due to settings in the home dir that were to no avail anymore in the new dist. I plan to upgrade to 10.04 lucid but waint until I really can take at least a day off to back up, install the new dist and then all applications and packages. It is easy to make a list of installed applications but less easy to fine-tune with all additional packages...
I hope that there is finally a well-supported way to switch on and off services in the new dist! :D

---

### Post by finito on 2010-05-07
I fixed this with a simple mark for re-installation on synaptic.

Thanks.

Please mark as Solved.

For some saying it's better to do clean install I agree, but when you have a lot of data and settings, upgrading seems so much easier and with a community backing like this, I shall not fear the upgrade.

I had this problem when I upgraded from 9.10 to 10.04.

---

