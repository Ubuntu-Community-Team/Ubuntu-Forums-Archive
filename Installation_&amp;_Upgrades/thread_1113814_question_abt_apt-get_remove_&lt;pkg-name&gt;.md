---
title: "question abt apt-get remove &lt;pkg-name&gt;"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by siddukirk on 2009-04-02
Hi Guys,

I apt-get removed apache2 from my machine and it went fine like shown below but then what surprises me is that i still see apache2 directory sitting under  /etc and /etc/init.d/apache2 restart is still active (working)

please tell me what exactly is happening in the remove <pkg> 

and all my conf files are messed up so i want to go for a fresh installation . what do i do ?

Thanks in advance 
siddu


apt-get remove apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopencdk10-dev apache2-utils libgnutlsxx13 libtasn1-3-dev libgpg-error-dev libgcrypt11-dev apache2.2-common libgnutls-dev
  cabextract liblzo2-dev apache2-mpm-worker
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 205829 files and directories currently installed.)
Removing apache2 ...

/etc/init.d/apache2 
 * Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean}
root@azingo-desktop:~# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                   apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                            [ OK ]

---

### Post by mcduck on 2009-04-02
"apt-get remove" removes the package only, but leaves all system-wide & personal configuration files.

"apt get remove --purge " removes both the package and system-wide configuration files, but leaves personal configuration files (the dotfiles in user's home directory).

In the same way, you'll find that Synaptic has two options, "Mark package for Removal" and "Mark Package for Complete Removal"

---

### Post by siddukirk on 2009-04-02
Thanks Dude :)

---

