---
title: "No network available - using WindowsXP to fix Linux?"
date: 2009-07-08
forum: Hardware
---

### Post by Oceanwatcher on 2009-07-08
I know this is kinda backwards, but it seems to be the only solution!

This project is making me a bit desperate as everything is working fine in Windows XP Pro, but I can not connect to the network in Linux.

So far I have tried the Kubuntu 9.04 LiveCD and also installed it on the computer. I tried the Xubuntu 9.04 as well, but both live CD's and the installation share the same problem.

Now, there COULD be a "confusion" problem in the installed version as I have tried several network cards in different PCI slots. Not sure if this will make a difference.

I have 3 network cards available. But first, let me do a quick list of the system - it is not the latest and greatest :lolflag:

Asus A7M266-D motherboard with the latest BIOS revision.
Two AMD Athlon MP 1800+ processors
512MB RAM
Two harddisks, The OS boot is on a harddisk in a tray so I can swap it with a Windows XP boot disk plus a DVD and floppy.
Matrox G550 dualhead
Two monitors
RealTek RTL8139 network card

Based on the tests I have done with the Kubuntu LiveCD, this computer will run it very ok for the use I need it for. And the fact that none of the components are bleeding edge should actually make it possible to get things to work?

The other two network cards I have are RealTek RTL8100C and a 3Com 3C905C-TX. These two cards have problems with Linux. The RealTek card is detected wrong (comes up as a 8139) and the other one - well, I do not know. Just don't work.

The fact that the RTL8139 card actually works is based on the fact that I just used it in a different PC and installed Kubuntu and Xubuntu on it. So I do not know why it is not working here! Also, it works fine in Windows XP...

I am only using static addresses here in the house now. Seems there is a problem with the DHCP and this can definitely add to the problem I am experiencing. I have only been able to get NetworkManager in Kubuntu to work on one computer. All the others I have caved in and installed wicd on them. This works well, but how on earth can I install wicd without having network? I have downloaded a .deb package and will try to install it. I know I might get some problems with dependencies, but I hope to be able to write that down, change to Windows and download the extra stuff, boot back into Kubuntu and add it...

By using lspci, I can see the network card and it is detected correct. Is there any test I can run on it without connecting it to a network.

I can not think about anything else than configuration problems.

Do you have any idea where I should start looking? I really want to get this system up and running.

One more bit of information. I had Mint running on it with the 3Com card (8.10 version), but as all other PC's are on Kubuntu 9.04, I wanted this one to be on the same. A little difficult... :-)

I have been searching all over for network information. Would it be an idea to just uninstall NetworkManager and try without it?

---

### Post by pytheas22 on 2009-07-08
Moving the network card into a different PCI slot should not affect anything.

The .deb package for wicd should also not have any dependencies, as long as you're using the one from the wicd website or from [http://packages.ubuntu.com](http://packages.ubuntu.com).

To figure out why your network card is not working correctly, please post the output of these commands:
```

lshw -C Network
lspci -nn
dmesg | grep -e eth -e rtl -e 8139
```

---

### Post by Oceanwatcher on 2009-07-12
Thank you for answering. There appears to be at least twhre things that made this problem happen.

1. I do not have a working DHCP on the network.

2. NetworkManager is not working. I have never been able to get it to work with static addressing.

3. Somehow NetworkManager blocks the manual network setup (editing /etc/network/interfaces). I had a full setup there, and it still did not work.

After reading you message, I decided to try to install wicd and removed NetworkManager first, just to be sure. And out of curiosity, I tested the network after doing that. It worked!

The network card has always been listed correctly when doing a dmesg or lspci.

After this, I could go on and update everything on the pc :-) I now have KDE 4.3 installed and it is really looking beautiful!

I had other hardware problems that was actually solved by booting WinXP and then back to Kubuntu. Very strange, but it works. The only problem I have not been able to fix yet is the dual monitors with the Matrox G550. I will make a new thread for that.

---

### Post by pytheas22 on 2009-07-12
Glad you got the networking straightened out.  I don't know much about video issues, so I'm afraid I can't be of any help with dual-monitor setup.

---

