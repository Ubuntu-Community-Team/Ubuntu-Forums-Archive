---
title: "6800GS support"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by AvvY on 2006-01-26
Just tried installing 5.10 on my new system:
MoBo::		Asus A8N-SLI Premium
CPU::		AMD Athlon 64 3700+
Ram::		Kingston 1GB (2x512mb) Value Ram DDR400
Graphics:: 	Gigabyte nVidia 6800GS 256mb pci-e
Sound card::	Audigy ZS 2

But at the end of the install when it boots Ubuntu for the first time and goes to the logon screen, it is all scrambled. It is impossible to read/make out anything being displayed. This is using the default resolutions (tried using custom settings too). I get the feeling the graphics card isn't supported although no problems are mentioned during install.

---

### Post by luna6 on 2006-01-26
Hello I got a eVGA video card based on the same chipset by nvidia and had the same problem. The default 5.10 install botches up something with the nvidia drivers and xorg settings. Anyways the easiest way to get past this problem is to 
1)do a reinstall of ubuntu, but at the first bootup type in "server" rather then just hitting the enter key. This will do a minimum server install without installing x or desktop manager. Once that is complete you will have a barebones install, and will be placed at a terminal. 
2.)From there login to your account and type in "sudo apt-get update" then "sudo apt-get install ubuntu-desktop". The reason you are doing this is that it will skip the automatic hardware detection that occurs during the breezy install that botches your video settings. When you do the "sudo apt-get install ubuntu-desktop" it will install X then the ubuntu desktop (gnome..etc) but with the vanilla vesa settings for X. 
3.)From there go into synaptic and install the nvidia drivers (they are newer and work fine). Hope that helps....

---

### Post by mips on 2006-01-26
Your Xorg.conf might be fooked, try [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

Look at the first section, How to reconfigure Xorg

---

### Post by AvvY on 2006-01-26
luna6:
Thanx mate, worked like a treat, sure it look a little longer, but I am up and running fine now. I installed the server, then installed ubuntu-desktop, updated the nVidia drivers, ran xorgconfig setup and set it all up easy!

Now onto setting up the rest of my system. It feels so good to use Ubuntu again (haven't in a few months and not the latest version) everything is so slick!

---

### Post by jwj12001 on 2006-01-27
I was really struggling as well as this was my first try of Ubuntu.
After similar scrambled display problems with the 6800gs card, I ran the Xorg config program from the recovery mode (as detailed in the 'mips' link above) and selected the VESA driver with a simple monitor config set to a low res and refresh rate.
This got the GDM going so I could log in and do the synaptic update and install the Nvidia drivers. So i didn't have to do a complete re-install, but was a fairly fraught few hours trying to work it all out!
So, thanks for the tips.

---

### Post by Mr Darcy on 2006-03-16
I have exactly the same problem with my 6800GS.
I've installed Kubuntu 5.10 x64 as a server by following the instructions of Luna6 and am now at the point where the desktop is installed and I'm back to the prompt.
I know this is probably a dumbass question, but how do I get it to start up?
When I tell the system to restart it just boots back to the command line prompt.
Please be gentle with me. This is my first foray into linux.

**** Ah, found it in the post from mips. thanks very much, all ****

If it's any help, my system is;
AMD Opteron 146 processor
XFX 6800GS video
2x1gb Corsair XMS ram
Abit KN8 Ultra mobo
Onboard sound.
250gb Samsung spinpoint sata
200gb Seagate barracuda sata
NEC 4550 DVD-RW
17" TFT monitor

---

