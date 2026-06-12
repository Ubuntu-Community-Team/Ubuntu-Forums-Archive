---
title: "HELP: My computer did not start after upgrading Ubuntu 8.04 to 9.04"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by jhoeijao on 2009-06-25
I manage to install Ubuntu 8.04 in my computer before using the graphical installation by pressing F4 at start and Use safe graphics because I can't install it using the default setup. Just today I upgraded it using 9.04 alternative CD but after restarting it my Ubuntu 9.04 does not boot and I think the problem is my built in video card.

Here are the info's about my motherboard: 

```
[COLOR=Red]olshs10@olshs10-desktop:~$ sudo lspci[/COLOR]
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
olshs10@olshs10-desktop:~$ 
[COLOR=Red]
olshs10@olshs10-desktop:~$ sudo glxinfo | grep direct[/COLOR]
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
olshs10@olshs10-desktop:~$
```

---

### Post by Divider on 2009-06-25
First off, thats a huge post. lol.

Next Can i get an lspci from you.

```
sudo lspci
```

repost that and any info you have on your intergrated card.

and if possible...

```
sudo glxinfo | grep direct
```

type that above exactly as its seen.

---

### Post by jhoeijao on 2009-06-25
> **Divider said:**
> First off, thats a huge post. lol.

Next Can i get an lspci from you.

```
sudo lspci
```repost that and any info you have on your intergrated card.

and if possible...

```
sudo glxinfo | grep direct
```type that above exactly as its seen.

Sorry... :) just a noob in Ubuntu. I don't know the commands yet.

---

### Post by jhoeijao on 2009-06-25
Now I have edited my post. Thanks for the commands anyway but I need help on this problem.

---

### Post by jhoeijao on 2009-06-25
Need help on this problem please.

---

