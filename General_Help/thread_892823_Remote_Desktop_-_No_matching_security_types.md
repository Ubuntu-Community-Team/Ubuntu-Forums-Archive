---
title: "Remote Desktop - No matching security types"
date: 2008-08-17
forum: General Help
---

### Post by r_baker on 2008-08-17
I have a background in Solaris and Red Hat, but I am new to Ubuntu. I am trying to use free VNC Viewer from Windows based workstations (XP, Vista), to use any one of three Ubuntu 9 workstations that has the Edubuntu add-ons.

Last weekend, I downloaded and installed three Ubuntu 9 workstations and the Edubuntu add-ons last on a Virtual Server. I was able use VNC Viewer to access all three Edubuntu Desktops until yesterday, when I had to move the VMWare server.  All VM's were gracefully shut down, and the server restarted after the move.  Everything came back up okay, except for the Remote Desktop on all three Edubuntu workstations.

When connecting any of the three Edubuntu workstations, I now get the error "No matching security types, Do you wish to attempt to reconnect to..."  I believe this means that the Edubuntu Remote Desktop is expecting encryption, and the free version of VNC client and Tight VNC client do not have encryption.

While I have not seen any postings directly related to this issue, I have tried some of the suggestions in related posts, such as turning off Remote Desktop, then restarting, or turning on encryption and then turning it back off.  I have also rebooted the workstations more than once with various Remote Desktop configurations.  I am stumped.

My current Remote Desktop settings are:
[General Tab]
Allow other users to view your desktop - CHECKED
Allow other users to control your desktop  - CHECKED
Ask you for confirmation  - UNchecked
Require the user to enter this password  - CHECKED

[Advanced Tab]
Only allow local connections - UNchecked
Use and alternative port - UNchecked
Require encryption - UNchecked
Lock screen on disconnect - UNchecked
Notification Area - Only display an icon when there is someone connected.

I can use Remote Desktop Viewer between Edubuntu workstations, and I cannot see a firewall in the process list.  I have deleted one of the Virtual Edubuntu Workstations and I am in the process of building another Edubuntu workstation from scratch.

Any ideas what the problem is?

Thank you.
rb

Update:

I have built another Edubuntu VM and I tested one stage at a time.
1: Installed Ubuntu Workstation 9 2.6.24-19-generic
** Windows VNC Clients work with this configuration.
2: Installed Edubuntu add-in, no reboot
** Windows VNC Clients work with this configuration.
3: Rebooted Edubuntu Workstation
** Windows VNC Clients DO NOT work with this configuration.
4: Fully patched (107 files downloaded)
** Windows VNC Clients DO NOT work with this configuration.

---

### Post by luke_shepp on 2009-01-27
hi, i am having basically the same problem. i have Edubuntu 7.04 installed on my machine. i am tring to access the shared files, and do remote desktop, but when i try, it comes up with a message box, "Connecting to..." 
and asks for a username and password
i tried imputting my user name and password for the machine i am trying to connect to, but it failed and also i tried all the usernames and passwords for the machine i am trying to connect with. I know how you clear this error in windows vista,(the computer i am connecting off) but not in edubuntu. Is there a place i can get rid of this or is there a default password. 

thanks

luke

(i have atatched the screenshot of what it comes up with...)

---

