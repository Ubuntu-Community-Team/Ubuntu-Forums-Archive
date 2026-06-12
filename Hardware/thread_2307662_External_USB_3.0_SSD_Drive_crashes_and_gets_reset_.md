---
title: "External USB 3.0 SSD Drive crashes and gets reset all the time"
date: 2015-12-27
forum: Hardware
---

### Post by a-max-p on 2015-12-27
Hello everyone,
I've got a rather ugly hardware problem in Ubuntu 15.10 with a Samsung 840 Pro ssd drive that I'm using inside an Icy Box IB-253U3 case. I'm pretty sure that this is a kernel problem, because it also exists in Manjaro Linux but I am not really confident about reporting. 
The problem is: When I am trying to copy a large file (about 1GB) to the external drive it takes a very long time and the transfer rate approaches zero after a couple of minutes (!). Then the device gets reset again and again. dmesg gives the following: (using usb 3.0 port, because there are no other ports on my laptop)

```
[39832.424281] usb 2-2: new SuperSpeed USB device number 2 using xhci_hcd
[39832.441138] usb 2-2: New USB device found, idVendor=357d, idProduct=7788
[39832.441141] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[39832.441143] usb 2-2: Product: USB to ATA/ATAPI Bridge
[39832.441144] usb 2-2: Manufacturer: JMicron
[39832.441145] usb 2-2: SerialNumber: 3118E3168034537
[39832.975465] usbcore: registered new interface driver usb-storage
[39832.978722] scsi host4: uas
[39832.979166] usbcore: registered new interface driver uas
[39832.979188] scsi 4:0:0:0: Direct-Access     Samsung  SSD 840 PRO Seri 0114 PQ: 0 ANSI: 6
[39832.979925] sd 4:0:0:0: Attached scsi generic sg1 type 0
[39832.980101] sd 4:0:0:0: [sdb] Spinning up disk...
[39833.981294] .........ready
[39842.018334] sd 4:0:0:0: [sdb] 1000215216 512-byte logical blocks: (512 GB/476 GiB)
[39842.018337] sd 4:0:0:0: [sdb] 4096-byte physical blocks
[39842.018837] sd 4:0:0:0: [sdb] Write Protect is off
[39842.018839] sd 4:0:0:0: [sdb] Mode Sense: 53 00 10 08
[39842.019113] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA
[39842.021133]  sdb: sdb1
[39842.022374] sd 4:0:0:0: [sdb] Attached SCSI disk
[39881.118780] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[39881.118959] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[39917.357598] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[39948.302799] sd 4:0:0:0: [sdb] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[39948.302803] sd 4:0:0:0: [sdb] tag#11 CDB: Write(10) 2a 00 01 38 54 72 00 02 00 00
[39948.302832] sd 4:0:0:0: [sdb] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[39948.302834] sd 4:0:0:0: [sdb] tag#10 CDB: Write(10) 2a 00 01 38 53 02 00 01 70 00
[39948.302898] sd 4:0:0:0: [sdb] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[39948.302901] sd 4:0:0:0: [sdb] tag#9 CDB: Write(10) 2a 00 01 38 51 92 00 01 38 00
[39948.302921] sd 4:0:0:0: [sdb] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[39948.302923] sd 4:0:0:0: [sdb] tag#8 CDB: Write(10) 2a 00 01 38 3f e2 00 00 30 00
[39948.302982] sd 4:0:0:0: [sdb] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[39948.302983] sd 4:0:0:0: [sdb] tag#7 CDB: Write(10) 2a 00 01 38 50 ca 00 00 c8 00
[39948.302998] sd 4:0:0:0: [sdb] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[39948.303000] sd 4:0:0:0: [sdb] tag#6 CDB: Write(10) 2a 00 01 38 9b 5a 00 00 10 00
[39948.303069] sd 4:0:0:0: [sdb] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[39948.303070] sd 4:0:0:0: [sdb] tag#5 CDB: Write(10) 2a 00 01 38 96 12 00 01 d0 00
[39948.303084] sd 4:0:0:0: [sdb] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[39948.303086] sd 4:0:0:0: [sdb] tag#4 CDB: Write(10) 2a 00 01 38 92 c2 00 01 00 00
[39948.303154] sd 4:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[39948.303155] sd 4:0:0:0: [sdb] tag#3 CDB: Write(10) 2a 00 01 38 91 02 00 00 a0 00
[39948.303168] sd 4:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[39948.303169] sd 4:0:0:0: [sdb] tag#2 CDB: Write(10) 2a 00 01 38 90 92 00 00 08 00
[39948.303208] sd 4:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[39948.303210] sd 4:0:0:0: [sdb] tag#1 CDB: Write(10) 2a 00 01 38 4e fa 00 01 20 00
[39948.303248] sd 4:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[39948.303250] sd 4:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 01 38 8d a2 00 02 98 00
[39948.303310] scsi host4: uas_eh_bus_reset_handler start
[39948.415081] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[39948.432555] scsi host4: uas_eh_bus_reset_handler success
[39949.156257] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[39964.588849] wlp2s0: AP 30:b5:c2:22:e8:9a changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[39965.623502] wlp2s0: AP 30:b5:c2:22:e8:9a changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[39979.357658] sd 4:0:0:0: [sdb] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[39979.357662] sd 4:0:0:0: [sdb] tag#9 CDB: Write(10) 2a 00 01 3d 99 1a 00 04 00 00
[39979.357689] sd 4:0:0:0: [sdb] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[39979.357692] sd 4:0:0:0: [sdb] tag#8 CDB: Write(10) 2a 00 01 3d 95 1a 00 04 00 00
[39979.357724] sd 4:0:0:0: [sdb] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[39979.357726] sd 4:0:0:0: [sdb] tag#7 CDB: Write(10) 2a 00 01 3d 91 1a 00 04 00 00
[39979.357764] sd 4:0:0:0: [sdb] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[39979.357765] sd 4:0:0:0: [sdb] tag#6 CDB: Write(10) 2a 00 01 3d 8d 1a 00 04 00 00
[39979.357803] sd 4:0:0:0: [sdb] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[39979.357804] sd 4:0:0:0: [sdb] tag#5 CDB: Write(10) 2a 00 01 3d 89 1a 00 04 00 00
[39979.357842] sd 4:0:0:0: [sdb] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[39979.357844] sd 4:0:0:0: [sdb] tag#4 CDB: Write(10) 2a 00 01 3d 85 1a 00 04 00 00
[39979.357882] sd 4:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[39979.357883] sd 4:0:0:0: [sdb] tag#3 CDB: Write(10) 2a 00 01 3d 81 1a 00 04 00 00
[39979.357922] sd 4:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[39979.357924] sd 4:0:0:0: [sdb] tag#2 CDB: Write(10) 2a 00 01 3d 7d 1a 00 04 00 00
[39979.357961] sd 4:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[39979.357963] sd 4:0:0:0: [sdb] tag#1 CDB: Write(10) 2a 00 01 3d 79 1a 00 04 00 00
[39979.358001] sd 4:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[39979.358002] sd 4:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 01 3d 75 1a 00 04 00 00
[39979.358041] sd 4:0:0:0: [sdb] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[39979.358042] sd 4:0:0:0: [sdb] tag#11 CDB: Write(10) 2a 00 01 3d 71 1a 00 04 00 00
[39979.358080] sd 4:0:0:0: [sdb] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[39979.358082] sd 4:0:0:0: [sdb] tag#10 CDB: Write(10) 2a 00 01 3d 6d 1a 00 04 00 00
[39979.358127] scsi host4: uas_eh_bus_reset_handler start
[39979.469900] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[39979.487297] scsi host4: uas_eh_bus_reset_handler success
[39980.054375] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[40010.416601] sd 4:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[40010.416605] sd 4:0:0:0: [sdb] tag#2 CDB: Write(10) 2a 00 01 40 a5 1a 00 04 00 00
[40010.416635] sd 4:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[40010.416638] sd 4:0:0:0: [sdb] tag#1 CDB: Write(10) 2a 00 01 40 a1 1a 00 04 00 00
[40010.416668] sd 4:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[40010.416670] sd 4:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 01 40 9d 1a 00 04 00 00
[40010.416709] sd 4:0:0:0: [sdb] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[40010.416710] sd 4:0:0:0: [sdb] tag#11 CDB: Write(10) 2a 00 01 40 99 1a 00 04 00 00
[40010.416775] sd 4:0:0:0: [sdb] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[40010.416778] sd 4:0:0:0: [sdb] tag#10 CDB: Write(10) 2a 00 01 40 95 1a 00 04 00 00
[40010.416799] sd 4:0:0:0: [sdb] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[40010.416801] sd 4:0:0:0: [sdb] tag#9 CDB: Write(10) 2a 00 01 40 91 1a 00 04 00 00
[40010.416862] sd 4:0:0:0: [sdb] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[40010.416863] sd 4:0:0:0: [sdb] tag#8 CDB: Write(10) 2a 00 01 40 8d 1a 00 04 00 00
[40010.416878] sd 4:0:0:0: [sdb] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[40010.416880] sd 4:0:0:0: [sdb] tag#7 CDB: Write(10) 2a 00 01 40 89 1a 00 04 00 00
[40010.416918] sd 4:0:0:0: [sdb] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[40010.416920] sd 4:0:0:0: [sdb] tag#6 CDB: Write(10) 2a 00 01 40 85 1a 00 04 00 00
[40010.416958] sd 4:0:0:0: [sdb] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[40010.416959] sd 4:0:0:0: [sdb] tag#5 CDB: Write(10) 2a 00 01 40 81 1a 00 04 00 00
[40010.416997] sd 4:0:0:0: [sdb] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[40010.416998] sd 4:0:0:0: [sdb] tag#4 CDB: Write(10) 2a 00 01 40 7d 1a 00 04 00 00
[40010.417037] sd 4:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[40010.417038] sd 4:0:0:0: [sdb] tag#3 CDB: Write(10) 2a 00 01 40 79 1a 00 04 00 00
[40010.417098] scsi host4: uas_eh_bus_reset_handler start
[40010.528848] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[40010.546465] scsi host4: uas_eh_bus_reset_handler success
[40011.393910] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[40042.436060] sd 4:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[40042.436063] sd 4:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 01 47 69 1a 00 04 00 00
[40042.436087] sd 4:0:0:0: [sdb] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[40042.436089] sd 4:0:0:0: [sdb] tag#11 CDB: Write(10) 2a 00 01 47 65 1a 00 04 00 00
[40042.436122] sd 4:0:0:0: [sdb] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[40042.436124] sd 4:0:0:0: [sdb] tag#10 CDB: Write(10) 2a 00 01 47 61 1a 00 04 00 00
[40042.436162] sd 4:0:0:0: [sdb] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[40042.436164] sd 4:0:0:0: [sdb] tag#9 CDB: Write(10) 2a 00 01 47 5d 1a 00 04 00 00
[40042.436209] sd 4:0:0:0: [sdb] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[40042.436213] sd 4:0:0:0: [sdb] tag#8 CDB: Write(10) 2a 00 01 47 59 1a 00 04 00 00
[40042.436252] sd 4:0:0:0: [sdb] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[40042.436255] sd 4:0:0:0: [sdb] tag#7 CDB: Write(10) 2a 00 01 47 55 1a 00 04 00 00
[40042.436289] sd 4:0:0:0: [sdb] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[40042.436291] sd 4:0:0:0: [sdb] tag#6 CDB: Write(10) 2a 00 01 47 51 1a 00 04 00 00
[40042.436323] sd 4:0:0:0: [sdb] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[40042.436324] sd 4:0:0:0: [sdb] tag#5 CDB: Write(10) 2a 00 01 47 4d 1a 00 04 00 00
[40042.436362] sd 4:0:0:0: [sdb] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[40042.436363] sd 4:0:0:0: [sdb] tag#4 CDB: Write(10) 2a 00 01 47 49 1a 00 04 00 00
[40042.436402] sd 4:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[40042.436404] sd 4:0:0:0: [sdb] tag#3 CDB: Write(10) 2a 00 01 47 45 1a 00 04 00 00
[40042.436442] sd 4:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[40042.436443] sd 4:0:0:0: [sdb] tag#2 CDB: Write(10) 2a 00 01 47 41 1a 00 04 00 00
[40042.436482] sd 4:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[40042.436483] sd 4:0:0:0: [sdb] tag#1 CDB: Write(10) 2a 00 01 47 3d 1a 00 04 00 00
[40042.436528] scsi host4: uas_eh_bus_reset_handler start
[40042.548289] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[40042.565869] scsi host4: uas_eh_bus_reset_handler success
[40042.934955] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[40073.430979] sd 4:0:0:0: [sdb] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[40073.430984] sd 4:0:0:0: [sdb] tag#11 CDB: Write(10) 2a 00 01 47 c9 1a 00 04 00 00
[40073.431017] sd 4:0:0:0: [sdb] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[40073.431020] sd 4:0:0:0: [sdb] tag#10 CDB: Write(10) 2a 00 01 47 c5 1a 00 04 00 00
[40073.431048] sd 4:0:0:0: [sdb] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[40073.431049] sd 4:0:0:0: [sdb] tag#9 CDB: Write(10) 2a 00 01 47 c1 1a 00 04 00 00
[40073.431087] sd 4:0:0:0: [sdb] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[40073.431088] sd 4:0:0:0: [sdb] tag#8 CDB: Write(10) 2a 00 01 47 bd 1a 00 04 00 00
[40073.431136] sd 4:0:0:0: [sdb] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[40073.431139] sd 4:0:0:0: [sdb] tag#7 CDB: Write(10) 2a 00 01 47 b9 1a 00 04 00 00
[40073.431166] sd 4:0:0:0: [sdb] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[40073.431167] sd 4:0:0:0: [sdb] tag#6 CDB: Write(10) 2a 00 01 47 b5 1a 00 04 00 00
[40073.431205] sd 4:0:0:0: [sdb] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[40073.431207] sd 4:0:0:0: [sdb] tag#5 CDB: Write(10) 2a 00 01 47 b1 1a 00 04 00 00
[40073.431245] sd 4:0:0:0: [sdb] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[40073.431246] sd 4:0:0:0: [sdb] tag#4 CDB: Write(10) 2a 00 01 47 ad 1a 00 04 00 00
[40073.431284] sd 4:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[40073.431286] sd 4:0:0:0: [sdb] tag#3 CDB: Write(10) 2a 00 01 47 a9 1a 00 04 00 00
[40073.431323] sd 4:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[40073.431325] sd 4:0:0:0: [sdb] tag#2 CDB: Write(10) 2a 00 01 47 a5 1a 00 04 00 00
[40073.431363] sd 4:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[40073.431364] sd 4:0:0:0: [sdb] tag#1 CDB: Write(10) 2a 00 01 47 a1 1a 00 04 00 00
[40073.431403] sd 4:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[40073.431404] sd 4:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 01 47 9d 1a 00 04 00 00
[40073.431465] scsi host4: uas_eh_bus_reset_handler start
[40073.543332] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[40073.561082] scsi host4: uas_eh_bus_reset_handler success
```


This goes on forever. I've tried the device on a mac (usb 3.0) and on a server running debian stable (usb 2.0 only). No problems at all. On another system running Ubuntu 15.10 the problem persists on both usb 3.0 and usb 2.0 ports.

Any ideas?

Thanks for your help!

M

---

### Post by matt_symes on 2015-12-27
Hi

This *may* be due to USB autosuspend power management. There are bug reports that suggest this may help fix it in some cases. I would disable it and see if that helps fix the problem.

You'll need to edit your grub configuration file to do this.

Open a terminal and type

```
sudo nano /etc/default/grub
```

Enter your password. It will not be echoed to the screen. This is normal.

Use the arrow keys to move to the to the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change to it

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
```

Press <ctrl> + o to save and <ctrl> + x to exit.

Then type

```
sudo update-grub
```

Reboot your computer, open a terminal and type

```
cat /proc/cmdline
```

Look for *usbcore.autosuspend=-1* in the ouput. If it's not there, you've done something wrong with the above steps.

If it is there then use the USB drive as before and try to create the failure condition.

Does it still fail ?

Please post back either way.

Kind regards

---

### Post by a-max-p on 2016-01-11
Hi matt_symes,

thanks a lot for you very quick reply! I'm sorry to not have responded to it as quickly - I'm currently a little snowed under with exam preps.. -.-

However, I've tried the kernel parameters that you suggested. Unfortunately it didn't change anything:

```
[   51.566660] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT [   51.566664] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 0c c0 c5 00 00 04 00 00
[   51.566702] sd 4:0:0:0: [sda] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[   51.566704] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 0c c0 c1 00 00 04 00 00
[   51.566748] sd 4:0:0:0: [sda] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[   51.566749] sd 4:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 0c c0 bd 00 00 04 00 00
[   51.566765] sd 4:0:0:0: [sda] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[   51.566767] sd 4:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 0c c0 b9 00 00 04 00 00
[   56.506151] sd 4:0:0:0: [sda] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[   56.506154] sd 4:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 00 00 08 00 00 00 08 00
[   56.506175] scsi host4: uas_eh_bus_reset_handler start
[   56.506569] sd 4:0:0:0: [sda] tag#5 uas_zap_pending 0 uas-tag 6 inflight: CMD 
[   56.506570] sd 4:0:0:0: [sda] tag#5 CDB: Write(10) 2a 00 00 00 08 30 00 00 08 00
[   56.506572] sd 4:0:0:0: [sda] tag#6 uas_zap_pending 0 uas-tag 7 inflight: CMD 
[   56.506573] sd 4:0:0:0: [sda] tag#6 CDB: Write(10) 2a 00 2e c0 09 00 00 00 08 00
[   56.622102] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[   56.639729] scsi host4: uas_eh_bus_reset_handler success
[   58.496196] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[   89.506422] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[   89.506434] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 0d 00 e5 00 00 04 00 00
[   89.506582] sd 4:0:0:0: [sda] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[   89.506592] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 0d 00 e1 00 00 04 00 00
[   89.506656] sd 4:0:0:0: [sda] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[   89.506663] sd 4:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 0d 00 dd 00 00 04 00 00
[   89.506706] sd 4:0:0:0: [sda] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[   89.506710] sd 4:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 0d 00 d9 00 00 04 00 00
[   89.506819] scsi host4: uas_eh_bus_reset_handler start
[   89.618745] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[   89.636686] scsi host4: uas_eh_bus_reset_handler success
[   91.490396] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[  122.546604] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[  122.546608] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 0d 41 05 00 00 04 00 00
[  122.546634] sd 4:0:0:0: [sda] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[  122.546636] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 0d 41 01 00 00 04 00 00
[  122.546710] scsi host4: uas_eh_bus_reset_handler start
[  122.659045] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[  122.676678] scsi host4: uas_eh_bus_reset_handler success
[  127.217657] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[  157.568566] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[  157.568578] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 0e 40 25 00 00 04 00 00
[  157.677343] usb 1-1: USB disconnect, device number 2
[  168.541347] sd 4:0:0:0: [sda] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[  168.541351] sd 4:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 00 08 00 00 00 10 00
[  168.541383] scsi host4: uas_eh_bus_reset_handler start
[  168.542073] sd 4:0:0:0: [sda] tag#1 uas_zap_pending 0 uas-tag 2 inflight: CMD 
[  168.542075] sd 4:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 00 00 08 c0 00 00 08 00
[  168.542077] sd 4:0:0:0: [sda] tag#2 uas_zap_pending 0 uas-tag 3 inflight: CMD 
[  168.542079] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 00 00 28 38 00 00 50 00
[  168.542080] sd 4:0:0:0: [sda] tag#4 uas_zap_pending 0 uas-tag 5 inflight: CMD 
[  168.542081] sd 4:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 2e c0 08 00 00 00 10 00
[  168.542083] sd 4:0:0:0: [sda] tag#5 uas_zap_pending 0 uas-tag 6 inflight: CMD 
[  168.542084] sd 4:0:0:0: [sda] tag#5 CDB: Write(10) 2a 00 2e c0 08 80 00 00 08 00
[  168.542085] sd 4:0:0:0: [sda] tag#6 uas_zap_pending 0 uas-tag 7 inflight: CMD 
[  168.542086] sd 4:0:0:0: [sda] tag#6 CDB: Write(10) 2a 00 2e c0 09 00 00 00 08 00
[  168.542087] sd 4:0:0:0: [sda] tag#7 uas_zap_pending 0 uas-tag 8 inflight: CMD 
[  168.542088] sd 4:0:0:0: [sda] tag#7 CDB: Write(10) 2a 00 2e c1 09 00 00 00 08 00
[  168.653564] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[  168.670954] scsi host4: uas_eh_bus_reset_handler success
[  201.448966] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[  231.587940] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[  231.587946] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 14 40 45 00 00 04 00 00
[  231.587987] scsi host4: uas_eh_bus_reset_handler start
[  231.700213] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[  231.718270] scsi host4: uas_eh_bus_reset_handler success
[  233.574190] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[  264.564738] sd 4:0:0:0: [sda] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[  264.564742] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 00 06 c0 00 00 04 00 00
[  264.564770] sd 4:0:0:0: [sda] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[  264.564772] sd 4:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 00 06 bc 00 00 04 00 00
[  264.564818] sd 4:0:0:0: [sda] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[  264.564819] sd 4:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 06 b8 00 00 04 00 00
[  264.564875] sd 4:0:0:0: [sda] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[  264.564877] sd 4:0:0:0: [sda] tag#11 CDB: Write(10) 2a 00 00 06 b4 00 00 04 00 00
[  264.564894] sd 4:0:0:0: [sda] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[  264.564895] sd 4:0:0:0: [sda] tag#10 CDB: Write(10) 2a 00 00 06 b0 00 00 04 00 00
[  264.564964] sd 4:0:0:0: [sda] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[  264.564965] sd 4:0:0:0: [sda] tag#9 CDB: Write(10) 2a 00 00 06 ac 00 00 04 00 00
[  264.564980] sd 4:0:0:0: [sda] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[  264.564981] sd 4:0:0:0: [sda] tag#8 CDB: Write(10) 2a 00 00 06 a8 00 00 04 00 00
[  264.565048] sd 4:0:0:0: [sda] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[  264.565050] sd 4:0:0:0: [sda] tag#7 CDB: Write(10) 2a 00 00 06 a4 00 00 04 00 00
[  264.565061] sd 4:0:0:0: [sda] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[  264.565062] sd 4:0:0:0: [sda] tag#6 CDB: Write(10) 2a 00 00 06 a0 00 00 04 00 00
[  264.565129] sd 4:0:0:0: [sda] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[  264.565130] sd 4:0:0:0: [sda] tag#5 CDB: Write(10) 2a 00 00 06 9c 00 00 04 00 00
[  264.565143] sd 4:0:0:0: [sda] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[  264.565145] sd 4:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 00 06 98 00 00 04 00 00
[  264.565184] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[  264.565186] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 00 06 94 00 00 04 00 00
[  264.565228] scsi host4: uas_eh_bus_reset_handler start
[  264.677011] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[  264.694534] scsi host4: uas_eh_bus_reset_handler success
[  266.224907] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[  296.581123] sd 4:0:0:0: [sda] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[  296.581129] sd 4:0:0:0: [sda] tag#6 CDB: Write(10) 2a 00 00 16 e8 00 00 04 00 00
[  296.581158] sd 4:0:0:0: [sda] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[  296.581161] sd 4:0:0:0: [sda] tag#5 CDB: Write(10) 2a 00 00 16 e4 00 00 04 00 00
[  296.581192] sd 4:0:0:0: [sda] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[  296.581194] sd 4:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 00 16 e0 00 00 04 00 00
[  296.581232] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[  296.581233] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 00 16 dc 00 00 04 00 00
[  296.581271] sd 4:0:0:0: [sda] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[  296.581272] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 00 16 d8 00 00 04 00 00
[  296.581312] sd 4:0:0:0: [sda] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[  296.581313] sd 4:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 00 16 d4 00 00 04 00 00
[  296.581350] sd 4:0:0:0: [sda] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[  296.581351] sd 4:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 16 d0 00 00 04 00 00
[  296.581392] sd 4:0:0:0: [sda] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[  296.581394] sd 4:0:0:0: [sda] tag#11 CDB: Write(10) 2a 00 00 16 cc 00 00 04 00 00
[  296.581432] sd 4:0:0:0: [sda] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[  296.581434] sd 4:0:0:0: [sda] tag#10 CDB: Write(10) 2a 00 00 16 c8 00 00 04 00 00
[  296.581471] sd 4:0:0:0: [sda] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[  296.581473] sd 4:0:0:0: [sda] tag#9 CDB: Write(10) 2a 00 00 16 c4 00 00 04 00 00
[  296.581522] sd 4:0:0:0: [sda] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[  296.581523] sd 4:0:0:0: [sda] tag#8 CDB: Write(10) 2a 00 00 16 c0 00 00 04 00 00
[  296.581573] sd 4:0:0:0: [sda] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[  296.581574] sd 4:0:0:0: [sda] tag#7 CDB: Write(10) 2a 00 00 16 bc 00 00 04 00 00
[  296.581634] scsi host4: uas_eh_bus_reset_handler start
[  296.693397] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[  296.711168] scsi host4: uas_eh_bus_reset_handler success
[  297.718634] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted
[  328.661648] sd 4:0:0:0: [sda] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD OUT 
[  328.661652] sd 4:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 00 1f c4 00 00 04 00 00
[  328.661685] sd 4:0:0:0: [sda] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD OUT 
[  328.661687] sd 4:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 1f c0 00 00 04 00 00
[  328.661746] sd 4:0:0:0: [sda] tag#11 uas_eh_abort_handler 0 uas-tag 12 inflight: CMD OUT 
[  328.661747] sd 4:0:0:0: [sda] tag#11 CDB: Write(10) 2a 00 00 1f bc 00 00 04 00 00
[  328.661764] sd 4:0:0:0: [sda] tag#10 uas_eh_abort_handler 0 uas-tag 11 inflight: CMD OUT 
[  328.661765] sd 4:0:0:0: [sda] tag#10 CDB: Write(10) 2a 00 00 1f b8 00 00 04 00 00
[  328.661831] sd 4:0:0:0: [sda] tag#9 uas_eh_abort_handler 0 uas-tag 10 inflight: CMD OUT 
[  328.661832] sd 4:0:0:0: [sda] tag#9 CDB: Write(10) 2a 00 00 1f b4 00 00 04 00 00
[  328.661848] sd 4:0:0:0: [sda] tag#8 uas_eh_abort_handler 0 uas-tag 9 inflight: CMD OUT 
[  328.661849] sd 4:0:0:0: [sda] tag#8 CDB: Write(10) 2a 00 00 1f b0 00 00 04 00 00
[  328.661915] sd 4:0:0:0: [sda] tag#7 uas_eh_abort_handler 0 uas-tag 8 inflight: CMD OUT 
[  328.661917] sd 4:0:0:0: [sda] tag#7 CDB: Write(10) 2a 00 00 1f ac 00 00 04 00 00
[  328.661931] sd 4:0:0:0: [sda] tag#6 uas_eh_abort_handler 0 uas-tag 7 inflight: CMD OUT 
[  328.661932] sd 4:0:0:0: [sda] tag#6 CDB: Write(10) 2a 00 00 1f a8 00 00 04 00 00
[  328.662000] sd 4:0:0:0: [sda] tag#5 uas_eh_abort_handler 0 uas-tag 6 inflight: CMD OUT 
[  328.662002] sd 4:0:0:0: [sda] tag#5 CDB: Write(10) 2a 00 00 1f a4 00 00 04 00 00
[  328.662013] sd 4:0:0:0: [sda] tag#4 uas_eh_abort_handler 0 uas-tag 5 inflight: CMD OUT 
[  328.662015] sd 4:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 00 1f a0 00 00 04 00 00
[  328.662080] sd 4:0:0:0: [sda] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD OUT 
[  328.662081] sd 4:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 00 1f 9c 00 00 04 00 00
[  328.662092] sd 4:0:0:0: [sda] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD OUT 
[  328.662094] sd 4:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 00 1f 98 00 00 04 00 00
[  328.662178] scsi host4: uas_eh_bus_reset_handler start
[  328.774024] usb 2-2: reset SuperSpeed USB device number 2 using xhci_hcd
[  328.791542] scsi host4: uas_eh_bus_reset_handler success
[  333.864320] xhci_hcd 0000:00:14.0: ERROR Unknown event condition 10, HC probably busted



```

---

### Post by matt_symes on 2016-01-11
Hi

I agree with you. This looks a kernel or driver issue connected with USB3 (altough i am surprised you are seeing it on USB2 under 15.10).

I notice the uas driver is being loaded and I'm wondering if the issue is connected with that.

> idVendor=357d, idProduct=7788 

This is a stab in the dark but let's try blacklisting it for your device. We have nothing to lose and can undo the changes if they makes no difference.

```
echo options usb-storage quirks=357d:7788:u | sudo tee /etc/modprobe.d/blacklist_uas_357d.conf
```

```
sudo update-initramfs -u
```

```
sudo reboot
```

Let us know how that goes.

BTW: I could not find that vendor and device conbination on pcidatabase.com or in /usr/share/misc/pci.ids after running *sudo update-pciids*.

Kind regards

---

### Post by nicofrand on 2016-04-28
Hi,

I was having the same issue (but only with files > 4 Gio most of the times), with an ICY BOX case too (hmm…) with two HDDs in it, but it seemed that it crashed only with one of the HDD.

My kernel is 4.4.0-21-generic.

I tried your solution @matt_symes and it seems it fixed the issue ! I am not sure what it did though, it disabled UAS (whatever it is) ?

Thanks anyway !

---

