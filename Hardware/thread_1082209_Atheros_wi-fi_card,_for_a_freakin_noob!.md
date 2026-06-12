---
title: "Atheros wi-fi card, for a freakin noob!"
date: 2009-02-27
forum: Hardware
---

### Post by tallicdeth1 on 2009-02-27
I got ubuntu 8.10 Intrepid yesterday, and I'm still having issues with wireless, I found out that it should have worked fine out of the box, but it doesn't so I'm looking for ways to fix this issue, if you're pointing to previous posts on here, explain the functions, I'm still getting used to this.

I'd like to know if I'm looking for a file to edit, or if I'm going to be doing the code in the terminal.

I hate being a noob, but freakin Vista pushed me too far!

---

### Post by stchman on 2009-02-27
> **tallicdeth1 said:**
> I got ubuntu 8.10 Intrepid yesterday, and I'm still having issues with wireless, I found out that it should have worked fine out of the box, but it doesn't so I'm looking for ways to fix this issue, if you're pointing to previous posts on here, explain the functions, I'm still getting used to this.

I'd like to know if I'm looking for a file to edit, or if I'm going to be doing the code in the terminal.

I hate being a noob, but freakin Vista pushed me too far!

Post an lspci output of the PC here in this thread.  We need to know more specific information about the wireless card.

---

### Post by tallicdeth1 on 2009-02-27
```
tallicdeth@tallicdeth-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by tallicdeth1 on 2009-02-27
Ok, so I just tried installing mad-wifi via [http://ubuntuforums.org/showthread.php?t=798485&highlight=Atheros+Communications+Inc.+AR242x+802.11abg+Wireless+PCI+Express+Adapter]("http://ubuntuforums.org/showthread.php?t=798485&highlight=Atheros+Communications+Inc.+AR242x+802.11abg+Wireless+PCI+Express+Adapter")

and I got stonewalled, its not making the wireless work, none of the commands work proper, and I have no clue what to do with any of this mess....

---

### Post by binbash on 2009-02-27
I wrote 2 blog posts, 2 different methods to get it working (ndiswrapper one and other one)

Please check both : 

Method 1 : [http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html)
Method 2 : [http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html)

---

### Post by tallicdeth1 on 2009-02-27
Ok, I did way 27...I can't get online but it will recognize that its there.  I don't know if I should try the other method or not.

edit: I also can't input the connection info when I try to select it.  I can't get this thing to figure out what its doing

---

### Post by 5BallJuggler on 2009-02-27
this works

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by tallicdeth1 on 2009-02-27
ok, that method didn't work, here's teh code

```
tallicdeth@tallicdeth-laptop:~$ sudo aptitude install linux-backports-modules-$
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-backports-modules-$"
Couldn't find any package whose name or description matched "linux-backports-modules-$"
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 52.0MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
tallicdeth@tallicdeth-laptop:~$ sudo aptitude install linux-backports-modules-$(tallicdeth -r)
bash: tallicdeth: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find package "linux-backports-modules".  However, the following
packages contain "linux-backports-modules" in their name:
  linux-backports-modules-intrepid linux-backports-modules-2.6.27-11-server 
  linux-backports-modules-2.6.27-7-server 
  linux-backports-modules-intrepid-server 
  linux-backports-modules-2.6.27-9-generic 
  linux-backports-modules-2.6.27-7-generic 
  linux-backports-modules-intrepid-virtual 
  linux-backports-modules-2.6.27-11-generic 
  linux-backports-modules-intrepid-generic 
  linux-backports-modules-2.6.27-9-server 
Couldn't find package "linux-backports-modules".  However, the following
packages contain "linux-backports-modules" in their name:
  linux-backports-modules-intrepid linux-backports-modules-2.6.27-11-server 
  linux-backports-modules-2.6.27-7-server 
  linux-backports-modules-intrepid-server 
  linux-backports-modules-2.6.27-9-generic 
  linux-backports-modules-2.6.27-7-generic 
  linux-backports-modules-intrepid-virtual 
  linux-backports-modules-2.6.27-11-generic 
  linux-backports-modules-intrepid-generic 
  linux-backports-modules-2.6.27-9-server 
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 52.0MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
tallicdeth@tallicdeth-laptop:~$ sudo aptitude install linux-backports-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 52.0MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 
128060 files and directories currently installed.)
Removing linux-headers-2.6.27-7-generic ...
Removing linux-headers-2.6.27-7 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

```

---

### Post by skriefal on 2009-02-27
I had this issue a few months ago when I tried out Ubuntu 8.10.  Turned out to be a result of bugs in the NetworkManager 0.7 app when used with Atheros wireless cards.  I suggest that you replace NetworkManager with wicd, which you can find at [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php).  Follow the directions on that page to add wicd's apt repository, and then install the wicd package.  This will simultaneously remove NetworkManager.

---

### Post by tallicdeth1 on 2009-02-27
Ok, for some reason wicd is not working the way the command prompt states

```
tallicdeth@tallicdeth-laptop:~$ wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-ket add -
[sudo] password for tallicdeth: 
sudo: apt-ket: command not found
tallicdeth@tallicdeth-laptop:~$ wget -q http://apt.wicd.net/wicd.gpg -O-
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBEjLjXARBADZlh3xU/ea+8ZDvaagLGfm2HW+ezqQULu5bORwdRCZFCIU7Ivs
Xc+LoLA6wZ19i7rmH2esJsDRwPQh9uXFvG9tpShvKS1ZeCWdqkTu94K5dh1jZcBY
x2PReZSO78ee9TEVvyChtoxtPE3fDRve1IIOGkfmE6N7UwvBc78BVtZMhwCg6TcJ
IF4I3HV3yRfIrQ+WQ+PCrIcD/0zypCkYWjPxn5j7M0K/i3qSo9a0IrMqkgR/OwlI
XkeajyTTU83RtAYcxBOXmwQP0SXbmdWuw7G6IeammRoKbJgP8gUj+cAZA9e5PfPO
NHH8V7Nh4tNWJOw8qAAGmobCod/b4zM/P2x8jBYXBmXXKaG+q75PUhwQHq09u25K
5YJjA/9LyCDHbvExQ0KqeOFJmS5gs66SW2L6QbEaI58v/bf+mSdHQew0G4QPrzxQ
CPLBsDW8dkdfrMEp5XAXYnX0kVedGmMYm0nyb+ViYX+7cgOKJ/jr7KMecPCBnVq5
eH5+W87vOZ7sKGcaY3PbVRPQfRpIOT7DkrjFpgoiAUmzbiY47LQkQWRhbSBCbGFj
a2J1cm4gPGNvbXB3aXoxOEBnbWFpbC5jb20+iGAEExECACAFAkjLjXACGyMGCwkI
BwMCBBUCCAMEFgIDAQIeAQIXgAAKCRD+yCD0uMB1WnPRAJ0apOsvtPHExnzPFMl3
d3X4cUYVYQCfQO5dqYO/VljCH6RAx+xxmG+VLxi5Ag0ESMuNdxAIAJl4gDqnnAIX
b84V3Y60v8WKUEh2Mnnm8fJUS/bwi1akQK0zYq1kOyzwk8lzHKwk8ta/H9QWCrii
mmkGVOLEjbgGQ1XGCLysENpnqtS9+d4tv8wAkLfXHsUBqPuRfYd9weks3rmSuzAu
vbzxoYOlqANTLQlY7JB/btWzmZkbmsPkSzldXY6NpdT8y6De1Kr2wSvweHPqJ6FH
J9visouftCDG0NIi2Lliynp45+/lufgY8Npdn8X/WFAMyNHhXDKnM9T+lVCyL6fO
RQZVFs36c7X5UC54D1s6pWBTq8rLoqXIp8o8qx/SEY3PGTeTRYkLR3mlN85bugQG
8/C51xT6Zo8AAwcH/2BArifRmPfiUNOs1uOsEPn2amQA3551HCZ3SJvIqID9V0uQ
8J+wwy2Of+FOFRy7OVGkZ+TXzMNljQUkLnmpVJwQ5uSzHOkvwCcXVRsS2RIks5uk
+zM5Qt8uKxp2UnfakP5W1akuBw8khA9wt34BCKf2g8ZbsdRP5i4TZXur+Vx1TvZG
4ncT0cxfpkZoeuZjxgSXPFyYOuSaEzn7FkOeNkv2gjRQfc1gHQ3jXFcp9sKTVUqB
G88fayzyEmmBD6/LCS47zzvhFT70pve3UO8eaBjqXMnZfEhKhm+SMy6RNYOMSA/x
Qyg84CmxvXVP5WTOhrh6YA7N8v3hKXp/W70oWMaISQQYEQIACQUCSMuNdwIbDAAK
CRD+yCD0uMB1WvbpAKDjW7jJ69HZam6yBzirQDZPpJA26wCghSyIyVRQ5VjxsMPX
w1tbOMzmmxM=
=PjHi
-----END PGP PUBLIC KEY BLOCK-----
tallicdeth@tallicdeth-laptop:~$ sudo apt-key a
```

---

### Post by skriefal on 2009-02-27
You mistyped "apt-key" as "apt-ket"...

---

### Post by tallicdeth1 on 2009-02-27
I got closer by copying the text and then running it on terminal, now I just can't get connected to my wireless

---

### Post by mickey57 on 2009-02-27
[SIZE="5"]**Install the linux-backports-modules-intrepid-generic  from synaptic**[/SIZE]

---

### Post by skriefal on 2009-02-27
> **tallicdeth1 said:**
> I got closer by copying the text and then running it on terminal, now I just can't get connected to my wireless

You'll need to reconfigure the connection with your WEP/WPA key, etc.  You should see a wicd icon that you can click/right-click on to do this.  If you can't find it then reboot first.

---

### Post by tallicdeth1 on 2009-02-27
> **mickey57 said:**
> [SIZE="5"]**Install the linux-backports-modules-intrepid-generic  from synaptic**[/SIZE]

Remember, noob here, gotta tell me where I'm doing this!  I have to learn...

---

### Post by tallicdeth1 on 2009-02-27
Ok, how does one get online, only on a wired connection, but nothing I do seems to work for wireless!?

---

### Post by skriefal on 2009-02-27
Did you reboot, as I suggested above?  If so then wicd should have placed a small network icon in the toolbar area.  Click on that to run the wicd configuration app.  From there you'll be able to set up your wireless or wired connection.

---

### Post by Hobgoblin on 2009-02-28
> **tallicdeth1 said:**
> Remember, noob here, gotta tell me where I'm doing this!  I have to learn...

Open up synaptic package manager (on the system menu).

Search for backports

select linux-backports-modules-intrepid-generic to install, click apply.

After it's installed you'll have a new restricted driver available.  You need to disable the current one then enable the new one (ath5k if I remember correctly).

---

### Post by tallicdeth1 on 2009-02-28
somehow I'm not getting it to come up

when i search, i get nothing

Edit:
Ok, when in package manager, goto origin button. click on us.archive.ubuntu.com/main and look for linux-backports, but it's already installed with the latest version. 2.6.27-11.12

ok, so what am i doing wrong?  I get stuck in a loop on the normal kernel based internet module, and I get stuck without internet connectivity in FF3 with wicd...I'm screwed here

---

### Post by tallicdeth1 on 2009-02-28
OMFG! I'm a freakin NOOB!  In the wicd manager settings I checked run in debug mode, and it connected RIGHT AWAY!!!! Two days, countless blog searches and many pissed off tirades later, it works in two seconds! BAH!

Tthanks for the help to all who offered!!

---

