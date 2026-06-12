---
title: "Evolution not working with Exchange Server 2003"
date: 2008-10-19
forum: General Help
---

### Post by r042wal on 2008-10-19
I am trying to find alternate solutions for my Windows customers and thought I had found it with Unbuntu 8.04 and Evolution 1.22.3.1.

All my customers have an Exchange Server and I have an Exchange Server at my office as part of my test platform.  No matter what I try, Evolution always returns one of several errors:

error while scanning folders in "Exchange server
Exchange accoung is offline

I can access my exchange account in Ubuntu using OWA.  It also works in Outlook 2003.  When I set up the mail 'receive' properties and hit the 'authenticate' button, every thing works fine.

Then it might say "no mailbox for user myname on mail.mydomain.com.  I have also substituted the public IP address fro my mail server instead of the MX record (which resolves to the server) but it makes no difference.

I hae tried the domain in front of the username.  The NetBIOS name for my domain is CONTECH.  The Active Directory FQDM is ct.local.  Neither of these work for DOMAIN\username

I really want this to work and would appreciate any suggestions.  Thanks.

Edit:
I have tried creating new users in Ubuntu and then setting up Evolution to connect to other Exchange mail servers (customers) across the Internet instead of on my LAN.  I get the identical errors: "error while scanning folders in "Exchange Server"

Edit:
Reinstalled Ubuntu.  Set up Evolution and Exchange with default package in 8.04 distro.  Ran all updates except Evolution updates.  Rebooted.  Installed remaining Evolution updates.  Exchange connection works.

---

### Post by Skerit on 2008-10-21
It doesn't work for me, neither.

I know I have to use a domain in front of my username.
When I don't, it spews out a lot of white lines in the terminal and takes 2 minutes to tell me it failed. (Could not connect to server. Make sure the URL is correct and try again)

When I do use the domain in front of my username (w2k\) it immediately tells me it failed, but a bit more hopeful: Could not find Exchange Web-storage system. (Should OWA run on a different path, ...)

So it does login, it's unable to get the info?

I do know our webmail uses the ISA security thing.

---

### Post by r042wal on 2008-10-21
As I mentioned in my edited post, by reinstalling Ubuntu and setting Exchange up with the earlier version of Evolution (2.1???) it worked.  Then I ran the updates and I think the latest Evolution that Ubuntu installs in 2.22 or 2.23.  It worked by upgrading the older version of Evolution and keeping all the original settings.

---

