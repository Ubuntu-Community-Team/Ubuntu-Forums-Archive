---
title: "DMA problem with Harddisk"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by spooky-mac on 2005-11-14
Hello. :)

I have Ubuntu 5.10 running on my Laptop and I experienced some DMA problems. Now I am unsure if I should disable DMA in grub or in fstab (and if yes, how?) or if this is a bug or something else. Here is what I found in my /var/log/messages file:
```

...
Nov 12 23:36:30 localhost kernel: [4295186.931000] hda: dma_timer_expiry: dma status == 0x20
Nov 12 23:36:30 localhost kernel: [4295186.931000] hda: DMA timeout retry
Nov 12 23:36:30 localhost kernel: [4295186.931000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 12 23:36:30 localhost kernel: [4295186.931000] 
Nov 12 23:36:30 localhost kernel: [4295186.931000] ide: failed opcode was: unknown
Nov 12 23:36:30 localhost kernel: [4295187.217000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Nov 12 23:36:30 localhost kernel: [4295187.217000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Nov 12 23:36:30 localhost kernel: [4295187.217000] ide: failed opcode was: unknown
...
```
This is, of course only the relevant part in the file, but I hope you get apicture of my problem. I have encountered it repeatedly that my harddrive locks up for some seconds due to the DMA timeouts and works okay afterwards again.

Are these timeouts dangerous? I have some critical files on that work-laptop (I make frequent backups, though). Oh, and I have tried other distros, too, and all seem to have the same problem.

Any ideas?

PS: If you need special hardware info (dmesg) I will post that, but I think it is not necessary right now, right?

Thanks for any help in advance! :D

---

### Post by spooky-mac on 2005-11-14
Some more information I found (learning new things is amazing :) ):

I ran "hdparm -i /dev/hda" and got:
```

/dev/hda:

 Model=HITACHI_DK23FB-40, FwRev=00M1A0A1, SerialNo=4CY679
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=78140160
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:

 * signifies the current active mode

```
Hope this helps.
I am currently reading the man page of hdparm but it is soooo huge... *sigh*

---

### Post by poptones on 2005-11-14
You got a read error from your HD. It is "locking up" because the drive is failing and retrying. This is why it happens no mattter the distro you use.

You have a failing hard drive. Back your stuff up, write zeroes to the drive to remap those bad sectors, and reinstall.

backup
reboot to single user mode
type dd if=/dev/zero of=/dev/hda
when it's done, reinstall.

Do NOT do that until you have your stuff backed up. But back your stuff up NOW because it seems destined that you are going to lose it otherwise.

If the above steps do not fix the problem, time to shop for a new drive...

---

### Post by spooky-mac on 2005-11-14
Umm... a failing drive? I doubt that. THe laptop is not even one month old and the drive passed all sanity checks I did. But I will back up right now, in case you are right with your disaster prediction.

---

### Post by poptones on 2005-11-14
If it is a new drive then the "write zeroes" part will likely fix it. It has some bad sectors, to get the drive to remap them you have to write data to them. Most reliable way to do this is to always write zeroes to a new drive before installing. It can take a while with a large drive, but it is cheap insurance.

Even new drives can fail.

---

### Post by spooky-mac on 2005-11-14
Okay... I understand.

I did what you said and now the system shows the following messages:

*cannot execute "/sbin/getty"
*Id "2" respawning too fast: disabled for 5 minutes
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*Id "3" respawning too fast: disabled for 5 minutes
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*Id "4" respawning too fast: disabled for 5 minutes
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*cannot execute "/sbin/getty"
*Id "5" respawning too fast: disabled for 5 minutes
*cannot execute "/sbin/getty"

and so on and so on, till it reaches 6, then starts again at "Id 2"... what does that mean?

---

### Post by poptones on 2005-11-14
I really hope you did ALL I suggested and backed it up first :)

OK, reboot from the install CD and type "expert" at the prompt. Follow along with the default choices as you would a normal install until you get to the choice "detect network hardware." 

now, go down the menu to "execute a shell."

When the shell prompt pops up, type 

/bin/dd if=/dev/zero of=/dev/hda

It SHOULD run properly... if it does and it finishes, hit ctrl-c to exit the prompt, scroll back up to the "detect network hardware" prompt and finish the installation.

---

### Post by spooky-mac on 2005-11-14
Nice idea... but it didn't work. All partitions were gone. I checked with a knoppix live-cd, too. Bah.. I will format the whole drive again and reinstall. Maybe everthing works then. If not, I will start the procedure once again and tell you so.

Thanks for sharing your time and wisdom. :)

---

### Post by poptones on 2005-11-14
all partitions were *supposed* to be gone. Did you try to run the command I told you? What messages did it give you?

Like I said: it WILL take a while. It may appear it is not doing anything. That is my fault... try this command instead:

/bin/dd -v if=/dev/zero of=/dev/hda

It sounds liek you started to run it since it reports the partitions are gone. You just need to let it run to completion.

If you just reinstall and you don't write zeroes to that drive you are just going to have the same problem. 

Edit.. duh, you have knoppix.

OK, boot from knoppix. From a terminal window make sure /dev/hda is there. Tnen run the command I showed you above. Let it run until it says it is done.

---

### Post by spooky-mac on 2005-11-14
Oh.. I thought it had stalled as it did absolutely nothing when I ran the command. But I did some researches (google is your friend) as well and it seems that there is a bug concerning the /sbin/getty thing in ubuntu. I will try to do the whole thing from a knoppix cd. Maybe that works instantly. :)

After all, now I have my data on these two CDs, so I can kill my system as often as I like. ;)

---

### Post by poptones on 2005-11-14
I don't know how big your hard drive is, but it's not likely to work "instantly." For example, I just happen to have received a warrantied drive today and am in the process of installing it. It's a 160GB Seagate and it seems to be taking about a half hour to wipe 20GB... at that rate it will take about four hours to initialize this drive.

It's NOT going to happen instantly. Let it get started, it'll take a while.

Oh, BTW - I had a brain fart because, as I said I am in the process of installing a drive myself and I accidentally wiped my partition table and about a half gig of data (good thing for backups!) Anyway, if you use knoppix you will need to login to a terminal "su root" and then dd if=/dev/zero of=/dev/hda.

---

### Post by spooky-mac on 2005-11-16
Okay, I ran the whole thing from Knoppix and it seems as if it worked okay. I also downloaded some diagnostics-tools for Linux from the Toshiba website (it is a 40GB hdd) and did intense checks on the drive and not even one error could be found. 

Maybe there was not really any corrupted cluster... I almost suspect that the partitioning of my drive did not work 100% okay when I first formatted my drive with the Ubuntu-cd (the laptop came without any OS preinstalled). I flattened the / partition several times now, but the /home partition was not reformatted before and maybe the problem lay right there.
Anyway, I have formatted everything again (started from scratch) and everything is working right now and no hickups, no stalls, no freezes anymore. I hope it stays that way.

Thank you for your help. :)

---

### Post by spooky-mac on 2005-11-17
Okay. Final note and sad ending: You were right. Today, the drive died completely. :( 

I will send the lappy back to the vendor tomorrow.

---

