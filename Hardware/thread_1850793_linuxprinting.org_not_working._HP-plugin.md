---
title: "linuxprinting.org not working. HP-plugin"
date: 2011-09-27
forum: Hardware
---

### Post by Lexus45 on 2011-09-27
Hello all.
I've faced a problem - the [http://www.linuxprinting.org/](http://www.linuxprinting.org/) is closed for maintenance. And all programms and tools for setting up HP printers/MFPs try to connect to this website to download the plugin.

So, it means that without this site we can not get the required plugin and make the devices work.
I want to ask you if there's any other place where we can get that propriate plugin.

I tried the latest 3.11.7 hplip from hplipopensource.com. I tried 3.10.2 from native Ubuntu 10.04.3 repository.
All of them are trying to download the plugin from that site.
For exaple, I saw this link:
[http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.10.2-plugin.run](http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.10.2-plugin.run)
 And this [http://hplip.sf.net/plugin.conf](http://hplip.sf.net/plugin.conf) which has inside the file the links to the linuxprinting.org. Openprinting.org also doesn't work, it leads to the linuxprinting.


So, the question is: where can we get that plugin?
Without it neither printer, no scanner works.

Best regards,
Alexey

---

### Post by Lexus45 on 2011-09-28
[U]**Found the solution:**
[http://hplipopensource.com/hplip-web/plugin_download.html](http://hplipopensource.com/hplip-web/plugin_download.html)
Just install the latest hplip version from [http://hplipopensource.com/](http://hplipopensource.com/) and then the downloaded plugin.[/U][]("http://hplipopensource.com/hplip-web/plugin_download.html")

---

### Post by Lexus45 on 2011-10-06
Great, now [http://hplipopensource.com/hplip-web/plugin_download.html](http://hplipopensource.com/hplip-web/plugin_download.html) shows "Page not found".

---

### Post by Ahunt on 2011-10-18
I am having this same problem, trying to set-up my HP 1018 with sudo apt-get install hplip and the installation fails because the proprietary plug in from [http://www.openprinting.org/]("http://www.openprinting.org/") is unavailable. The site has been down for days, any explanation why?

---

### Post by jack.b on 2011-10-28
> **Ahunt said:**
> I am having this same problem, trying to set-up my HP 1018 with sudo apt-get install hplip and the installation fails because the proprietary plug in from [http://www.openprinting.org/]("http://www.openprinting.org/") is unavailable. The site has been down for days, any explanation why?

short & sweet
{
printer quit for no known reason, and got all kind of conflicting errors
$ apt-get install --reinstall hplip did not work
$ sudo hp-check	
error: Unsupported model: f2105_2PORT_USB_2.0_HUB <-----[ error as root ]---
$ hp-check
warning:     Device URI: (Makeuri FAILED) <-------------[ error as jack ]---
$ hp-devicesettings
error:  No devices that support device setup found.
wasted several hours following insane suggestions from google searches for
above errors like; google[ Makeuri FAILED ]--

	
finally ---------------

searched google[ hp laserjet 2420 ubuntu 9.10 ]--
chose
---
HP LaserJet 2420 - HP Linux Imaging and Printing
clicked to
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)
1/2 way down the page click on [ Download HPLIP ]
after download finished from konsole
$ ls ~/Downloads/hplip-3.11.10.run
give it execute permissions
$ chmod a+x ~/Downloads/hplip-3.11.10.run
$ cd  ~/Downloads/
$ ./hplip-3.11.10.run
when asked chose automatic
when finished
$ lpstat -s 
system default destination: hp-LaserJet-2420  
device for hp-LaserJet-2420: hp:/usb/hp_LaserJet_2420?serial=CNGJD25271
if no system default destination: is shown
run
$ lpoptions -d hp-LaserJet-2420
check & it should be there
$ lpstat -s 
system default destination: hp-LaserJet-2420
}

jackb

---

### Post by Ahunt on 2011-10-28
Jack:

Thanks for all those instructions. I followed it and they all worked fine, created a print queue and everything but it still won't print. I have no idea why. It sends jobs to the print queue but they never arrive and the print queue remains blank. Very frustrating.

---

### Post by Ahunt on 2011-10-28
My mistake. I tried rebooting the whole system and now it prints! Thank you!

---

### Post by jack.b on 2011-10-28
> **Ahunt said:**
> My mistake. I tried rebooting the whole system and now it prints! Thank you!

glad to hear that !

frustration is evil, hp-setup should provide suggestions not just
errors.

jack

---

### Post by Ahunt on 2011-10-28
I'll vote for that!

Thanks again for your help! I mostly use my printer for printing CD envelopes for giveaway CDs of Ubuntu, Lubuntu and Puppy Linux, so you got me back in production there!

---

