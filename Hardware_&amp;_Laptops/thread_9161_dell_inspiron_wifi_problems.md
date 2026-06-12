---
title: "dell inspiron wifi problems"
date: 2004-12-25
forum: Hardware &amp; Laptops
---

### Post by Krash1201 on 2004-12-25
installed ubuntu fine.  pretty sure i installed ndis wrapper 0.12 correctly.  had no problem installilng the .inf for the chipset, a broadcom corp. BCM94306 802.11g.  thats no problem.  the error comes when i try to set up the connection.  through gnome network set-up, it does not see the hardware.  when i run ifup wlan0, it won't recognize the hardware.

anyone have any ideas?

Thanks in advanced.

---

### Post by varunus on 2004-12-26
What is the output of "iwconfig"?

Also, what is the output of "lsmod"?

---

### Post by Krash1201 on 2004-12-28
user@computer:~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


user@computer:~ $ lsmod
Module                  Size  Used by
radeon                129252  2
acpi                    5996  0
proc_intf               3776  0
freq_table              4196  1 acpi
cpufreq_userspace       5240  2
cpufreq_powersave       1728  0
ipv6                  256996  8
ds                     18436  2
button                  6584  0
ac                      4812  0
battery                 9388  0
af_packet              22088  0
ohci1394               34884  0
ieee1394              108408  1 ohci1394
yenta_socket           20992  0
pcmcia_core            68404  2 ds,yenta_socket
b44                    21476  0
mii                     5056  1 b44
snd_intel8x0m          19656  0
snd_intel8x0           35468  0
snd_ac97_codec         67844  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            52968  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                95140  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              24900  1 snd_pcm
snd_page_alloc         11432  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7776  1 snd_intel8x0
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  1 snd_rawmidi
snd                    55300  10 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  1 snd
ehci_hcd               30756  0
uhci_hcd               31952  0
usbcore               115684  4 ehci_hcd,uhci_hcd
pci_hotplug            33680  0
intel_agp              22112  1
agpgart                33640  2 intel_agp
rtc                    12536  0
pcspkr                  3592  0
nls_cp437               5696  1
ntfs                  100276  1
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
parport_pc             34752  1
lp                     10724  0
parport                40712  2 parport_pc,lp
ide_cd                 41572  0
cdrom                  39392  1 ide_cd
tsdev                   7232  0
evdev                   9440  0
mousedev               10220  1
psmouse                19720  0
ext3                  123880  1
jbd                    60824  1 ext3
mbcache                 9092  1 ext3
ide_generic             1408  0
piix                   13088  1
ide_disk               18752  4
ide_core              136120  4 ide_cd,ide_generic,piix,ide_disk
unix                   28080  701
fan                     3980  0
thermal                12976  0
processor              17392  2 acpi,thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb

---

### Post by clsdaniel on 2004-12-29
My Laptop (an HP Pavilion ze4900 actually) uses the same wifi card, i already submited some instructions on how to set it up to linux-laptop.net, but it seems they didn't accept it (it may be poorly written maybe), but i give detailed instructions on how to setup this wifi card, it may help you as well:

[http://www.geocities.com/clsdaniel/ze4900.html](http://www.geocities.com/clsdaniel/ze4900.html)

Good luck.

---

### Post by Krash1201 on 2004-12-30
followed those instructions and i still have nothing.  it installed and created all the directories fine, but when i did iwconfig, wlan0 wasn't listed, and the three other network devices listed as not wireless.  the network config tool in gnome won't recognize the broadcom card either.  any ideas?

---

### Post by clsdaniel on 2004-12-30
Maybe there is a difference with software installed, i got the latest linux-wlan-ng installed and i'm using a custom 2.6.9 compiled kernel, maybe something of that makes my card work. Scary, maybe i should not move my laptop from current distro.

I'm using slackware on this machine, a bunch of things are compiled from sources. I don't know what versions are abailable from ubuntu repositories.

Good luck

---

### Post by Krash1201 on 2004-12-30
i compiled the package from kernel 2.6.8.1-3-686, and ndis wrapper seemed to install fine.  i run ndis wrapper to install the windows driver no problem from my windows partition mounted on my desktop.  then i do modprobe ndiswrapper, and it creates the module.  then i save the module, ndiswrapper -m, and it sets up the wlan0.  after doing this i go to the gnome network setup, and ubuntu doesn't recognize my wireless card.  all the settings under iwconfig and ls are listed earlier in this thread and they don't look to have changed.  i can use my wireless card through windows just fine.  any ideas?

Thanks

---

### Post by clsdaniel on 2004-12-31
Well, as last resource, you can buy a supported wireless card, like a D-Link DWL-650, it works pretty well for me, and you can find them for 4 or 5 dollars, altough is a b card, that is why is so cheap.

Good luck.

---

### Post by Krash1201 on 2005-01-01
after looking at more commands, going through the instalation wiki from sourceforge again, and reviewing what the terminal outputs are, i came across these discrepancies.  i have installed ndis-utils which is ndiswrapper version 0.10, using bcwml5a.inf from the AR directory of the dell driver, as per the wiki instructions.  after the install of the driver which is no problem, i modprobe and check the system log.  when i check the system log, i get ndiswrapper version 0.10, failed to initialize wireless device, and then it will recognize the driver.  i think the failure to initialize the graphics card is what is preventing wlan0 from being recognized.  any ideas?  could leaving the wireless card enabled at windows shutdown possible fix the problem?

---

### Post by angrylittleman on 2005-01-01
The graphics card should not really impact your system.  If you are getting your x-server to start, then the graphics card should be working ok (now whether it is running the correct ati or nvidia drivers is another matter :P)....Windows should not have any impact on how the Ubuntu operates in terms of your wifi card, aside from you needing the driver for it to operate.  

clsdaniel has a good idea, you can never have enough wifi cards (says the guy with three laptops and one wifi card)..... :P

---

### Post by clsdaniel on 2005-01-02
ummmm, this is quite weird, but yes, the graphics card should not stop you from using you wireless card, my graphics card also failed and the screen blinked a few times (no, that was not X, was the console framebuffer driver) and wifi worked ok.

I suggest you to try to compile yourself the newer ndiswrapper (which is at version 0.12) and also you can try the driver from HP, you don't loose anything with trying, also don't forget to uninstall previous drivers :).

If you have any problem decompressing the driver, like that the setup program will deny to work on your laptop, then reply, i can send you the files you need by mail or something.

Cheers!

---

### Post by Snomad on 2005-01-05
Hi,

A longshot probably but quick to try out:

[http://www.ubuntuforums.org/showthread.php?t=660](http://www.ubuntuforums.org/showthread.php?t=660) (last post)

HTH.

Cheers, Dave.

---

### Post by Krash1201 on 2005-01-09
my bad, not the graphics card i am having a problem with, its the wireless card that won't initialize.  i am going to try updating to the newer version of ndis wrapper, with the older driver.  the problem is finding time to do the work and test.  thanks for the help thus far, i doubt this is the end of my questions though.

---

