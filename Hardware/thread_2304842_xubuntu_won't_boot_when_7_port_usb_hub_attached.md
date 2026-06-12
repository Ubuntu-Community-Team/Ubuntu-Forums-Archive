---
title: "xubuntu won't boot when 7 port usb hub attached"
date: 2015-11-30
forum: Hardware
---

### Post by Kilarin on 2015-11-30
This is an odd one.  
I purchased a "Link Depot" 7-port usb 2.0 hub to use with my new Lenovo thinkpad e555 (xubuntu 14.04 32bit dual boot with windows 7)
this model: [http://www.frys.com/product/7200823](http://www.frys.com/product/7200823)

The usb hub specifically states that it is linux compatible (Well, Red Hat Linux9 anyway)

When I boot into windows 7 with the usb hub connected, the usb hub works just fine.
And, when I boot into Xubuntu without the usb hub connected, then connected it, it works just fine.

BUT, if I try to boot xubuntu with the usb hub already plugged in, I just get a blank screen and a blinking cursor.  Nothing else.  Doesn't matter if any other devices are connected to the hub or not.  If the hub is connected, Xubuntu won't boot.

Does anyone have a clue what could be causing this problem, or what could be the solution?

Or even what log I should look into to see what the actual error is?

I would REALLY appreciate some help.  thank you,

---

### Post by matt_symes on 2015-11-30
Hi

Remove quiet and splash

```
sudo nano /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

from your kernel command line, update grub

```
sudo update-grub
```

and reboot with the hub plugged in. what does it say on the screen when it's hanging ?

I would also look in your old syslogs for clues.

```
gedit /var/log/syslog{,.1}
```

What USB BIOS settings do you have set ?

Does it hang if you reboot to the recovery console ?

That's where i would start looking.

Kind regards

---

### Post by Kilarin on 2015-11-30
Thank you SO much for your help on this!

Well, this is fascinating.  Thanks for the info on how to turn off quiet and splash, that is VERY useful to know.  I did that, and I did it correctly because if I boot without the usb hub connected, I can now see the log displaying as xubuntu loads.

But here is the strange part.  If I boot with the usb hub connected, I don't get ANY output.  Just a blank black screen.  So, I am guessing that means it is locking up VERY early in the process?

This is what syslog shows when I try to boot with the usb hub connected:
```

Nov 30 12:04:26 perelandra kernel: [  531.104203] usb 5-1: new high-speed USB device number 2 using ehci-pci
Nov 30 12:04:26 perelandra kernel: [  531.237382] usb 5-1: New USB device found, idVendor=14cd, idProduct=8601
Nov 30 12:04:26 perelandra kernel: [  531.237395] usb 5-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Nov 30 12:04:26 perelandra kernel: [  531.237402] usb 5-1: Product: USB 2.0 Hub
Nov 30 12:04:26 perelandra kernel: [  531.237407] usb 5-1: Manufacturer: USB Device
Nov 30 12:04:26 perelandra kernel: [  531.239803] hub 5-1:1.0: USB hub found
Nov 30 12:04:26 perelandra kernel: [  531.240623] hub 5-1:1.0: 4 ports detected
Nov 30 12:04:26 perelandra kernel: [  531.512252] usb 5-1.1: new high-speed USB device number 3 using ehci-pci
Nov 30 12:04:26 perelandra kernel: [  531.609519] usb 5-1.1: New USB device found, idVendor=14cd, idProduct=8601
Nov 30 12:04:26 perelandra kernel: [  531.609532] usb 5-1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Nov 30 12:04:26 perelandra kernel: [  531.609539] usb 5-1.1: Product: USB 2.0 Hub
Nov 30 12:04:26 perelandra kernel: [  531.609544] usb 5-1.1: Manufacturer: USB Device
Nov 30 12:04:26 perelandra kernel: [  531.610182] hub 5-1.1:1.0: USB hub found
Nov 30 12:04:26 perelandra kernel: [  531.610390] hub 5-1.1:1.0: 4 ports detected
Nov 30 12:04:32 perelandra dbus[719]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Nov 30 12:04:32 perelandra dbus[719]: [system] Successfully activated service 'org.freedesktop.systemd1'
Nov 30 12:04:32 perelandra rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="732" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

it just stops there.  Nothing else in the log until I pulled the connection and rebooted.

[quote="matt_symes"]What USB BIOS settings do you have set?[/quote]
USB UEFI Bios Support [Enabled]
Always on USB [Enabled]
  Charge in Battery Mode [Disabled]
USB 3.0 Mode [Auto]

Is that what you were looking for, or something else?

When I connect the usb hub, and then do lsusb, it adds these lines:
```
Bus 005 Device 003: ID 14cd:8601 Super Top
Bus 005 Device 002: ID 14cd:8601 Super Top 
```

Now, here is another odd piece of this puzzle.  I tried booting into recovery mode with the usb hub connected as you suggested.  It went all the way to the recovery console with no problems.  From there I selected "resume normal boot", and it proceeded to boot into Xubuntu normally WITH NO PROBLEMS, the usb hub connected all the time.

tested normal reboot after that, and it still goes directly to the blank screen if the usb hub is attached.

Thank you again for your help.

---

### Post by matt_symes on 2015-11-30
Hi

> **Kilarin said:**
> Thank you SO much for your help on this!

Well, this is fascinating.  Thanks for the info on how to turn off quiet and splash, that is VERY useful to know.  I did that, and I did it correctly because if I boot without the usb hub connected, I can now see the log displaying as xubuntu loads.

No problem. It's very useful. 

I believe there is a kernel command line parameter *log_level=* for more control and  *ignore_loglevel* that will print all kernel commands to the console.
```

        loglevel=       All Kernel Messages with a loglevel smaller than the
                        console loglevel will be printed to the console. It can
                        also be changed with klogd or other programs. The
                        loglevels are defined as follows:

                        0 (KERN_EMERG)          system is unusable
                        1 (KERN_ALERT)          action must be taken immediately
                        2 (KERN_CRIT)           critical conditions
                        3 (KERN_ERR)            error conditions
                        4 (KERN_WARNING)        warning conditions
                        5 (KERN_NOTICE)         normal but significant condition
                        6 (KERN_INFO)           informational
                        7 (KERN_DEBUG)          debug-level messages
```

```
        ignore_loglevel [KNL]
                        Ignore loglevel setting - this will print /all/
                        kernel messages to the console. Useful for debugging.
                        We also add it as printk module parameter, so users
                        could change it dynamically, usually by
                        /sys/module/printk/parameters/ignore_loglevel.
```

There is also a way to get the early printk message that miss the console if there is a hang (they get buffered until the console is up and then displayed) but it's fiddly and i would need to refresh my memory on it.

> But here is the strange part.  If I boot with the usb hub connected, I don't get ANY output.  Just a blank black screen.  So, I am guessing that means it is locking up VERY early in the process?

USB UEFI Bios Support [Enabled]
Always on USB [Enabled]
  Charge in Battery Mode [Disabled]
USB 3.0 Mode [Auto]

Is that what you were looking for, or something else?

The reason why i asked about your BIOS settings is because I once had a laptop  that would not recognise a USB keyboard unless the 'enable legacy USB' option was enabled in the BIOS. However, with that setting enabled, if the keyboard was plugged in when the laptop was started, the laptop would not boot. It would not even start to the POST tests.

I take it this issue is not affecting you as you can get to the grub menu to boot into recovery mode and then resume normal boot but it does show that tweaking with your BIOS setting can sometimes make a  difference.

What ever is happening is happening really early in the boot process, after grub has loaded but before the console is enabled and before it's writing to the logs - it looks to be still buffered in memory.

<**EDIT**: We may be able to check this hypothesis by setting the loglevel= to log (almost) everything and see if you get anything onm the console.>

On my machine this early stage includes setting up memory and *reading ACPI tables* so play with your USB and other BIOS settings. 

> ```

Nov 30 12:04:26 perelandra kernel: [  531.104203] usb 5-1: new high-speed USB device number 2 using ehci-pci
Nov 30 12:04:26 perelandra kernel: [  531.237382] usb 5-1: New USB device found, idVendor=14cd, idProduct=8601
Nov 30 12:04:26 perelandra kernel: [  531.237395] usb 5-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Nov 30 12:04:26 perelandra kernel: [  531.237402] usb 5-1: Product: USB 2.0 Hub
Nov 30 12:04:26 perelandra kernel: [  531.237407] usb 5-1: Manufacturer: USB Device
Nov 30 12:04:26 perelandra kernel: [  531.239803] hub 5-1:1.0: USB hub found
Nov 30 12:04:26 perelandra kernel: [  531.240623] hub 5-1:1.0: 4 ports detected
Nov 30 12:04:26 perelandra kernel: [  531.512252] usb 5-1.1: new high-speed USB device number 3 using ehci-pci
Nov 30 12:04:26 perelandra kernel: [  531.609519] usb 5-1.1: New USB device found, idVendor=14cd, idProduct=8601
Nov 30 12:04:26 perelandra kernel: [  531.609532] usb 5-1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Nov 30 12:04:26 perelandra kernel: [  531.609539] usb 5-1.1: Product: USB 2.0 Hub
Nov 30 12:04:26 perelandra kernel: [  531.609544] usb 5-1.1: Manufacturer: USB Device
Nov 30 12:04:26 perelandra kernel: [  531.610182] hub 5-1.1:1.0: USB hub found
Nov 30 12:04:26 perelandra kernel: [  531.610390] hub 5-1.1:1.0: 4 ports detected
Nov 30 12:04:32 perelandra dbus[719]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Nov 30 12:04:32 perelandra dbus[719]: [system] Successfully activated service 'org.freedesktop.systemd1'
Nov 30 12:04:32 perelandra rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="732" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

it just stops there.  Nothing else in the log until I pulled the connection and rebooted.


That shows nothing, i suspect maybe because of my comment above.

> When I connect the usb hub, and then do lsusb, it adds these lines:
```
Bus 005 Device 003: ID 14cd:8601 Super Top
Bus 005 Device 002: ID 14cd:8601 Super Top 
```

That gives us some hardware (14cd:8601) to start looking to see if this is known issue.

> Now, here is another odd piece of this puzzle.  I tried booting into recovery mode with the usb hub connected as you suggested.  It went all the way to the recovery console with no problems.  From there I selected "resume normal boot", and it proceeded to boot into Xubuntu normally WITH NO PROBLEMS, the usb hub connected all the time.

tested normal reboot after that, and it still goes directly to the blank screen if the usb hub is attached.

That is odd but potentially useful.

> Thank you again for your help.

I'm going to have to think and do some research for this one. Hopefully we'll find a solution.

EDIT:

To get more information about your system, please post the output of these commands.

```
cat /etc/lsb-release && uname -a
```

Kind regards

---

### Post by Kilarin on 2015-11-30
```
$ cat /etc/lsb-release && uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
Linux perelandra 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:49 UTC 2015 i686 athlon i686 GNU/Linux
```

I'll see if I can figure out how to set the log level later this evening.

In the meantime, my son came home and suggested a few more tests.  we discovered the following:
1: The lockup only happens when the usb hub is powered.
2: The usb hub only works when plugged into a 2.0 usb port.  Plug it into a 3.0 usb port and it is not recognized.  which seems odd.  should be backwards compatible.
3: My son is also running xubuntu 14.04 on his laptop, we plugged the usb hub into his laptop and booted, no problem.

Again, thank you!

---

### Post by matt_symes on 2015-11-30
Hi

> **Kilarin said:**
> ```
$ cat /etc/lsb-release && uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
Linux perelandra 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:49 UTC 2015 i686 athlon i686 GNU/Linux
```

I'll see if I can figure out how to set the log level later this evening.

In the meantime, my son came home and suggested a few more tests.  we discovered the following:
1: The lockup only happens when the usb hub is powered.
2: The usb hub only works when plugged into a 2.0 usb port.  Plug it into a 3.0 usb port and it is not recognized.  which seems odd.  should be backwards compatible.
3: My son is also running xubuntu 14.04 on his laptop, we plugged the usb hub into his laptop and booted, no problem.

Again, thank you!

Have you checked to see if there is a BIOS update for your problem machine ? If there is then don't install it yet as i may be barking up the wrong tree, but if you could post a link to the BIOS update then it would be interesting to see if there's any mention of USB fixes.

Does your sons laptop boot correctly when the hub is powered ?

Kind regards

---

### Post by Kilarin on 2015-11-30
> Does your sons laptop boot correctly when the hub is powered ?
Yes, boots just fine and the hub works great there.

My bios is HTET43ww (1.15) 2015-04-28
Looks like there are two new versions available, 1.17 and 1.18?
[http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-edge-laptops/thinkpad-e555/downloads/DS100991](http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-edge-laptops/thinkpad-e555/downloads/DS100991)
[https://download.lenovo.com/pccbbs/mobiles/htuj46wd.txt](https://download.lenovo.com/pccbbs/mobiles/htuj46wd.txt)

can't find the readme for 1.17, but 1.18 doesn't appear to mention usb.

<edit>
Ah, found it, typo on the bios page.  typos on anything to do with bios makes me nervous. :)
[https://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/htuj45wd.txt](https://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/htuj45wd.txt)
no mention of usb.

---

### Post by Vladlenin5000 on 2015-11-30
> **Kilarin said:**
> no mention of usb.

Actually there is:
```
- Fixed an issue related to Non-AOU USB port power lackage when enable AOU.
```

It may or may not be related but I bet it is considering the issue occurs only with the hub's power supply connected. It can be some sort of a nasty over-current or something like that.
Perhaps you can test it without updates just by disabling the "Always On USB" at BIOS/UEFI. If it works -and- you need that feature enabled then I'm sure you know what to do next ;-)

---

### Post by Kilarin on 2015-11-30
> Actually there is:
UGH!  I looked right at that and saw the AOU (and didn't recognize it) and missed the usb.  Duh!  Thank you.

I tried disabling it.  No fix.  

So, even though that didn't work:
>  I'm sure you know what to do next
I'm betting my next best bet is the very scary bios upgrade.  Ick!

But it IS odd that this doesn't cause a problem in windows 7.  Only in Xubuntu.

---

### Post by coldraven on 2015-12-01
This is probably not relevant as I don't know anything about UEFI bios thingy, but out of interest I'll ask anyway :)
Did you install Xubuntu from a USB memory stick? If so did you remember to change back the boot order?

---

### Post by Kilarin on 2015-12-01
And now, for the next episode in the ongoing saga of the usb hub that stops Xubuntu booting!

I successfully installed the scary bios update, confirmed that yes, the bios is now version 1.18, and, no change.  booting with the usb hub connected and powered still locks up xubuntu at a blank screen.
I was afraid that would be the case, because if it was a bios problem, it seems like it would happen in windows 7, not just in xubuntu, but it was still the right thing to try next.

So, I did sudo nano /etc/default/grub
changed the entry to:
GRUB_CMDLINE_LINUX_DEFAULT="--verbose nosplash debug"
did sudo update-grub

and booted again to see if I got any more messages, and I didn't, it still hung up at a blank screen.  But then I tried something different, I powered down and booted a second time with the usb hub still connected and powered and learned that after the first hang up, repeat boots DO display something on the monitor
[ATTACH=CONFIG]265872[/ATTACH]
Final text is:
[    0.267039] pci 0000:00:01.0: Video device with shadowed ROM

and that is very repeatable.  Every subsequent boot with the hub still attached locks up after that shadowed ROM line.
Which doesn't tell me anything, and may still not be related to what is actually causing the problem.

syslog for boot 1 (the one that displays nothing on the screen during boot) is longer now and includes info about the usb hub:
```
Dec  1 07:38:04 perelandra kernel: [ 1185.872230] usb 5-1: new high-speed USB device number 2 using ehci-pci
Dec  1 07:38:04 perelandra kernel: [ 1186.005335] usb 5-1: New USB device found, idVendor=14cd, idProduct=8601
Dec  1 07:38:04 perelandra kernel: [ 1186.005348] usb 5-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Dec  1 07:38:04 perelandra kernel: [ 1186.005355] usb 5-1: Product: USB 2.0 Hub
Dec  1 07:38:04 perelandra kernel: [ 1186.005360] usb 5-1: Manufacturer: USB Device
Dec  1 07:38:04 perelandra kernel: [ 1186.007749] hub 5-1:1.0: USB hub found
Dec  1 07:38:04 perelandra kernel: [ 1186.008580] hub 5-1:1.0: 4 ports detected
Dec  1 07:38:04 perelandra kernel: [ 1186.024877] init: Handling usb-device-added event
Dec  1 07:38:04 perelandra kernel: [ 1186.032968] init: Handling usb-device-added event
Dec  1 07:38:04 perelandra kernel: [ 1186.280251] usb 5-1.1: new high-speed USB device number 3 using ehci-pci
Dec  1 07:38:04 perelandra kernel: [ 1186.373672] usb 5-1.1: New USB device found, idVendor=14cd, idProduct=8601
Dec  1 07:38:04 perelandra kernel: [ 1186.373685] usb 5-1.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Dec  1 07:38:04 perelandra kernel: [ 1186.373693] usb 5-1.1: Product: USB 2.0 Hub
Dec  1 07:38:04 perelandra kernel: [ 1186.373698] usb 5-1.1: Manufacturer: USB Device
Dec  1 07:38:04 perelandra kernel: [ 1186.375071] hub 5-1.1:1.0: USB hub found
Dec  1 07:38:04 perelandra kernel: [ 1186.375284] hub 5-1.1:1.0: 4 ports detected
Dec  1 07:38:04 perelandra kernel: [ 1186.385865] init: Handling usb-device-added event
Dec  1 07:38:04 perelandra kernel: [ 1186.395057] init: Handling usb-device-added event
Dec  1 07:38:10 perelandra dbus[678]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Dec  1 07:38:10 perelandra dbus[678]: [system] Successfully activated service 'org.freedesktop.systemd1'
Dec  1 07:38:10 perelandra kernel: [ 1192.098329] init: Connection from private client
Dec  1 07:38:10 perelandra kernel: [ 1192.100718] init: Handling runlevel event
Dec  1 07:38:10 perelandra kernel: [ 1192.100786] init: nmbd goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.100966] init: nmbd state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.101103] init: nmbd state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.101457] init: rc goal changed from stop to start
Dec  1 07:38:10 perelandra kernel: [ 1192.101587] init: rc state changed from waiting to starting
Dec  1 07:38:10 perelandra kernel: [ 1192.101745] init: rsyslog goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.101880] init: rsyslog state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.102008] init: rsyslog state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.102163] init: tty4 goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.102294] init: tty4 state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.102419] init: tty4 state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.102574] init: udev goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.102703] init: udev state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.102827] init: udev state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.102983] init: whoopsie goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.103113] init: whoopsie state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.103243] init: whoopsie state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.103398] init: winbind goal changed froso i assume your reboot was a warm reboot and, therfore, maybe keeping hardware initialised from the previous run.m start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.103527] init: winbind state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.103654] init: winbind state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.103809] init: apport goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.103936] init: apport state changed from running to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.106283] init: hwclock-save goal changed from stop to start
Dec  1 07:38:10 perelandra kernel: [ 1192.106607] init: hwclock-save state changed from waiting to starting
Dec  1 07:38:10 perelandra kernel: [ 1192.106961] init: irqbalance goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.107287] init: irqbalance state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.107611] init: irqbalance state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.107966] init: smbd goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.113703] init: smbd state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.113910] init: smbd state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.114121] init: tty5 goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.114300] init: tty5 state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.114490] init: tty5 state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.114946] init: rfkill-store goal changed from stop to start
Dec  1 07:38:10 perelandra kernel: [ 1192.115134] init: rfkill-store state changed from waiting to starting
Dec  1 07:38:10 perelandra kernel: [ 1192.115413] init: atd goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.115600] init: atd state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.115778] init: atd state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.115990] init: resolvconf goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.122067] init: resolvconf state changed from running to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.122960] init: alsa-store goal changed from stop to start
Dec  1 07:38:10 perelandra kernel: [ 1192.123194] init: alsa-store state changed from waiting to starting
Dec  1 07:38:10 perelandra kernel: [ 1192.123411] init: cups-browsed goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.123598] init: cups-browsed state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.123769] init: cups-browsed state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.123974] init: cron goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.124481] init: cron state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.124669] init: cron state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.124875] init: lightdm goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.125054] init: lightdm state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.125232] init: lightdm state changed froso i assume your reboot was a warm reboot and, therfore, maybe keeping hardware initialised from the previous run.m pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.125441] init: acpid goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.125591] init: acpid state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.125793] init: acpid state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.126012] init: cups goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.126169] init: cups state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.126342] init: cups state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.126533] init: upstart-socket-bridge goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.126682] init: upstart-socket-bridge state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.126859] init: upstart-socket-bridge state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.127059] init: tty2 goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.127217] init: tty2 state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.127391] init: tty2 state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.127586] init: upstart-file-bridge goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.127737] init: upstart-file-bridge state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.127912] init: upstart-file-bridge state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.128321] init: tty3 goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.128540] init: tty3 state changed from ruso i assume your reboot was a warm reboot and, therfore, maybe keeping hardware initialised from the previous run.nning to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.128715] init: tty3 state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.129141] init: plymouth-upstart-bridge goal changed from stop to start
Dec  1 07:38:10 perelandra kernel: [ 1192.129289] init: plymouth-upstart-bridge state changed from waiting to starting
Dec  1 07:38:10 perelandra kernel: [ 1192.129449] init: tty1 goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.129589] init: tty1 state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.129733] init: tty1 state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.129911] init: tty6 goal changed from start to stop
Dec  1 07:38:10 perelandra kernel: [ 1192.130058] init: tty6 state changed from running to pre-stop
Dec  1 07:38:10 perelandra kernel: [ 1192.130202] init: tty6 state changed from pre-stop to stopping
Dec  1 07:38:10 perelandra kernel: [ 1192.130357] init: Handling stopping event
Dec  1 07:38:10 perelandra kernel: [ 1192.130536] init: nmbd state changed from stopping to killed
Dec  1 07:38:10 perelandra kernel: [ 1192.130710] init: Sending TERM signal to nmbd main process (1555)
Dec  1 07:38:10 perelandra kernel: [ 1192.130952] init: Handling starting event
Dec  1 07:38:10 perelandra kernel: [ 1192.131154] init: rc state changed from starting to security
Dec  1 07:38:10 perelandra kernel: [ 1192.131379] init: rc state changed from security to pre-start
Dec  1 07:38:10 perelandra kernel: [ 1192.131513] init: rc state changed from pre-start to spawned
Dec  1 07:38:10 perelandra rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="860" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec  1 07:46:45 perelandra rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="711" x-info="http://www.rsyslog.com"] start

```

Interesting thing is that boot 2 has NOTHING in syslog.   Boot attempt 2 with the usb hub attached and powered started at 7:41, and there is nothing in the syslog for that time at all.  The next entry is at 7:46 which is after I powered down from the locked up boot 2 and rebooted without the usb hub attached.  And interestingly enough, the new boot starts at the same place that the bad boot stops.

Does any of this information tell anything useful to anyone else?  It's way outside my area of knowledge.

---

### Post by Kilarin on 2015-12-01
[quote="coldraven"]Did you install Xubuntu from a USB memory stick? If so did you remember to change back the boot order? [/quote]
installed from a dvd, and so I didn't mess with the boot order.   It doesn't have any problems booting with a usb drive attached, just with the usb hub (powered), and ONLY in Xubuntu, windows 7 boots just fine.

---

### Post by matt_symes on 2015-12-01
Hi

I'll read your post more deeply after i have eaten and kicked my shoes off.

I though i would mention that:

Your attachment is not working for me. I'm getting an invalid attachment error.

Also:

> I was afraid that would be the case, because if it was a bios problem, it seems like it would happen in windows 7, not just in xubuntu, 

I would not rely on the fact that it worked in Windows 7 and not Linux to be an indicator that it's not a BIOS or ACPI problem.

Windows was far less strict with buggy ACPI tables than Linux.

```
[ 0.267039] pci 0000:00:01.0: Video device with shadowed ROM
```

That's really early in the boot process to hang. 

It should be before the console is initialised (or at least that was my understanding) so i assume your reboot was a warm reboot and, therfore, maybe keeping hardware initialised from the previous run. This is conjecture though.

It would be really useful to see the text from a failed boot as per the attachment.

Kind regards

---

### Post by Kilarin on 2015-12-01
Lets try it this way then:
[IMG]http://i65.tinypic.com/24obo7n.jpg[/IMG]

[quote="matt_symes"]Windows was far less strict with buggy ACPI tables than Linux.[/quote]
good point.

[quote="matt_symes"]so i assume your reboot was a warm reboot and, therfore, maybe keeping hardware initialised from the previous run.[/quote]
first boot was just a "restart" I think, so warm reboot.  But for the second reboot I had to power down and power back up.
I've done cold reboots for the first boot and not noticed any difference, if the usb hub is connected and powered up, right after I select "Ubuntu" in grub, I get a blank black screen, and nothing else.

---

### Post by Kilarin on 2015-12-01
And I was able to repair the attachment above, so both should work now!

---

### Post by Kilarin on 2015-12-01
Sorry for the repeat posts, but one more point of data.
I tried hooking up a plain unpowered 4 port usb hub, and it works just fine.

---

### Post by matt_symes on 2015-12-01
Hi

I'm not sure what to make of this.

What i find really odd is that you can boot to the recovery menu and then resume normal boot and the laptop will boot normally, with the hub powered (it was powered wasn't it ?) when the laptop is first switched on. I really don't understand this.

It's difficult to decipher if the problem is an incompatibility between the hardware of the hub and the ports on the laptop, although it boots in Windows and the method above (recovery boot) works, a BIOS problem or BIOS settings issue but then it still boots using the method above (recovery boot) or something else.

That screen shot does not contain enough information to identify a problem that i can see either.

The hub was definitely powered when you booted to recovery mode and then resumed booting ? 

Kind regards

---

### Post by Kilarin on 2015-12-02
[quote="matt_symes"]The hub was definitely powered when you booted to recovery mode and then resumed booting ?[/quote]
Yes, it was.

For now, I'm throwing in the towel.  I swapped usb hubs with my son.  Now he has a fancy powered 7 port hub he doesn't really need.  And I've got his unpowered 4 port usb expansion hub.  But thats enough for me to hook up my mouse, keyboard, an externally powered usb disk drive, and a thumb drive I use for daily backups.  None of those things requires much power, and they seem to work through the unpowered hub just fine.  

So, not real happy with this, but it is working.

Thank you VERY much for your time and effort on this very confusing issue.

---

