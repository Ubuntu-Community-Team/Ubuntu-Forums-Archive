---
title: "Incompatible medium installed -- (asc=0x30, ascq=0x00)"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by [S2] on 2005-09-10
Hello all,
i bought a new DVD drive for my laptop, and it works perfectly, but the kernel keeps writing
```
Sep 11 02:24:15 localhost kernel: ATAPI device hdc:
Sep 11 02:24:15 localhost kernel:   Error: Not ready -- (Sense key=0x02)
Sep 11 02:24:15 localhost kernel:   Incompatible medium installed -- (asc=0x30, ascq=0x00)
Sep 11 02:24:15 localhost kernel:   The failed "Read Cd/Dvd Capacity" packet command was:
Sep 11 02:24:15 localhost kernel:   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
Sep 11 02:24:17 localhost kernel: ATAPI device hdc:
Sep 11 02:24:17 localhost kernel:   Error: Not ready -- (Sense key=0x02)
Sep 11 02:24:17 localhost kernel:   Incompatible medium installed -- (asc=0x30, ascq=0x00)
Sep 11 02:24:17 localhost kernel:   The failed "Read Cd/Dvd Capacity" packet command was:
Sep 11 02:24:17 localhost kernel:   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

```
in my log files.
is there a way to filter this out, so my disk stops spinning all the time?

---

### Post by kaaspad on 2005-09-15
I'm having this exact same problem, on an HP2005 with the lightscribe dvd installed....
extremely annoying....

the only way I got around it for now was to do what I did in the olden days.... put this in your boot options (in grub just add it to your kopt line and run update-grub): 

hdc=ide-scsi

this kinda sux, since using this old hacks, makes the machine see like 6 devices... but it works, and you don't get that message, if anyone has a different hack please let me know

---

### Post by incunabulum on 2005-10-24
Well, same here. But - and this is interesting - I did an upgrade from hoary to breezy. On my hoary installation no errors where reported. Now - with breezy - the log keeps growing and growing. Same error message as metioned above.

Any other clues how to stop this error message (the drive works fine)? hdb=ide-scsi did not work....

ps: this happens on a hp nx 6110 laptop.

---

### Post by incunabulum on 2005-10-24
sorry for the double posting  (slow connection)

---

### Post by subbia on 2005-11-07
here's an HP pavilion zv6158ea with the same problem. No hacks works. Even with kernel 2.6.14. Please let me know.

---

### Post by ruudiculus on 2005-11-11
Hi,

My HP pavilion (zv6000) has the same problem. With both Kubuntu 5.10 32-bit and with Kubuntu 5.10 64-bit.

I thought there might be a firmware upgrade for my TSST corp CD/DVDW TS-L532M (which is Samsung's) that fixes the problem. But it doesn't (which might be sound very logical since my Windows XP CAN deal with the drive). It must be a driver question. But Samsung doesn't provide TS-L532 (M) drivers for linux, so has anyone figured out where the fault message comes from and what it means exactly?

Because as long as my drive is occupied with a cdrom, there' s no problem. But when I eject it and close the cdrom tray again it starts complaining with this fault message. Same in your situation people?

---

### Post by ruudiculus on 2005-11-11
Seems like everyone of you has the same DVDW in their computer.

I found a possible solution on this site:
[http://www.humboldt.edu/~te8/misc/hpzd8230us.html](http://www.humboldt.edu/~te8/misc/hpzd8230us.html)

It seems to have something to do with the 'hal' (higher abstraction layer) program which as I understand is the interface between the hardware and the kernel.

It luckily described exactly my DVDW drive, so it was quite copy paste for me. Please recall you're DVDW drive device name (hdb or hdc) when editing :)

For now it seems to work on my Kubuntu 5.10 AMD64...I'll get back for evaluation.

Good luck with prob-solving and please share your evaluation!

---

### Post by subbia on 2005-11-13
Trying passing ide-scsi for my optical device doesn't work for me. I thought that could be hal too, and this is a confirm. Now I've tried to insert that <match> in storage-policy.fdi and wait a day or two in order to say if it works or not. ;)

---

### Post by ruudiculus on 2005-11-13
Well,

I said I would get back to share my evaluation:

It didn't work. It's still giving the same error messages. :(

Don't know exactly where to look, since I've also got other configuration problems on my to-do list (such as setting up wireless). When I've got time I'll get back here...

---

### Post by subbia on 2005-11-13
for the wireless it doesn't matter. you need only the driver in 64 bit for the broadcom and ndiswrapper. google and synaptic should help you ;)

---

### Post by matis on 2006-01-07
Hi everyone. First of all I'd like to say "Hello !" to You. I'm a really beginner of Linux topic but as I bought my new hp nx6110 i decided to install Linux on it.

Notebook has a DVD-RW included, and when I installed Linux on it, it's occured that I've the same problem as You with terribly annoying message... 

I did my best to find a solution, also tried "hdb=ide-scsi" on grub but didn't work. 
As i said I'm a really beginner but I think I've found a sollution of that problem. 
What the sollution? It's suprisingly easy... I opened /etc/fstab in vim and just comment the last line. Now it seems:

###############################################
# Static entries below, do not use 'users' option in this area
/dev/hda3 / reiserfs defaults,noatime,notail 0 0
/dev/hda4 swap swap sw,pri=1 0 0
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0

# Dynamic entries below, identified by 'users' option
/dev/hda1 /mnt/hda1 ntfs auto,users,exec,rw,umask=0000 0 0
/dev/hda5 /mnt/hda5 ntfs auto,users,exec,rw,umask=0000 0 0
#/dev/cdrom /mnt/cdrom udf,iso9660 noauto,users,dev,ro 0 0
###############################################

More suprisingly was, as when I put :wq the annoying message STOPPED... 

What about mounting cd-rom now? When I put the CD into    and wrote (as a user) "mount /dev/cdrom /mncdrom" it was really mounted and I was able to see my files on CD (alfo on DVD). 

Sorry if sollution isn't good and I really didn't find something new, but in my opinion it really works... My Linux (unfortunately :) ) isn't Ubuntu but SimplyMEPIS, but as I noticed, the problem we had started with 5.10 Ubuntu (new kernel).

Thanks for any post :)
Matis

---

### Post by peholmst on 2006-01-13
Hello everybody,
I just wanted to say I'm having the exact same problem on my HP zv6279ea (Ubuntu 5.10 64-bit, kernel 2.6.12-10-amd64-generic).

I have tried all tips found in this post, but nothing helped (i.e. you are not alone ;-) ). I haven't given up yet, though, it will just need some more fighting, that's all. Does anybody know whether this has been (or should be) submitted as a bug report?

-Petter-

---

### Post by ehsan on 2006-03-30
I'm having this problem as well.  Here's what I did to solve it in Breezy (running a manually compiled 2.6.16 kernel, but the problem did happen with Breezy's 2.6.12 kernel as well).

At first, I was following the instructions in [this page](http://www.humboldt.edu/~te8/misc/hpzd8230us.html), but that did not work for me.  After some poking around, I found out that a hald-addon-storage which is running in the background is the culprit, i.e. if I kill it, the messages stop.  Now, I had noticed in Device Manager that my DVD-RW drive seems to have the hald-addon-storage add-on enabled.  Now, this is done by a rule in /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi:

```

  <device>
    <match key="storage.media_check_enabled" bool="true">
      <append key="info.addons" type="strlist">hald-addon-storage</append>
    </match>
  </device>

```

This rule enables this addon for any storage media on which media checking is enabled.  The trick is to disable the storage.media_check_enabled option in /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi **before** hitting this rule.  I just moved that code to the top of the aforementioned rule, and here's the final excrept from /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi:

```

  <device>
    <match key="storage.bus" string="ide">
     <match key="storage.model" string="TSSTcorpCD/DVDW TS-L532M">
       <match key="block.device" string="/dev/hdc">
         <merge key="storage.media_check_enabled" type="bool">false</merge>
       </match>
     </match>
    </match>
  </device>
  
  <device>
    <match key="storage.media_check_enabled" bool="true">
      <append key="info.addons" type="strlist">hald-addon-storage</append>
    </match>
  </device>

```

Make sure the storage.model in your own config file matches the output of lshal.  After changing this, you should either restart the hald daemon or reboot your machine for the change to take effect, and the problem will go away.

Ehsan

---

### Post by n0ah420 on 2006-03-30
This is great, thanks.  Have you submitted this to the devs? Perhaps they could add it for dapper.

---

### Post by ehsan on 2006-04-02
[QUOTE=n0ah420]This is great, thanks.  Have you submitted this to the devs? Perhaps they could add it for dapper.[/QUOTE]
Check out [this support tickect]("https://launchpad.net/distros/ubuntu/+ticket/656").  It would be great if others that have the same problem (and possibly my fix works for them too) can comment on this problem in that page, so that we have better hope of getting this fixed in Dapper.

Thanks!
Ehsan

---

### Post by n0ah420 on 2006-04-06
Thanks man.  Looks like it does the job.

---

### Post by ufa on 2006-04-15
It didnt work for me :(

al least, partially...
the message continue to appear in the beginning of the boot process. But it stops right after it

---

### Post by kenboo on 2006-06-27
this is only happening while no disc presents in the drive.

it's a bug of the dvd drive.

what's happening is that the drive returns asc=0x30 which means "Incompatible medium installed" where the drive really should say asc=0x3a "Medium not present"

Open /usr/src/linux/drivers/ide/ide-c.c and look for 0x3a;
You'll find this line...
if (sense->asc == 0x3a || sense->asc == 0x04)
So..add 0x30 for work around..
if (sense->asc == 0x30 || sense->asc == 0x3a || sense->asc == 0x04)

The drive maker should release a fix, and that's the only right way.

---

### Post by n0ah420 on 2006-06-27
This file doesn't exist in dapper, at least not on my system.  Any clue where else I may look.  The above fix only 'appears' to work.

---

