---
title: "Alternative CD for Server 64 9.04?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by california-ken on 2009-04-25
I upgraded Desktop 64 to V 9.04 on my laptop using the "Update Manager".  As far as I can tell the upgrade was error-free.

I tried to update Server 64 from 8.10 to 9.10 using "Update Manager".  I had installed the "gnome-desktop-environment" some time ago.  Reading many messages of woe from users trying to upgrade a "pure" text-only installation of Server, I thought I could "outsmart" the system by using the Update Manager.  No such luck!!!

The upgrade seemed to go OK until the virtual end of the process. All 1067 files were fetched although the process was extremely slow due to the load on the Ubuntu servers.  Near the end of the file installation process, I received some error messages about not being able to install SLAPD, the LDAP server.
That was just the start of it!

When I rebooted the machine, I found that the NVIDIA driver was not found, the scrolling script said the file system had errors, the screen went totally black and mouse/keyboard response was gone.  

Using a root terminal session I downloaded the latest NVIDIA drivers and installed them.  No luck!

After saying all of that, my current question is:  "Is there an alternative installation disk for Server 64 V9.10?"  If so, where can I download an image?  My last resort my be to try to rerun the update from a alternative CD is one exists.

Although my server setup is used only for a home network, I have spent many hours getting V8.10 configured and software added and I don't want to have to resort to using the V9.10 normal install disk to totally over-write my Ubuntu partitions?

Any ideas/suggestions?????

Ken

---

### Post by cariboo on 2009-04-25
You can use the sever installation cd to upgrade your sever installation, as always backup your important files, and configuration files. THe server iso is available [here]("http://noncdn.releases.ubuntu.com/releases/9.04/")

---

