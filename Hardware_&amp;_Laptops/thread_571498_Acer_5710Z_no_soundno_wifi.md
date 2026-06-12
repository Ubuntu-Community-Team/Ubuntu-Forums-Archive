---
title: "Acer 5710Z no sound/no wifi"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by manbill on 2007-10-09
Hi:

I've read that Acer offered an Aspire 5710Z powered by Ubuntu for Singapore customers.
I've purchased this laptop in Spain, but neither mi sound nor my wifi works properly with Ubuntu (Feisty & Gutsy).

Does someone know which version of Ubuntu works ok with this laptop?

I've been seeking in forums for the tweaks to get all my hardware working 100% with no success. 

Need some help!!.

Thanks in advance.

P.S.
I can post what you need to help me. Please tell me what must I do.

---

### Post by cubeist on 2007-10-09
The first step is to post the ouput of "lspci" ... just type that in your terminal and it will show the hardware detected by your computer...

---

### Post by manbill on 2007-10-09
This is the lspci output command

 ```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
06:00.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:00.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:00.2 FLASH memory: ENE Technology Inc Unknown device 0720
06:00.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

```

As you can see, the wireless is an AR5006EG, but  under the laptop there is a sticker with the AR5BXB63 code.
The sound apparently works fine, but the speakers are mutted.

What more?...

Thanks.

---

### Post by cubeist on 2007-10-09
I have no personal experience with atheros cards... but lots of people seem to have trouble with them.

There is one site with a specific driver that should work with your card, but you will have to browse through that site to be sure...

[http://madwifi.org/](http://madwifi.org/)

---

### Post by manbill on 2007-10-10
After several days of investigation, i am thinking that the problen is not in the wireless or the sound drivers. Instead, i am thinjing the main problem could be in the ACPI interface.

None of the buttons that activate the wireless or the mail works, so i'm working with acer_acpi to see what can i do...

Thanks after all.

---

### Post by cubeist on 2007-10-11
hmm, usually acpi is more of a power thing... I know that to get my hp to boot from a live cd I have to turn off acpi with the noapic, nolapic, noapci options at boot.  You could try that and see if your buttons work.   BUT! be cautioned because acpi is sometimes needed to control computer temp... for example my computer fan doesn't run without acpi so I have to make sure I don't do anything that will overheat the beast!

---

### Post by danigb on 2007-10-13
i've bought the same computer and i was able to turn on the wifi (but i'm so exhausted that i didnt try with the audio driver). 

briefly: madwifi doesnt support the drivers yet, so you have to install ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
dont forget to disable the hal modules!

also you have to turn on the wifi. you can do it with acer_acpi:
[http://www.ubuntu-es.org/index.php?q=node/42148](http://www.ubuntu-es.org/index.php?q=node/42148)
and
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

i dont remeber where i found the drivers, but i made a google with:
AR5006EG
that is the name of the wifi driver and i found it... you can ask me for them:
danigb  (en gmail)

it worked for me!!

good luck, and if you found how to turn on the audio, i wil apreciate!!
saludos
dani

---

### Post by manbill on 2007-10-13
Ok, Ok... we're on the way...

If I boot my laptop with acpi=off...  tachan!!! the ubuntu initial "melody" sounds at a louder level...

So, the drivers are ok.. the problem is how do we activate the speakers when we boot with acpi on?...
There's a new deb acer_acpi package on [http://code.google.com/p/acer-acpi-deb/]("http://code.google.com/p/acer-acpi-deb/") but i've tried with no luck...

Seguimos en la búsqueda...
Saludos.

---

### Post by manbill on 2007-10-14
OK this looks better...

The wifi-adapter AR5XBX63 is working!
I'm using ndiswrapper 1.48 and acer_acpi. The drivers are from XP.
thanks! danigb. Those tutorials were tried with no luck before. But...

Now...
The Webcam, works too with amsn.

Only the sound is missing...

Saludos.

---

### Post by manbill on 2007-10-19
Hi:

If you have this problem with the touchpad:

```
Oct 14 09:25:47 baco kernel: [   39.852000] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
Oct 14 09:25:47 baco kernel: [   39.872000] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
```

add this ```
i8042.reset i8042.nomux
``` to the /boot/grub/menu.lst

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=616d8f17-1544-45c9-9f60-7de76c4bc6b6 ro quiet splash i8042.reset i8042.nomux
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

The i8042.reset i8042.nomux corrects the problems with the touchpad.

The problems with the sound follows, but now a I think could be a misconfiguration due to the modem because the volume control and the osd indicator works well thus the fn+f8.

Have you found something? 

Thanks.
Saludos.

---

### Post by Goh on 2007-10-19
Hi guys 

i just bought this laptop on Wed, immediately i installed ubuntu 7.04 and ecnounter the same problems.
I am using wired ADSL modem. Does anyone knows how to make it work for the interent connection? No sound as well. I tried Fedorea too but having the same two issues here. And later I found from Acer that this model does not support XP drivers only Vista...:P I am really stuck here :(

Can anyone help? I guess i have the same result with lspic.

Regards
Goh

---

### Post by danigb on 2007-10-19
no luck with the audio driver :(

i will keep you informed here
saludos
dani

---

### Post by Goh on 2007-10-20
hmm.. at least you have the wirless connection up...but mine using erthnet adsl wired...and cant use..:(

---

### Post by danigb on 2007-10-21
the ethernet connection worked perfectly for me at the first installation. can you detail your problems? (lspci helps a lot!)

saludos
dani

---

### Post by Goh on 2007-10-22
The lspic shows exact as what ManBill has shown earlier. I tried vista and the configurations works fine. Well at least its not the hardware that spolit iinstead its the configuration problem:). phew ( i have to try since i just bought it last wed).

hmm...i am using adsl modem from prolink. While i connect to the cable, the icon on the top right shows that i am connected and the sound icon is unmuted. But no sound comes out. So what would you want to see? Do you really need the outpu of lspic?
Thanks.

Regaards
Goh

---

### Post by manbill on 2007-11-03
yeeeehhhhaa!!!

Now everything is working!...
I've got it!!


Simply follow these instructions... [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)


Saludos...

---

### Post by Goh on 2007-11-04
hmm..which method did you use? I tried installing the backport generic module and add the line of code in alsa-base. But nothing happens. Any specific steps i miss or using other method as the link illustrate?
Thanks.

---

### Post by danigb on 2007-11-22
ooeee!! sound in linux!!
what i did:

sudo apt-get install linux-backports-modules-generic
added this line in /etc/modprobe.d/alsa-base: options snd-hda-intel model=acer

reboot... and hear the drums!

:guitar:

---

### Post by manbill on 2007-11-25
Hi again:

First of all, i apologize Goh, because since everything was working on my laptop, I didn't visit this topic.

Today I was surfing the net, and saw your question. I hope you'll be already interested.

The method used was the E method, as danigb said, is based on the instalation of a patch and the linux-backports-modules for the current kernel.

This was the last thing a needed, because the webcam worked with no problem in aMsn and Skype Beta 2.0. 

The problem with the internal mic was solved changing the preferences on the gnome-alsa-mixer applet (doubleclick on the loudspeaker on the top panel) and check the Internal mic Boost channel.

Those problem referred to the adsl/usb modem haven't been probed because I have no the appropiate hardware.

So, that's all. I hope this will be usefull for you.
Regards from Spain.

---

### Post by Bukarts on 2008-04-27
1. This is my first introduce with Linux! So please dont lugh about me! I got the wi-fi but i still cant get Sound! I installed drives i culd found but no luck! Then I tried to add line to alsa base but it says that i have no permission! So the question How to get this permission??

---

