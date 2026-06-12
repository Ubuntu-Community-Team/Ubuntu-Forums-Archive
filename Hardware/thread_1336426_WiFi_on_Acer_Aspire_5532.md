---
title: "WiFi on Acer Aspire 5532"
date: 2009-11-24
forum: Hardware
---

### Post by tittiger on 2009-11-24
I can not get WiFi working on my new Acer Aspire. I am a Linux moron and really need an easy fix guys.

Device manager says it's an Atheros AR5B93 chipset.

Is there a common USB WiFi modem that would be recognized by Ubuntu and make for an easy fix?

TIA


Joe

---

### Post by RedSingularity on 2009-11-24
Did you check in System>Admin>Hardware Drivers?

---

### Post by tittiger on 2009-11-24
Thanks! I went there and was told that "No proprietary drivers are in use in this system"


Joe

---

### Post by RedSingularity on 2009-11-24
Post the output of lspci

---

### Post by rasan on 2009-11-24
I had fixed this problem sometime back with Aetheros, by compiling latest madwifi. Try compiling latest madwifi if the one in Synaptic manager does not work. 
Also google for ndiswrapper, that is also known to help.

---

### Post by tittiger on 2009-11-24
Sorry no way to get it all here easily. This looks like what you are looking for:

"Network Controller: Atheros Communications Inc. AR928X Wireless network adapter (PCI express)m (rev 01)"


conversely Windows 7 identifies it as AR5B93

---

### Post by tittiger on 2009-11-24
> **rasan said:**
> I had fixed this problem sometime back with Aetheros, by compiling latest madwifi. Try compiling latest madwifi if the one in Synaptic manager does not work. 
Also google for ndiswrapper, that is also known to help.

I really am Linux illiterate. :-)
It would take an act of congress and a good video to get me though that it sounds like. 

Why can't the developer just add the driver/fix or recommend a USB WiFi card? 

Thanks

Joe

---

### Post by RedSingularity on 2009-11-24
Ok we will first try the madwifi drivers.  Here is how.

1)  Go to System>Admin>Software sources.  Third party software tab.
2)  Add this to it.............deb [http://ppa.launchpad.net/timg-tpi/ppa/ubuntu](http://ppa.launchpad.net/timg-tpi/ppa/ubuntu) karmic main
3)  Right click [this](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA093F9BA8C12F8B6) link and save it to the desktop.
4)  Authentication tab click import key file.  Import the file u just downloaded.
5)  Close software sources and open a terminal
6)  In terminal type "sudo apt-get update" then "sudo apt-get install madwifi"
7)  Restart the computer.

Lets see if this works.

---

### Post by tittiger on 2009-11-24
Thanks it is going to take me a bit as I am at a library and can't even DL anything at the moment and don't even know if Ubuntu will  see a memory stick etc, etc, etc.

Will work on it the next few days and get back with you.

Thanks,
Joe

---

### Post by coffeecat on 2009-11-24
**Do not install madwifi just yet!** You may not need it.

That Atheros chipset works just fine if you install some backported kernel modules (drivers) from the repository. In fact it works without the updated drivers, but the connection is flakey. So - can you connect to your router with an ethernet cable? If you can, the system will autoconnect and you will be on the internet. Go to System > Administration > Synaptic, press the Reload button and let it download the package metadata. If Update Manager prompts you for updates, ignore it for the time being. Now have a look at my post #2 in this thread:

[http://ubuntuforums.org/showthread.php?t=1332317](http://ubuntuforums.org/showthread.php?t=1332317)

Install the four packages I list there. The first one will probably be *2.6.31-15* rather than *2.6.31-14* because there has been a kernel update since I posted that post. Once they have been installed don't reboot yet if prompted, but click on 'Mark all upgrades' and then 'Apply' and all the updates will be installed. Reboot without the ethernet cable in and once you're in the desktop, click on the network manager icon (top right, next to the volume control icon). Your wireless network should be listed in the drop-down. Click on it and put in your passphrase where prompted. You are now connected wirelessly with a a fully updated system with stable wireless.

I promise you! :) (Posting from an Acer laptop with the self-same wireless chipset and not a sniff or whisper of madwifi about it. :wink:)

By the way, ****I'm assuming you're using Karmic and not Jaunty. Please always tell us your Ubuntu version when posting support requests.

---

### Post by FrodoB on 2009-11-30
This should be possible as my 5532 worked out of the box with Fedora 12. It can work with Ubuntu as well with a little work I am sure. Good luck.

Also check this thread, as someone has it working with Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1309854&highlight=Acer+5532](http://ubuntuforums.org/showthread.php?t=1309854&highlight=Acer+5532)

---

### Post by tittiger on 2009-12-01
That's an  interesting idea. Does Fedora 12 have a Windows side install like Ubuntu does?

TIA
Joe

---

### Post by FrodoB on 2009-12-02
> **tittiger said:**
> That's an  interesting idea. Does Fedora 12 have a Windows side install like Ubuntu does?

TIA
Joe

Well if you mean can you dual boot them the answer in theory is yes, but the Acer recovery tool did not like having the windows partition shrunk and I just blew Windows 7 away and now have Fedora only.  

That is fine for me, but if you want both I never figured it out and I have done it on other systems like XP without issue.

---

### Post by |{urse on 2010-04-01
> **coffeecat said:**
> **Do not install madwifi just yet!** You may not need it.

That Atheros chipset works just fine if you install some backported kernel modules (drivers) from the repository. In fact it works without the updated drivers, but the connection is flakey. So - can you connect to your router with an ethernet cable? If you can, the system will autoconnect and you will be on the internet. Go to System > Administration > Synaptic, press the Reload button and let it download the package metadata. If Update Manager prompts you for updates, ignore it for the time being. Now have a look at my post #2 in this thread:

[http://ubuntuforums.org/showthread.php?t=1332317](http://ubuntuforums.org/showthread.php?t=1332317)

Install the four packages I list there. The first one will probably be *2.6.31-15* rather than *2.6.31-14* because there has been a kernel update since I posted that post. Once they have been installed don't reboot yet if prompted, but click on 'Mark all upgrades' and then 'Apply' and all the updates will be installed. Reboot without the ethernet cable in and once you're in the desktop, click on the network manager icon (top right, next to the volume control icon). Your wireless network should be listed in the drop-down. Click on it and put in your passphrase where prompted. You are now connected wirelessly with a a fully updated system with stable wireless.

I promise you! :) (Posting from an Acer laptop with the self-same wireless chipset and not a sniff or whisper of madwifi about it. :wink:)

By the way, ****I'm assuming you're using Karmic and not Jaunty. Please always tell us your Ubuntu version when posting support requests.

I can confirm this works on an aspire 5532 with the same atheros chipset as the OP. Thx =)

---

### Post by DigitalDakness on 2010-04-03
Thanks cofeecat I to have the same laptop as you acer aspire 7540g and recently installed ubuntu karmic koala and had awfull issues with wireless but thanks to your guide its sorted!!! Many Thanks for your support and guide. :popcorn::KS

---

### Post by XxBJDxX on 2010-04-23
> **coffeecat said:**
> **Do not install madwifi just yet!** You may not need it.

That Atheros chipset works just fine if you install some backported kernel modules (drivers) from the repository. In fact it works without the updated drivers, but the connection is flakey. So - can you connect to your router with an ethernet cable? If you can, the system will autoconnect and you will be on the internet. Go to System > Administration > Synaptic, press the Reload button and let it download the package metadata. If Update Manager prompts you for updates, ignore it for the time being. Now have a look at my post #2 in this thread:

[http://ubuntuforums.org/showthread.php?t=1332317](http://ubuntuforums.org/showthread.php?t=1332317)

Install the four packages I list there. The first one will probably be *2.6.31-15* rather than *2.6.31-14* because there has been a kernel update since I posted that post. Once they have been installed don't reboot yet if prompted, but click on 'Mark all upgrades' and then 'Apply' and all the updates will be installed. Reboot without the ethernet cable in and once you're in the desktop, click on the network manager icon (top right, next to the volume control icon). Your wireless network should be listed in the drop-down. Click on it and put in your passphrase where prompted. You are now connected wirelessly with a a fully updated system with stable wireless.

I promise you! :) (Posting from an Acer laptop with the self-same wireless chipset and not a sniff or whisper of madwifi about it. :wink:)

By the way, ****I'm assuming you're using Karmic and not Jaunty. Please always tell us your Ubuntu version when posting support requests.

I followed your steps on my Acer Aspire 5532 and it worked to a T. just wanted to thank you for the info. And add my model for anyone with this product that wants to use linux and not have the wireless keep dropping. :guitar:

---

