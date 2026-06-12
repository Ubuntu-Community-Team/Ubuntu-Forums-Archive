---
title: "Failed kde 4.2 upgrade on 8.10"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by dutler on 2009-01-31
Hello, I have my kubuntu 8.10 workstation that I waited until early this morning to upgrade to the KDE 4.2 release packages.

The upgrade had some overwrite errors, but one all the packages got installed, things just aren't right :)

Upgrading KDE 4.1 to 4.2 on 8.10 I get the following errors:
> Unpacking replacement kde-window-manager ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb (--unpack):
 trying to overwrite `/usr/share/kde4/apps/kconf_update/plasma-add-shortcut-to-menu.upd', which is also in package kdebase-workspace-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace systemsettings 4:4.1.3-0ubuntu1~intrepid1 (using .../systemsettings_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb) ...
Unpacking replacement systemsettings ...
dpkg: error processing /var/cache/apt/archives/systemsettings_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/kcm_colors.so', which is also in package kdebase-workspace-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb
 /var/cache/apt/archives/systemsettings_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I then force overwrite and get:
> tom@sofia:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb
(Reading database ... 128862 files and directories currently installed.)
Preparing to replace kde-window-manager 4:4.1.3-0ubuntu1~intrepid1 (using .../kde-window-manager_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb) ...
Unpacking replacement kde-window-manager ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/kde4/apps/kconf_update/plasma-add-shortcut-to-menu.upd', which is also in package kdebase-workspace-data
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kdebase-workspace-bin
Setting up kde-window-manager (4:4.2.0-0ubuntu1~intrepid1~ppa5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
tom@sofia:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/systemsettings_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb
(Reading database ... 128877 files and directories currently installed.)
Preparing to replace systemsettings 4:4.1.3-0ubuntu1~intrepid1 (using .../systemsettings_4%3a4.2.0-0ubuntu1~intrepid1~ppa5_i386.deb) ...
Unpacking replacement systemsettings ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/kde4/kcm_colors.so', which is also in package kdebase-workspace-bin
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/kde4/kcm_style.so', which is also in package kdebase-workspace-bin
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/kde4/kcm_fonts.so', which is also in package kdebase-workspace-bin
Setting up systemsettings (4:4.2.0-0ubuntu1~intrepid1~ppa5) ...


No when I update:
> The following packages have been kept back:
  gwenview kate kdebase-plasma kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdeplasma-addons
  kdeplasma-addons-data ksysguard plasmoid-quickaccess python-kde4

What are these packages not updating?

Now, when I start kdm back up and log in, it shows kde 4.1 splash image and I have not windows decorations - ouch.

---

### Post by abn91c on 2009-01-31
did you run the upgrade this way?  [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

### Post by dutler on 2009-01-31
Hello abn91c, thanks for the quick reply. Yes I followed those directions. I didnt have koffice installed nor any extra plasmoids, so I add the repo, the key and update/upgrade.

---

### Post by tomdavidson on 2009-01-31
I have uninstalled and then reinstalled the kept back packages. apt did a lot of work downgrading and managing dependencies, then i had to upgrade again to catch libkdecorations4 and the window decorations were restored. 

i had to remove quanta...  will work on that.

thank you to mefisto__ *from the kubuntu  irc channel for your help.

---

### Post by Thorjelly on 2009-02-07
Excuse me, can you go over exactly everything you did to get it to work? I am having the exact same issue! I have reinstalled several times because neither apt-get -f install nor dpkg --reconfigure -a make any difference at all. Help?

---

### Post by dutler on 2009-02-08
no, i cant tell you exactly, sorry.

But....

After adding the repo for 4.2 (and the gpg key) I "apt-get update && apt-get upgrade".

Apt gave me a list of packages that were held back - this is the problem.

With kdm stoped, I .... :

Uninstalled the existing versions of the held back packages, this created some unmet dependencies, so I had all effected packages removed.

Once apt was satisfied, (apt-get -f install) I then reinstalled each of the packages I manually installed (except quanta - it had issues).

Still the window decoration was missing, although this time when kdm was started, the chances were visually apparent.

I ran apt-get upgrade and pick up two more packages, one being libkdecorations4. Restarted kdm and all has been well.

---

### Post by dutler on 2009-02-08
ps the #kubuntu irc channel is quite helpful - unlike some channles ( cough cough ... centos )

---

### Post by Altacus on 2009-02-08
I also had the same error while upgrading kde.  Oddly, I resolved the error by installing the kubuntu-desktop package, which strangely wasn't installed already.  Oh, and I stopped KDM when I did it.

Hope this helps.

---

### Post by alubu on 2009-02-09
I had the same error. I installed kubuntu 8.10. I followed the instructions on kubuntu site. I didnt remove any packages as i handnt installed any plasmoids.

The update fail as reported above.

I stopped kdm (/etc/init.d/kdm stop), but that killed the desktop so i restarted my machine. 

After the restart the keyboard no longer works.

Does anyone have explicit instructions to upgrade to kde 4.2 from a virgin install of kubuntu-8.10?

---

### Post by dutler on 2009-02-09
The keyboard does not work in KDE? or it doesn't work in Kubuntu at all? can you do alt+f2 to get a different console? (kdm/kde by default runs on f7).

Stopping kdm will "kill the desktop", this is the purpose. To stop running the software that you are updating - oft not an issue for Linux, but after doing heavy kde upgrades on a few machines... it "seems" to  go better with kdm stopped.

---

### Post by dabl on 2009-02-09
Check out the fix in post #6 here:

[http://kubuntuforums.net/forums/index.php?topic=3101546.0](http://kubuntuforums.net/forums/index.php?topic=3101546.0)

---

### Post by alubu on 2009-02-09
Nope, the ONLY keyboard related feature that works is ALT-F1 which expands the 'start menu'. I cannot get a console with ALT-<anything>. 

I'm reinstalling to fix the keyboard, but would love to try out KDE 4.2 and not sure how to....

---

### Post by dutler on 2009-02-09
sorry.... crl+alt+f2 ....

---

### Post by dutler on 2009-02-09
dabl: force the overwrite clearly has been the trick for some... it didnt do me any good. still, i should have remembered to mention it when i posted my solution.

---

