---
title: "Power-Off_Retract_Count"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by enkoan on 2007-11-02
After coming across the Load_Cycle_Count issue....

[http://ubuntuforums.org/showthread.php?t=591503]("http://ubuntuforums.org/showthread.php?t=591503")
[https://launchpad.net/bug59695.html]("https://launchpad.net/bug59695.html")

And fixing the issue (my Load_Cycle_Count is no longer increasing at a maddening rate) I began considering my Power-Off_Retract_Count:
```
sudo smartctl -d ata -a /dev/sda
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       693

```

which seems high compared to what others have posted.  There seems to be some disagreement about whether this is an Ubuntu issue or simply BIOS/firmware settings from the manufacturer.  The Load_Cycle I'm not really sure about, haven't tested it in windows yet, but I am fairly certain that Power-off_Retract is NOT an Ubuntu issue.  I say this because I have been running Vista for 6 months, XP Professional for 1/2 month, and Ubuntu for about 1 week.  There's no way that count could increase so fast in 1 week.  So, at least in this case it must be BIOS.  See: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")

My HDD does emit a very loud clicking when I shutdown, whether from Ubuntu or XP, and I think this is what is being counted.  My tech level is very low.. does anyone know if this is harmful to the hdd drive or not?  And if so, how to fix it?

---

### Post by Linicks on 2007-11-02
Yes, it can be harmful as the disk is being powered off while still spinning/not shut down.

The fix is found in the link you supplied:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

Gutsy doesn't have this issue, BTW.

Nick

---

### Post by enkoan on 2007-11-02
I applied the recommend change...

created file /etc/rc0.d/S00hdd-shutdown-workaround
```
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
```
then
```
 chmod +x /etc/rc0.d/S00hdd-shutdown-workaround
```

But it did not work.  I still hear the clicking sound when I shutdown, and Power-Off_Retract_Count increases whenever I do.  I'm running Gutsy.

As I said, I don't think this is an Ubuntu issue AT ALL because my count being ~696, and I've only had Ubuntu installed for 1 week.   Prior to this Windows Vista and XP.  I receive the same clicking when I shutdown from those OS as well.  

Maybe this is a BIOS issue?  If so, why would it be configured from the manufacturer in such a way as to break it?  Is it really that harmful?  Is there any other way to fix it?

---

### Post by enkoan on 2007-11-03
bump... anyone? sounds like a bios/firmware issue right?

---

### Post by kiloecho7 on 2007-11-03
I've been looking into this a little bit recently because I was concerned about a "tok" sound coming from my hard drive when I suspend and wake from it.  I'm running Gutsy on a three month old Thinkpad x61s (very nice hardware, by the way, I don't want to damage it.)  What beets me is the smartctl output for the Power-Off_Retract_Count.  It says it's done it 91 million times!  I'm somewhat suspicious of the claim.:confused:

# smartctl -a /dev/sda | grep Power-Off_Retract_Count
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       91619391

The load cycle count is accurate enough, even though it's a little scary.  I just implemented the fixes for that yesterday.

# smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count      0x0012   094   094   000    Old_age   Always       - 
65804

The reassuring thing is that the 91 odd million retract count never goes up even when I suspend and hear the "tok."

---

### Post by DMcA on 2007-11-03
I think I'm having a similar problem. With "sudo smartctl -d ata -a /dev/sda" I get:

```
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2549
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       2550

```

which means I'm getting Power-Off_Retract_Count increasing by one every time I shutdown. I've tried the fix mentioned above but that hasn't done anything for me either.

Also

```
193 Load_Cycle_Count        0x0032   008   008   000    Old_age   Always       -       184224

```

which is a little scary, but I've sorted that by adding "hdparm -B 200 /dev/sda" to my rc.local file.

---

### Post by enkoan on 2007-11-03
Well, my friends.. here is my current smartctl info:
```
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       699
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       697
193 Load_Cycle_Count        0x0032   184   184   000    Old_age   Always       -       48554

```

Power-Off_Retract_Count still increasing...

This is not an Ubuntu issue for me, it has done this in Windows since the day I bought this laptop.  Ubuntu only installed 1 week.  Assuming its a firmware issue from the factory.. well.. time will tell, I hope my hdd doesn't break.

---

### Post by nick_h on 2007-11-03
This Ubuntu problem would be fixed with the code you posted earlier and doesn't occur in Gutsy anyway.  I suspect that Ubuntu and Windows are issuing the command to park the heads but it is ignored by the drive or BIOS.

My understanding is that the heads will be parked when the power is cut using the momentum of the drive platters.  Whilst this is obviously not ideal it shouldn't cause any immediate problems.

---

### Post by dasunst3r on 2007-11-03
Here's the results on my computer:
```
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1297
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       348
193 Load_Cycle_Count        0x0032   191   191   000    Old_age   Always       -       27955

```This computer's been through Edgy and Feisty and is about seven months old now.

---

### Post by enkoan on 2007-11-04
Well, thank you.. I guess since this is a BIOS issue if I want to pursue it further I'll take it up with my hardware mfg. thanks!

---

### Post by truse on 2007-11-07
My smartctl..

Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       241827905

WTF? Isnt this a shitty high number? I have a few months old T61..

---

### Post by ubuntu_demon on 2007-11-21
> **truse said:**
> My smartctl..

Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       241827905

WTF? Isnt this a shitty high number? I have a few months old T61..

Don't worry the number is so big that your WORST shouldn't be at 100 if the number was correct. It's a raw value which isn't always the real value. You are probably fine.

---

### Post by ubuntu_demon on 2007-11-22
This issue isn't related to Load_Cycle_Count in any way.

For people who are hearing a bad noise and/or see an increase in Power_Off_Retract_Count : Please upgrade to Gutsy. The issue should be solved in Gutsy. If you are running Gutsy but still have this problem please report it in the bug report.

Here's the bug report :  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/)

---

### Post by bkraptor on 2007-12-15
I'm also running Gutsy and having this problem. Power-Off_Retract_Count increases on every shutdown. This doesn't happen with Windows XP.

Gutsy 32bit on a Dell Inspiron E1505 with a Seagate Momentus 7200.2 HDD.

The proposed fix, the one from [here](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60) doesn't work. The target file isn't even there.

---

### Post by mbze500 on 2008-01-18
Hi I have same issue as bkraptor mentioned.  I am using Gutsy.  I have m1330 with Seagate Momentus 7200.2 HDD and Power-Off_Retract_Count is increasing by 1 on every shutdown except I set hdparm -B 254.  Actually I would like to set hdparm -B 208 to fix Load Cycle bug because I can see the hard drive run 5-6 degrees cooler on value 208.

It seems this Seagate drive is having problem with double spin shutdown problem - [http://linux-ata.org/shutdown.html](http://linux-ata.org/shutdown.html) and [http://kerneltrap.org/mailarchive/linux-kernel/2007/8/8/156918](http://kerneltrap.org/mailarchive/linux-kernel/2007/8/8/156918).

Does anyone experience similar problem?  Or can someone provide the potential fix on this issue?

---

