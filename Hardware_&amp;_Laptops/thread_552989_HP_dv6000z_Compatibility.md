---
title: "HP dv6000z Compatibility"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by uzerzero on 2007-09-17
Since I haven't seen any other threads about compatibility with an HP dv6000z laptop (most of them simply list errors), I decided to list how I managed to get my system up and running flawlessly. I am using Ubuntu Feisty Fawn 7.04 x86 32 Bit Edition on here.

**Specs**
Hewlett Packard dv6000z Laptop
AMD Turion 64 X2 Mobile Technology TL-56 @ 1.8 gHz
120 GB Fujitsu SATA Hard Disk Drive
Lightscribe 8x Super DVD Burner (DVD-/+R, DL support)
2 GB of RAM
Nvidia GeForce Go 6150 Mobile Card with Productivity Ports
Broadcom BCM4130 UART Wireless A/B/G card with Bluetooth
Media Center Remote with Philips USB receiver and built in receiver
MCP51 HDA Conexant Audio
USB 2.0 Webcam
Dual omnidirectional microphones
MCP51 SD/SDIO/MMC/MS/MSPRO/XD Adapter
MCP51 Nvidia Ethernet Controller
HP DVB Expresscard TV Tuner

**Installation Process**
Booting the LiveCD was a little tricky, as it doesn't seem to like laptops. Hitting F6 at the first menu will allow you to edit the boot settings. I removed the last two dashes and inserted the following commands. These all may or may not be necessary, this is just what has worked for me.
```
live noapic acpi=off pnpbios=off
```
After this, press enter and the system should start up. If not, turn it off and try it again. It can be a little finicky. Once it is in the desktop, click the Install icon and let it do its job. I had Vista on this laptop originally, but decided that I wanted nothing to do with Windows, so I told Ubuntu to completely wipe everything out. Take that, Bill Gates!

**Working out of the box**
Once it had installed and I had removed the disc, the system needed a quick fix. When the Grub menu comes up, edit the first boot option (or whichever is your Ubuntu installation). Now add the following commands to it in order to get it to boot perfectly everytime.```
noapic acpi=off pnpbios=off
``` Sound was working right out of the box, along with network, my USB mouse, the webcam, microphones, even the LEDs on the Quickstart Media Bar changed colours when I pressed them (volume up/down, mute) and they even worked! I have no need for the Memory Card reader, so I'm not sure if it works, but it should seeing as how lspci lists it. The small Media Center remote that fits in the Expressscard bay worked fine as well. I managed to get the Philips USB receiver works fine out of the box with the Media Center remote, but I couldn't get LIRC to recognize the big Media Center remote that came with the TV Tuner. Perhaps a project for a rainy day. Both headphone ports worked great, even outputting audio to both jacks at the same time and disabling the onboard speakers. The microphone/line-in jack worked fine as well, although the Line-In/Mic switch is not enabled by default in the Mixer. If you plan on using it with either an external mic and line-in at different times, you will have to enable this. Brightness controls work as well, although I haven't found a way to have the system automatically dim the display while running on battery power. All three USB ports work fine. DVD Burner works fine, both reading and writing discs. Nvidia drivers support maximum screen resolution (1280x800) and full 3d graphics.

**Working after a few fixes**
The biggest issue that I had to fix was to edit the /boot/grub/menu.lst file and give the bootloader the "noapic acpi=off pnpbios=off" commands. After this, the laptop should boot fine everytime. Bluetooth worked fine after installing the Bluetooth Obex client. Wireless should work with one of the BCM fixes. I don't have a need for wireless as my school supplies 10/100 jacks in all the rooms, and I don't take my laptop to class. I'm using mostly native Linux applications, with the exception of Guitar Pro 5, Total Annihilation, Unreal Tournament, GTA San Andreas, and Oblivion. Guitar Pro 5 was the only program had a hard time running, you have to enable Timidity in order for it to work. Cedega does crash rather often, resulting in a lot of bad boots :/ I had to turn the Fsck boot count to 50, the default was only 22. Audio worked after installing all the libraries for Amarok. Beryl worked after installing the latest Nvidia drivers and using the restricted drivers. Funny seeing as how Beryl refused to work on my old laptop which had the exact same graphics card.

**Not working**
Try as I might, I could not get the DVB tuner card to work. I have the Windows drivers, but have no way of getting the system to handle them. After some furtive searching of the MythTV forums, I still couldn't find any fix. Perhaps someone will have some sort of fix for this. 

**Things I haven't tested**
Not sure if video-out works, but on my old laptop (a dv6113us), the TV out worked fine after installing NvTVout. As mentioned before, I don't know if the memory reader works or not as I don't use memory cards. Expansion 3 is up in the air. I've never even used it with Windows. 

So that's it. Hopefully this will clear up any problems concerning HP Ubuntu installs. Perhaps one day HP will start preinstalling Ubuntu on their laptops. If you have any questions or wish to add, feel free to post.

---

