---
title: "Advice: ASUS X35SD flash BIOS"
date: 2015-03-25
forum: Hardware
---

### Post by Lalaith on 2015-03-25
Hi all, 

I was having loads of problems with my laptop in dual boot. I eventually installed only Ubuntu 14.04 on it. But it took for ages to install, and it always reported problems when updating packages and in some installs had problems while booting (complaining about I/O). During this process I kept reading some log files stored in /var/log and found the following message:

```

[    1.770772] [drm] Wrong MCH_SSKPD value: 0x16040307
[    1.770774] [drm] This can cause pipe underruns and display issues.
[    1.770775] [drm] Please upgrade your BIOS to fix this.

```

Meanwhile, Ubuntu was running smoothly from my liveUSB. So I checked the HDD  with Spinrite (a tool to check HDDs): and it found quite some errors. Formatted the HDD, and Spinrite still found some errors, but just a few. (By the way, the Disk utility of Ubuntu finds 65k bad sectors, but says that the HDD is OK.:?)

**So I plan to update the BIOS and then buy a new HDD and install it in the laptop**. My logic is: since flashing the BIOS is risky, I better try it first and save the money of a new HDD if I end up breaking the laptop.

So my questions are:

- In this situation, would you run any test to check the health of the BIOS/Mother board/whatever, just to make sure I found where the problems are?

- Do you really think it is necessary to update the BIOS? I saw many people on the forums advising not to do it... however, this site says the contrary: [https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate)

- How can I back-up my current BIOS? I didnt find anything useful searching the net for tutorials on that.

- At the moment my HDD is formatted and completely empty. I know that after updating the BIOS the computer restarts. I plan to keep my liveUSB plugged in to restart in the liveUSB. Is there any risk in doing so? Would you rather advise me to install first Ubuntu in the faulty HDD, just for the purpose of updating BIOS?

many thanks for your feedback and help!

---

### Post by weatherman2 on 2015-03-25
A BIOS update - if one is even available - may not fix the error you are seeing, and the error may not really mean much anyway.

Yes, a BIOS update is slightly risky.  And you will probably need to do it from Windows, anyway.  It sounds like you don't have Windows anymore.

Your real problem sounds like the hard drive.  Check the S.M.A.R.T. status with GSmartControl.  Look for Attributes highlighted in pink.  If you have Pending Sectors (raw value > 0) - sectors that cannot be read - that is usually bad and will cause lots of problems with updates and everything else.  Each time the operating system tries to save a file that uses one of those bad sectors, you may get freezes or other errors.  You can't get rid of bad sectors on a hard drive just be re-formatting (though if you zero the entire drive out, sometimes you can clear them, often not).

Replace the hard drive first, then see what problems remain, if any.  Don't update the BIOS just to get rid of a log message that may not mean anything - update the BIOS to address a real problem.

---

### Post by Lalaith on 2015-03-25
There is an update available, Asus describes the contents of the update:

```
1.Update CPU microcode
2.Show serial number in main page of setup menu
3.Add "Intel AES-NI" item in in Advance selection of BIOS Setup Menu
```

Not sure if anything described above will help. 
What it makes me wonder is why the Ubuntu Wiki advises so clearly to update the BIOS, if everyone in the forums agree not to. (in FAQ, question 4: [https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate))



I run GSmartControl: I have 65k (Raw data) in Pending Sectors. So you would definitely put a new HDD, without touching the BIOS?

---

### Post by weatherman2 on 2015-03-25
I assume you really don't have 65,000 pending sectors or the drive would be almost unusable.  Do you mean 65 sectors?  Even 65 is bad enough to warrant replacing your hard drive.

Whether one should upgrade the BIOS is one of those opinion questions experts disagree on.  There is a small risk involved, which is the biggest reason NOT to do it.  But if you choose the correct BIOS file, under typical circumstances, with no other weird issues, it is very safe to do  The biggest risk is that you will choose the wrong file, lose power during the BIOS flash, interrupt it by accident, etc.

But as I said, unless you can say, "I am trying to fix this specific problem with a BIOS update," I wouldn't bother.   The 3 listed updates seem irrelevant to Ubuntu (#1 would allow newer/more CPUs to be used on the motherboard, so if you ever considered upgrading your CPU, you'd want to do the BIOS upgrade before that, for sure).

---

### Post by Lalaith on 2015-03-25
Yes, I do have 65000 bad sectors, if I understand correctly what is written in the GSmartControl: [http://pbrd.co/1y8Gccu](http://pbrd.co/1y8Gccu)

Is it possible to damage the HDD by means of installing/uninstalling Operating systems? I didnt move my laptop for a while so it cant be a nasty hit.

---

### Post by weatherman2 on 2015-03-25
OK - then your hard drive is basically dead.  You can keep using it if you are willing to put up with continual problems, but I wouldn't.  I'd use the live USB myself until I could afford to replace the hard drive.

Hard drives fail all the time for no obvious reason.  They have moving parts.  They are not perfect.  I've replaced lots of bad hard drives.  It's something routine that happens with computers.  Spend a little more and get an SSD next time if you want something more reliable.  SSD prices are coming down quickly.  You can easily find a 256GB SSD for well under $100 USD now, sometimes a 512GB SSD for around $100.  Next year, they will be even cheaper.

---

### Post by Lalaith on 2015-03-25
I see. I will check HDD and SSDs, then. Forget about flashing BIOS (more than happy to avoid that, I must say).
On the meantime, if I could get an external USB hard drive, is it sustainable to use it as main hard drive? I dont think USB ports are meant to be used as the connection to the Hard drive, right?


Anyway, I will mark the thread as solved, just in case any other user bumps into it.
Many thanks for your support!!!

---

### Post by weatherman2 on 2015-03-25
I wouldn't expect a USB flash drive to last forever when used for a Ubuntu installation.  It's nothing to do with the port (unless you are moving around with it plugged in, probably not a great idea).  It's more that the flash memory in a USB drive can eventually wear out after too many writes (that's why using ext2 format for the main partition may be better - no journaling).  And I wouldn't expect it to be that fast.  I have used a few like this.  They do work but not nearly as fast as a regular hard drive.

An SSD uses the same type of flash cells inside (though probably a lot faster than a USB drive's flash memory).  But an SSD has a controller that balances writes within the whole array of flash cells, so it can distribute writes among flash cells and not keep re-writing the same ones over and over again.  With a USB flash drive, you have none of that - you could be re-writing the same cells repeatedly.  As I said, I wouldn't expect it to last forever.  Just make regular backups of important files.  And they don't cost much - if it costs a few bucks and wears out in a year, so what?

---

### Post by Lalaith on 2015-03-27
Great, thanks.
I have been checking HDDs and SSDs. Is there any compatibility issue with hard drives? I have seen posts about it from 2009 or before, but nothing newer, so I guess i can choose anything?

Update: I bought a Seagate HDD and the installation process went really smooth. Very happy to have rescued the laptop!

---

