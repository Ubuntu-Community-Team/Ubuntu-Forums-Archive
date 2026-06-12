---
title: "No screens found - error"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by patrioticcow on 2009-08-02
hello, 
my problem is that i can't install ubuntu 8.10 or higher because it gives me NO SCREENS FOUND error and doesn't want to start x.

what i did is I install ubuntu 8.04 witch works fine, then i try to upgrade it and it gives me the same error.

I know that the problem is because i have 2 video cards (nvisia gtx 8800) and i use SLI
but i dont know how to fix it.


there must be a "cure" for this, too many people have this problem,

thans

---

### Post by dagrump on 2009-08-02
Here give this a shot,After the drivers are installed & it boots back up, go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.
I had to search a bit, but that should do it.

---

### Post by patrioticcow on 2009-08-03
thanks for reply,

hi can't find the BusID

are is what i get, maybe you know witch is it:

xxx@xxx-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a4)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a5)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:00.0 Class ff00: AGEIA Technologies, Inc. Unknown device 0000
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)


thanks for being patient with me.

---

### Post by dagrump on 2009-08-03
OK, the first on is @ 01:00:00, & the other one is @ 06:00:00. Both list as VGA compatible controllers. You should only need to identify the one your monitor is hooked to, if it boots you back to a command change it to the other BusID.
******
If it would help I posted a copy of my xorg.conf file in another thread, but I'm too lazy to go look for it. I think it was titled "GUI won't load after installing nvidia drivers", or something very close to that. It would be in the 64 bit user section. I'd search for nvidia SLI & GUI, might get you there quicker.

---

### Post by dagrump on 2009-08-05
Did you get this working? If so you might want tag it solved.

---

