---
title: "Ubuntu locks up when printing and randomly shuts down"
date: 2008-09-11
forum: General Help
---

### Post by Matthew T. on 2008-09-11
I have two problems with Ubuntu 8.04, which may be unrelated to each other. I'm running an emachine t5234 with an AMD Athlon 64x2 4200+ processor and 2 gigs of RAM. 

Printing ties up a lot of the CPU and sometimes freezes the system to the extent that CTRL+ALT+BACKSPACE and REISUB won't free it up. I have turned off Advanced Desktop Affects and this is still happening. 

Syslog from the last lock up looked like this:
Sep 11 09:36:48 ubuntu kernel: [ 9805.930824] ppdev0: registered pardevice
Sep 11 09:37:17 ubuntu kernel: [ 9834.447941] ppdev0: unregistered pardevice
Sep 11 09:37:27 ubuntu parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Sep 11 09:37:27 ubuntu kernel: [ 9844.571837] ppdev0: unregistered pardevice
Sep 11 09:37:27 ubuntu parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Sep 11 09:37:27 ubuntu kernel: [ 9844.599790] ppdev0: registered pardevice
Sep 11 09:37:27 ubuntu kernel: [ 9844.681880] audit(1221143847.299:10): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6726 profile="/usr/sbin/cupsd" namespace="default"
Sep 11 09:37:27 ubuntu kernel: [ 9844.926337] sysctl table check failed: /dev/parport/parport0/devices/ppdev0/timeslice  Sysctl already exists
Sep 11 09:37:27 ubuntu kernel: [ 9844.926354] Pid: 6735, comm: hpijs Tainted: P        2.6.24-19-generic #1
Sep 11 09:37:27 ubuntu kernel: [ 9844.926371]  [set_fail+0x45/0x60] set_fail+0x45/0x60
Sep 11 09:37:27 ubuntu kernel: [ 9844.926383]  [sysctl_check_table+0x296/0x5b0] sysctl_check_table+0x296/0x5b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926389]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30
Sep 11 09:37:27 ubuntu kernel: [ 9844.926401]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926407]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30
Sep 11 09:37:27 ubuntu kernel: [ 9844.926418]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926423]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30
Sep 11 09:37:27 ubuntu kernel: [ 9844.926433]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926439]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30
Sep 11 09:37:27 ubuntu kernel: [ 9844.926450]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926456]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30
Sep 11 09:37:27 ubuntu kernel: [ 9844.926466]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926472]  [sysctl_set_parent+0x19/0x30] sysctl_set_parent+0x19/0x30
Sep 11 09:37:27 ubuntu kernel: [ 9844.926482]  [ipv6:register_sysctl_table+0x50/0x150] register_sysctl_table+0x50/0xa0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926492]  [<f8a9d90e>] parport_device_proc_register+0xae/0xe0 [parport]
Sep 11 09:37:27 ubuntu kernel: [ 9844.926506]  [<f8a9be29>] parport_register_device+0x139/0x260 [parport]
Sep 11 09:37:27 ubuntu kernel: [ 9844.926524]  [<f8afa765>] pp_ioctl+0x445/0x830 [ppdev]
Sep 11 09:37:27 ubuntu kernel: [ 9844.926530]  [<f8afa240>] pp_irq+0x0/0x50 [ppdev]
Sep 11 09:37:27 ubuntu kernel: [ 9844.926545]  [do_ioctl+0x78/0x90] do_ioctl+0x78/0x90
Sep 11 09:37:27 ubuntu kernel: [ 9844.926554]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926561]  [do_sys_open+0xbe/0xe0] do_sys_open+0xbe/0xe0
Sep 11 09:37:27 ubuntu kernel: [ 9844.926569]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
Sep 11 09:37:27 ubuntu kernel: [ 9844.926576]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Sep 11 09:37:27 ubuntu kernel: [ 9844.926596]  =======================
Sep 11 09:37:27 ubuntu kernel: [ 9844.926598] ppdev0: registered pardevice
Sep 11 09:37:27 ubuntu hpijs: io/hpmud/pp.c 627: unable to read device-id ret=-110 

I don't have the syslog from a random shutdown in front of me, but I have looked at it in the past and there were no error messages of any sort from those times. Temperature is between 90 and 115 degrees. Temperature-related auto shutdown isn't even enable in the BIOS. I have replaced the power supply. 

I tried replacing powernowd with cpudyn last night for the heck of it. Don't know if this will do any good at all.

Any help is much appreciated.

---

### Post by jblackthorne on 2008-09-11
I see that the spec on your original PC came with 1mb ram.  

- Did you add the additional ram to make 2 gigs?
- If so, did you replace both chips or just add one?

As you can guess, my first thought is that there might be a memory issue.  Memory problems can definitely cause lockups and crashes like you are describing.  Can you please try rebooting and running the memtest86+ option?

Next, did you install Hardy as a clean install or upgrade for Gutsy?  If you performed an upgrade, I might suggestion trying a clean install to see if that helps.  Sadly, the Gutsy to Hardy upgrade had a lot of problems.  None of 3 Ubuntu machines upgraded successfully and all of them had to be installed with a clean copy of Hardy.

> Temperature is between 90 and 115 
That is very low.  Though, most processors have a thermal fuse that will clip and cut power in case of overheating.  Thus, it would not matter what you set in the bios, the processor might clip in case of overheat.  If that did happen, then your pc would not restart right away after a crash.  If you can turn it off and back on again immediately, then it is not a thermal fuse.

So, the question is, "Does the lockup happen due to hardware or software?"  If it is a software problem, then Ubuntu should capture the issue in one of four logs:

* /var/log/messages
* /var/log/dmesg
* ~/.xsession-errors
* /var/log/syslog

Please check all 4 of those logs now to see if there are errors.  Otherwise, wait until the next time your machine clips or halts.  Then, boot with a rescue disk, such as this one:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Then, mount the Ubuntu harddisk and check those 4 log files.  The most recent errors would of course then be at the bottom.  That makes it much easier to find.

If you check the logs and don't find anything.  Then, you are probably dealing with a hardware issues.  With a full-blown lock-up, there are number of things to try

* disable drivers bios peripherals one at time to try and isolate the problem. 
* disabling APIC (you add noapic to the kernel entry in /boot/grub/menu.lst). 

The best thing I can suggest for now is to try and find any more hints as the nature of the problem.  If you suspect any of the above, let us know.  Otherwise, please try and catch a log file or find any clue as to the nature of the problem.  I will subscribe to this thread to find out when you reply.

Good luck and keep at it!

---

### Post by Matthew T. on 2008-09-11
I have memtest86+ running now. It has completed one pass with no errors. 

I replaced both chips at the same time.

Hardy was a clean install. I keep /home in a separate partition to avoid potential upgrade problems.

I'll wait until the thing shuts down again and check the logs as you suggest.

Thank you very much.

---

### Post by Matthew T. on 2008-09-12
Memtest86+ was working on pass 16 with no errors when I restarted the computer this morning. I'll keep you posted. 

Thanks.

---

### Post by jblackthorne on 2008-09-12
16 passes of Memtest86+ means that the ram is most likely ok.  You can go ahead and stop Memtest.  

Before we jump through too many more hoops, it would be best to delete the parallel port cups driver from your system.  That could in fact be the cause of your crashing.  Please remove that driver and see how things go. 

If your system locks up after removing the parallel port driver:

Can you please attach your hardware profile by dumping the contents of :

> sudo lshw

Also, 

* Can you please post the brand and model of ram you added?
* Please post the voltage your ram is running at
* Please confirm that you are not over-clocking in any way?
* Have you upgraded to the latest bios?
* Did you add any new hardware recently?
* How old is this box? 
* When did the lock-up behavior start?  Any ideas or possible correlation to any event?

I am thoroughly researching ram because you have ruled out processor and all the software logs look clean.  Plus, aftermarket ram is not always compatible with MBs.  Furthermore, it is now very common for ram sellers to assemble chips and bin them with heatsinks at higher speeds than the chips might have been originally manufactured for.  For example, GSkill, OCZ, and Patriot repackage ram as a business.  Often times, the SDP values (values read automatically from the ram chips) do not match binned values.  For example, I have an OpenSuse 11 system that locked up and halted every day or so.  The problem ended up being Gskill ram with a SPD voltage of 2.0 volts that ran memtest+ ok.  However, with a maxiumum number of chips, there was a slight voltage loss making 2.0 volts 0.1 volts too low.  Once voltage was increased to 2.1, crashing stopped and the system is now stable.  Hence, I would suggest checking RAM manufacture specs of the ram you put in aftermarket.  

* Did crashing start after replacing the ram?
* Could you test for a day or so with the old ram to see if crashing still occurs?
* Is your aftermarket ram certified for the MB you put it in?
* Is the aftermarket RAM spec'ed to run in a voltage range?  If so, what are you running your system at in relation to that range?

Any way, here are a bunch of thoughts to either confirm or rule out ram issues.  Good luck and let me know how it goes.

---

### Post by Matthew T. on 2008-09-12
I will try to post the information you requested tonight. In the meantime, what is the name of the parallel port driver, please?

---

### Post by jblackthorne on 2008-09-12
> **Matthew T. said:**
> I will try to post the information you requested tonight. In the meantime, what is the name of the parallel port driver, please?
My suggestion is to remove the printers configured to use the parallel port since we confirmed that this is not supported. :)

---

### Post by Matthew T. on 2008-09-12
I removed the printer and reinstalled it today using hplip-gui. It is now connected using a USB cord.

---

### Post by Matthew T. on 2008-09-12
I installed two Corsair ValueSelect 1 GB DDR2 SDRAM DDR2 667 model VS1GB667D2 RAM cards.
If the RAM voltage = VDIMM, it's running at 1.8 volts.
I'm not overclocking.
Not intentionally. Never tried to upgrade my BIOS.
No new hardware added recently. I added the additional RAM several months ago. The mystery shut downs started happening a few weeks ago.
I bought the box new this January.
It hasn't locked up since I uninstalled the printer in hplip and re-enabled it using a USB connection. Of course, that was just done this afternoon.
In the past, it has shut down when surfing or browsing e-mail in Evolution.
FWIW, when the computer shuts down on its own, it suddenly turns itself off. No warning, no shut down process. One second it's working, the next it's not.

---

### Post by Sef on 2008-09-12
Have you an extra power supply?  Yours could be bad.  

What make and model is your printer?

---

### Post by Matthew T. on 2008-09-12
I replaced the power supply last Saturday. It's an HP Deskjet 940c.

---

### Post by jblackthorne on 2008-09-15
Is your printer working ok now that you are on USB? If so, has the system crashed since switching over the printer?  Both the crashing and print issues could have been the bad parallel port driver.  Thus, I would recommend waiting to see what happens with the new USB connection.

Keep us posted.

P.S. I checked your ram chips, the VS1GB667D2, out.  While some chips can operate in a voltage range, yours do not.  They should run at 1.8 volts only.  This rules under-volting of the ram chips out.

---

### Post by Matthew T. on 2008-09-17
So far, so good. The computer and printer have been rocking along nicely ever since you suggested I use a USB cord for the printer connection, remove/re-enable the printer, etc. I'll let you know if something suddenly goes south.

Thank you very much for your help.

---

### Post by jblackthorne on 2008-09-17
Glad to hear it was something simple and that things are going your way at last. Good luck and enjoy Linux :)

---

### Post by Matthew T. on 2008-09-26
I was just thinking that my mystery shutdowns might have stopped when the computer decided to surprise last night. No warning, no error messages. One second it's working and the next it's not. The shutdown occurred at 10:13 p.m. Here's the syslog entries around that time. They look pretty innocuous to a novice such as myself. The fatal x error occurred when firefox locked up while surfing. My wife CTRL+ALT+BACKSPACEd and kept on rollin until the machine took matters into its own hands.

Sep 25 20:59:53 ubuntu kernel: [50283.365690] compiz.real[6025]: segfault at 00018c17 eip 08055a6d esp bfb8feb0 error 4
Sep 25 20:59:54 ubuntu gdm[5350]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Sep 25 21:00:14 ubuntu pulseaudio[18557]: pid.c: Stale PID file, overwriting.
Sep 25 21:00:18 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 25 21:00:18 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 25 21:00:18 ubuntu NetworkManager: <info>  Updating VPN Connections... 
Sep 25 21:17:01 ubuntu /USR/SBIN/CRON[18926]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 25 21:40:09 ubuntu kernel: [52696.942283] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:1e:90:65:a3:11:00:1a:70:69:7a:58:08:00 SRC=72.21.81.133 DST=192.168.1.102 LEN=1500 TOS=0x00 PREC=0x00 TTL=54 ID=31722 DF PROTO=TCP SPT=80 DPT=34218 WINDOW=135 RES=0x00 ACK PSH URGP=0 
Sep 25 21:42:09 ubuntu kernel: [52816.862204] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:1e:90:65:a3:11:00:1a:70:69:7a:58:08:00 SRC=72.21.81.133 DST=192.168.1.102 LEN=1500 TOS=0x00 PREC=0x00 TTL=54 ID=31723 DF PROTO=TCP SPT=80 DPT=34218 WINDOW=135 RES=0x00 ACK PSH URGP=0 
Sep 25 22:01:42 ubuntu -- MARK --
Sep 26 06:14:27 ubuntu syslogd 1.5.0#1ubuntu1: restart.

I have already replaced the power supply. I'm thinking it might be some kind of hardware problem?

---

