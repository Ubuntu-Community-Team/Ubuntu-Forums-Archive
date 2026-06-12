---
title: "Switching from Desktop to Server install"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by earthmeLon on 2009-07-12
I have the Desktop version of Ubuntu installed on my laptop, but I would like to add the server kernel or a server mode option to my grub list.

I am not sure if I can do this by adding a new entry to grub with some extra arguments, or if I need to download and add a new kernel.


If anybody could get me started on the right path or give any information about this, I'd very much appreciate it.


Thanks

---

### Post by Hobgoblin on 2009-07-12
AFAIK the server version is simply the desktop version without the desktop (and associated apps).

Why do you need (or think you need) the server version?

---

### Post by earthmeLon on 2009-07-12
> **Hobgoblin said:**
> AFAIK the server version is simply the desktop version without the desktop (and associated apps).

Why do you need (or think you need) the server version?

As the OP said, I would like to run Ubuntu as a server on my laptop.  I need information on how to do this.

---

### Post by Hobgoblin on 2009-07-12
Ah, I don't think you understand the meaning of server edition.

The server edition just installs Ubuntu with no GUI (and none of the desktop apps)

You can install all the server apps to your desktop edition, no need to have separate installs.

So, what is it you want to do?  A webserver?  A fileserver? A printserver?

---

### Post by VastOne on 2009-07-12
> **earthmeLon said:**
> As the OP said, I would like to run Ubuntu as a server on my laptop.  I need information on how to do this.

As hobgoblin said, your desktop Ubuntu is easy to bring up to a server by adding the server components.

You can either download the server ISO and install a new side by side setup with you current environment or add the following:

Web

    * Apache 2.2 event/prefork/worker/dev
    * Tomcat 6

Database

    * MySQL 5 (5.1 in Universe)
    * PostgreSQL 8.3

Email

    * Dovecot 1.1
    * Postfix 2.5
    * Exim 4.69
    * SpamAssassin 3.2
    * ClamAV 0.95
    * amavisd-new 2.6

Languages

    * PHP 5.2
    * Perl 5.10
    * Python 2.6
    * Gcc 4.3
    * Ruby 4.2

Networking

    * LTSP 5.1
    * Samba 3.3
    * OpenLDAP 2.4 (cn=config)
    * OpenVPN 2.1
    * FreeRadius 2.1

Monitoring

    * Munin 1.2
    * Nagios 3

Backup

    * Bacula 2.4
    * BackupPC 3.1

Package management

    * Aptitude 0.4
    * APT 0.7
    * Dpkg 1.14

Security

    * AppArmor 2.3
    * Iptables 1.4
    * ufw 0.27

Clustering

    * Ocfs 2
    * Gfs 2
    * RH-Cluster 2
    * DRDB 8

Virtualization

    * KVM 84
    * Libvirt 0.6
    * Virt-Manager 0.6

Storage

    * Lvm 2
    * aoetools 26
    * openiscsi 2.0

Power Management

    * Nut 2.4
    * pwrkap 7.3

---

### Post by earthmeLon on 2009-07-12
Alright guys, I think you're totally misunderstanding the question.

I want to run Ubuntu server edition on my laptop that has Desktop edition running.  It's that simple.  I want whatever happens when you run "Server edition" of Ubuntu (ie: No gui, no need for login for services to start) to happen.

Do I need a new kernel or do I need to add some flags to the end of my grub config or what?


Edit:

I know what an httpd/ftpd is.  I have them running.  That's not the point here

---

### Post by earthmeLon on 2009-07-12
I would like to have two options at grub:

1) Desktop mode (as it is now)
2) Server mode (services start up and there is no gui)

---

### Post by VastOne on 2009-07-12
> **earthmeLon said:**
> Alright guys, You're totally misunderstanding the question.

I want to run Ubuntu server edition on my laptop that has Desktop edition running.  It's that simple.  I want whatever happens when you run "Server edition" of Ubuntu (ie: No gui, no need for login for services to start) to happen.

Do I need a new kernel or do I need to add some flags to the end of my grub config or what?


Edit:

I know what an httpd/ftpd is.  I have them running.  That's not the point here

Get the ISO server disk of Ubuntu

Install it

This will add a server install to your grub

Boot into the server install

Then add the desktop environment to it using apt-get (if you want it!)

Then you will have a server install with a desktop environment

Go to the Ubuntu site and it is filled with this information

Or search google for Ubuntu + server + desktop

Bottom line is you will have to do some work to get what you want

---

### Post by earthmeLon on 2009-07-12
Thanks for the suggestion

I really don't want to have to install the server iso.  I'd like to keep my current installation.  Is there any way I could just modify/change something and then keep x from starting and having my servers run before anybody even logs into the laptop.  I would like to be able to turn the laptop on, it boot up, and me to be able to SSH into it, with only touching the power button.

---

### Post by VastOne on 2009-07-12
> **earthmeLon said:**
> I'm really just trying to figure out where I can find some information on using different kernels.

Installing the server kernel is using a different kernel.

Using a different kernel means setting one up or using make to do it

Kernelcheck in this forum may offer you other options, you may want to check it out

---

### Post by Hobgoblin on 2009-07-12
> **earthmeLon said:**
> I would like to have two options at grub:

1) Desktop mode (as it is now)
2) Server mode (services start up and there is no gui)

OK then, though I'm at a loss to see what you are achieving.  Im not sure what (if any) difference there is between the desktop and server kernel.

Download the server ISO, boot from it, install it alongside your current install.  I assume it will give you the option resize your current partitions to create space, if not then boot from a desktop liveCD and make some space with the partition editor.

---

### Post by earthmeLon on 2009-07-12
Is there a way to install a new version of Ubuntu without removing my configuration?  That might be a solution.


I wish I knew what the difference in the two actually were.

---

### Post by VastOne on 2009-07-12
> **earthmeLon said:**
> Is there a way to install a new version of Ubuntu without removing my configuration?  That might be a solution.

_**Yes. **_

Again,installing the server kernel sets up a new kernel that will be in your grub as a new boot option an your original one is preserved.

---

### Post by VastOne on 2009-07-12
> **Hobgoblin said:**
> OK then, though I'm at a loss to see what you are achieving.  Im not sure what (if any) difference there is between the desktop and server kernel.

Download the server ISO, boot from it, install it alongside your current install.  I assume it will give you the option resize your current partitions to create space, if not then boot from a desktop liveCD and make some space with the partition editor.

+1 for OP make sure you understand this

---

### Post by VastOne on 2009-07-12
> **earthmeLon said:**
> Is there a way to install a new version of Ubuntu without removing my configuration?  That might be a solution.


I wish I knew what the difference in the two actually were.

I outlined that for you with my first post here it is again

Web

* Apache 2.2 event/prefork/worker/dev
* Tomcat 6

Database

* MySQL 5 (5.1 in Universe)
* PostgreSQL 8.3

Email

* Dovecot 1.1
* Postfix 2.5
* Exim 4.69
* SpamAssassin 3.2
* ClamAV 0.95
* amavisd-new 2.6

Languages

* PHP 5.2
* Perl 5.10
* Python 2.6
* Gcc 4.3
* Ruby 4.2

Networking

* LTSP 5.1
* Samba 3.3
* OpenLDAP 2.4 (cn=config)
* OpenVPN 2.1
* FreeRadius 2.1

Monitoring

* Munin 1.2
* Nagios 3

Backup

* Bacula 2.4
* BackupPC 3.1

Package management

* Aptitude 0.4
* APT 0.7
* Dpkg 1.14

Security

* AppArmor 2.3
* Iptables 1.4
* ufw 0.27

Clustering

* Ocfs 2
* Gfs 2
* RH-Cluster 2
* DRDB 8

Virtualization

* KVM 84
* Libvirt 0.6
* Virt-Manager 0.6

Storage

* Lvm 2
* aoetools 26
* openiscsi 2.0

Power Management

* Nut 2.4
* pwrkap 7.3

---

### Post by earthmeLon on 2009-07-12
Okay guys.   This is what I've done so far:

I removed networkmanager, added wpa_supplicant for wireless connection at boot.

I removed gdm from startup using rcconf.


This has achieved my main goal :D


Now I just want to be able to boot with gdm or without gdm from different grub entries, if that's possible

---

### Post by Hobgoblin on 2009-07-13
> **earthmeLon said:**
> 
Now I just want to be able to boot with gdm or without gdm from different grub entries, if that's possible

Did you look at session options on the login screen?

A long time since I looked (probably Hardy or thereabouts) but I'm sure there used to be the option of starting with just the terminal.

With and without GDM is nothing to do with the kernel BTW.  It's also noting to do with being a desktop/server.  Lots of us have used desktops with no GUI in the past ;)

---

### Post by ankitgoel9999 on 2009-07-13
you can install new server and take backup of your old files

---

### Post by VastOne on 2009-07-13
> **Hobgoblin said:**
> Did you look at session options on the login screen?

A long time since I looked (probably Hardy or thereabouts) but I'm sure there used to be the option of starting with just the terminal.

With and without GDM is nothing to do with the kernel BTW.  It's also noting to do with being a desktop/server.  Lots of us have used desktops with no GUI in the past ;)

Ain't that the truth!

there is the term option when booting with recovery option and a ctrl + alt + f1 to tty and then killing gdm would be effective too.

---

