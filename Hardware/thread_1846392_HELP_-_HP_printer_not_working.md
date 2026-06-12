---
title: "HELP - HP printer not working"
date: 2011-09-18
forum: Hardware
---

### Post by monomox3000 on 2011-09-18
Summary:
I have an HP printer and it was working perfectly with hplip.  Now I can't print, I get the following error all the time: "Printer error.  Printer is busy, offline, or in an error state."
Today I completely uninstalled hplip and reinstalled to no avail. 

The long story:
A few months ago I installed hplip in my computer.  It was the version that exists in Ubuntu repositories (3.10.2).  This wasn't compatible with my new-ish printer (Laserjet Professionel m1212nf MFP) and so I had to download a newer version from HP (3.10.6 or above).  I installed it OVER the old version and it worked beautifully, until Ubuntu released an major (?) update and my hplip version was downgraded to 3.10.2.  I reinstalled newer version on top of 3.10.2 several times and it worked OK for a while, but about a month ago I started struggling a lot.  That's when I noticed my mistake and completely uninstalled hplip through Synaptic and by following the instructions on HP.  I just installed 3.11.7, but I still can't print from my computer (my wife has a windows computer which works well with the printer).  

When I run hp-setup I can't find the printer automatically (the connection is through a WiFi network).  The terminal shows the error "unable to send broadcast DNS packet."  However, when I input the ip address of the printer, the setup wizard finds it. So far so good.  But then, in the final screen of the wizard I select the option to send a test page and I get the error that the printer is busy.  Whenever I run HP Device Manager, the printer shows an hourglass icon, which means is busy.  As far as I can tell there are no jobs in the queue (I can print from my wife computer, as I said).

I've run hp-check -t, the output says at the end "no errors or warnings"
I can ping the printers ip address with no problem. I can see the printer status on my browser by entering its ip address in the address box.  I don't know what else to do.

Thanks!

---

