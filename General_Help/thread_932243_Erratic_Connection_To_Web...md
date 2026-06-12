---
title: "Erratic Connection To Web.."
date: 2008-09-28
forum: General Help
---

### Post by TheWizardofOdds on 2008-09-28
Hi,
 I've recently installed Ubuntu onto my new PC which came with Vista. Now, Linux is the sole OS. I'm new to all this, and may well have erased Vista prematurely, but I did plenty of research into Linux beforehand and am/was confident in its abilities.

The problem that I have, is to me at least, quite strange. My connection to the web is erratic. I can log on and it all works very well, and then I use the PC the next morning and there is a page saying 'not connected to server'. I have checked my internet connection and it is working no problem at all. I use a BT voyager 210 ADSL Router. I can switch off the PC turn it back on 30 mins later and it all works very well.

I installed Ubuntu 8.04 Hardy Heron and Firestarer firewall.

I would appreciate any help/suggestions on this matter.

Thanks, David.

---

### Post by artships on 2008-09-28
Connecting to the internet involves feeding a browser a name, say, google.com, and having that name converted to an address that your browser needs inorder to find the page you want.  In other words, the name is resolved to an IP address.  The servers that do that are listed in /etc/resolv.conf .  "man resolver" will tell you how that file is built. What are the contents of your /etc/resolv.conf?  Is the first entry the IP address of your router?  Are the next ones the IP addresses recommended by your service provider?

---

