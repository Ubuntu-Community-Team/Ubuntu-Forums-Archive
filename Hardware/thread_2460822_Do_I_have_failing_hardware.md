---
title: "Do I have failing hardware?"
date: 2021-04-19
forum: Hardware
---

### Post by ciphin78 on 2021-04-19
Hi All -   I have been running Ubuntu for a while on old hardware and never had any issues.  I could run that thing for months at a time without a reboot and it was solid.  I recently bought a new PC "kit" with all new hardware and put it all together.  I'm pretty tech literate, I'm a software engineer but I don't do hardware stuff all that often.  Anyway, ever since getting this new machine together I've had nothing but issues.  It just constantly locks up/screen freezes and becomes completely unresponsive.  If I'm watching a youtube video (just as an example) it will freeze, but the sound will continue.  The only way to recover is to do a hard restart.  Other times (when not doing anything) it will still just freeze up.  Sometimes it freezes after a few minutes of booting up and sometimes it will go 6-8 hours without a freeze.  Lately, it won't go more than a few mins to a few hours before locking up.  I've been using pSensor to check the temps and they are all within norms.  

Running
-Ubuntu 20.10
-ASUS TUF B450-PLUS GAMING AM4 AMD B450 SATA 6Gb/s ATX AMD Motherboard
-WD Blue 3D NAND 1TB Internal SSD
-AMD RYZEN 5 2600X 6-Core 3.6 GHz (4.2 GHz Max Boost) Socket AM4 95W YD260XBCAFBOX Desktop Processor
-ASRock Phantom Gaming D Radeon RX 570 DirectX 12 RX570 4G 4GB 256-Bit GDDR5 PCI Express 3.0 x16 HDCP Ready Video Card
-G.SKILL Ripjaws V Series 16GB (2 x 8GB) 288-Pin DDR4 SDRAM DDR4 3200 (PC4 25600) Desktop Memory Model F4-3200C16D-16GVKB

In the logs I'm seeing errors like:


#PF: error_code(0x0010) - not-present page
#PF: supervisor instruction fetch in kernel mode
BUG: Kernel Null pointer dereference, address: 0000000000000000000
get_swap_device: Bad swap file entry
Failed to start GNOME media keys handling
gkr-pam: unable to locate daemon control file.
THD engine start failed

I'm really struggling to diagnose what the issue is.  I've done a mem-test and it was clean after several hours, but as far as the other hardware...I just don't know.  As far as the software, I've tried every flavor of Ubuntu starting with 16 thru 20.10 and I get the same issues.  I'm happy to post any logs or try any diagnostics, I just need help on where to start.  I'm close to chucking it and starting over.

Thanks.

---

### Post by oldfred on 2021-04-19
Have you updated UEFI and SSD firmware?
Many have needed those updates, even new systems.
Many AMD systems also need changes to UEFI setting for IOMMU.

Asus ROG strix b450-F
[https://askubuntu.com/questions/1267714/error-while-trying-to-install-any-linux-version-ubuntu-ubuntu-budgie-solus-gn?noredirect=1#comment2146118_1267714](https://askubuntu.com/questions/1267714/error-while-trying-to-install-any-linux-version-ubuntu-ubuntu-budgie-solus-gn?noredirect=1#comment2146118_1267714)
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

### Post by ciphin78 on 2021-04-20
Thanks - 

I've updated the UEFI version and changed the IOMMU settings.  I'm not really seeing how to update the SSD firmware (without switching over to Windows), but I'll keep looking for a linux native option.

System is running, but I don't think it's 100% yet.  Just got a little freeze, but it came back after a second and the latest error in the log is:

BUG: Bad page state in the process apport-gtk pfn:53209f

Oh, and now as I'm typing this on another machine, it just froze up completely again.  Have to do a hard-reset.  I'll boot into windowz and try the SSD firmware update - SSD Firmware is now updated

---

### Post by TheFu on 2021-04-20
I have a Ryzen 2600, Asus B450 ROG STRIX B450-F GAMING MB, and 32GB total G.Skill F4-3200C16-8GVKB RAM (4 sticks of 8GB ea).  Ensure the MB firmware is completely up to date.  I use the built-in updater for that.  Then you'll need to work on the RAM timing.  The XMP profiles doesn't work (or whatever AMD calls them), IME.  I've never gotten 3200 Mhz to work with my RAM, even with 16G matched RAM.

There are two ways to address this.  
[LIST]
[*]Slow the RAM down - nothing over 2800 Mhz ever worked for me, but it is extremely stable at that speed.
[*]Relax the timings to 18-18-18-39 and increase the voltage to 1.410.
[/LIST]
Someone else got 16-18-18-38 and 1.35V working. I've not tested it.

```
$ sudo inxi -mxx
Memory:    Used/Total: 15965.4/32108.7MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 8 GB speed: 2800 MT/s type: DDR4
           manufacturer: G Skill Intl part: F4-3200C16-8GVKB serial: N/A
           Device-2: DIMM_A2 size: 8 GB speed: 2800 MT/s type: DDR4
           manufacturer: G Skill Intl part: F4-3200C16-8GVKB serial: N/A
           Device-3: DIMM_B1 size: 8 GB speed: 2800 MT/s type: DDR4
           manufacturer: G Skill Intl part: F4-3200C16-8GVKB serial: N/A
           Device-4: DIMM_B2 size: 8 GB speed: 2800 MT/s type: DDR4
           manufacturer: G Skill Intl part: F4-3200C16-8GVKB serial: N/A
```
My 4 sticks are unmatched. They are 2x8GB pairs. The system hasn't shown any issues once I got the RAM speed set. Any speed higher, say 2866Mhz would crash after a few days.  I didn't take the time to tweak the timings after the 2nd pair of sticks were added. Before that, with just 16G total RAM, it would run at higher speeds - I don't recall what anymore. Sorry.

---

### Post by ciphin78 on 2021-04-20
Thanks for the suggestion.  I've clocked the RAM at 2400 for now.  My output looks identical to yours (save for the 2400).  FYI, it was only running at 1800 before.  My logs generally look the same so far.  I'll try running like this for a bit and see what happens, then I'll report back here.

---

### Post by Yellow Pasque on 2021-04-20
You should consider running Memtest if you continue experiencing errors.

I guess I should consider myself lucky that my RAM kit worked at 3200 after enabling XMP

---

### Post by ciphin78 on 2021-04-20
I've done a memtest and it came back clean after a few hours, however, I could run it again just to be sure.

---

### Post by TheFu on 2021-04-20
> **Yellow Pasque said:**
> You should consider running Memtest if you continue experiencing errors.

I guess I should consider myself lucky that my RAM kit worked at 3200 after enabling XMP

Matched sets matter greatly with DDR4.  I moved from 16G to 32G after 2 yrs.  Suppose I could return under the "lifetime warranty" and ask for a 4-stick matched timing set?

> **ciphin78 said:**
> Thanks for the suggestion.  I've clocked the RAM at 2400 for now.  My output looks identical to yours (save for the 2400).  FYI, it was only running at 1800 before.  My logs generally look the same so far.  I'll try running like this for a bit and see what happens, then I'll report back here.

1800 Mhz is the "safe-mode" speed for DDR4 RAM. That's what the BIOS sets automatically when the system fails BIOS checks - I don't know if those failures are RAM-only or for all system components.

I'm happy to run other commands, but cannot reboot (or directly look at the BIOS) until Saturday - it is a production system with many VMs running for clients.

---

### Post by ciphin78 on 2021-04-21
The system ran pretty well (no freezing) yesterday afternoon.  I turned it off for the night, but it's back up now and I'll let it run today and see how it goes.  If I encounter any freezing or other issues, i'll report back here.  RAM is still set to 2400:

Memory:
  RAM: total: 31.33 GiB used: 1.62 GiB (5.2%) 
  Array-1: capacity: 128 GiB slots: 4 EC: None max module size: 32 GiB 
  note: est. 
  Device-1: DIMM_A1 size: 8 GiB speed: 2400 MT/s type: DDR4 
  manufacturer: G-Skill part-no: F4-3200C16-8GVKB 
  Device-2: DIMM_A2 size: 8 GiB speed: 2400 MT/s type: DDR4 
  manufacturer: G-Skill part-no: F4-3200C16-8GVKB 
  Device-3: DIMM_B1 size: 8 GiB speed: 2400 MT/s type: DDR4 
  manufacturer: G-Skill part-no: F4-3200C16-8GVKB 
  Device-4: DIMM_B2 size: 8 GiB speed: 2400 MT/s type: DDR4 
  manufacturer: G-Skill part-no: F4-3200C16-8GVKB

---

### Post by TheFu on 2021-04-21
Give it a week, but I bet you can get 2800 Mhz - which would feel faster. I think you'd notice that difference.

---

### Post by ciphin78 on 2021-04-23
Day 3 and running pretty well.  I've not yet let it sleep at night, I power down each evening.  However, this morning right after I booted and logged in, it self-reboot.  No freezing, just a moment after logging in, it cycled itself.  The only thing in the logs where:

Apr 23 08:18:32 adgr-fast kernel: [   80.735585] snd_hda_intel 0000:08:00.1: AER: can't recover (no error_detected callback)
Apr 23 08:18:32 adgr-fast kernel: [   80.735601] pcieport 0000:00:03.1: AER: device recovery failed
Apr 23 08:18:32 adgr-fast kernel: [   80.757621] pcieport 0000:00:03.1: AER: Multiple Uncorrected (Non-Fatal) error received: 0000:00:00.0
Apr 23 08:18:32 adgr-fast kernel: [   80.757629] pcieport 0000:00:03.1: AER: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Receiver ID)
Apr 23 08:18:32 adgr-fast kernel: [   80.757632] pcieport 0000:00:03.1: AER:   device [1022:1453] error status/mask=00200000/04400000
Apr 23 08:18:32 adgr-fast kernel: [   80.757634] pcieport 0000:00:03.1: AER:    [21] ACSViol                (First)

Rinse and repeat the above many times in the log.  Cause for concern or any corrective action to take?

Thanks All!

---

### Post by TheFu on 2021-04-23
I don't let my Ryzen sleep. Looked through the logs and all I saw was that a $9 HDD used for sneaker-net is about to fail. Thanks?  The drive has lasted 3 yrs. More than I'd expect for a use WD-Blue. The syslog error, if anyone cares:
```
Apr 23 09:45:33 hadar smartd[2886]: Device: /dev/sda [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 96 to 100
```
Heck, I barely care myself. ;)

I do have an intel core i5 laptop that sleeps nightly. It isn't awake yet for today, so I can't easily look through the logs. All I know is that when it does wake up, everything works.  I've been having it sleep a few minutes after the daily backups complete for about 2 yrs. It is solid with a very long battery life for my workloads.  I don't bring a power cable along when going out all day.

---

