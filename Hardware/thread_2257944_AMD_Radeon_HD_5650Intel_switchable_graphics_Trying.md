---
title: "AMD Radeon HD 5650/Intel switchable graphics: Trying to get vgaswitcheroo to work"
date: 2014-12-23
forum: Hardware
---

### Post by jack124 on 2014-12-23
[COLOR=#333333][FONT=UbuntuRegular]I'm fairly new to linux.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I understand that the fglrx drivers don't work with the Radeon HD 5XXX dedicated card, but I'm wondering if anyone is aware of other options to be able to switch from the on-board Intel graphics card to my Radeon HD 5650 graphics card. I have the HP Envy 14 Beats Edition laptop.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've had to reinstall ubuntu a few times now after trying and failing to get the fglrx drivers to work properly. After installing the drivers and restarting my computer, it goes into low graphics mode and I can't get out of it. Because of this, I've abandoned trying to get fglrx to work properly, and now I'm trying for vgaswitcheroo to solve my problems.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm now trying to use vgaswitcheroo (which appears to be present in 14.04). I'm following [this guide]("http://forums.linuxmint.com/viewtopic.php?f=49&t=139413"), but my outputs are telling me that my discrete card is not beign activated, and it's staying on the intel chip.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm on the **MUXed systems** section, because my laptop is MUX, not MUXless.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I enter the command:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]while i'm in root, and the output from cat /sys/kernel/debug/vgaswitcheroo/switch gives me:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynPwr:0000:01:00.0
2:DIS-Audio: :Pwr:0000:01:00.1
[COLOR=#333333]
```
[FONT=UbuntuRegular]
This makes sense, because the discrete card should only get turned on after I log out and back in. the problem is, when I log back in, the output is exactly the same:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynPwr:0000:01:00.0
2:DIS-Audio: :Pwr:0000:01:00.1
[COLOR=#333333]
```
[/COLOR][COLOR=#333333][FONT=UbuntuRegular]
And it appears that the discrete card is not being activated.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Does the version of ubuntu I'm using (14.04 x86_64 LTS) have anything to do with this?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can anyone help me out?[/FONT][/COLOR]

---

