---
title: "Cups and the Deskjet 932C"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by BCRailrodder on 2006-09-14
Hi,

I am having a dreadful time trying to access my Deskjet across the network.

Currently I am running 2 machines (ip's 192.168.0.3 & 0.5, respectively) with the printer hanging off of .0.5 as a local machine.  

After several different attempts got get .0.3 to see it, I was partly successful using this guide:
 [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
My cuspd.conf files are identical to these with the exception of changing the ip addresses to reflect mine.

I say partly because while I can see the printer ok (both lpq and lpstat comes back with the right info) and I can print to it (sort of), all I get is the typical hash that you would get if you were using the wrong driver.

I have confirmed (to the best of my knowledge) that I am using the correct driver (hpijs).  Matter of fact, I can't seem to install an other driver as it always seems to default to this one, regardless of what I chose.  I did try to install the pcl3 driver with the printer defaulting to the hpijs driver again.  I tried the pcl3 driver because the only thing understandable with the test pages is "Enter Language=PCL3" .

One thing - I had to set up the client by hand as the printer appears nto to have been published to the network.

I don't know if this is a symptom of some other network problems that I appear to have - for instance, I can ping the local network by ip but not by machine name, I can ssh but not telnet and I seem to be having a problem with NAT being set up right.  I hope not as I do need to get the printing working.

Worse comes to worse, I will transfer the printer to .0.5 .

Thanks in advance for any suggestions,

Kent

---

### Post by IcemanV9 on 2006-09-15
You may want to try this [**[COLOR="RoyalBlue"]solution[/COLOR]**]("http://cups.org/articles.php?L230+I0+THow-To+P1+Qnetwork") from CUPS website. It is very straightforward information.

---

