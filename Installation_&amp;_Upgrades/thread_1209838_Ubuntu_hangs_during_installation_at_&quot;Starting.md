---
title: "Ubuntu hangs during installation at &quot;Starting Bluetooth&quot;"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by CommNet on 2009-07-10
[COLOR=black][FONT=Verdana]Googled around and found that this is a very common issue, but found no real solutions. Trying to install Ubuntu 9.2 Desktop AMD64 on a clean HDD. System: ACPI x86 Based PC (ABIT NF8 Motherboard), AMD Athlon 64 3400+ CPU, SATA HDD, ATAPI DVD-RW, 1.25Gb DDR1 RAM, NVIDIA nForce PCI LAN, PS/2 Keyb + Mouse, ATI RADEON 9550 AGP Graphics, FDD. Peripherals attached are HP USB Printer/Scanner, USB Memory Stick, External USB HDD and DSL Modem connected via wired LAN. All external USB devices are disconnected during installation. This is a pretty basic, standard desktop PC, yet when booting from the installation CD, Ubuntu hangs indefinitely at "Starting Bluetooth" and after Ctrl + Alt + [/FONT][/COLOR][COLOR=black][FONT=Verdana]Del[/FONT][/COLOR][COLOR=black][FONT=Verdana] it hangs at Stopping Bluetooth. That’s it. No error codes / messages, just hangs, waiting for the cows to come home. Guess I've just joined the vast number of unsuspecting Linux wannabes ending up with the hanging Bluetooth device that they never had. Please, if there is an expert out there, put us out of our misery. Thank you![/FONT][/COLOR]

---

### Post by merlinus on 2009-07-10
You might try the text-based alternate install cd, especially with an ATI card.

---

### Post by CommNet on 2009-07-10
Thanks, will give it a go and report back.

---

### Post by CommNet on 2009-07-11
[COLOR=black][FONT=Verdana]Well, downloaded Alternate AMD64 and managed to manually install Ubuntu, but when it finally rebooted to complete the installation it hung again, waiting for that illusive bluetooth device. I'd really like to get this going, would absolutely hate to give up. Willing to try out any reasonable suggestions. Fingers poised over the keyboard, eagerly awaiting new ideas.[/FONT][/COLOR]

---

### Post by OscarLorin on 2009-08-09
Same problem on an old Dell otherwise running XP SP2. Dimension 4700. Intel Pentium 4.

If I use F12 during boot to redirect boot to the Ubuntu 9.04 Intel 32 bit CD and choose the Demo option, it runs fine (except can't find network).

But whether I choose the Install option off the booted CD or boot Windows first and then run the Ubuntu autoplay CD to do the install, it gets as far as the Bluetooth line and hangs indefinitely. No errors, nada.  

Give it the three finger salute and it hangs again on stopping bluetooth.

I don't have bluetooth on the machine. I don't like bluetooth - people walking around talking to themselves. In fact, at this point, I hate bluetooth.

Same CD works under VMware Fusion on my Mac, except VMware tools can't install...9.04 isn't supported.  But running Ubuntu on a Mac seems a bit like coals to Newcastle anyway.

Someone please help me eradicate windows, instead!

---

### Post by OscarLorin on 2009-08-11
Many years ago in my first job in "DP" as it was then, I went to a consultant who was on staff to ask why a particular system error was showing up intermittently. We worked it for several days until he eventually decided it was a 'bacon and eggs problem' and decided to live with it.
When pressed, he explained that it was the kind of problem that only showed up when the cafe down the road was serving bacon and eggs....ie, no rational explanation was possible.

SO: I removed the Linksys WUSB54GSC usb network device from my old dell and started the install again; hard boot, F12 to get the boot menu, chose boot from CD; chose Install Ubuntu.

No hang, no goofiness at all until it hit the partioning process (that I had not previously seen) and errored off.  Fair enough, thought I, I'll go back to windows and clean some winsh*t up. 

Re-inserted the wusb, booted winders, backed up a crapton of pictures to external drive, rebooted to Ubuntu CD and *without removing the wusb* rebooted from CD, creating a single partition 40G replacing windows (at last).

Lo! and behold, I have a clean install of Ubuntu 9.04 and with no trouble except keying in the WEP key, Ubuntu recognized the much maligned WUSB54GSC and I have network too.

Thought I'd share in case it helps anyone else hung up on bluetooth during boot.

---

### Post by trashanken on 2009-08-19
I get the same problem with US Robotics 5421 MaxG USB WiFi. Works with kernel 2.6.28.13, after update to 2.6.28.14 it hangs on startup (Bluetooth) as described, Ctrl-Alt-Delete (or backspace, can't remember) and it hangs when closing Bluetooth. Just updated to kernel 2.6.28.15 - after reboot ubuntu was fine, restarted several times no problem. Started 2.6.28.14 again and it progressed normally to GUI Login, what the ****! Restarted from GUI Login-screen and the computer started beeping insanely followed by a continous looong beep until restart! Kernel 2.6.28.14 is seriously out of wack! Started 2.6.28.15 again and it seems to be working. This behaviour is unprecedented, I've used Linux distros regularly since 2003, ubuntu since 2006, and never seen anything like it! Reminds me of Windows Millennium Edition (Win98Ed3)!

---

### Post by Dr. Manhattan on 2009-09-29
> **OscarLorin said:**
> 

I don't have bluetooth on the machine. I don't like bluetooth - people walking around talking to themselves. In fact, at this point, I hate bluetooth.



Ditto! :P

I'm having the same issue while using the Wubi 9.04 installer.

I was able to select Ubuntu at the boot screen and even watched a few lines of glorious "OK"s until it got to "Starting Bluetooth" and we've been sitting there ever since.

Any ideas would be appreciated.. i'll keep digging until then.

---

### Post by Dr. Manhattan on 2009-09-29
Well, I found this link posted in a similar thread and it looks helpful:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/197522](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/197522)

> while hanged press <ctrl> <alt> <f2> to display the root login ( your machine name login actually)
login with your administrator account

sudo vi /etc/default/bluetooth

switch the variable BLUETOOTH_ENABLED from 1 to 0 (zero)

save the file

reboot

I'm hopeful the above will work for me when I try tomorrow.

---

