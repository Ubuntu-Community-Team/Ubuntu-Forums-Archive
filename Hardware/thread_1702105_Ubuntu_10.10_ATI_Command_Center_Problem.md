---
title: "Ubuntu 10.10 ATI Command Center Problem"
date: 2011-03-07
forum: Hardware
---

### Post by toseethefruit on 2011-03-07
Hello Everyone,

I have what I hope will be a quick question for any of you who would be willing to offer me some help. I've not been able to find an answer to this question here or elsewhere.

I'm running Ubuntu 10.10 on a Dell Studio laptop with an ATI graphics card. I had everything set up as I liked, but then my computer started booting to a black screen (I had been fiddling with the ATI Catalyst Command Center settings just before -- I didn't mean to change anything, but I might have applied some changes inadvertently), so I booted into Safe Graphics Mode, uninstalled the ATI driver through Ubuntu's Hardware Drivers manager, and then reinstalled it. My computer now boots normally.

The puzzling thing is that ATI Catalyst Command Center no longer shows up in any of the Ubuntu menus (neither in the Application menus nor under the "System" menu. I went into Synaptic and noticed that, for some reason, fglrx-amdcccle wasn't installed, so I went ahead and installed it, and rebooted. The ATI Control Center still doesn't show up in the menus. Furthermore, if I go to Terminal and type "fglrx-amdcccle", I get "fglrx-amdcccle: command not found." Same with just "amdcccle": I get "amdcccle: command not found." I need the ATI Command Center to configure my second monitor, which has just been showing a clone of my main desktop since all this happened.

I'm not sure whether it's relevant, but glxgears works, and aticonfig is a recognized command in Terminal.

Does anyone have any ideas about getting ATI Catalyst Command Center back? It continues to show up as installed in both Synaptic and the Software Center.

I'd be very grateful for any help you would be willing to offer! Thank you in advance!

My best,
Jacob L.

---

### Post by toseethefruit on 2011-03-09
Hello everyone,

Might anyone have any ideas to get me pointed in the right direction?

I appreciate your help!

My best,
Jacob

---

### Post by Yellow Pasque on 2011-03-10
Personally, I would purge all of the fglrx packages: Run the first block of (2) commands here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

Make sure /etc/ati is empty or non-existent. Then, install latest Catalyst manually: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by toseethefruit on 2011-03-11
Temüjin, purging the packages worked perfectly. I guess that I was only removing the packages rather than purging them before I posted here. I was able to purge the packages, then re-install the driver through Ubuntu's Additional Drivers menu item. ATI Catalyst Controller now is showing up like it's supposed to.

Thank you very much! I'm very grateful for your help!

My best,
Jacob

---

### Post by jjjB on 2011-12-25
marking for future reference regarding

ATI graphics driver reset

Thanks for the info

---

