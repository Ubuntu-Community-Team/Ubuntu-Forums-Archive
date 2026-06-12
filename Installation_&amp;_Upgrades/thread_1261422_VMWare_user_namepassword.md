---
title: "VMWare user name/password"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by brianmahler on 2009-09-08
Well I finally got VMware Server installed on Unbuntu 9.0.4. server edition.

But when I try to login to the VMware web interface it prompts me for a user name and password.  These credential I don't know or have.   What are these or how can i reset them?

There is only 1 account on the server,  I tried those credentials with no success (yes I can login into the server itself).  I also tried several from various articles posted on the web, these credentials include root/blank, root/root,  user/user,  the servers command line  user id/password.  

One article even suggested I change the root password. but the command provided in the article did not work.

Any help is appreciated.

---

### Post by oaklad on 2009-09-24
You do not say how Ubuntu Server was created. If it was from an appliance  provided on the VM Ware Fusion web site there should be a text file which provides a user name and password.

I recently installed the desktop version of 9.0.4  as an appliance and there was a text file included which provide the required information.

Check around to see if there was a info or text file. Mine was:

Brought to you by Chrysaor.info ([http://chrysaor.info](http://chrysaor.info))
Problems or feedback: [http://chrysaor.info?page=contact](http://chrysaor.info?page=contact)
Like the image? Make a donation: [http://chrysaor.info?page=donations](http://chrysaor.info?page=donations)

VMware info
 - Date of creation: 8 May 2009
 - CPUs		: 1
 - RAM		: 512 MB
 - Networking	: NAT
 - Harddisk	: 8 GB SCSI (expanding)
 - VMware tools	: Installed

OS info
 - OS		: Ubuntu 9.04 Desktop
 - Installation	: Standard
 - Hostname	: ubuntu904desktop
 - Patches	: till date of creation
 - IPv4 address	: dhcp
 - IPv6 address	: dhcp
 - DNS name	: none
 - Nameserver	: dhcp
 - Route	: dhcp
 - Keyboard	: US_intl

Login credentials
 - Root password: not set (use sudo to execute commands as root)
 - User login	: user
 - User password: chrysaor.info

---

