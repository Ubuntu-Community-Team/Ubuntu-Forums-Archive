---
title: "Laptop Screen Causing RFI"
date: 2019-02-28
forum: Hardware
---

### Post by adkinsc on 2019-02-28
I hope this is the right place for this. I have 18.04LTS and a 2m ham radio. I'm getting interference in my radios when the screen on my laptop is on. I have a dual boot with W10 and it doesn't do it when the W10 partition is booted. I hate using W10 and would like to get my Ubuntu and radios to play nice. Just seeing if anyone had any suggestions on where I should start troubleshooting. My laptop is an HP DV7. Thanks

---

### Post by kc1di on 2019-03-01
Hi adkinsc and Welcome to Ubuntu from another Ham,
RFI can be a bear to track down.  It's actually most often caused by the power supply.  Perhaps Ubuntu puts extra strain on that.  try unplugging the power supply  if you have it plugged in and see if the RFI goes away?
if it does then get some of those snap on rf beads and place a couple on the power cord and output cord see if that will control it. 
Good luck.

---

### Post by adkinsc on 2019-03-01
@kc1di Well, my battery doesn't hold a charge any more so as soon as i unplug the power the rfi goes away but the laptop also goes dead lol. I do have some snap on beads on a monitor cable in my junk somewhere. I'll give those a try. It seems to be in the lcd or backlight though. Whatever it is it's pumping out massive amounts, I can go outside and its almost all the way around the house. 73 ke8lnf

---

### Post by Autodave on 2019-03-01
Realize that your battery will absorb some of that noise.  The fact that it is bad could be causing some or all of that noise.  And, I understand that it doesn't do it on Windows, but it could still be the problem on Ubuntu.

---

### Post by adkinsc on 2019-03-01
I just figured out if i execute "xset dpms force off" as soon as the screen turns off the rfi disappears. I'm still going to try the snap on beads as it could be from the screen drawing more power through the power supply but I'm still leaning towards it being the lcd or backlight. I might also try installing a different flavor of linux to see if it just my installation. I did manage to screw up my sound config a couple weeks ago, maybe that wasn't all that got wonky.

---

### Post by kc1di on 2019-03-01
when you get into the ubuntu desktop install inxi ```
sudo apt install inxi
```
then exicute this command and post the output here.  ```
inxi -Fxz
```

---

### Post by adkinsc on 2019-03-01
```
inxi -Fxz
System:    Host: DV7 Kernel: 4.15.0-45-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu2) Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion dv7 Notebook PC v: 058C110000244720001620100 serial: N/A
           Mobo: Hewlett-Packard model: 165B v: 10.31 serial: N/A BIOS: Hewlett-Packard v: F.1B date: 10/05/2011
Battery    BAT0: charge: 0.0 Wh 0.0% condition: 66.4/98.2 Wh (68%) model: Hewlett-Packard 8850 status: Charging
CPU:       Quad core Intel Core i7-2630QM (-MT-MCP-) arch: Sandy Bridge rev.7 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15963
           clock speeds: max: 2900 MHz 1: 798 MHz 2: 798 MHz 3: 798 MHz 4: 798 MHz 5: 798 MHz 6: 798 MHz
           7: 798 MHz 8: 798 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915 Resolution: 1600x900@60.08hz
           OpenGL: renderer: Mesa DRI Intel Sandybridge Mobile version: 3.3 Mesa 18.2.2 Direct Render: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card: Broadcom and subsidiaries BCM4313 802.11bgn Wireless Network Adapter driver: wl bus-ID: 07:00.0
           IF: wlo1 state: up mac: <filter>
Drives:    HDD Total Size: 750.2GB (6.5% used)
           ID-1: /dev/sda model: Hitachi_HTS54757 size: 750.2GB temp: 0C
Partition: ID-1: / size: 343G used: 46G (14%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 296 Uptime: 7:30 Memory: 2106.0/5908.1MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```

---

### Post by kc1di on 2019-03-02
Only thing I can think of is that the battery being dead puts extra stress on the power supply.  Let us know how the rf beads work out and if it makes any difference. 
The Ubuntu graphic's driver may also be stressing the system where the windows one does not. I'm not sure if it's not the P.S. that there would be anything you can really do for that machine. But maybe some one has dealt with the problem before.  73, Dave
P.S. found this [You Tube video]("https://www.youtube.com/watch?v=zNByPgCAuUc") which may be of help

---

