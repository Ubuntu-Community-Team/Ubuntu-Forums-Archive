---
title: "Very queer PC hardware error."
date: 2009-06-11
forum: Hardware
---

### Post by ugriffin on 2009-06-11
Ok, this might be overheating, but, then again, it CAN'T BE!

Here's what happens: PC boots up fine, and I use it quite a while for diffrent purposes. Shuts down fine, turns on again, blah blah. 

HOWEVER, sometimes, when I turn it on after it's hot, it turns off again. It seems to be Windows related: but the thing usually shuts down on GRUB. It's never done it with Kubuntu, for some reason. Although maybe it is because Kubuntu's been lucky.

My theories:

My CPU's fried: Kubuntu hard freezes while using Amarok. Needs a hard reboot.

Weird case of overheating: It is always hot when it does that. Then again, if the computer's hot, why doesn't it shut down while using the OS? Why does it die when it's being turned on only?

BIOS Error: The BIOS panics and kills my PC.

NVIDIA Overheating issue: The fan only turns on while using NVIDIA drivers? Linux doesn't recognize my GeForce by default, and obviously GRUB will do an even worse job. This is prolly it. Then again, aren't fans completely hardware related?


Could someone explain this? I've Googled, but nothing matches my problem.

---

### Post by bol0 on 2009-06-11
Try to get software which can shows you the temperature of the CPU, system... if the temp is normal then it's BIOS. Try to set default settings first, if it won't help go with the fail-safe. If you're familiar with your PC hardware try setting up the BIOS settings manualy (CPU ratio, RAM ratio, speeds). I had the same issue with my new PC. It wasn't overheating but it looked like it was and BIOS went mad and cut the CPU clock by half. Had to set it up manualy.

---

### Post by Ferrat on 2009-06-11
This is just a guess but perhaps your setting for BIOS shutdown in low? and on top of that Windows doesn't cool it as much as kubuntu because of some fan scaling or something? 

So say your BIOS is set to 70C for shutdown
when Windows turns of it's at say 68C
when Kubuntu finished due to running the fan more it's 63C
BIOS for some reason (might be a setting) isn't running FAN full then when it gets to GRUB and starts to load the CPU  it goes above 70C and BIOS does a instant shutdown for protection.


you said nVIDIA, is it a total shutdown, power and all or a Graphic shutdown with just screen going black?

Same theory applies to that as above just switch CPU with GPU more or less. 

Have you checked so that there isn't a new BIOS version out there? know that my motherboards first bios had similar problems with temperature sensors not working correctly.

---

### Post by ugriffin on 2009-06-11
Hmm... intresting stuff. If it's BIOS cuz GRUB won't run the fan properly then yeah, I guess it is such.

I read on the Wikipedia that fans are entirely hardware related: and I still wouldn't understand why Windows wouldn't cool my system properly: Linux does, and Linux is... Linux. Not too much support for it from the hardware makers. Also, once the system boots up, neither Windows nor Kubuntu do a shutdown. It must be BIOS related, cuz apparently the GPU doesn't shut the entire system down if it overheats. But why only during the booting process of ALL operating systems? Usually happens during GRUB, but it's happened using Windows 7 and Kubuntu. Vista, I haven't tried, cuz it's darn slow. But I expect the same thing.


Ok, will mess with my BIOS and post back. It's an NVIDIA nForce.

---

### Post by ugriffin on 2009-06-12
No temp settings, or anything. Typical PhoenixBIOS.

---

