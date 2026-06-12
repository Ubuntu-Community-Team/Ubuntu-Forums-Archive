---
title: "Flickering Mouse Ubuntu 14.04 (Sometimes it dissapear)"
date: 2015-01-02
forum: Hardware
---

### Post by eduardo22 on 2015-01-02
Hi friends, as you can see, i'm new here, and it's because i'm new on ubuntu too, but, i'm a little bit scared because my pointer mouse is flickering too much and sometimes it disappear, i used to connect dual screen, the onboard VGA on my pc HP COMPAQ 6200 and another video card (ATI).

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X600/X600 SE]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV380 [Radeon X300/X550/X1050 Series] (Secondary)

And. (Built in)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


My complete log is:


```
eduardo-poo@HP-Compaq-6200-Pro-MT-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Q65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X600/X600 SE]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV380 [Radeon X300/X550/X1050 Series] (Secondary)


```

Some ideas?

P.S. Sorry for my bad english, my native language is spanish.
Thanks.

---

### Post by Bucky Ball on 2015-01-02
Welcome. What are the details of the mouse? Is it wireless or plugged in USB? A standard, generic mouse or something special? Does it work with other OSs (Windows for instance)?

PS: Your English is fine. ;)

---

### Post by eduardo22 on 2015-01-03
> **Bucky Ball said:**
> Welcome. What are the details of the mouse? Is it wireless or plugged in USB? A standard, generic mouse or something special? Does it work with other OSs (Windows for instance)?

PS: Your English is fine. ;)

Thanks for the support. 

Yes, my mouse works fine on Windows, is USB, i guess it's a generic mouse, with two triggers and one trackball.

I'm very scared because this OS seems to be great, but today i've been trying to find the pointer on the screen many times and all i can do is move slowly and see when some button or links are focused.

Really i feel like a blind sometimes :c

Thanks

---

### Post by Bucky Ball on 2015-01-03
Try this. Type control+alt+t, then this line:

```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

If the command comes up with a 'Permission denied' error, try it with 'sudo' first, like:

```
sudo gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

Hit return after typing (or pasting) the command into the terminal. Once finished, close the terminal and reboot. Any different?

Info from [THIS]("http://askubuntu.com/questions/362321/no-mouse-pointer-ubuntu-13-10") thread.

---

### Post by eduardo22 on 2015-01-04
> **Bucky Ball said:**
> Try this. Type control+alt+t, then this line:

```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

If the command comes up with a 'Permission denied' error, try it with 'sudo' first, like:

```
sudo gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

Hit return after typing (or pasting) the command into the terminal. Once finished, close the terminal and reboot. Any different?

Info from [THIS]("http://askubuntu.com/questions/362321/no-mouse-pointer-ubuntu-13-10") thread.

Hi, nothing happens, still flicker a lot and disappear sometimes. As i  can see, the mouse seems to work normal just when i disable the  secondary screen. but... in windows use to work fine in both screens (i  have dual OS too) so i can see their both behaviours. Thanks for the  support.

---

