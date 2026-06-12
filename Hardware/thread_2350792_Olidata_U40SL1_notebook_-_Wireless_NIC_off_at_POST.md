---
title: "Olidata U40SL1 notebook - Wireless NIC off at POST"
date: 2017-01-27
forum: Hardware
---

### Post by lah-ca on 2017-01-27
[SIZE=3]**Preamble**[/SIZE]


I am refurbing an older Olidata U40SL1 notebook for charity.  This notebook is apparently identical to ECS, Uniwill, and Olivetti units with the same model number.  


I am trying to get the notebook to a point where a non-techie user could be happy with it.  


(See back story and successful efforts with SIS video drivers here: [https://ubuntuforums.org/showthread.php?t=2350126](https://ubuntuforums.org/showthread.php?t=2350126))


[SIZE=3]**OS**[/SIZE]


The notebook is loaded with LUbuntu 16.04 32 bit.


[SIZE=3]**Problem**[/SIZE]


There is a wireless networking problem that I did not notice initially because the notebook was always plugged into the wired LAN.  The problem is that the wireless NIC works perfectly but is almost completely useless.  The setting for the wireless NIC is Off at POST/boot.  And, If there is no connection on the _***wired***_ NIC, network services in Lubuntu 16.04 either do not start or start but then shut down.  Turning the wireless NIC on after boot accomplishes nothing as there are no services running to support it, and there is no PnP-type thing that wakes up and turns services on. Trying to turn the wireless NIC on during POST or boot seems to hang the system.  So the situation is that I can ***only*** use the wireless NIC if I plug into the wired LAN, boot/reboot, login, turn on the wireless NIC, go to network settings, choose a wireless network, and then unplug the cable.  Hmmm .... highly useful.


The real problem here, I think, is with a stupid Pheonix BIOS implementation that allows control of pretty much nothing other than choosing the order of boot devices and toggling boot to LAN on/off.  There was apparently a BIOS update that addressed this issue (toggle wireless NIC on/off at POST), along with unlocking FSB settings so that DDR2 800 SODIMMs could be used.  But ..... no one offers any support for this model anymore, and I am leary, in this evil day and age of firmware- embedded malware, to download something from a sketchy-looking archive site.  I have emailed Olidata, but I expect no reply.


ECS, the actual manufacturer of the notebook, or Pheonix, the BIOS people, (can't remember which now) has a support redirect to a third party website that will use a software app to see if they have a BIOS update in their archive.  But this is for Windows only, I think.  I guess I could pull the drive and install Win 7 on a spare, assuming that 7 will have sufficient native driver support.


Is there an easy way to kick start the networking services after enabling the wireless NIC?

---

### Post by geeksmith on 2017-01-27
This doesn't sound right -- networking services should always start, regardless of whether any particular interface is active at boot. Can you provide more detail on what you're seeing at boot, both before and after activating Wi-Fi?

---

### Post by lah-ca on 2017-01-27
> **geeksmith said:**
> This doesn't sound right -- networking services should always start, regardless of whether any particular interface is active at boot

Hi,

Thanks for the reply.

You are correct.  It does not sound right, and networking services should always start.

What I was getting when I started up with the LAN cable unplugged was pretty much everything in the task-bar (windows term - sorry) network indicator applet greyed-out and networking was disabled.  Turning on the wireless NIC did not change this.  Trying to click the enable networking button did not change this.   Dead in the water.  I assumed networking services had shut down.  ***I replicated this a few times.  ***

I have been playing around since your post.  I have booted with the LAN cable unplugged.  Plugging the LAN cable in (with the wireless NIC off) starts up the connection process as expected.  Unplugging the LAN cable and then turning on the wireless NIC on also started up the wireless connection process - and successfully.  This is how we expect it to work.

After having done this, I hot rebooted with the LAN cable unplugged, logged in, turned on the wireless NIC, and it worked properly as expected.  

Just to make sure, I cold booted the system with the LAN cable unplugged, logged in, turned on the wireless NIC, and again it worked.

Weird, but good.  It is working now.  I will keep testing this for reliability.

I have had problems with this notebook.  At one point in working with it, I had to force reload Alsa to get the sound to work.  Edit: I am also getting sporadic, non-fatal Ubuntu-has-experienced-an-internal-error problems associated with XOrg, probably as a result of the bleeding-edge, non-Ubuntu-native, SIS 771/671 video chipset drivers the computer has to use.

I can't say the problem is solved, since I didn't do/change anything.  All I can say is that it has gone away.  Let's hope for good.

---

