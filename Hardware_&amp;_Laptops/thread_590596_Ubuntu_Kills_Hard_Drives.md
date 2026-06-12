---
title: "Ubuntu Kills Hard Drives?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by kadath on 2007-10-24
I just came across this article on Digg: ["Explanation of Ubuntu Hard Drive Wear and Tear"]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")

Does anyone have any experience with this? Is it a serious issue like the article makes it out to be? I can certainly say that I notice my laptop's HD grinding away more often when booted into Xubuntu than I do when booted into Windows XP.

---

### Post by toupeiro on 2007-10-24
I'd read the comments to the thread, as they bear the truth about this particular issue.

the answer is: no, Ubuntu does not "kill hard drives". If your drive mechanically crashes or its prom or buffer suddenly go ka-put, blame the manufacturer.

Sincerely yours from a Thinkpad T60 with default PM settings and runs the majority of the day without spinning down,

---

### Post by -grubby on 2007-10-25
Windows was the culprit when my other Hard drive died (worked fine before windows)

---

### Post by mridkash on 2007-10-25
Now after I installed ubuntu 7.10 hard disk noises have gone away from my laptop. Earlier when I shutdown or suspend the harddisk sounded like " tick tick teoooooo..." like a motor spinning down, it happened in windows too.

But its okay now.

Also, in windows the laptop hard disk regularly makes tick tick sounds after boot up, i wonder why.

---

### Post by toupeiro on 2007-10-25
> **mridkash said:**
>  Earlier when I shutdown or suspend the harddisk sounded like " tick tick teoooooo..." like a motor spinning down, it happened in windows too.

.

This is your hard disk read/Write head and control arm parking and unparking so it does not damage the disk surface while powered off.  Some laptops have the ability to detect erratic movement via a built in sensor that will park the control arm until the motion has stopped. Older drives did not necessarily have this.  Almost all drives do now days.

---

### Post by FuturePilot on 2007-10-25
I think 2.6.20 had a problem with [shutdown(8)]("http://linux-ata.org/shutdown.html") 
[https://bugs.launchpad.net/ubuntu/+bug/67810]("https://bugs.launchpad.net/ubuntu/+bug/67810")
but as far as I can tell, and I think I also read it somewhere, 2.6.22 fixed this.

---

### Post by SunnyRabbiera on 2007-10-25
well I would not be shocked if it does do this but you can be sure that windows does the same thing.

---

### Post by bytor4232 on 2007-10-25
This is mostly BS. To know if your effected by this, run:

sudo hdparm -i /dev/sda | grep AdvancedPM

If you get back: AdvancedPM=no WriteCache=enabled
Then your not effected. I checked two desktops that I have access to here, and neither of them are effected. Its probably a laptop issue, or a non-issue period. You want your hard drive to spin down when using a laptop, it saves while on battery.

---

### Post by Calash on 2007-10-25
At work, we had IBM blame one of our applications for killing hard drives.  This was a windows based system, but according to them it was writing to one area of the drive over and over.

We called there bluff and they replaced the failing drive (DiamondMax 8)

I have seen cases where systems with low memory ruin drives by paging too much.  Usually the OS fails first though due to page-file corruption and not being able to update the registry correctly, but in some cases it can cause issues.

Never seen any issues on our Redhat systems though.

---

### Post by PriceChild on 2007-10-25
[A creditible explanation by an Ubuntu Developer. http://mjg59.livejournal.com/77672.html]("http://mjg59.livejournal.com/77672.html")

---

### Post by osxcapades on 2007-10-25
> **SunnyRabbiera said:**
> well I would not be shocked if it does do this but you can be sure that windows does the same thing.

Evidence?

I don't understand all this comparison with Windows. Why are we forced to compare Ubuntu with Windows so often?

---

### Post by mridkash on 2007-10-25
sudo hdparm -I /dev/sda on my laptop gives "Advance Power Management level: Unknown Setting (0x0080)"

What does that mean?:confused:

And also, should I enable the hdparm service in the services window. It says "hdparm : Hard Disk Tuning" . what's its purpose?

Thanks.

whole output:
```
/dev/sda:

ATA device, with non-removable media
        Model Number:       WDC WD800BEVS-60LAT0                    
        Serial Number:      WD-WXE506375333
        Firmware Revision:  01.06M01
Standards:
        Supported: 7 6 5 4 
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        LBA48  user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0080)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns

```

---

### Post by FuturePilot on 2007-10-25
> **mridkash said:**
> sudo hdparm -I /dev/sda on my laptop gives "Advance Power Management level: Unknown Setting (0x0080)"

What does that mean?:confused:

And also, should I enable the hdparm service in the services window. It says "hdparm : Hard Disk Tuning" . what's its purpose?

Thanks.

whole output:
```
/dev/sda:

ATA device, with non-removable media
        Model Number:       WDC WD800BEVS-60LAT0                    
        Serial Number:      WD-WXE506375333
        Firmware Revision:  01.06M01
Standards:
        Supported: 7 6 5 4 
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        LBA48  user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0080)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns

```
That's for laptops mostly. Helps save on power by spinning down the hard drive. You probably don't want to enable that if you're on a desktop machine.

---

### Post by Interestedinthepenguin on 2007-12-17
My output of 'hdparm -i /dev/hda | grep  AdvancedPM' is:  AdvancedPM=yes: disabled (255) WriteCache=enabled.  

Is "AdvancedPM=yes: disabled (255)" equivalent to "AdvancedPM=no"?


EDIT:  I think I'm fine (output of 'grep ENABLE_LAPTOP_MODE /etc/default/acpi-support' returned false.), but if anyone knows otherwise, please let me know.

---

### Post by Rashedul on 2007-12-17
sudo hdparm -i /dev/sda | grep AdvancedPM  gives me the error */dev/sda: No such file or directory* .Any suggestions? I'm somewhat new to Linux/Ubuntu. I've been using it fully for the last 3 weeks and learning slowly.

---

### Post by dizee on 2007-12-18
> **Rashedul said:**
> sudo hdparm -i /dev/sda | grep AdvancedPM  gives me the error */dev/sda: No such file or directory* .Any suggestions? I'm somewhat new to Linux/Ubuntu. I've been using it fully for the last 3 weeks and learning slowly.
Try typing *hda* instead of* sda*.

---

### Post by Rashedul on 2007-12-18
Thanks that worked. So my output is 
AdvancedPM=yes: mode=0x80 (128 ) WriteCache=enabled .

Is 128 too aggressive for power management? Should I go to 255 to save my hard drive from excess wear and tear like the article is suggesting?

---

### Post by Ripfox on 2007-12-18
Ok, I am getting 

 AdvancedPM=yes: unknown setting WriteCache=enabled

I did notice this machine making weird noises...what do I do?

---

### Post by Ripfox on 2007-12-18
Anyone? This is really troubling...

---

### Post by Interestedinthepenguin on 2007-12-19
> **Rashedul said:**
> Thanks that worked. So my output is 
AdvancedPM=yes: mode=0x80 (128 ) WriteCache=enabled .

Is 128 too aggressive for power management? Should I go to 255 to save my hard drive from excess wear and tear like the article is suggesting?

I read that 1 is the most aggressive setting.  You have a medium setting.  I guess it's up to you.  ...That's just my nooby two cents...

@**ripfox**:  I don't know anything about the "unknown setting" in your output, but reading this page may help: [http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions](http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions)

---

### Post by Ripfox on 2007-12-20
well, I installed Gutsy thinking it would be better for this laptop (and was going to anyways) but on this issue I get the same output as above. Can anyone tell me how to change this setting?

---

### Post by Ripfox on 2007-12-20
Bump

---

### Post by forrestcupp on 2007-12-20
I can't help you, but I can say that in Gutsy and every version before, I get the ticking sound.  But in Windows on the same computer I don't hear the noise.  I don't know what it is or if it is harmful, but it's annoying.

---

### Post by Ripfox on 2007-12-20
God someone must know how to manipulate these settings...:lolflag:

---

### Post by K.Mandla on 2007-12-20
It was my understanding that this was a non-issue, since Ubuntu doesn't touch the drive settings. 

[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)
[http://mjg59.livejournal.com/77672.html](http://mjg59.livejournal.com/77672.html)

I'm tempted to move this to Recurring Discussions, but since some people are asking legitimate questions about how to manage the power settings, I'll put it in Hardware and Laptops.

---

### Post by Ripfox on 2007-12-21
Ok I have a better understanding of what is going on now. I am currently checking into the bios settings of my particular laptops and also searching the net for firmware settings ect...

Thank you for the links.

---

