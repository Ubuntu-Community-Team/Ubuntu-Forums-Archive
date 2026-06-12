---
title: "Heron broke my Nokia bluetooth support"
date: 2008-04-27
forum: Hardware
---

### Post by PsychedelicReaction on 2008-04-27
I upgraded to Hardy Heron since last beta but the upgrade broke support to my Nokia 6680 on bluetooth. On Gutsy I used to send sms through gnome-phonemanager and surf mobile's memory with nautilus obex module, both stopped working after the upgrade. I think it's a bug because i also tried with the live cd and had the same results. Devices are paired correctly and files sending works both ways.
Any idea? Thank you

---

### Post by derailed1 on 2008-04-27
Hi,

I have the same problem.  Bluetooth headset pairs and bonds, but doesn't connect.  I get some stupid obex errors.  I tried using gtbsco and it works awesome in gutsy but not in hardy.  I don't what to do.  I guess hardy isn't ready for me yet.  I'll keep hardy until tomorrow.  If I don't find a solution its back to gutsy.

---

### Post by kkirjala on 2008-04-28
I can confirm this bug to be true for me as well.

I can't browse my phone anymore using bluetooth, and I also cannot receive files I try to transfer from my phone to my laptop using bluetooth. I have used an application called "Bluetooth File Sharing" (gnome-obex-server) for this task, but now with Hardy Heron (8.04) my phone just says that connection failed when I try to send files.

Sending files from my laptop to my phone works ok, though. I just select "Send To" -> "Bluetooth" from Nautilus and it works.

I'm using following equipment:

Phone: Nokia N95
Laptop: HP Nx6110 + Epox USB bluetooth adapter

Hope there is a way to solve this, as I really need to be able to send files to my laptop via bluetooth.

---

### Post by thomasf on 2008-04-28
I confirm that the problem exists. I am not able to send files using OBEX from my Nokia N80 to desktop computer running Ubuntu 8.04 (I'm using it since alpha 5,system is up to date now). Phone can receive files sent from computer. I think that phone is not able to perform service discovery on computer. I wrote two Java apps - bluetooth server to be installed on computer, and client for cell phone. Client is not able to connect.
The strange thing is that with another phone (tested with Nokia 6500) everything is fine. OBEX works both ways, client app can connect.
Any suggestions?

---

### Post by thomasf on 2008-04-28
Guys, look here: [http://ubuntuforums.org/showthread.php?p=4822829](http://ubuntuforums.org/showthread.php?p=4822829)
It appears to be a problem with bluez-utils.

---

