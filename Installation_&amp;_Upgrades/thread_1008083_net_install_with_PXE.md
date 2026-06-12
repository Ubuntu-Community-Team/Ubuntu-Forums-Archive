---
title: "net install with PXE"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by la1234uk on 2008-12-11
:popcorn:

Hi,

I succeded to install Xubuntu via a PXE netboot.
I had difficulties to find information to do this, after several days of struggle I made it. I want to post here how I did it.

The background:

1) a Toshiba note book (Dynabook SS) without a CD-ROM. Bios allows a PXE net booting.
I call this machine "the host" from now on.
2) another notebook with windows XP installed (Panasonic "Let's note"). I call this machine "the server" from now on.
3) a router. The two PCs are connected by LAN cables to this router. The router is connected to the external world (internet) by a third cable.

In short:

- I dowloaded a Xubuntu iso file and burned it to make a live CD
- I verified the existence of the folder "netboot" in the live CD
- downloaded a TFTP server for windows ([http://tftpd32.jounin.net/tftpd32.html]("here"))
- I setted the server this way:
0) you will see a main menu with several tabs. I changed only the mentioned below:
1) Current directory: "the directory where the pxelinux.0" file is. Usually it is located in "...\netboot\ubuntu-installer\i386\"
2) [COLOR="DarkRed"]DHCP server:[/COLOR] IP Pool starting address: I put the IP address for the host. If you are under a fixed IP environment you MUST give the correct IP address. I was in this situation and I had to ask for an extra IP address.
  [COLOR="DarkRed"] Size of pool[/COLOR]: I put "1" because I had only one PC to install.
[COLOR="DarkRed"]Boot file:[/COLOR] pxelinux.0
[COLOR="DarkRed"]WinDNS server:[/COLOR] I put the IP of my DNS server. If you do not know yours, just open a COMMAND PROMPT windows and execute "ipconfig/all". 
[COLOR="DarkRed"]default router:[/COLOR] to discover what it was, I disconnetted all cables, I connected only the windows PC (server) to the router via a single LAN cable. The router was NOT connected to anything else. If I reset the PC and execute ipconfig/all on the command prompt window, I saw the IP of the router. Then I connected again the other PC (host) and the main internet cable to the router.
[COLOR="DarkRed"]mask: [/COLOR]in my case was 255.255.255.0 as copied from ipconfig/all
domain name: I put my name
3) PRESS SAVE buttom (vertically placed in the center)
4) press "setting"
base directory: I put the same as in 1) 
Checked PXE compatibility
press OK
5) press save again.
- at this point I boot the other computer, press F12 to enable PXE boot

that was it.

SMALL PROBLEMS I ENCOUNTERED:

- I had to modify the pxelinux.cfg/default file to match the folder names. The host computer booted, but gave "file not found" when loading files. The TFTP32 application use the base directory you give it. If you have the same problem (file not found) check that the paths are OK in the default file.
- once the net boot started I was asked for the proxy name, I gave it and nothing worked. After one day of struggling I noticed ... proxy name MUST be given with http:// in front of it and :8080 at the end. (if you port number is 8080)...!!

good luck and report if you have any success/problems.

---

