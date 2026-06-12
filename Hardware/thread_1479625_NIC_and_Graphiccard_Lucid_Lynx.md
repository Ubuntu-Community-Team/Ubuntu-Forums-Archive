---
title: "NIC and Graphiccard Lucid Lynx"
date: 2010-05-10
forum: Hardware
---

### Post by Kobus14 on 2010-05-10
Hey there,
First of all , I'm a Ubuntu users since Ubuntu 8.04 . I know my way around a little bit with the desktop , but when it comes to the terminal and its commandline I'm a newby. 

Now my problem. Everytime when a upgrade came availlable , I installed it without any problem. When I did an upgrade 9.10 to 10.04 nothing bad happened. But when I wanted to change a theme the system crashed. After rebooting my desktop frooze , the menu's and icons didn't load. The only thing I could see was my desktop wallpaper. The tty screens , as I call them , wher accessable. But as I said , I don't know anything about terminals and commandlines. Then I figured out how to perform a reset for my Gnome Panel , so that the desktop would be standard. It worked , Ubuntu did boot. But my NIC(NetworkCard) and my Graphic Card Nvidia GeForce Go 7400 where not there anymore. Everytime I reboot an error is there just before the grubmenu loads. 
This is what it says:

[I][B]Initializing intel (r) bootagent GE V1.2.28
PXE-E05: The LAN  adapter's configuration is corrupted or has not been initialized.
The  boot agent cannot continue.

[/B][/I]But when I choose Windows Vista in the Grub Menu , everything works just fine. Even Aero works , so my NIC and my Graphiccard are just fine. 
So I thought , this is a Ubuntu problem. I downloaded Ubuntu 10.04 and burned it. I formatted the ext3. partition and installed Ubuntu 10.04 again.

Nothing has changed. Ubuntu can't even find any drivers when I hightlight  Hardwaredrivers in the menu. Please help me find a solution. Ask me witch information you need , I can use the terminal if you give me the commandlines. I already tryed the dutch Ubuntuforum , but nobody helps there. My English isn't to good. I know that this forum is a lot bigger , so that's why I try here.

Help!!:(

---

### Post by Kobus14 on 2010-05-11
Today I noticed another thing. While in Ubuntu I can start up Synaptic Package Manager. I uninstalled my Network Manager and tried to install it again. I hoped that maybe this would fix it , but I coul not install it again. With Synaptic Package manager I can uninstall things , but I can't Install things. Tried Ubuntu Software Centre , but this also fails. Same problem. Can uninstall everything , but can not install anything. Is this also the cause of my NIC problem. Please reply?

---

### Post by Kobus14 on 2010-05-12
:popcorn::confused:

---

### Post by Kobus14 on 2010-05-14
:popcorn::guitar::mad::confused:

---

### Post by cascade9 on 2010-05-15
> **Kobus14 said:**
>  With Synaptic Package manager I can uninstall things , but I can't Install things. Tried Ubuntu Software Centre , but this also fails. Same problem. Can uninstall everything , but can not install anything. Is this also the cause of my NIC problem. 

You cant install anything because your network card isnt working..so you have no internet. 

try post the output from this-

sudo lshw

---

### Post by Kobus14 on 2010-05-23
Thnx guys for the reply's. But my problem is solved. After the Graphic card crash in ubuntu lucid lynx my bootAgent was corrupted. This Bootagent is not a part of Windows or Ubuntu. It is a manager that comes with the BIOS of my HP pavilion notebook. It has an Intel Network Card and it uses the bootagent. Windows can run fine without it , because it has its own settings for the nic. Ubuntu however, needs the bootagent to connect with the nic. Because it was corrupted , Ubuntu couldn't find the nic. My bootagent could not be flashed because it was managed by the BIOS. In the menu of BIOS however , I could not find anykind of setting.
After a search through some forums ( even Windows forums) I found a tool named PROboot. It is a bootable disk that can run a tool named Ibautil. With this tool you can reset the bootagent to its default settings. In some cases you can flash the agent aswell. Not in my case though. 

Because PROboot runs under MSdos enviroment I will tell you guys how it works.

1. Download PROboot and burn it as a bootable disk. I did this with Windows so I   burned it with Nero 7. 

2. Restart the notebook/pc and boot it again with the disk.

3. MSdos (Caldera) will start up. Search for the right prompt. In my case this was the E:\ drive. [ type:  cd E:\ ]

4. To check if you have the right drive selected type : dir

5. Now you will see wat is on the disk. Ibautil must be one of them.

6. Then type: IBAUTIL.exe -defcfg

7. When Ibautil is finished , restart the computer and youre problem is solved.

If you want to flash then you have to type : IBAUTIL -up
When flashing is not enabled type: IBAUTIL -flashenable and then type IBAUTIL -up again. If after the flashenable MSdos tells you that it can't enable flash because BIOS is preventing it , you can only perform a default reset as discribed above. How to enable the flash in this case I don't know yet. 

The Graphic card problem was easily solved after I was connected to the internet. I was able to install a driver for it.

I hope this will fix the problem for other users who have the same problem as I had.

THNX:P

---

