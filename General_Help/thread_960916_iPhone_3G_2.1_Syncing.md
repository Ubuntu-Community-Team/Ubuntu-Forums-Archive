---
title: "iPhone 3G 2.1 Syncing?"
date: 2008-10-27
forum: General Help
---

### Post by blis102 on 2008-10-27
Hey everyone,

Wondering if there has been any success out there getting an iPhone 3G (with 2.1 ver. of the software) to sync in any way on Ubuntu 8.04? I have a VirtualBox of Windows XP with iTunes installed and I have iTunes installed (but not working...) with Wine but no luck getting syncing to work... Has anyone gotten their phones to sync? Or should I hold off hopes for this till the future?

Cheers!
D

---

### Post by tact on 2008-10-28
I have my iPhone 3G sync'ing to the latest itunes installed on WinXP Pro that is installed in a VM created and run under VMWare Server 2.0 

The latest VMWare Server 2.0 supports the needed USB 2.0 for connecting to iPhone with no further tweaking of config files etc.

The only non-intuitive part is getting the iPhone<>USB connection linked properly to the VM.  When you have your VM running (with USB hub installed/enabled) you will find a little button labelled USB under the "Devices" menu... it doesn't work.

You must open the VMWare Server 2.0 web based admin tool, select the appropriate VM, (launch it from here is best)...  then on the web based admin tool (not the actual VM window) find and click the USB icon for that VM, if the iPhone is plugged in it will appear in a drop down menu.  Check the box beside it.   This action is what passes the USB connection to the VM.   

(Totally ignore whatever the USB drop down list on the actual VM window (under "devices") says about the iPhone not being connected.  It is, and your virtualised XP will already be installing the newfound "digital camera - iPhone" for you.)

Dismiss the virtualised XP box asking if you want to open the "camera"...   Run itunes and your iPhone will be found by itunes nicely.

---

### Post by blis102 on 2008-10-29
Hi tact, thanks for the response and the how to, Ill have to try that out shortly and see if I have any luck!

Cheers

---

### Post by tact on 2008-11-23
..and as I just found out - you cannot do restores or install software updates when using iTunes in a VM.

Part way through the process of installing the v2.2 software update the installation process reboots the iPhone into a service mode and this breaks the USB connection to the VM.  If you try this you will end up with an unusable iPhone!   Don't go there.

To get my iPhone working again I had to dust off an old box with XP installed (on bare metal, not in a VM) and boot it up...  install iTunes...  connect the iPhone...  download and do the update to v2.2 and was happy to see the iPhone activated and unlocked automatically as per its state before the update.  

Note!: My iPhone was purchased as a fully telco unlocked iPhone - if your's was locked to a particular telco when you bought it and you used some nefarious means (hehe) to unlock it - be prepared in case the v2.2 relocks your iPhone!

After seeing the update installed and phone activated and unlocked, basically back in a virgin state - I could then connect it back to the iTunes running in my ubuntu VM and sync back all my music, videos, contacts, etc.

You have been warned!   :)

---

### Post by Lex Luthor on 2008-11-25
I've got my iTunes working on Virtualbox after I found this script, thar downloads the kernel source, modify the needed configuration, recompiles and reinstall it.

It is very easy, and worked for me. But I'll have to do this everytime a kernel update is installed.

the Link: [http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/](http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/)

------------------

Yesterday I was upgrading from 2.1 to 2.2, and after all updates (iTunes to 8.0.2 also), iTunes stopped recognizing my iPhone, giving me the error: 0xE8000035. I don't know what was wrong, but I reinstalled my VM from scratch, and the error got away just after some updates of windows.

So, be carefull with the updates....

---

### Post by blis102 on 2008-11-25
Thats interesting that you got VirtualBox to work, Ill have to check that out some time. 

I decided to go ahead and set up another computer running XP and setting up Synergy to share my mouse and keyboard, which ended up working great, and now Ive got two computers to split the load (movies on one, work on the other :)

Cheers,
D

---

