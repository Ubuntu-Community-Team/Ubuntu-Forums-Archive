---
title: "VMWare and Pocket PC"
date: 2005-11-28
forum: General Help
---

### Post by padamson on 2005-11-28
Hi,

I have been trying to get my Pocket PC (axim x50v) running through Linux with synce. I have followed a few guides and it still does not work. 

Now what I am trying to do is connect to the pda through Windows XP using VMWare. When ever I try this, vmware gives my an error advising me that the host operating system has control of the ipaq driver. 

Doing a quick search on the forum, I try using a suggested command.

rmmod -r ipaq

This only seems to work if I quickly run the command after connecting the pda. 

To work around this issue, I added the line "ipaq" (without the quotes) to the usb hot-plug blacklist. Now the host operating system (ubuntu) does not interfere with the pda.

Now, I am using active sync, it syncs everything correctly. When I try to do a file copy, after a minute of copying, active sync's status goes to disconnected.

Does anyone have any clues to work around this problem?

---

### Post by Jindro on 2005-11-30
I am using Breezy, vmware player with a MS image.
My PDA is USB connected to my note. It works as in MS native.

Check in devices menu in vmware that your connection is active in the session.

---

### Post by padamson on 2005-12-15
Hey,

I will try vmware player and see how I go.

Thanks for the help.

---

