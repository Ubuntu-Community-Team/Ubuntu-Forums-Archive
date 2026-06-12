---
title: "external hard drive not recognized in virtualbox using xp"
date: 2010-06-25
forum: Hardware
---

### Post by just7peters on 2010-06-25
i was hoping if someone could help me.  i am a new user of Ubuntu and of VirtualBox but so far i am enjoying my self a lot.  i do have one problem however... in my virtual version of XP it does not recognize my usb external hard drive, and my drive has all my programs on it that i wish to install to XP.   Is there any way to fix this? it would help me a lot.

---

### Post by dino99 on 2010-06-25
look at usb settings into virtualbox

---

### Post by pricetech on 2010-06-25
If you're using the OSE version from the repositories, it doesn't support USB.  You need the PUEL version from Sun.

If you installed it using Synaptic or Ubuntu Software Center, then it would be the OSE version.

---

### Post by ScrewBaxster on 2010-09-22
Hi.:) 
I have an external hard drive in an enclosure, connected via USB to my desktop PC (running 10.04). I open virtualbox (Oracle version) and when I went to the USB options, I added with what seemed to be the usb hard drive in the 'filters' box, but running the XP virtual machine the drive isn't recognized anywhere. Somewhere I read about 'shared folders' but that did not work either--I cannot copy/paste between machines. 

If you could help me please?:P

Thanks.

---

### Post by CharlesA on 2010-09-22
Do you have guest additions installed on the XP guest?

That'll enable it to see the USB drive and shared folders (if there are any)

---

### Post by ScrewBaxster on 2010-09-22
I am searching for a guide on how to install them but nothing clear I can use. Do you have a link I can follow to install those on XP? 
thanks!!!!!

---

### Post by ScrewBaxster on 2010-09-22
Ok I installed guest additions. I cannot view my hard drive nor can I copy/paste files or text between machines.

---

### Post by CharlesA on 2010-09-22
Do you still have the drive attached to the virtual machine? If so, shutdown the VM and restart it.

If you can't copy/paste between host and guest, then the guest additions didn't get installed correctly.

---

### Post by ScrewBaxster on 2010-09-22
Ok. I restarted VM, the drive and host pc... nothing. 

I reinstalled the guest additions the same way I did at first: 

1. I clicked 'Devices' on loaded VM.
2. I clicked on Install Guest Additions.
3. I followed the on-screen instructions.
4. There is a point in which the installation gives the option to check a box to install "Direct3D Support -enables Direct3D Support for guests (Experimental)". I leave this blank.
5. I click "Install" and it starts processing. During this step it prompts to continue or stop at installing 'VirtualBox Graphics Adapter' and 'Mice and other pointing devices'.
6. After installation is completed, it prompts to reboot. I rebooted. 
After it booted up I can see the taskbar icon 'Oracle VM VirtualBox Guest Additions 3.2.8'. 

I clicked on 'Devices' again and noticed the 'USB DEVICES' sub-menu not grayed out. I clicked on the hard drive and it worked!! Great. I guess reinstalling it did it cuz it used to be grayed out. Thanks

I still can't get the copy/paste function to work. Do I have to work with the 'shared folders' options? I now see there is a new option in the folders list box called 'Transient Folders'.

Suggestions?

---

