---
title: "Ubuntu 10.04 slows down when adding RAM"
date: 2012-02-21
forum: Hardware
---

### Post by williepabon on 2012-02-21
I increased the RAM in my pc from 1 Gig to 3 Gig. After that the boot up time almost tripled. Also, now applications take longer to load. Really (I swear), the only thing I did was to increase the RAM and everything I just described started to happen. Please help.

---

### Post by roelforg on 2012-02-21
Give me the output of:
```

sudo lshw -C memory

```
Warning: may take time, it'll appear to hang on PCI(sysfs) but it's just scanning.

---

### Post by |{urse on 2012-02-21
Hi there, sounds like fun, I have 2 guesses but it's going to take some footwork (i.e i need more info)

Would you kindly remove your old 1gb stick of ram and install the 2 new ones, boot up and tell us if it is still slow?

ALLLSO What is your motherboard make and model, what brand, speed, and cas latency is the original 1gb of ram, and what brand, speed and cas latency is the ram upgrade? Is the ram upgrade new sticks or used and did you run the memtest on the whole 3gb with ubuntu livecd yet?

---

### Post by roelforg on 2012-02-21
> **|{urse said:**
> Hi there, sounds like fun, I have 2 guesses but it's going to take some footwork (i.e i need more info)

Would you kindly remove your old 1gb stick of ram and install the 2 new ones, boot up and tell us if it is still slow?

ALLLSO What is your motherboard make and model, what brand, speed, and cas latency is the original 1gb of ram, and what brand, speed and cas latency is the ram upgrade? Is the ram upgrade new sticks or used and did you run the memtest on the whole 3gb with ubuntu livecd yet?
Actually, i was asking for the lshw output because it shows the memspeeds as well.
Allows for accurate diagnosing of which stick is the problem.

---

### Post by ahallubuntu on 2012-02-21
Did you run Memtest to test the new RAM?  It is possible to install RAM in a computer that will kind of work but is not compatible with the motherboard.  I'd run Memtest for 60 seconds on this.  You can launch Memtest from a Grub menu - hold down the Shift key upon boot if you don't get the menu automatically.  Or run Memtest from your Ubuntu CD.

---

### Post by williepabon on 2012-02-21
> **roelforg said:**
> Actually, i was asking for the lshw output because it shows the memspeeds as well.
Allows for accurate diagnosing of which stick is the problem.

Thanks for answering.  My pc is a DELL workstation Precision 670 with memory chips rated at PC2-3200R-333-10. Since I have dual boot up, I have no problems when booting Windows XP. My issue is only with Ubuntu 10.04. I have no problems also, when I boot Ubuntu 10.10(maverick) from a usb flash drive. Please, advise.

---

### Post by roelforg on 2012-02-21
> **williepabon said:**
> Thanks for answering.  My pc is a DELL workstation Precision 670 with memory chips rated at PC2-3200R-333-10. Since I have dual boot up, I have no problems when booting Windows XP. My issue is only with Ubuntu 10.04. I have no problems also, when I boot Ubuntu 10.10(maverick) from a usb flash drive. Please, advise.

Please see my first post.

---

### Post by |{urse on 2012-02-21
> **roelforg said:**
> Actually, i was asking for the lshw output because it shows the memspeeds as well.
Allows for accurate diagnosing of which stick is the problem.

I know what lshw does, thanks. :)

---

### Post by ahallubuntu on 2012-02-21
> **williepabon said:**
> I increased the RAM in my pc from 1 Gig to 3 Gig. After that the boot up time almost tripled. Also, now applications take longer to load. Really (I swear), the only thing I did was to increase the RAM and everything I just described started to happen. Please help.

Open a terminal and type "top" and see what's going on.  Can you paste the top few lines of "top" here?

When you  launch an application while top is running, watch the list of processes.  Notice anything while the application is trying to start up?

---

### Post by williepabon on 2012-02-21
> **roelforg said:**
> Please see my first post.

roelforg:

Here are the results of lshw:


williepabon@Precision-WorkStation-670:~$ sudo lshw -C memory
[sudo] password for williepabon: 
  *-firmware              
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A02 (09/02/2004)
       size: 64KiB
       capacity: 448KiB
       capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 16KiB
       capacity: 16KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 701
       size: 1MiB
       capacity: 1MiB
       capabilities: internal varies unified
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 3GiB
     *-bank:0
          description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
          physical id: 0
          slot: DIMM_1
          size: 512MiB
          width: 64 bits
          clock: 400MHz (2.5ns)
     *-bank:1
          description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
          physical id: 1
          slot: DIMM_2
          size: 512MiB
          width: 64 bits
          clock: 400MHz (2.5ns)
     *-bank:2
          description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
          physical id: 2
          slot: DIMM_3
          size: 1GiB
          width: 64 bits
          clock: 400MHz (2.5ns)
     *-bank:3
          description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
          physical id: 3
          slot: DIMM_4
          size: 1GiB
          width: 64 bits
          clock: 400MHz (2.5ns)
     *-bank:4
          description: DIMM SDRAM Synchronous 400 MHz (2.5 ns) [empty]
          physical id: 4
          slot: DIMM_5
          width: 64 bits
          clock: 400MHz (2.5ns)
     *-bank:5
          description: DIMM SDRAM Synchronous 400 MHz (2.5 ns) [empty]
          physical id: 5
          slot: DIMM_6
          width: 64 bits
          clock: 400MHz (2.5ns)
williepabon@Precision-WorkStation-670:~$ 


Thanks for the help.
wp

---

### Post by williepabon on 2012-02-22
> **ahallubuntu said:**
> Open a terminal and type "top" and see what's going on.  Can you paste the top few lines of "top" here?

When you  launch an application while top is running, watch the list of processes.  Notice anything while the application is trying to start up?

Here is a sample of top:

williepabon@WP-WrkStation:~$ top

top - 08:42:23 up 19 min,  2 users,  load average: 2.16, 2.46, 1.97
Tasks: 158 total,   2 running, 156 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7%us,  6.3%sy, 88.4%ni,  0.0%id,  0.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3095340k total,   999416k used,  2095924k free,    87640k buffers
Swap:  1991672k total,        0k used,  1991672k free,   477400k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2242 root      30  10 66440  49m 4700 R 91.8  1.6   0:11.91 update-apt-xapi    
 1224 root      20   0 71680  50m  16m S  2.3  1.7   0:29.64 Xorg               
 1834 williepa  20   0 70224  54m  17m S  2.0  1.8   0:06.46 compiz             
 2171 williepa  20   0 47888  13m 9956 S  1.7  0.4   0:01.47 gnome-terminal     
 1853 williepa  20   0  232m  50m  18m S  1.0  1.7   0:07.91 skype              
 1953 williepa  20   0 40684  19m 5100 S  0.3  0.6   0:03.42 ubuntuone-syncd    
 2189 williepa  20   0  2548 1204  904 R  0.3  0.0   0:00.43 top                
    1 root      20   0  2812 1656 1196 S  0.0  0.1   0:00.88 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.35 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.05 events/0           


I don't know what to look for on the terminal screen when an application is trying to start up. Any suggestions? Please, advise.
wp

---

### Post by roelforg on 2012-02-22
> **williepabon said:**
> Here is a sample of top:

williepabon@WP-WrkStation:~$ top

top - 08:42:23 up 19 min,  2 users,  load average: 2.16, 2.46, 1.97
Tasks: 158 total,   2 running, 156 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7%us,  6.3%sy, 88.4%ni,  0.0%id,  0.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3095340k total,   999416k used,  2095924k free,    87640k buffers
Swap:  1991672k total,        0k used,  1991672k free,   477400k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2242 root      30  10 66440  49m 4700 R 91.8  1.6   0:11.91 update-apt-xapi    
 1224 root      20   0 71680  50m  16m S  2.3  1.7   0:29.64 Xorg               
 1834 williepa  20   0 70224  54m  17m S  2.0  1.8   0:06.46 compiz             
 2171 williepa  20   0 47888  13m 9956 S  1.7  0.4   0:01.47 gnome-terminal     
 1853 williepa  20   0  232m  50m  18m S  1.0  1.7   0:07.91 skype              
 1953 williepa  20   0 40684  19m 5100 S  0.3  0.6   0:03.42 ubuntuone-syncd    
 2189 williepa  20   0  2548 1204  904 R  0.3  0.0   0:00.43 top                
    1 root      20   0  2812 1656 1196 S  0.0  0.1   0:00.88 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.35 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.05 events/0           


I don't know what to look for on the terminal screen when an application is trying to start up. Any suggestions? Please, advise.
wp

Your problem is already solved.
See here: [http://ubuntuforums.org/showthread.php?p=6935368](http://ubuntuforums.org/showthread.php?p=6935368)

Long story short, solution that fixed the same issue on my pc:
run (replace <username> with your username):
```

sudo cp -a /etc/cron.weekly/apt-xapian-index /home/<username>/apt-xapian-index
sudo nano /etc/cron.weekly/apt-xapian-index

```
Empty the file and replace the contents with the version i added below;when done:
Hit CTRL-O
Hit Enter
Hit CTRL-X
Reboot

apt-xapian-index:
```

#!/bin/sh

CMD=/usr/sbin/update-apt-xapian-index

# ionice should not be called in a virtual environment
# (similar to man-db cronjobs)
egrep -q '(envID|VxID):.*[1-9]' /proc/self/status || IONICE=/usr/bin/ionice

# Check if we're on battery
if which on_ac_power >/dev/null 2>&1; then
    on_ac_power >/dev/null 2>&1
    ON_BATTERY=$?

    # Here we use "-eq 1" instead of "-ne 0" because
    # on_ac_power could also return 255, which means
    # it can't tell whether we are on AC or not. In
    # that case, run update-a-x-i nevertheless.
    [ "$ON_BATTERY" -eq 1 ] && exit 0
fi

# Rebuild the index
if [ -x "$CMD" ]
then
        if [ -x "$IONICE" ]
        then
                nice -n 19 $IONICE -c 3 $CMD --update --quiet
        else
                nice -n 19 $CMD --update --quiet
        fi
fi

```

---

### Post by williepabon on 2012-02-22
I ran bootchart and I'm enclosing the png file for you  to analyze. thanks

---

### Post by roelforg on 2012-02-22
> **williepabon said:**
> I ran bootchart and I'm enclosing the png file for you  to analyze. thanks
I pondered with that one a lot.
When i ran top i noticed that apt-xapian-index was the problem;
the difference with the nice commands (e.g. the adding of the --update arg to apt-xapian-index fixed it).
It's a known bug.

---

### Post by williepabon on 2012-02-22
> **roelforg said:**
> I pondered with that one a lot.
When i ran top i noticed that apt-xapian-index was the problem;
the difference with the nice commands (e.g. the adding of the --update arg to apt-xapian-index fixed it).
It's a known bug.

Thanks for answering so fast. I implemented your solution for the xapian-index but, still the boot process is awfully long. It should be noted also, that, after boot up, when I run an application, the initial loading takes a long time. After that it runs normal (I assume it's already in RAM). Again, roelforg, thanks for the help.
wp

---

### Post by roelforg on 2012-02-22
> **williepabon said:**
> Thanks for answering so fast. I implemented your solution for the xapian-index but, still the boot process is awfully long. It should be noted also, that, after boot up, when I run an application, the initial loading takes a long time. After that it runs normal (I assume it's already in RAM). Again, roelforg, thanks for the help.
wp
Give it 1 min after logging in; init is still starting stuff behind the scenes.
The ram gets cleared after closing the app; the 2e time you try only goes faster because the timing is just right and init has finished launching stuff.

---

### Post by williepabon on 2012-02-22
> **roelforg said:**
> Give it 1 min after logging in; init is still starting stuff behind the scenes.
The ram gets cleared after closing the app; the 2e time you try only goes faster because the timing is just right and init has finished launching stuff.

roelforg:
Thanks for answering. I understand what you say but, this long boot times didn't exist when I only had 1 Gig of RAM on my pc. They started when I increased to 3 Gig. Also, as I said before, this situation happens only with Ubuntu 10.04 (on the hard drive). When I boot up with Ubuntu 10.10 or 11.10 (have them on removable flash drives), the problem doesn't show up. Any suggestions?
wp

---

### Post by roelforg on 2012-02-22
> **williepabon said:**
> roelforg:
Thanks for answering. I understand what you say but, this long boot times didn't exist when I only had 1 Gig of RAM on my pc. They started when I increased to 3 Gig. Also, as I said before, this situation happens only with Ubuntu 10.04 (on the hard drive). When I boot up with Ubuntu 10.10 or 11.10 (have them on removable flash drives), the problem doesn't show up. Any suggestions?
wp
I'd say upgrade to 11.10.
It's probably a bug that's fixed in newer releases.

---

### Post by ahallubuntu on 2012-02-22
> **williepabon said:**
> roelforg:
Thanks for answering. I understand what you say but, this long boot times didn't exist when I only had 1 Gig of RAM on my pc. They started when I increased to 3 Gig. Also, as I said before, this situation happens only with Ubuntu 10.04 (on the hard drive). When I boot up with Ubuntu 10.10 or 11.10 (have them on removable flash drives), the problem doesn't show up. Any suggestions?
wp

Have you tested your hard drive?  Could it be having issues coincidentally?

Try removing the RAM you just added and see if things speed up again.  If so, then your hard drive is fine and it really is the RAM.  If things are still slow, time to test your hard drive.  Also run an e2fsck on your / filesystem.

---

### Post by Yellow Pasque on 2012-02-22
Have you tried putting the 2 1GB modules in the first two slots (and the 512MB modules in the next slots)?

[http://support.dell.com/support/edocs/systems/ws670/en/ug_en/before.htm#wp1131665](http://support.dell.com/support/edocs/systems/ws670/en/ug_en/before.htm#wp1131665)

---

### Post by williepabon on 2012-02-22
> **ahallubuntu said:**
> Have you tested your hard drive?  Could it be having issues coincidentally?

Try removing the RAM you just added and see if things speed up again.  If so, then your hard drive is fine and it really is the RAM.  If things are still slow, time to test your hard drive.  Also run an e2fsck on your / filesystem.

ahallubuntu:
Thanks for answering. I used a DELL diagnostics program (that comes with the pc) that thoroughly checks the RAM chips, and they are OK.  Will do the e2fsck thing. Next thing I need to do is check the health of the hard drive.Need to know what Linux app does that.
wp

---

### Post by williepabon on 2012-02-22
> **Temüjin said:**
> Have you tried putting the 2 1GB modules in the first two slots (and the 512MB modules in the next slots)?

[http://support.dell.com/support/edocs/systems/ws670/en/ug_en/before.htm#wp1131665](http://support.dell.com/support/edocs/systems/ws670/en/ug_en/before.htm#wp1131665)

Temujin:

Not possible on this case because 512 MB chips are rank 2 and the 1 Gib chips rank 1. The higher rank chips have to be in the first two slots.
wp

---

### Post by williepabon on 2012-02-22
> **ahallubuntu said:**
> Have you tested your hard drive?  Could it be having issues coincidentally?

Try removing the RAM you just added and see if things speed up again.  If so, then your hard drive is fine and it really is the RAM.  If things are still slow, time to test your hard drive.  Also run an e2fsck on your / filesystem.

Ahallubuntu:
Forgot to ask you in my last post a little help on using the e2fsck command. Would you? Thanks.
wp

---

### Post by ahallubuntu on 2012-02-22
You can use GSmartControl in Ubuntu (install it first) to check the drive's S.M.A.R.T. status.  First look at the Attributes tab and see what Attributes if any are highlighted in pink - those are the "errors" you need to worry about.  You can also run the Extended S.M.A.R.T. test (may take a while) which should thoroughly check the drive itself with a surface scan.

e2fsck checks the FILESYSTEM not the drive, and you won't be able to check the / filesystem while you are actually booted to it.  So you'll need to run it from a live CD or USB flash drive.

sudo e2fsck /dev/sda1 

if your filesystem is on /dev/sda1 partition.

It may say it's clean; you can force a check:

sudo e2fsck -f /dev/sda1

Note, this can take a long time.  You can also google for more info on this command.  If there are no filesystem issues, it should just take a while and then complete on its own, but if there are filesystem issues you may be prompted to fix them with various options.

---

### Post by williepabon on 2012-02-23
> **ahallubuntu said:**
> You can use GSmartControl in Ubuntu (install it first) to check the drive's S.M.A.R.T. status.  First look at the Attributes tab and see what Attributes if any are highlighted in pink - those are the "errors" you need to worry about.  You can also run the Extended S.M.A.R.T. test (may take a while) which should thoroughly check the drive itself with a surface scan.

e2fsck checks the FILESYSTEM not the drive, and you won't be able to check the / filesystem while you are actually booted to it.  So you'll need to run it from a live CD or USB flash drive.

sudo e2fsck /dev/sda1 

if your filesystem is on /dev/sda1 partition.

It may say it's clean; you can force a check:

sudo e2fsck -f /dev/sda1

Note, this can take a long time.  You can also google for more info on this command.  If there are no filesystem issues, it should just take a while and then complete on its own, but if there are filesystem issues you may be prompted to fix them with various options.

ahallubuntu
Unfortunately, my disk is old and does not support SMART technology. What other options I have? I there  a possibility that the problem might be that something in the OS kernel be corrupted? I haven't erased the previous versions of the kernel. Can I start the machine with a previous version without affecting anything? Please, advice, I don't want to make it worse. This hard drive has critical data. I have a back up, but it is various weeks old.
Thanks.

---

### Post by ahallubuntu on 2012-02-23
Are you sure S.M.A.R.T. is enabled in the BIOS Setup?  S.M.A.R.T. is not that new - I have used it on many old hard drives including some ancient 10GB Western Digital drives I use for old builds.  Those came out of systems that could not support even 1GB of RAM.

You can try the Ultimate Boot CD and try to find a hard drive utility to test your make of hard drive.  Or try Dell's diagnostic for the drive if they have one.

---

### Post by williepabon on 2012-02-23
> **ahallubuntu said:**
> Are you sure S.M.A.R.T. is enabled in the BIOS Setup?  S.M.A.R.T. is not that new - I have used it on many old hard drives including some ancient 10GB Western Digital drives I use for old builds.  Those came out of systems that could not support even 1GB of RAM.

You can try the Ultimate Boot CD and try to find a hard drive utility to test your make of hard drive.  Or try Dell's diagnostic for the drive if they have one.

Yes, SMART is enabled. My pc has two additional hard drives with SMART technology. The difference is that the hard drive with Ubuntu is external (USB). DELL diagnostics has utilities for examining the hard drives. My question is, if it safe to check a drive that is not formatted NTFS (my drive is Ext4)?

---

### Post by ahallubuntu on 2012-02-23
The fact that it's an external drive is important information.  Adding RAM should not make an external drive slower, but external drives connected via USB are affected by the speed of the USB port.

Can you revert the computer back to the original RAM (1GB)?  Is the PC fast booting Ubuntu again?  If not, then clearly RAM is not a factor.

In a terminal, type this

sudo hdparm -t /dev/sda

for each of your drives (replacing /dev/sda).  What is the reading for your external drive with Ubuntu?  If the transfer speed to that external drive is too slow, then that is why your computer is slow. (For example: on my laptop with internal drive/ I get a reading of 78.10 MB/sec.)  In general, I'd expect Ubuntu to run much slower off an external drive than off an internal drive.

It is possible to test S.M.A.R.T. on many external drives, but you may need to build a new version of SmartMonTools and figure out the drive controller's chipset - perhaps not worth the trouble at the moment.

I don't think Dell Diagnostics will run on an external drive anyway, so don't worry about it.

---

### Post by williepabon on 2012-02-24
> **ahallubuntu said:**
> The fact that it's an external drive is important information.  Adding RAM should not make an external drive slower, but external drives connected via USB are affected by the speed of the USB port.

Can you revert the computer back to the original RAM (1GB)?  Is the PC fast booting Ubuntu again?  If not, then clearly RAM is not a factor.

In a terminal, type this

sudo hdparm -t /dev/sda

for each of your drives (replacing /dev/sda).  What is the reading for your external drive with Ubuntu?  If the transfer speed to that external drive is too slow, then that is why your computer is slow. (For example: on my laptop with internal drive/ I get a reading of 78.10 MB/sec.)  In general, I'd expect Ubuntu to run much slower off an external drive than off an internal drive.

It is possible to test S.M.A.R.T. on many external drives, but you may need to build a new version of SmartMonTools and figure out the drive controller's chipset - perhaps not worth the trouble at the moment.

I don't think Dell Diagnostics will run on an external drive anyway, so don't worry about it.

I checked the speed of the drive with the command suggested and I get like 1.04 MB/sec reads with the external hd. But I also did the same check with my USB flash drive and I get basically the same results. On the other hand, the OS in the hard drive boots slow (Ubuntu 10.04)but the OS on the flash drive (Ubuntu 10.10) boots fast. What you make of this?

I haven't reverted my pc to the original RAM (1Gig)yet because it's a hassle. Eventually will do it to see if the boot times speed up. If it does, what would be the conclusion for this problem? Thanks.
wp

---

### Post by williepabon on 2012-02-24
> **williepabon said:**
> I checked the speed of the drive with the command suggested and I get like 1.04 MB/sec reads with the external hd. But I also did the same check with my USB flash drive and I get basically the same results. On the other hand, the OS in the hard drive boots slow (Ubuntu 10.04)but the OS on the flash drive (Ubuntu 10.10) boots fast. What you make of this?

I haven't reverted my pc to the original RAM (1Gig)yet because it's a hassle. Eventually will do it to see if the boot times speed up. If it does, what would be the conclusion for this problem? Thanks.
wp

New info to add:
The timings above were checked using hdparm run from the OS on the external drive (Ubuntu 10.04). Out of curiosity, I ran the same command using the OS on the flash drive (Ubuntu 10.10) and the results I get are like 30.8 MB/sec! What this means?

---

### Post by williepabon on 2012-03-13
> **ahallubuntu said:**
> Have you tested your hard drive?  Could it be having issues coincidentally?

Try removing the RAM you just added and see if things speed up again.  If so, then your hard drive is fine and it really is the RAM.  If things are still slow, time to test your hard drive.  Also run an e2fsck on your / filesystem.

Ahallubuntu:

Sorry it took so long to answer. I was deeply investigating my problem. Indeed, I made the investigation with the memory. This is what I did.

 But before doing it, to check out any possibility of hardware issues on the hard drive, I did the following: (1) purchased a new hard drive enclosure and moved my hard drive to this one, (2) purchased a new USB cable and used it to connect my hard drive/enclosure setup to a different USB port on my pc.

Then, I performed speed tests with 1 Gig, 2 Gigs and 3 Gigs of RAM with my Ubuntu 10.04 OS. Ubuntu 10.04 worked well when the pc had 1 Gig or 2 Gigs of RAM. When I increased to 3 Gigs, it slowed down to a crawl. I can't understand the relationship between an increase of 1 Gig and the effect it has in Ubuntu 10.04. This doesn't happens with Ubuntu 10.10 and 11.10. Unfortunately for me, Ubuntu 10.04 is my principal work operating system. So, I need a solution for this. Thanks for the help.

---

### Post by williepabon on 2012-03-14
My suspicions on the cause of this problem is moving into the way the OS loads the USB drivers (uhci-hcd and ehci_hcd). It appears that the OS is not loading ehci_hcd, which is the fast usb driver.

Here are the results of lsusb -t for ubuntu 10.04

williepabon@WP-WrkStation:~$ sudo lsusb -t
[sudo] password for williepabon: 
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 1: Dev 3, If 0, Class=HID, Driver=usbhid, 12M
        |__ Port 1: Dev 3, If 1, Class=HID, Driver=usbhid, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=stor., Driver=ums-cypress, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 12M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 12M
    |__ Port 2: Dev 2, If 2, Class=audio, Driver=snd-usb-audio, 12M
    |__ Port 2: Dev 2, If 3, Class=audio, Driver=snd-usb-audio, 12M

Compared to booting with Ubuntu 10.10,

williepabon@Precision-WorkStation-670:~$ sudo lsusb -t
[sudo] password for williepabon: 
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 1: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 2: Dev 3, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 2: Dev 3, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 2: Dev 3, If 2, Class=audio, Driver=snd-usb-audio, 480M
    |__ Port 2: Dev 3, If 3, Class=audio, Driver=snd-usb-audio, 480M

where you see ehci_hcd loaded.

 Something strange is happening as you can see on the attached picture. I seems that the OS goes into a loop when loading the driver. Has anybody here seen something like this? If so, any ideas to solve it?

---

### Post by williepabon on 2012-03-14
I'm including here a portion of the /var/log/message for you people to analyze and advice.


Problem messages from messages log.

Mar 12 13:16:07 WP-WrkStation kernel: [    0.735247] pci 0000:00:1d.7: BAR 0: can't allocate resource
Mar 12 13:16:07 WP-WrkStation kernel: [    0.735398] Expanded resource reserved due to conflict with PCI Bus 0000:00

Mar 12 13:16:07 WP-WrkStation kernel: [    0.814255] pci 0000:00:1d.7: EHCI: unrecognized capability e0
Mar 12 13:16:07 WP-WrkStation kernel: [    0.814260] pci 0000:00:1d.7: EHCI: unrecognized capability e0
Mar 12 13:16:07 WP-WrkStation kernel: [    0.814265] pci 0000:00:1d.7: EHCI: unrecognized capability e0
Mar 12 13:16:07 WP-WrkStation kernel: [    0.814269] pci 0000:00:1d.7: EHCI: unrecognized capability e0
.....
Mar 12 13:16:07 WP-WrkStation kernel: [    0.814517] pci 0000:00:1d.7: EHCI: unrecognized capability e0
.....
Mar 12 13:16:07 WP-WrkStation kernel: [    0.883387] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 12 13:16:07 WP-WrkStation kernel: [    0.883428] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Mar 12 13:16:07 WP-WrkStation kernel: [    0.883458] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 12 13:16:07 WP-WrkStation kernel: [    0.883526] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Mar 12 13:16:07 WP-WrkStation kernel: [    0.883571] ehci_hcd 0000:00:1d.7: debug port 15 IN USE
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907258] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xbff00000
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907284] ehci_hcd 0000:00:1d.7: USB bus 1 deregistered
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907359] ehci_hcd 0000:00:1d.7: PCI INT D disabled

.....
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907434] uhci_hcd: USB Universal Host Controller Interface driver
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907479] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907495] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907553] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907590] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907757] usb usb1: configuration #1 chosen from 1 choice
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907815] hub 1-0:1.0: USB hub found
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907828] hub 1-0:1.0: 2 ports detected
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907919] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907934] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907991] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908026] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908191] usb usb2: configuration #1 chosen from 1 choice
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908242] hub 2-0:1.0: USB hub found
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908253] hub 2-0:1.0: 2 ports detected
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908329] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908346] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908403] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908429] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908587] usb usb3: configuration #1 chosen from 1 choice
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908636] hub 3-0:1.0: USB hub found
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908648] hub 3-0:1.0: 2 ports detected
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908721] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908736] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908799] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908825] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
Mar 12 13:16:07 WP-WrkStation kernel: [    0.908983] usb usb4: configuration #1 chosen from 1 choice
Mar 12 13:16:07 WP-WrkStation kernel: [    0.909033] hub 4-0:1.0: USB hub found
Mar 12 13:16:07 WP-WrkStation kernel: [    0.909045] hub 4-0:1.0: 2 ports detected
......
Mar 12 13:16:07 WP-WrkStation kernel: [    1.968031] usb 4-1: new full speed USB device using uhci_hcd and address 2
Mar 12 13:16:07 WP-WrkStation kernel: [    2.137898] usb 4-1: configuration #1 chosen from 1 choice
Mar 12 13:16:07 WP-WrkStation kernel: [    2.145795] hub 4-1:1.0: USB hub found
Mar 12 13:16:07 WP-WrkStation kernel: [    2.146757] hub 4-1:1.0: 3 ports detected
Mar 12 13:16:07 WP-WrkStation kernel: [    2.425732] usb 4-1.1: new full speed USB device using uhci_hcd and address 3


On the kern.log I get the following:

.........
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907258] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xbff00000
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907273] ehci_hcd 0000:00:1d.7: startup error -19
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907284] ehci_hcd 0000:00:1d.7: USB bus 1 deregistered
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907359] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Mar 12 13:16:07 WP-WrkStation kernel: [    0.907365] ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -19

---

### Post by williepabon on 2012-03-26
Problem is solved. One of the folks from AskUbuntu showed me how to install the 11.10 kernel in my Ubuntu LTS, and with the new kernel, the problem of low speed disappeared. Evidently, there is an issue with 10.04 when you increase RAM, that makes it not to load the ehci_hcd driver (USB) which causes such ports to run very slow.
wp

---

### Post by Dread78 on 2012-05-22
Well I have to admit. After reading your guys posts and seeing the collaborative effort you all showed to try to work through the issue it really makes me want to jump in bed with the Penguin.
I've been staring out the Window for so long my reflection is embedded into it.

Anyways.. So I have a question and I really do not hope anyone minds me asking - this was the main reason why I signed up to the Ubuntu forums... (although now it may be to run Ubuntu on the side in a VM or something)

I have the same situation as [williepabon]("http://ubuntuforums.org/member.php?u=1165026"). Except I am experiencing it on Windows 7. With the (?)distribution(?) that willie was encouraged to run. Would this version have had a driver update newer than the distro he was using?
Sorry I just re-read his last post a little more carefully. So the problem was "ehci_hcd " because of the h and the d I want to call it a hard drive but I see that this is the USB driver? So i guess that means that release would have an updated USB driver.
I wonder if I am going to be able to get around this by removing all USB devices from the system because I certainly doubt I am going to find driver for this unsupported system.

This is at my job site. Its occurring on both of our workstations i recently  resurrected and just got the ram in to upgrade today. (A system that beefy can be used way past its prime.)

In all my years of supporting computers I have never encountered an  issue where when you stuck more RAM into the computer - it made it  slower.

Thanks

---

