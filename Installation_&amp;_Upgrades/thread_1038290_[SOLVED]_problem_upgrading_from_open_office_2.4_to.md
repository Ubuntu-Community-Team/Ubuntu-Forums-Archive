---
title: "[SOLVED] problem upgrading from open office 2.4 to 3.0"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by pmcginley on 2009-01-12
hi all - i've had open office 3.0 running smoothly on my machine for several months, but after a meltdown and total reinstall of ubuntu and all software i've been having problems.  2.4 worked fine after the reinstall, but after trying to update again to 3.0 nothing's worked.  i get this message if i try to run oo from a terminal:

/usr/lib/openoffice/program/soffice: /usr/lib/openoffice/program/libuno_sal.so.3: version `UDK_3.8' not found (required by /usr/lib/openoffice/program/../basis-link/program/libsofficeapp.so)
/usr/lib/openoffice/program/soffice: /usr/lib/openoffice/program/libuno_sal.so.3: version `UDK_3.8' not found (required by /usr/lib/openoffice/program/../basis-link/program/../ure-link/lib/libuno_cppuhelpergcc3.so.3)
/usr/lib/openoffice/program/soffice: /usr/lib/openoffice/program/libuno_sal.so.3: version `UDK_3.8' not found (required by /usr/lib/openoffice/program/../basis-link/program/libsvtli.so)
/usr/lib/openoffice/program/soffice: /usr/lib/openoffice/program/libuno_sal.so.3: version `UDK_3.8' not found (required by /usr/lib/openoffice/program/../basis-link/program/libtlli.so)
/usr/lib/openoffice/program/soffice: /usr/lib/openoffice/program/libuno_sal.so.3: version `UDK_3.8' not found (required by /usr/lib/openoffice/program/../basis-link/program/libsaxli.so)

i've uninstalled, reinstalled, tried to install from synaptic, command line, and applications/add/remove.  i've tried reinstalling this libuno_sal.so.3 from synaptic (or as close as i could find - uno-libs3) but to no avail.  i'm running ubuntu 8.10.  any ideas?

this is my first post to the forum - it was a great resource for me while getting myself going with ubuntu - thanks!

---

### Post by ajgreeny on 2009-01-12
How have you tried to do the upgrade and where did you get the .debs from to do it?

---

### Post by dustyg54 on 2009-01-12
I'm new to Ubuntu and really like it. I used OOo3 on Win XP and liked it as well. I can't figure out how to install/upgrade from OOo2.4 to 3.0 at all  :confused:

---

### Post by ajgreeny on 2009-01-12
There are some guides to this but you just need to get the .debs from openoffice website in a large (140MB) zip file and extract them to a folder in which will be a folder called DEBS.  You then navigate in terminal to that DEBS folder and run ```
sudo dpkg -i *.deb
```The executable will be in /opt, and you will need to make your own launcher to it using the command ```
/opt/openoffice.org3/program/soffice %U
```though if yopu remove OOo 2.4, you can add shortcuts to your menu by running the deb file in the subfolder of the DEBS folder I mentioned earlier.

---

### Post by pmcginley on 2009-01-12
> **ajgreeny said:**
> How have you tried to do the upgrade and where did you get the .debs from to do it?

i had already added 

[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main 

to my software sources list, so it was actually the upgrade manager that launched the upgrade itself.  like i mentioned, first time around that worked great, but after my reinstall something went wrong and i can't seem to get out of it...

for dustyg - if i've got this right you should be able to add the above line to your software sources (system/administation/software sources - click 'third party software, then add), and then your update manager will (eventually) propose the necessary updates.  but maybe you shouldn't take my work for it, mine's broken...  ;-)

---

### Post by pmcginley on 2009-01-12
> **ajgreeny said:**
> There are some guides to this but you just need to get the .debs from openoffice website in a large (140MB) zip file and extract them to a folder in which will be a folder called DEBS.  You then navigate in terminal to that DEBS folder and run ```
sudo dpkg -i *.deb
```The executable will be in /opt, and you will need to make your own launcher to it using the command ```
/opt/openoffice.org3/program/soffice %U
```though if yopu remove OOo 2.4, you can add shortcuts to your menu by running the deb file in the subfolder of the DEBS folder I mentioned earlier.

actually, i already downloaded those debs, but didn't quite know what to do with them, apart from try to launch them all individually, and in the right order, which seemed foolish.

but forgive my ignorance - i don't know how to navigate anywhere in terminal.  could you spell it out for me?

---

### Post by pmcginley on 2009-01-12
ok, i found this thread, and followed caleb12's instructions for installing the debs downloaded directly from OOo, and that seems to have worked:

[http://ubuntuforums.org/showthread.php?t=957453](http://ubuntuforums.org/showthread.php?t=957453)

thanks!

---

### Post by dustyg54 on 2009-01-13
I did what you said about the Software Sources and it worked!  I'm now 3.0!  ^^   Thanks!

---

