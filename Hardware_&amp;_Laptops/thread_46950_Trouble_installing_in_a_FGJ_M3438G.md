---
title: "Trouble installing in a FGJ M3438G"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by KLG on 2005-07-06
hello ppl,

I have trouble installing ubuntu 5.04 in a brand new laptop -Fujitsu Siemens Amilo M3438 G
I have already made 3 atempts, and all failed

1st attempt
On my first boot, and while unpacking the packages it stopped in:

> Creating symlink /usr/lib/openoffice/share/dict/ooo -> usr/share/myspell/dicts... 

2nd attempt
stopped while setting xserver-xorg (immediately)

3rd attempt
stopped while setting xserver-xorg 
<7>eth1: no IPv6 router present

and it crashed again

-----
In both 1,2,3 Ctrl+Alt+del doesnt works, a message :
> *ror temporary failure in name resolution 
-----
for you information:
eth0 is an Inter Pro/wireless 2200 BG
eth1 is a  Realtek RTL8169/8110 Family Ethernet Gigabit NIC
Laptop specifications
Intel Pentium M Processor 750
1.86GHz,2MB L2 cache,533MHz FSB
1024MB RAM
80GB+80GB SATA Hdisks
The 1st hdisk is NTFS with WinXP Home SP2
The 2nd hdisk:
12gb ext3 primary  /.
27gb ext3 logical   /home
2.7 gb swap
8 gb FAT32 (1st an 2nd attempt mounted as /windows, 3rd nothing)
rest NTFS
------

Please help, and into serious consideration that i am very very inexperienced linux user, actually i am a rookie . Ubuntu is my 2nd attempt to install linux, (my 1st was RedHat 5.2 8 years ago and it failed miserably)
I hope i am more lucky this time :???:

---

### Post by KLG on 2005-07-06
I am currently working on the same laptop, using ubuntu 5.04 LiveCd, 

As you can see it is working absolutely fine, unfortunately i can't say the same for the InstallCD :-( 

-Actually everything is fine, except the touchpad's "wheel" which is not working

---

### Post by KLG on 2005-07-07
Can't you help ? Is this already answered? I am sorry i couldn;t find it

---

### Post by KLG on 2005-07-07
Another 2 attempts
1st attempt
I found how to deactivate DHCP during installation
[...failure in name resolution...] [SOLVED]
I continued the setup using my native language (greek:'el')

It crashed again in "Setting up xserver-xorg"
"Setting up xserver-xorg
xserver-xorg config warning:selected layout 'el' from 'gr-el_GR' is non-Latin;
adding us to the layout list, Alt+Shift toggles"

This msg was promped many times during the setup procedure with no problem

2nd attempt
Ok if xserver has problems with greek i can install them later, so i installed in english.
 \\:D/  \\:D/  Setting up xserver-xorg OK!!!!
 :? Crashed at setting up cupsys(1.1.23-.......)

Any help? Thank u in advance

---

### Post by hpw on 2005-07-15
[QUOTE=KLG]Another 2 attempts
1st attempt
I found how to deactivate DHCP during installation
[...failure in name resolution...] [SOLVED]
I continued the setup using my native language (greek:'el')

It crashed again in "Setting up xserver-xorg"
"Setting up xserver-xorg
xserver-xorg config warning:selected layout 'el' from 'gr-el_GR' is non-Latin;
adding us to the layout list, Alt+Shift toggles"

This msg was promped many times during the setup procedure with no problem

2nd attempt
Ok if xserver has problems with greek i can install them later, so i installed in english.
 \\:D/  \\:D/  Setting up xserver-xorg OK!!!!
 :? Crashed at setting up cupsys(1.1.23-.......)

Any help? Thank u in advance[/QUOTE]

I had similar problems with my M3438G. 

Have you tried to install it with the "linux acpi=off" switch?

This worked for me on 5.04 Hoary.

br

HPW

---

### Post by hpw on 2005-07-15
[QUOTE=hpw]I had similar problems with my M3438G. 

Have you tried to install it with the "linux acpi=off" switch?

This worked for me on 5.04 Hoary.

br

HPW[/QUOTE]

Oh - i forgot:
Dont expect the soundcard to work ....

---

