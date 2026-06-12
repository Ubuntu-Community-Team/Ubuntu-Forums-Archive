---
title: "Where can I find underlying os information?"
date: 2008-11-24
forum: General Help
---

### Post by leonardevens on 2008-11-24
I have many years experience with Linux, mainly Redhat/Fedora.  When the GUI interface doesn't seem to work, I can often revert to command line system calls and examine various configuration files to see what is going on.

I have just started with Ubuntu, but I don't have the corresponding depth, so I get stuck when things don't work.  For example, I am currently having a lot of trouble getting printing to work on a remote printer.

Is there any documentation available which will help me?

---

### Post by bab1 on 2008-11-24
I would start [**[COLOR="Red"]here[/COLOR]**]("https://help.ubuntu.com/")

---

### Post by porchrat on 2008-11-24
Are you using CUPS?

---

### Post by leonardevens on 2008-11-24
My system is using cups.

I am having real difficulty with the print administration tool.

First, I can't seem to reliably delete a printer to start over.  Also
sometimes a printer will show up that I didn't install.  For example,
I had installed a Windows printer on another machine using smb.  It then shows up also as an ipp printer to still another machine, but that machine is also running Windows.   I can't delete that printer because Delete is not active (grayed out).

The biggest problem I've been happening is connecting to a printer on a machine running Fedora 9 through ipp.  I can manage to set up the printer
but its model is remote printer.  If I try to change that to the correct
model, it stops working.  Then, all of a sudden, out of nowhere, it starts working.

It is possible that I am having trouble with the firewalls, but I believe I've  configured both to accept the other computer and the relevant services.   It may be that even if that is set up properly, I have to turn off the firewalls in order to make the connection, but I don't 
understand why that should be necessary.

If I could examine the relevant processes, configuration files, etc for 
the firewall and for cups, I might begin to understand what is going on.
I think I found some of the cups configuration information, but I have
no idea how the firewall is working.  It apparently is using iptables,
but I can't find any the file which contains the configuration information.  I also can't figure out how to check the status of
iptables from the command line.   Under Fedora, I would use
/sbin/service iptables status.

All this is rather frustrating!

---

