---
title: "printer networking?"
date: 2011-12-19
forum: Hardware
---

### Post by Super_Dork_42 on 2011-12-19
I know how to do it in Windows because they just taught us in class, but how do I set up a printer, connected to my Kubuntu machine by USB, to our home network so the Ubuntu and Windows computers on it can print from it? I have looked around but haven't been able to figure it out yet. Please help. I want my mom to be able to print from her laptop and for me from my room to be able to print too.
I have a feeling I can get it done from the command line, but I don't know the commands (obviously) or have the time to look around more. Please help. My mom is one of those that wants it to "just work already" so I need to get this done fast. Thanks in advance.

EDIT : The printer is an HP Photosmart C4680 if that helps.

---

### Post by Super_Dork_42 on 2011-12-21
Does anyone know?

---

### Post by kurt18947 on 2011-12-21
HP is usually the easiest to get working with Linux.  Unfortunately I am unfamiliar with Kubuntu.  Forgive me if I'm stating the obvious.  The first item is to be sure the printer is visible on your network.  If the printer is connected with a cable, there should be no configuration required beyond perhaps telling the printer to used the wired connection.  If you're using a wireless network connection, you'll need to configure that, entering SSID & key.  With Gnome it's a matter of opening the printer utility and click 'add printer' and after a few seconds to a minute, the printer will be listed, I assume Kubuntu has something similar.  HP does offer a printer utility, hplip to help with setup and to display an ink gauge etc.  I presume hplip works in Kubuntu.

---

### Post by mastablasta on 2011-12-21
you need to have samba to share files and printers with windows maschines. 
 
In kde to share you need the following packages:
 
Samba
Samba Client
kdenetwork-filesharing


Note that kdenetwork-filesharing might not install when you install samba. in that case you will need to install it separatelly.

 
then make printer as shared printer and then try to find it from windows maschine. you might need to put in it's samba address to see it. i don't know this part as i did it the other way arround (printer on XP)

---

### Post by Super_Dork_42 on 2011-12-21
I'll try Samba.

EDIT : What exactly would the commands be once I have those packages installed?

---

### Post by Super_Dork_42 on 2011-12-23
Does anyone know the commands after I get those installed?

---

### Post by mastablasta on 2011-12-23
you should be able to see printer from Windows once you have them installed.
 
if still no luck try installing hplip. it hsould be a tool to  help you configure it. 
 
Otherwise all printer configurations (sharing etc.) can be done via system settings/control panel.
 
a but old but might still be the basic of how you would do it: [http://www.kubuntu.org/doc/7.10/printing/C/print.html](http://www.kubuntu.org/doc/7.10/printing/C/print.html)
 
similar issue, but printer on windows. [http://ubuntuforums.org/showthread.php?t=1868207](http://ubuntuforums.org/showthread.php?t=1868207)
if oyu are having trouble, you can find the printer the same way as that user did.

---

### Post by Super_Dork_42 on 2011-12-23
Thanks mastablasta.

---

### Post by Super_Dork_42 on 2011-12-23
Well, there appears to be a bigger problem now. KLauncher is not working, so I can't launch any programs that aren't already open, so that means no Konsole or KPackageKit either. So how do I install those packages now? -_-

---

### Post by mastablasta on 2011-12-24
this is a new porblem right? if so. it would be best to post it in separate thread along with any error messages.

otherwise 11.10 uses Muon package manager.

---

### Post by Super_Dork_42 on 2012-01-06
I got Klauncher working again by restarting the computer. (I feel stupid for not doing that first, but that's beside the point) The point is, I have the packages installed and it still doesn't show up. Is there a way to assign it an IP address?

---

### Post by Super_Dork_42 on 2012-01-06
I just restarted into Ubuntu on my computer and it doesn't connect there either. I am at a loss as to what the problem is.

---

### Post by Super_Dork_42 on 2012-01-07
I'm starting to wonder if, since the kubuntu machine is OLD and on its last legs, if it would be simpler to do a fresh install of a server version of ubuntu on a new partition of the hard drive of a server we have and aren't using currently, and set it up as a print server.

---

