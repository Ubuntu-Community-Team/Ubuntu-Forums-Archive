---
title: "Possible Hard Drive Failure?"
date: 2009-12-28
forum: Hardware
---

### Post by stuartwood89 on 2009-12-28
Long time no post it seems.

I've just recently aquired a laptop ([Toshiba Equium M50-216]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&DISC_MODEL=0&ACTION=PRINT_WITH_BACK&com.broadvision.session.new=Yes&PRODUCT_ID=113323")) which runs Windows XP.  Apparently it was constantly BSODing so it was given to me.  Needles to say that I shall be running Ubuntu on this.  I've decided with Studio for now.  Upon testing the laptop for the first time.  The POST screen would come up, then a really long pause, followed by:

> A disk read error occured
Press Ctrl+Alt+Del to restart

So I tried running the recovery disc to see if that would resolve the issue, and to try and rule out HDD failure.  The process got to 99% and there were some beeps and !!!!!failure!!!!! appeared on my screen, then a wall of text appeared just after and now there's no OS on the laptop.

So...  I decided to download and install Ubuntu Studio anyway.  I booted from the CD and the install splash screen appeared.  I selected 'Install Ubuntu Studio' and there was a pause.  I could hear the DVD drive humming away so it was doing something.  Then after a minute or two, this came up:

```
udevadm settle - timeout of 180 seconds reached, the event queue contains:
  /sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1(800)
[   181.263314] Kernal panic - not syncing: Attempted to kill init!
```

I hope someone can figure out what this is, because I don't want to go out and buy a new drive, only to find that it's something else.  I'm a little strapped for cash at the moment.

Thanks for looking :)

---

### Post by stuartwood89 on 2009-12-30
Can anyone figure this out?  I'm thinking of just getting a new drive, but I don't want to spend money that I don't necessarily have to.

---

### Post by Bartender on 2009-12-30
How old is this laptop?  Has the CMOS battery ever been replaced?  Can you open up the back and get a halfway decent look at the motherboard?  Blown capacitors could be causing the odd behavior...

---

### Post by stuartwood89 on 2009-12-30
The laptop is not too old, probably about 5 years old.  I haven't taken the whole thing apart, but I guess there's no reason to not give it a go.  Although I've built desktop computers before, I have little experience with a laptop.  As far as I know, the CMOS battery hasn't been replaced.  What I'll do is try and get the thing dismantled within the next few days and post some pictures here for you.  There's a million and one screws in the bottom of this thing though, so it'll keep me busy for a while putting it back together :)

Oh and thanks for the reply, though I hope to God you're wrong.  I not in any position to buy a new laptop :D

---

### Post by stuartwood89 on 2010-01-01
Ok I've tried taking this thing apart, but I can't get the parts off.  I've removed *every single screw* from the bottom of the unit and still I can't seem to remove it.

---

### Post by viper250 on 2010-01-01
first thing download and burn the iso for d-ban and run it
dban will wipe the drive and perform a brute force disk test at the same time.
if the drive has bad sectors it will quit early but you will get the same message if it is a sata drive that is not set to ide mode.
you may have to use a ms disc to delete the disc partitions first.
also toshiba laptops cmos battery is usually located in two places (1) beneath the keyboard & (2) near the hard drive caddy.
some screws are hidden beneath rubber plugs.
anytime you remove or disassemble a laptop do so very gently and while you have it apart carefully clean out all the dust you can

---

### Post by ssulaco on 2010-01-01
> **viper250 said:**
> first thing download and burn the iso for d-ban and run it
dban will wipe the drive and perform a brute force disk test at the same time.

Back up your data.Recommend running a DFT (drive fitness test)Hitachi has an program that works on most drives,read this:
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
you are going to focus about midway down to **Drive fitness test**
very simple to use good luck
you should not lose any data except if it finds bad sectors and is able to repair them

---

### Post by stuartwood89 on 2010-01-01
Thanks guys.  I'm not worried about losing data, there's nothing important on there anyway.  I shall download this D-Ban and give that a go.  I assume I just boot it from the CD?  As far as I'm aware, there aren't any partitions on the drive, is there any way to find out?

I'll give taking it apart another go, and I'll look under the rubber pads as well.

Thanks for the support so far guys!

---

### Post by stuartwood89 on 2010-01-01
```
DBAN finished with non-fatal errors
Check the log for more information
Hardware clock operation start date: Fri Jan 01 21:03:05 2010
Hardware clock operation finish date: Fri Jan 01 21:49:35 2010
Saving logs to A:\DBANLOG on removable media... done
```

:confused:

---

### Post by stuartwood89 on 2010-01-01
Sorry for triple posting:

I decided to run a LiveCD, which seems to work fine.  I haven't tried installing yet, but I did try System Testing *(System>Administration>System Testing)* I unchecked everything I didn't need, so I just ran Hard Drive, Kernel and something else and started.  The dialogue box says 'Running test disk_bench...' and it's crashed.  Does this mean I can rule out everything else and say it's the hard drive or do you guys think it still could be something else?

Also on the top bar, there's an icon with a drive and an orange warning triangle, which when I hover over, it says *'One or more disks are failing'*.  If I click it, a box appears saying *'40GB Hard Disk - ATA TOSHIBA MK4026GAX - DISK FAILURE IS IMMINENT'*.

So I've tried installing from the LiveCD, I entered all the details and it started.  Now it's stuck on 5% *'Creating ext4 file system for / in partition #1 of SCSI1 (0,0,0) (sda)...'* and the hard drive is making some terrible ticking and beeping-like noises.

---

### Post by ssulaco on 2010-01-01
> **ssulaco said:**
> Back up your data.Recommend running a DFT (drive fitness test)Hitachi has an program that works on most drives,read this:
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
you are going to focus about midway down to **Drive fitness test**
very simple to use good luck
you should not lose any data except if it finds bad sectors and is able to repair them

I would recommend trying the Hitachi DFT program....run all the tests in the DFT test procedure to make sure.but before doing this,does the bottom of the laptop look like the one in this picture?you will notice 3 rectangle covers....under one of these is your hardrive,you wont have to split the whole case,try reracking/reseating the drive,gently pull the drive away from the connector,which should be hardmounted to the mobo,then reseat the drive,take caution the pins are lining back up,Laptops are more prone to bumps and bangs vs a desktop,and god knows if its been dropped a couple of times,so the life span of a hdd in a laptop is usually alot shorter than a desktop.

try reseating the hdd first and still having trouble run the Hitachi DFT

---

### Post by viper250 on 2010-01-01
yeah sounds like the hard drive is failing if you are hearing anything other than a very quiet clicking (nearly silent)
if the clicking is loud you are hearing the read write head arm bumping against the stops and the heads will soon be misaligned.
in some laptops you will be able to access the hard drive when you remove the battery.
and some will be beneath an access plate.
some systems will have a drive caddy

30 years as a pc hardware tech has taught me a lot.
if d-ban finished with any errors the drive usually has bad sectors, so its better to replace it.
Linux installations are more critical about hard drive condition so d-ban is a very good tool for you, It will securely wipe a drive (exceeding the requirements of the department of defense many times over) assuring a clean drive for installation

---

### Post by stuartwood89 on 2010-01-02
Excellent :) 

I've looked at the hard drive a few times, so it's been reseated several times.  I'm looking at some drives now.  Looks like can get 160gb for about £30.

---

