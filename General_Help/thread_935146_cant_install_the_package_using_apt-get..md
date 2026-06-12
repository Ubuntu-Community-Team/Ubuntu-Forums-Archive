---
title: "cant install the package using apt-get."
date: 2008-10-01
forum: General Help
---

### Post by Julius1988 on 2008-10-01
i am in recovery mode,gnome login screen is failing to start....any package i install using apt-get is reported with the following errors

> 
Reading package lists...
Building dependency tree...
Reading state information...
grdesktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
14 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up desktop-base (4.0.3) ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
dpkg: error processing desktop-base (--configure):
 subprocess post-installation script returned error exit status 127
Setting up dia-common (0.96.1-3) ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_option_context_new
dpkg: error processing dia-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of dia-gnome:
 dia-gnome depends on dia-common (= 0.96.1-3); however:
  Package dia-common is not configured yet.
dpkg: error processing dia-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm-themes:
 gdm-themes depends on desktop-base (>= 0.3.15); however:
  Package desktop-base is not configured yet.
dpkg: error processing gdm-themes (--configure):
 dependency problems - leaving unconfigured
Setting up seahorse (2.20.1-0ubuntu1) ...
update-mime-database: symbol lookup error: update-mime-database: undefined symbol: g_log_set_default_handler
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on seahorse (>= 1.0.1); however:
  Package seahorse is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
Setting up gnumeric-common (1.7.11-1ubuntu3.1) ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_option_context_new
dpkg: error processing gnumeric-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnumeric:
 gnumeric depends on gnumeric-common (= 1.7.11-1ubuntu3.1); however:
  Package gnumeric-common is not configured yet.
dpkg: error processing gnumeric (--configure):
 dependency problems - leaving unconfigured
Setting up planner (0.14.2-2ubuntu2) ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
dpkg: error processing planner (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-office:
 gnome-office depends on dia-gnome; however:
  Package dia-gnome is not configured yet.
 gnome-office depends on gnumeric (>= 1.4.0); however:
  Package gnumeric is not configured yet.
 gnome-office depends on planner; however:
  Package planner is not configured yet.
dpkg: error processing gnome-office (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-cups-manager (0.31-3ubuntu5) ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_option_context_new
dpkg: error processing gnome-cups-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome:
 gnome depends on gnome-desktop-environment (= 1:2.18.3ubuntu2); however:
  Package gnome-desktop-environment is not configured yet.
 gnome depends on gnome-office (= 1:2.18.3ubuntu2); however:
  Package gnome-office is not configured yet.
 gnome depends on gdm-themes; however:
  Package gdm-themes is not configured yet.
 gnome depends on gnome-cups-manager (>= 0.30); however:
  Package gnome-cups-manager is not configured yet.
dpkg: error processing gnome (--configure):
 dependency problems - leaving unconfigured
Setting up grdesktop (0.23-3) ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
dpkg: error processing grdesktop (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tsclient (0.148-3ubuntu1) ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_option_context_new
dpkg: error processing tsclient (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 desktop-base
 dia-common
 dia-gnome
 gdm-themes
 seahorse
 gnome-desktop-environment
 gnumeric-common
 gnumeric
 planner
 gnome-office
 gnome-cups-manager
 gnome
 grdesktop
 tsclient
]

---

### Post by russlar on 2008-10-01
it sounds like you've got some seriously hosed packages. dpkg-reconfigure gdm might fix your login screen, but it might be worth running dpkg-reconfigure -a to fix _all_ of them (WARNING: be careful when doing this. dpkg-reconfigure -a is very powerful. it will fix your system, if odne right. however, if done wrong, it will render your system useless, though it does sound like it's already in this state.)

---

### Post by Julius1988 on 2008-10-01
i did what u asked me to do."dpkg-reconfigure gdm"
this is what happend...
*Reloading gnome display manager configuration
*Change will take effect when all current sessions have ended
invoke-rc.d initscript gdm, action "reload" failed.
gtk_update_icon_cache:symbol lookup error:gtk_update_icon_cahe:undefined symbol:g_option_context_new.

---

### Post by Julius1988 on 2008-10-01
if i upgrade to hardy using the alternate cd, will the problem be resolved.

---

### Post by lintoon on 2008-10-01
Why are you in recovery mode?  Any more information on how you arrived at this point will help with the troubleshooting.

---

### Post by lintoon on 2008-10-01
I would think so.  Why not just bite the bullet and do a clean install.  Use your live cd to boot the pc and backup your files and continue with the install.

---

### Post by Julius1988 on 2008-10-01
i updated my system, i was not able to login i.e the login terminal never showed up. i think, i messed up with some imortant packages so i am not able to reconfigure gdm and many other essential packages.

---

### Post by lintoon on 2008-10-01
I'm not an expert with ubuntu but I had a similar issue.  My laptop lost power while installing updates and I couldnt use synaptic or apt-get. dpkg-reconfigure -a fixed it for me.

---

### Post by lintoon on 2008-10-01
If you install/upgrade your ubuntu it will be up and running in half an hour to an hour.  Depends how important your existing set up is to you.  Don't forget to ensure you have all your files backed up if you go that route.  If I'm not mistaken you can simply install and you have the option to keep you current partitions which will keep your home folder intact.  I've certainly done it in the past.  It's just a pity I can't remember the exact process.  It was quite simple though.

---

### Post by Julius1988 on 2008-10-01
anyway Thanks man,  I was afraid it would end this way.

---

