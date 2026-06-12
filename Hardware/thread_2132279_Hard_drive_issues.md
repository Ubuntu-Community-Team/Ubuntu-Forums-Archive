---
title: "Hard drive issues"
date: 2013-04-04
forum: Hardware
---

### Post by FrankBarmentlo on 2013-04-04
I am fairly new to linux, and ran in a few problems since installation on my laptop
most of them are just solved by doing some research, but one of them really bothers me: my harddrive reaches temperatures between 45~50 degrees celsius, on idle.
it also feels like the disk is spinning at full speed, which shouldn't be the case.
technical details:
hard drive is a st750LX003,
laptop is a samsung rc730-s02nl(if relevant)

this is the top5 results in Iotop:
> 
338 be/3 root          0.00 B    260.00 K  0.00 %  0.58 % [jbd2/sdb4-8]
6699 be/4 frank         0.00 B     24.00 K  0.00 %  0.02 % chromium-browser
8742 be/4 frank        64.00 K     52.00 K  0.00 %  0.02 % konsole
6689 be/4 frank         0.00 B     92.00 K  0.00 %  0.01 % chromium-browser
6691 be/4 frank         0.00 B     44.00 K  0.00 %  0.00 % chromium-browser

ah, maybe this is a nice addition:
[IMG]https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-ash3/45647_150884141747340_1537976653_n.jpg[/IMG]


edit after a lot of thinking and researching:
could it be a driver issue? could it be an issue with Ext4? one of my teachers(ubuntu-user), told me it could be the way ext4 works, and going back to ext3 could solve my issue..
it doesn't happen in windows 8(NTFS), at all.. no changes, no high temperatures.. just 30 degrees celsius.

I am not sure what to post more, so let me know if more information is needed.
kind regards,
Frank

---

### Post by vandorjw on 2013-04-04
Usually the hard drive is the least problematic. I doubt very much ext3 vs ext4 will make a difference.

My first suggestion is to go to a store, and get yourself a can of compressed air. Get all the dust out of your fans and fix the air flow.
It is far more likely to me that your GPU is heating up your computer, and this heat is being absorbed by your hard disk.

See, your hardisk is always spinning at 7200 revs. The only additional movement (and therefor heat) can be caused by the head moving up and down the platter.
It seems impossible to me that this causes a difference of 10degrees celcius.

Cheers

---

### Post by gordintoronto on 2013-04-04
Put things in context: your body temperature is 37, so 45 isn't all that hot. There are a few programs which are intended to reduce laptop temperatures; generally they trade off performance for power consumption. Have a look at laptop-mode-tools.

---

### Post by tgalati4 on 2013-04-04
What is your drive's idle timer set to?

tgalati4@Mint14-Extensa ~ $ sudo idle3ctl -g /dev/sda
Idle3 timer set to 80 (0x50)

tgalati4@Mint14-Extensa ~ $ sudo idle3ctl -s 158 /dev/sda
Idle3 timer set to 158 (0x9e), which is several minutes.

This was a work-around for a Western Digital Scorpio Blue drive that had too many load cycles:

  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       523
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   092   092   000    Old_age   Always       -       8592
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       272
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       12687

You might want to check your load cycle count.  When they get to hundreds of thousands, then your drive arm wears out.

It's possible that your drive is not going into power-saving mode.  There is typically an *hdparm* switch for that.  Also check your BIOS for energy saving options.  It's possible that Windows sets energy use lower to get bettery battery life--regardless of what the BIOS setting is.  Linux tends to respect the BIOS setting.

---

