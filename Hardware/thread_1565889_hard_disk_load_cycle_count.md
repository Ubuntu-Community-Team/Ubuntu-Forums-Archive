---
title: "hard disk load cycle count"
date: 2010-09-01
forum: Hardware
---

### Post by lecterror on 2010-09-01
Hi folks!

A fresh install of Ubuntu 10.04 on a brand-spankingly-new WD Green 1.5TB.

Since I've never owned a WD before, I've been watching it very carefully.. I've been reading a lot about dying disks, and although I've never had one drop dead (long live Seagate?), I'm a bit suspicious here..

My hard disk LED is blinking every ~1.5 seconds, and every ~15-20 seconds I hear a very faint click. It's barely audible, but audible after all.

I've been checking the disk with S.M.A.R.T. but I'm a complete plonker when it comes to hardware so I'm not sure if there is any cause for alarm.

```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   163   163   021    Pre-fail  Always       -       8816
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       16
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       27
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1405
194 Temperature_Celsius     0x0022   111   106   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

```As you can see, 27 hours, load cycle count 1405. Is this normal? Doesn't feel like it.. I've run short, long and conveyance tests, all passed with no errors. Sometimes, I wait for a minute or so and click refresh on GSmartControl and load cycle count has increased!? Doesn't seem like standard procedure..:confused:

I've done a lot of searching on this issue, and it seems like laptops are affected by some sort of aggresive power saving policy..but this is a desktop machine, how could it be affected as well?

Could the faint click be also the sound of head parking? Are there any daemons running by default which could use disk every few seconds?

I've attached an image of system monitor disk graph. Something is going on, even when I close everything and do nothing.

If you need more information to know what's going on, please let me know...

Thanks

---

### Post by lecterror on 2010-09-02
Did some more research...

[LIST]
[*][The S.M.A.R.T Attribute 193 Load/Unload counter keeps increasing on a SATA 2 hard drive]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5357&p_created=1266947046&p_sid=vfg5mY8k&p_accessibility=0&p_redirect=&p_srch=1&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NTEsNTEmcF9wcm9kcz0yMjcsMjk0JnBfY2F0cz0xMzAmcF9wdj0yLjI5NCZwX2N2PTEuMTMwJnBfcGFnZT0x&p_li=&p_topview=1")
[*][The S.M.A.R.T Attribute 193 Load/Unload counter continue to increase for the WD  RE2-GP SATA II hard drives]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=3263&p_sid=vfg5mY8k&p_lva=5357&p_accessibility=0&p_redirect=&p_srch=1&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NTEsNTEmcF9wcm9kcz0yMjcsMjk0JnBfY2F0cz0xMzAmcF9wdj0yLjI5NCZwX2N2PTEuMTMwJnBfcGFnZT0x&p_li=")
[*][RE2GP Idle Mode Update Utility]("http://support.wdc.com/product/download.asp?groupid=609&sid=113&lang=en")
[/LIST]
            It seems like WD Green drives are set to park their heads every 8 seconds by default. When this is combined with Linux syslogd, drive heads are parking and unparking a lot of times per minute..

WD is obviously aware of the problem, they have released the "RE2GP Idle Mode Update Utility" which solves the problem. Although their download page doesn't mention my drive model (WD15EARS), I've updated the drive and so far it seems to be working: my load/unload cycle is steady on 1967 for an hour of so. I will keep monitoring it of course, just in case..

I decided to risk it after reading this entire thread, which I recommend for everyone with "WD Green" drives: [Green Caviar: High Load Cycle Cout after short operation time]("http://community.wdc.com/t5/Desktop/Green-Caviar-High-Load-Cycle-Cout-after-short-operation-time/td-p/15731")

This is what I did, in case someone needs it:

1. Create a DOS boot disk/usb drive (I did it with Ultimate Boot CD: [URL="http://www.ultimatebootcd.com/"]http://www.ultimatebootcd.com/)
[/URL]2. If using UBCD, add the wdidle tool using [customization instructions for UBCD]("http://www.ultimatebootcd.com/customize.html"), otherwise refer to the tools available to you
3. Finally, create the boot disk (in case of UBCD, burn it on a CD or setup UBCD on an USB drive (there are detailed instructions for both of these on the customization page and relevant folders on the UBCD itself)
4. Boot from it, locate wdidle3.exe and run

```
wdidle3 /S300
```This will set the Idle3 time to 300 seconds (which is the maximum), instead of default 8 seconds. You can check the current setting with

```
wdidle3 /R
```For some reason, on UBCD you may need to load USB or CD drivers manually to locate wdidle3.exe (for some reason UBCD kept asking for wdidle.bat so their customization instructions may not be complete?).

That it all. I must say I am not delighted by this parking "feature". WD should rethink their strategy...[-X

Good luck!:-k

---

### Post by raghu1111 on 2010-12-08
Thanks for the instructions.

I have set it to 300 seconds. Any reason why we don't want to disable it completely (with /D option)?

Using UltimateCD to run WDIDLE3.EXE was very convoluted and I wasted couple of hours on it. The problem was with building a custom CD just for adding this one executable. Building the custom iso didn't work for me.

There is a simpler method : using freedos directly rather than with UltimateCD. The instructions are at [http://www.thelupine.com/content/howto-flash-bios-using-freedos-and-grub](http://www.thelupine.com/content/howto-flash-bios-using-freedos-and-grub) . I got freedos from [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/unofficial/balder/balder10.img](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/unofficial/balder/balder10.img) , and added WDIDLE3 to it. 

I am still using grub1, so added the following to grub config (/boot/grub/menu.lst) :

```

title		FreeDOS
kernel		/usr/lib/syslinux/memdisk
initrd		/boot/freedos.img

```
here, freedos.img is the modifed img that I created. Install syslinux package if you don't have memdisk file on your system.

I am attaching freedos.img that I used. Note that the original file is split into two parts in order to get around file size limits for this forum. To get the original file, run 'gzip -dc freedos-1.img.gz freedos-2.img.gz > freedos.img'. The size of the the file should be 1474560. (If you want to be very very sure that you have the right content, confirm that its shasum is 15c66285a3226f10b9c44ca1911592c20eeec3a0 ).

---

### Post by lecterror on 2010-12-08
raghu1111, that's great, thanks for posting!

Let's hope other people won't have to go through the pain we did...](*,)

---

### Post by cyvi on 2011-02-04
Edit: Solved by doing as adviced here

[http://www.geekstogo.com/forum/topic/285453-whats-the-optimal-time-in-seconds-for-hard-drives-to-park-heads/page__p__1896472#entry1896472](http://www.geekstogo.com/forum/topic/285453-whats-the-optimal-time-in-seconds-for-hard-drives-to-park-heads/page__p__1896472#entry1896472)


I'm getting the following error when I choose FreeDOS from GRUB:
[HTML]
error: file not found
error: you need to load the kernel first[/HTML]




I've added the following line into /etc/grub.d/40_custom
```
menuentry "FreeDOS" {
    linux16 /usr/lib/syslinux/memdisk
    initrd16 /boot/freedos.img
}
```

Tried it also with linux16 /boot/memdisk having copied the memdisk file into the directory. I've also tried different img's (raghus' and one I made).

I'm running Ubuntu 10.04 with GRUB 2.

I'm getting really frustrated here. Stayed up the whole night spending the last 6 hours trying to get this damn thing to work. Any help would be greatly appreciated.

---

### Post by bond711 on 2011-06-16
I had luck adding to my grub2 bootable usb :guitar:

```
menuentry "WD IDLE FreeDOS" { 
    linux16 /boot/grub/memdisk 
    initrd16 /boot/wdidle.img
}

```

---

### Post by CliveHarris on 2011-07-04
Thanks for the advice. I've just used the "wdidle3" tool on a couple of WD20EARX drives (2Tbyte WD "Green") I'd bought last month, and it seems to work fine with them. I set the idle period to 5 minutes and I've been running the drives for about 24 hours since that. So far they seem to be running correctly and the load cycle count has remained static. Interestingly, the SMART tool indicates that the drives are now running a few degrees cooler - around 28deg from about 32deg.
The drives were a RAID pair on an Ubuntu-10.04 server and were recommended to me by the supplier (who hadn't heard of this problem), when I upgraded the server last month. My first hint of trouble was when I did a routine SMART check last weekend and noticed a load cycle count of around 61000 after about 550 hours use.
Interestingly, I'm running another identical drive on a Mythbuntu server and this one doesn't seem to have a problem. It's showing around 1500 load cycles in about 1000 hours.

---

### Post by jonnyboysmithy on 2012-02-10
```
sudo hdparm -B 255 /dev/sda
``` fixed it for me

---

### Post by CliveHarris on 2012-02-16
I thought I'd better give an update on what happened to my system. The system is an Ubuntu server-10.04 server, running Apache, Asterisk, Squid, Squidguard and Shorewall, and acting as a fileserver for about 10 desktops and laptops. 

As I said in my last message about 6 months ago, I used the "wdidle3" tool to stop the load cycle count soaring. This stopped the problem and the count stayed static. 

Unfortunately, a week later it suddenly crashed with no obvious cause. From my experience, this is extremely unusual for a Linux server, which frequently run for years with no unplanned downtime. I re-booted it and it crashed a couple of days later, again with no obvious reason. 

This time, I removed one of the WD "Green" drives from the RAID array and replaced it with a 3Tb Hitachi drive (HDS723030ALA640). The system crashed while rebuilding the RAID array and then ran normally for about 2 weeks before "going slow" - it was still functioning, just very very slowly. Again there were no obvious reasons. I then replaced the other WD "Green" drive with a Hitachi one, and rebuilt the RAID array again. 

That was about 6 months ago. Since then the system has had 100% uptime (apart from a brief planned shutdown) and has given no trouble at all. The uptime counter is currently showing 99.999%.

Conclusion. These WD "Green" drives are no use for servers. Any power saving they give are more than offset by the trouble they cause.

---

### Post by cafeschintze on 2013-03-12
Thank you for the update, CliveHarris! I just got my second WD20EARX 64mb Green and I'm realizing I miss Samsung producing hard drives.

I run the discs in a 24/7 ubuntu server. Here is my S.M.A.R.T. values.

[LIST]
[*]sda (since 1.5 months)
Power_On_Hours  1108
Load_Cycle_Count 28323
[/LIST]

[LIST]
[*]sdb (since just today)
Power_On_Hours  7
Load_Cycle_Count 29
[/LIST]

hdparm isnt working:
```
stef@schubiduh:~# hdparm -B 255 /dev/sda

/dev/sda:
 setting Advanced Power Management level to disabled
 HDIO_DRIVE_CMD failed: Input/output error
 APM_level	= not supported
```

I would have used the wdidle tool, but after reading your problems I am not sure any more.
So what now?

---

### Post by CliveHarris on 2013-03-13
Hi  Cafeschintze
My conclusion was that those Western Digital Green drives are just not suitable for use in a high-reliability application such as a Linux server. They were suspiciously cheap, so there must have been some quality compromises, even without the Linux compatibility problems. I can't remember what I did with them in the end - I think one failed after I dropped it and I gave the other one away. Since replacing them with the more expensive Hitachi drives, the server has run faultlessly ever since - I've upgraded it to Ubuntu server 12.04, but it's still using the same drives, running 12/7. Trouble is, I think the Hitachi disk drive division has now been taken over by Western Digital, so I don't know who to recommend now. 
All the best
Clive

---

### Post by cafeschintze on 2013-03-13
I didnt like the idea of *eventually or not* losing all my data. So I gave back the two drives and got two of the [http://www.amazon.de/Western-Digital-WD20EFRX-Festplatte-NAS-Storage/dp/B008JJLZ7G]("WD20EFRX") instead.

I think its better to invest the time and money BEFORE all my data is gone.

---

