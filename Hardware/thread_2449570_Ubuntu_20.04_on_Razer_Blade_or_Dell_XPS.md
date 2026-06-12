---
title: "Ubuntu 20.04 on Razer Blade or Dell XPS"
date: 2020-08-29
forum: Hardware
---

### Post by kruemelprinz on 2020-08-29
Hi


 I am considering to purchase a new laptop computer and, after having been a MacOS user for 11 years, to convert to the linux world. The computer will mainly be used for video editing and thus needs to have some decent specs. I will want to install ubuntu or kubuntu 20.04 on it, either alongside factory windows or as a single OS.

 
 
 During my research, i became particularly interested in the recent (2020) Razer Blade Stealth 13 and Blade Base 15 inch models, and the 2019 Dell XPS 7590. All of these machines have 4K screen options, recent Intel i7 9th or 10th gen processors, and reasonably powerful graphics cards for being laptops, in particular the nvidia RTX 2060 MaxQ or GTX 1650 Ti models. I am currently using Davinci Resolve for video editing on my MacBook Pro, and want to continue using the linux version of the software with the new machine (yes there is a workaround to install it on other distros than CentOS). There are many reports of Resolve working like a charm on desktop computers with GTX or even RTX graphics cards under linux. But I don’t want a fixed desktop workstation, haven’t had that in 20 years and will stick to laptops.
 
 
 Unfortunately, neither of thes above laptop options come with a preinstalled linux option, and I have come across some compatibility issues during my research around these machines. However, rarely any of the forum posts I found was directly related to the specific years of the models I mentioned above in direct context with ubuntu 20.04 LTS. Most articles are about older models and ubuntu versions, or the new models with older ubuntu versions.
 
 
 There seem to be some issues that repeatedly appear which I’d like to ask if anyone has tested or found a solution for:
 
 
 
[LIST]
[*]WiFi not 	working (Killer 1650 card) – is this resolved in the standard 	kernel that comes with 20.04?

[*]OLED screen 	dimming not working – does anybody know whether this is still a 	problem and if there will soon be a solution for that?

[*]Nvidia graphics 	driver issues for both RTX and GTX – various reports from not 	working at all despite proprietary drivers to poor performance. Some 	report working systems but that’s mostly on PopOS, not 	ubuntu/kubuntu

[*]Issues resuming 	from sleep – crashes Dell XPS or causes screen issues

[*]poor battery 	life

[*]high rpm fan 	speed despite low system load

[*]HDMI out not 	working with one of the GPUs (not sure whether it was the dedicated 	nvidia or the Intel one

[*]external screen 	resolution and scaling issues
[/LIST]
 
 
 Looking into Davinci Resolve use, I am also a bit confused about the the GPU switching in linux. Does this completely deactivate the internal or dedicated gpu so apps can’t take advantage of them (Resolve can handle multiple GPUs at once for faster rendering on Win and MacOS) or does this just change the GPU that is used for screen display and external monitors?

 
 
 If there is anybody who has actually tested ubuntu/kubuntu 20.04 on any of these systems or knows more about the above issues, please share your experience, issues you encountered and whether they were solvable or not.
 
 
 Also, if you have any other laptop recommendations with similar specs that work with linux, please let me know. For found the Asus Zephyrus ROG G14 that sounded very interesting on paper, but I hardly found any report of even a successful installation procedure.

 
 
 Any help his highly appreciated
 Thanks in advance
kruemelprinz

---

### Post by CelticWarrior on 2020-08-30
Welcome.

> 
[LIST]
[*]WiFi not working (Killer 1650 card) – is this resolved in the standard kernel that comes with 20.04?
[/LIST]

[https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/](https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/)


> 
[LIST]
[*]OLED screen dimming not working – does anybody know whether this is still a problem and if there will soon be a solution for that?
[/LIST]

No idea.
Very likely it'll work with some additional kernel parameter if proper support hasn't been added to the current kernel yet.


> 
[LIST]
[*]Nvidia graphics driver issues for both RTX and GTX – various reports from not working at all despite proprietary drivers to poor performance. Some report working systems but that’s mostly on PopOS, not ubuntu/kubuntu
[/LIST]

It works with the correct drivers version correctly installed (you'll find it in Additional Drivers). Some very new Nvidia cards may need the additional repository Graphics Drivers PPA to be added in order to obtain newer Nvidia drivers versions.
And Pop_OS is based on Ubuntu and developed/optimized mainly for System76 machines. There's no difference in performance comparing to standard Ubuntu with the same correct Nvidia drivers correctly installed.


> 
[LIST]
[*]Issues resuming from sleep – crashes Dell XPS or causes screen issues
[/LIST]

Issues are related with the previous point - Nvidia drivers - and/or UEFI. Always make sure the UEFI as well as SSD firmware are updated even if new.


> 
[LIST]
[*]poor battery life
[/LIST]

No, it's a perception problem.
Many users aren't aware (or don't want to understand) hybrid graphics and try to compare what isn't comparable, the battery life always or mostly using the iGPU Intel in Windows with Ubuntu running always with Nvidia.


> 
[LIST]
[*]high rpm fan speed despite low system load
[/LIST]

Again:
- Mostly a perception issue.
- Update UEFI
- Switch to the iGPU if you don't need dGPU and conversely do not complain about the fans if you're stressing out the machine by using the iGPU for tasks where the dGPU would be strongly recommended.


> 
[LIST]
[*]HDMI out not working with one of the GPUs (not sure whether it was the dedicated nvidia or the Intel one
[/LIST]

Typically the HDMI out is connected to the dGPU only. It's not an OS issue.


> [COLOR=#000000]external screen resolution and scaling issues[/COLOR]
What issues?
[COLOR=#000000]
[/COLOR]

---

### Post by CatKiller on 2020-08-30
I wouldn't get a Razer anything for use with Linux.

For ease of production, Dell tend to use the same components in their Windows machines as they do in their Linux machines, which helps.

If you want to use Linux on a laptop you're much better off getting a laptop with Linux already on it. You can get machines from Dell, Lenovo, System76, Star Labs, Tuxedo, or a bunch of other places.

---

### Post by sanekoala on 2020-08-30
I just purchased a 2020 Razer Blade 15 Base (i7-10750H, 16GB Ram, RTX 2060, Intel AX-201, 1080p display) and am going to be installing Ubuntu 20.04.1 LTS on it today. I'll update you with my experience. It will be a dual-boot with Windows 10 since school requires Visual Studio, C#, WPF (that's the kicker), and .NET Framework for some coursework.

---

### Post by CelticWarrior on 2020-08-30
Again, make sure to update UEFI and SSD firmware before attempting the dual-boot.
Also make sure you understand that some SATA modes like "RAID" or "Intel RST" aren't supported so you need to change it to "AHCI" and then Windows won't boot unless you previously installed AHCI support in it. And, of course, disable Secure Boot and Fast Boot (UEFI) and Fast Startup (Windows), all of this BEFORE installing Ubuntu.

---

### Post by sanekoala on 2020-08-31
A quick report: I downloaded the Razer Bios update tool from their forum page ([https://insider.razer.com/index.php?threads/razer-blade-15-base-2020-firmware-updates.59001/](https://insider.razer.com/index.php?threads/razer-blade-15-base-2020-firmware-updates.59001/)) and confirmed my BIOS was up to date. I had already disabled Secure/Fast Boot but didn't change any other settings in the BIOS. I booted immediately into the live USB environment of Ubuntu 20.04.1 LTS. After checking to make sure I could connect to wifi, I proceeded with the dual boot. I chose the minimal installation and the proprietary drivers when offered the selection and didn't do any special partitioning. After the installation completed and I restarted, I quickly booted into Windows from the GRUB menu just to be sure that still worked. It did, and I rebooted again, this time into Ubuntu. I connected to my wifi network again and confirmed that everything worked right out of the box. It does seem like I'm getting slower speeds than I should via wifi but I'm fairly certain that is because of my older ISP-provided router, not the AX-201 chip/Ubuntu. The Nvidia proprietary drivers were installed allowing me to select a PRIME profile and all of the function keys worked (volumne, playback, brightness, keyboard backlight, print screen) with no issues. The only caveat here is that the 2020 Blade 15 is not yet supported by the OpenRazer project so there isn't a way to control the color or mode of the RGB lighting on the keyboard. This isn't a huge deal to me since A) It's single zone RGB anyways and B) I can still control the backlight level. The touchpad seemed to work just fine with no issues although I tend to just use a mouse anyways. The only thing I DID NOT test in Ubuntu was Bluetooth connectivity which was largely just an oversight on my part. 

The only issue I had was when I tested putting the device to sleep and waking it up. This is where things went a little weird for me. It took about 30 seconds for the devices to do anything (I thought nothing had happened at first). Then, the screen locked (so now it's at the user login screen). I thought something had gone wrong so I logged back in and after about 10 seconds POW, the device went to sleep. When I woke it up with a keystroke, I was still fully logged in instead of being at the lock screen to login. Then the device started going to sleep every 30 or so seconds without me initiating it and this continued until I rebooted the machine. 

To be fair, I did not perform any further testing with sleep to see if it was repeatable or not. This could just be related to how new the device is or it could have been user error! 

All in all, the initial experience was fine besides the sleep issue. I am writing this review from my Manjaro Gnome installation on the device and this is performing very well. I did connect my only Bluetooth peripheral (an Apple Magic mouse, blasphemy!) and it's working well so I would expect the same in Ubuntu but I don't guarantee it. I DO NOT have the sleep issue in Manjaro which does make me think I could have done something incorrectly or been too impatient when putting the device to sleep in Ubuntu. This wasn't meant to be a full, in-depth review of Ubuntu on the 2020 Razer Blade 15 Base but I can confirm all of the essentials seemed to be working well. Hopefully this helps!

EDIT: I forgot to include my observations on fan usage and heat! I am happy to report that on both Ubuntu (which I only tested for a few short hours) and Manjaro (which I've tested for about a half-day), the fans operate exactly as they do on Windows 10. There has been no excessive fan usage and they kick in appropriately when playing a game (Dirt Rally, Grid Autosport). Although I haven't actually  looked at temps, the deck/keys don't get hot under normal usage and the fans only kick in quickly when building packages from the AUR. The fans on the Blade are quiet IMO, especially when considering the amount of power (45 watt i7, RTX 2060) packed into a slim chassis. From a hardware standpoint, this thing is really impressive.

---

### Post by mastablasta on 2020-09-01
System76 Oryx Pro has RTX 2060, 2070 or 2080 and you can pump it up with 64 GB memory. 

there was another gaming one i saw a new one the other week, but i forgot the name. not very helpful i know but some search in gaming websites will reveal it. also came linux preloaded.

---

### Post by kruemelprinz on 2020-09-03
Hi everybody

Thanks for your thorough and detailed explanations and experience reports. After having had a chat with my university's IT department on computer choice they hinted me that they have an incredible 50% discount on the Dell precision laptop lineup. There is specifically the 5540 which is basically indistinguishable from the XPS 15 by its looks and you can choose between Intel 9th gen i7, i9 and even Xeon processors. They have Quadro T2000 graphics, which are not quite as powerful as the Razers with a RTX 2060/70/80, but still fairly powerful. And the best of all is that you can order them with ubuntu 18.04 preinstalled directly from Dell and save another 100 bucks on Windows. I assume that there should not be any issues upgrading to 20.04 or future versions since hardware support with newer versions usually is broader.

Even though the fairly working Razer Blade solution with RTX graphics sounds tempting, I am pretty convinced that the Precision 5540 with a Xeon or i9 will be the option to go for, but - again - thanks to all of you for your kind help.

One last question that has not been addressed yet:
Is switching between dGPU and iGPU only affecting which card generates the actual screen image or does it completely deactivate the other card? Just wondering if both cards can be utilized for rendering and GPU tasks simultaneously, eg Davinci Resolve, to increase performance.

Best wishes
Kruemelprinz

---

### Post by CelticWarrior on 2020-09-03
It deactivates the other card.
It's not the same as some desktops with multiple cards and firmware enabled multi-monitor support. Those can have one drawing the desktop and the other(s) doing something else.

---

### Post by kruemelprinz on 2020-09-06
Thanks! What a pity though. I assume if I'd decide to get an external GPU that one could be utilized on top of whichever GPU in the laptop is activated?

---

### Post by Mixa84 on 2020-11-27
So how is now the impression with Razer Blade 15 2020 on Ubuntu? Does everything works that you stated properly? Some more info on thermals? How about sleep and waking up from sleep, does it go in S3 sleep and how much battery goes out over rhe night? Battery life in average?

---

