---
title: "No audio on headphones, only on internal speakers"
date: 2011-09-01
forum: Hardware
---

### Post by jmarta on 2011-09-01
Hello
I have a VAIO Model: VPCEH14FM running Ubuntu 11.04, when I connect headphones the sound keep going out to the internal laptop mini-speakers and there is no sound on headphones.

I have tried on alsa-base.conf adding at the end
options snd-hda-intel model=vaio or 
options snd-hda-intel model=sony or
some other variants but there is no change

My alsa information:
[http://www.alsa-project.org/db/?f=c1905301d04acc50cd930afaef8c9347d7781ff7](http://www.alsa-project.org/db/?f=c1905301d04acc50cd930afaef8c9347d7781ff7)

My lspci output:
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
0d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)



Please recommend 


Thank you
:p

---

### Post by jim78880 on 2011-09-01
I am running 11.04 on a HP-dv7, and I have the opposite problem.  I have sound on the headset BUT the internal speakers also continue working.   I just moved back to Ubuntu from openSuSE and they had a relatively simple fix for this problem.  In their /etc/modprobe.d directory they had a file called 50-sound.conf
which contained the following code:

options snd-hda-intel model=hp-dv5 enable_msi=1
options snd slots=snd-hda-intel,snd-hda-intel
# 5Dex.54Z4e7pBsC8:SBx00 Azalia (Intel HDA)
alias snd-card-0 snd-hda-intel_msi
# l4dC.5MBuk33R4dE:ATI Technologies Inc
alias snd-card-1 snd-hda-intel

I'm sure that somewhere in /etc/modprobe.d/alsa-base.conf There is someplace to make changes similar to this.  Can anybody help.  It might just fix both of our problems.

Jim

P.S.  I just fixed the problem!

JMARTA you might try this and see if it fixes your problem too.

I decided "What the hey, and copied the file I mentioned above (50-sound.conf) into the /etc/modprobe.d directory.  I figured the worst that could happen was that I would have to delete it and reboot.  Amazingly IT WORKED!!!

Good Luck
Jim

---

### Post by jmarta on 2011-09-01
Thank you Jim

I copied:
options snd-hda-intel model=hp-dv5 enable_msi=1
options snd slots=snd-hda-intel,snd-hda-intel
# 5Dex.54Z4e7pBsC8:SBx00 Azalia (Intel HDA)
alias snd-card-0 snd-hda-intel_msi
# l4dC.5MBuk33R4dE:ATI Technologies Inc
alias snd-card-1 snd-hda-intel

to the end of the file alsa-base.conf and did not fix the problem.
I copied at the end because all the blogs recommends append these options at the end.

Jorge

---

### Post by .... on 2011-09-02
> I have tried on alsa-base.conf adding at the end
options snd-hda-intel model=vaio or 
options snd-hda-intel model=sony or
some other variants but there is no change


It would work better if you actually used one of the defined models for your system instead of making them up or using fixes from other laptops ;) (Please don't take my condescension too seriously as I realize the alsa model system is completely unintuitive).
Here's the list for your codec. Try thinkpad and ideapad first:
```
Conexant 5066
=============
  laptop    Basic Laptop config (default)
  hp-laptop    HP laptops, e g G60
  asus        Asus K52JU, Lenovo G560
  dell-laptop    Dell laptops
  dell-vostro    Dell Vostro
  olpc-xo-1_5    OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad    Lenovo Thinkpad
```
When you try a new model keyword, use this to reload ALSA:
```
sudo /usr/sbin/alsa force-reload
```

---

### Post by jmarta on 2011-09-02
Thank you very much
It was an excellent recommendation.

It is working now:
Only two of them did not work with external speakers
now testing the microphone reduces the success options.
Finally I selected "ideapad"

It is a summary:
laptop               Does not work
hp-laptop          Works internal and external speakers;  Microphone only external with a little noise
asus                 Works internal and external speakers;  Microphone only external with a little noise
dell-laptop         Does not work
dell-vostro        Works internal and external speakers;  Microphone both internal and external
olpc-xo-1_5       Works internal and external speakers;  Microphone does not work
ideapad            Works internal and external speakers;  Microphone both internal(sounds best) and ext.
thinkpad           Works internal and external speakers;  Microphone both internal and external

So I have dell-vostro, ideapad and thinkpad as working options but I selected ideapad because the internal microphone sound a little better that others(a little)

Recommendation for others with same problem on same machine:
Add: options snd-hda-intel model=ideapad 
at the end of the file with:
sudo gedit /etc/modprobe.d/alsa-base.conf

Thank you a lot

Jorge

---

### Post by soulman8605 on 2012-01-03
excellent suggestion this worked perfectly

---

