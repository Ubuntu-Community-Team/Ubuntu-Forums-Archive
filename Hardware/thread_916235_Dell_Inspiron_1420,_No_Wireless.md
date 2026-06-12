---
title: "Dell Inspiron 1420, No Wireless"
date: 2008-09-10
forum: Hardware
---

### Post by TheSe7enthProphet on 2008-09-10
Hello all! I received a new laptop to use at college a few months ago and it had Vista preinstalled on it. While I don't hate Vista, I needed something a little bit more reliable to use while I'm in class, so I went with Ubuntu. 

I have it installed on the same drive as Vista and I use Vista's bootloader. 

I'm having an issue with my wireless card. I honestly don't know if it is being recognized or not (more on that in a bit) but I can't see any wireless networks from the network manager. 

I followed the help file within Ubuntu and the one online to this page [https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html) . It suggests that I open the device manager from System &#8594; Preferences &#8594; Hardware Information. Well, "Hardware Information" isn't one of the options for me to click.

The wireless adapter is a Dell Wireless 1395 WLAN Mini-Card... Any help with this would be appreciated! Thanks in advance!

Also, I'll be searching Google for answers while I do this. I've already done so, but without any luck. If I find an answer, I'll be sure to update this thread. Thanks again!

---

### Post by Crafty Kisses on 2008-09-10
The driver I think is in the repos now. First you need to update using Synaptic:
```
sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
Remove the **ndiswrapper **line from the following:
```
/etc/modprobe.conf
```
Disable the wireless from the network manager and then try this:
```
sudo modprobe -r ndiswrapper
```
If you get an error about the module being in use, it means you have not disabled wireless. Restart if there were any kernel upgrades, then go to: **System->Administration->Hardware Drivers** and see if there is a Wireless driver that says "In use" if it doesn't mark "Install driver".

That should work, any problems please post back.

---

### Post by TheSe7enthProphet on 2008-09-10
Sorry this reply took so long. I had to get home so that I could use my wired network.

I ran into a bump on step 1... Picture included.

---

### Post by Crafty Kisses on 2008-09-10
Then try just installing it:
```
sudo apt-get install ndisgtk
```

---

### Post by TheSe7enthProphet on 2008-09-10
I got it working! Thanks!

The instructions in your first post were correct... I misinterpreted them, my apologies! 

Thank you again for your help!

---

### Post by Crafty Kisses on 2008-09-10
Glad I could help. :)

---

### Post by Tomlin on 2008-09-12
TheSe7enthProphet and Codename,

I read this thread with lots of interest. I'm in the process of buying a new laptop. I want to make sure it's COMEPLETELY Linux compatible (HH preferable). Checking [http://webapps.ubuntu.com/certification/list/?release=8.04%20LTS&category=Laptop]("http://webapps.ubuntu.com/certification/list/?release=8.04%20LTS&category=Laptop"), I found that Dell has an Inspiron 1525 that is certified. It comes pre-loaded with Ubuntu 8.04. By configuring my own 1525 on Dell's site, I can get *virtually* the same machine with vi$ta pre-loaded for $5 more. I'm assuming I can re-partition the HD and install 8.04 myself; I did on the old laptop I'm using now - xp and Hardy.

I say virtually because the Ubuntu version comes with the Intel 3945 wireless card, whereas the version I built comes with the Dell wireless 1395. There was NO option for upgrading (?) to the 3945.

My wife will most likely use the machine ocasionally too, so I'd still like to have windoze on one partion.

I'm trying to cover ALL my bases here before I plunk down the money.

So, TheSe7enthProphet, Is everything working fine w/ the 1395?

Thanks for reading this.

---

### Post by TheSe7enthProphet on 2008-09-12
> **Tomlin said:**
> So, TheSe7enthProphet, Is everything working fine w/ the 1395?

Thanks for reading this.

I'm loving Ubuntu on this machine. I've always been a dual-boot person just because there are a few Windows-only applications that I use pretty frequently (not to mention games). This is the fourth machine I've ran with Ubuntu and probably my favorite so far. 

The card works perfectly with Ubuntu (Just make sure you remember to update as soon as you get it installed). I've had an easier time configuring it with Ubuntu as well! 

I recommend getting the Vista version and dual-booting. The 1395 is a powerful card and worth the five dollars extra. I'd imagine the Ubuntu version 1525 wouldn't come with it because the driver for Linux is new. 

Vista makes it really easy to boot with Ubuntu, too. I used the Vista partition tool to shrink Vista's partition, then formatted it with the Ubuntu CD. I use the Vista boot loader to switch between the OS because I'm not a fan of GRUB (Which I set the timeout time to 0, haha). 

My machine works flawlessly with Ubuntu.

---

### Post by Tomlin on 2008-09-13
Thanks. That makes my decision a LOT easier.

Tomlin

---

