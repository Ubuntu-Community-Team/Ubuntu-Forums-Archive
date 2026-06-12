---
title: "getting a Linksys WPC54Gv2 card to work"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by sgusto on 2006-06-30
A noob getting a Linksys WPC54Gv2 to work. (Texas Instr acx111 chipset)

Xubuntu / IBM T20 (2647-41U) 256MB 20GB

Check to make sure this is in fact a WPC54Gv2 by typing "lspci" from terminal
With the card inserted you should see a listing;
"Network contoller: Texas Instruments ACX 111 54Mpps Wireless Interface"

I found two ways of making this card work (mostly from noob flailing), one with ndiswrapper, one without. 

Without ndiswrapper.;

I found robert114's post where he said the native Linux driver (acx.ko) references the wrong firmware in the card, to fix it;

$ sudo [your txt editor] /etc/modprobe.d/options
add the line (w/o quotes);
"options acx firmware_ver=1.2.1.34"

ctrl-alt-backspace and check it. 

This got the card to work. HOWEVER, it threw a warning in dmesg about possible I/O timing error (don't remember exactly) and also this in dmesg;
"wlan0: Driver using old /proc/net/wireless support, please fix driver!"
It worked, but the dmesg items were a worry. 

The ndiswrapper way (using Windows' drivers) 

Install ndiswrapper-utils from Synaptic or;
$ sudo apt-get install ndiswrapper-utils   

Go to Linksys web support and download the Windows XP driver for WPC54G ver2. I don't know but you could maybe copy & use the Win driver folder from a Linksys install CD if you don't have internet access. Unzip the downloaded file into a folder in your home space. Open the folder in a file manager.  

Many many posts I found said to use the lsbcmnds.inf file which invokes bcmwl5.sys. That is probably wrong. The correct inf file is Lstinds.inf which invokes tnet1130.sys,  BUT THERE IS A PROBLEM WITH IT!. But it's easy to fix. Note the spelling of the actual .inf & .sys file names in the folder. Copy Lstinds.inf for a backup. Then open up the Lstinds.inf file in a text editor and find/replace "TNET" with "tnet". The use of caps in the inf file mess it up. You want all file references in the Lstinds.inf file to match the actual driver file names in the folder exactly so check the whole inf file for case matching. Windows ignores case in the inf file, Linux does not. Save the file. Once you've got that sorted out, again from the driver folder open a terminal;

$ sudo ndiswrapper -i Lstinds.inf 
$ sudo modprobe ndiswrapper  (activates it)
$ sudo ndiswrapper -l  ("el" not "one", this polls the setup )
(it should say "lstinds      driver present, hardware present")
(You then probably need to activate/configure ESSID & wep via system/administration/networking from the menu)  
(if it's all working properly...)
$ sudo ndiswrapper -m (writes the modprobe configuration). 
(then to make it work evey boot...)
$ sudo [your txt editor] /etc/modules
(add the line at the end w/o quotes);
"ndiswrapper"
(save the file. This activates ndiswrapper for subsequent boots) 

btw "ndiswrapper -e [driver name}" removes a driver. 

From terminal, type "dmesg" and look for you card, probably wlan0, and for any error messages concerning it.   

Somehow during my flailing at this I had a warning in "dmesg" that said I had "two addresses" for wlan0. If you see that you've probably got half the ndiswrapper working and are using the Linux driver. If you use ndiswrapper, don't tweak the native Linux acx driver options with "ver=1.2.1.34" and it's probably safe to move it.  sudo launch a file manager and goto;

/lib/modules/[kernel ver]/kernel/drivers/net/wireless/acx 

cut the file "acx.ko" and paste it someplace safe like /root. If the card stops working next boot, you don't have ndiswrapper working correctly. 
 
Now ... if someone could kindly help me get suspend/resume to work on this T20 I'd be a VERY happy guy.
 
gusto

---

### Post by Agent86 on 2006-06-30
This HOWTO is specifically for your card:
[http://ubuntuforums.org/showthread.php?t=201633]("http://ubuntuforums.org/showthread.php?t=201633")
It might help you, or did you check it already?

---

### Post by sgusto on 2006-06-30
Thanks!  Sorry then for the redundant post. 

Don't know why I couldn't find those threads. I worked on that thing for a LONG time. lol

In Xubuntu I get "cardctl: command not found". 

Do one of those type of threads exist for suspend/resume on the T20!? I haven't been able to find anything helpful.

Gusto

---

