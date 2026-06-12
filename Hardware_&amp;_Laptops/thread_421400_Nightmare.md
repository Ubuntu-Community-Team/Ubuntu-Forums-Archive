---
title: "Nightmare"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by hnfmr on 2007-04-24
This is the primary reason that keeps stopping me from using Ubuntu....A month ago I installed Feisty Herd4, Herd 5, I experienced exactly the same error (as of now I'm using Feisty 7.04 release version)....I.E. system goes slow like hell....with terrible responsiveness, it's like CPU is under 100% load...e.g if I type a letter "F"...it'll appear on the screen 3 seconds later....

I checked kern.log..which appears to be like this when my system goes extremely slow

Apr 24 16:36:28 will-laptop kernel: [ 4726.184172] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:28 will-laptop kernel: [ 4726.184178] ide: failed opcode was: unknown
Apr 24 16:36:33 will-laptop kernel: [ 4731.185511] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:33 will-laptop kernel: [ 4731.185516] ide: failed opcode was: unknown
Apr 24 16:36:33 will-laptop kernel: [ 4731.185519] hda: drive not ready for command
Apr 24 16:36:38 will-laptop kernel: [ 4736.187037] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:38 will-laptop kernel: [ 4736.187042] ide: failed opcode was: unknown
Apr 24 16:36:38 will-laptop kernel: [ 4736.187044] hda: drive not ready for command
Apr 24 16:36:43 will-laptop kernel: [ 4741.188563] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:43 will-laptop kernel: [ 4741.188568] ide: failed opcode was: unknown
Apr 24 16:36:43 will-laptop kernel: [ 4741.188570] hda: drive not ready for command
Apr 24 16:36:48 will-laptop kernel: [ 4746.250059] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:48 will-laptop kernel: [ 4746.250065] ide: failed opcode was: unknown
Apr 24 16:36:48 will-laptop kernel: [ 4746.250070] hda: drive not ready for command
Apr 24 16:36:53 will-laptop kernel: [ 4751.251583] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:53 will-laptop kernel: [ 4751.251587] ide: failed opcode was: unknown
Apr 24 16:36:53 will-laptop kernel: [ 4751.251591] hda: drive not ready for command
Apr 24 16:36:58 will-laptop kernel: [ 4756.253104] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:36:58 will-laptop kernel: [ 4756.253108] ide: failed opcode was: unknown
Apr 24 16:36:58 will-laptop kernel: [ 4756.253111] hda: drive not ready for command
Apr 24 16:37:03 will-laptop kernel: [ 4761.254630] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:03 will-laptop kernel: [ 4761.254634] ide: failed opcode was: unknown
Apr 24 16:37:03 will-laptop kernel: [ 4761.254638] hda: drive not ready for command
Apr 24 16:37:08 will-laptop kernel: [ 4766.256155] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:08 will-laptop kernel: [ 4766.256159] ide: failed opcode was: unknown
Apr 24 16:37:08 will-laptop kernel: [ 4766.256162] hda: drive not ready for command
Apr 24 16:37:13 will-laptop kernel: [ 4771.257680] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:13 will-laptop kernel: [ 4771.257685] ide: failed opcode was: unknown
Apr 24 16:37:13 will-laptop kernel: [ 4771.257688] hda: drive not ready for command
Apr 24 16:37:18 will-laptop kernel: [ 4776.274896] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:18 will-laptop kernel: [ 4776.274901] ide: failed opcode was: unknown
Apr 24 16:37:18 will-laptop kernel: [ 4776.274905] hda: drive not ready for command
Apr 24 16:37:23 will-laptop kernel: [ 4781.368428] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:23 will-laptop kernel: [ 4781.368434] ide: failed opcode was: unknown
Apr 24 16:37:23 will-laptop kernel: [ 4781.368438] hda: drive not ready for command
Apr 24 16:37:28 will-laptop kernel: [ 4786.369951] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:28 will-laptop kernel: [ 4786.369954] ide: failed opcode was: unknown
Apr 24 16:37:28 will-laptop kernel: [ 4786.369958] hda: drive not ready for command
Apr 24 16:37:34 will-laptop kernel: [ 4791.371474] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:34 will-laptop kernel: [ 4791.371478] ide: failed opcode was: unknown
Apr 24 16:37:34 will-laptop kernel: [ 4791.371480] hda: drive not ready for command
Apr 24 16:37:35 will-laptop kernel: [ 4792.691884] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 24 16:37:38 will-laptop kernel: [ 4796.372999] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:38 will-laptop kernel: [ 4796.373387] ide: failed opcode was: unknown
Apr 24 16:37:38 will-laptop kernel: [ 4796.373391] hda: drive not ready for command
Apr 24 16:37:43 will-laptop kernel: [ 4801.386518] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:43 will-laptop kernel: [ 4801.386524] ide: failed opcode was: unknown
Apr 24 16:37:43 will-laptop kernel: [ 4801.386529] hda: drive not ready for command
Apr 24 16:37:49 will-laptop kernel: [ 4806.393652] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:49 will-laptop kernel: [ 4806.393657] ide: failed opcode was: unknown
Apr 24 16:37:49 will-laptop kernel: [ 4806.393661] hda: drive not ready for command
Apr 24 16:37:54 will-laptop kernel: [ 4811.395174] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:54 will-laptop kernel: [ 4811.395177] ide: failed opcode was: unknown
Apr 24 16:37:54 will-laptop kernel: [ 4811.395180] hda: drive not ready for command
Apr 24 16:37:59 will-laptop kernel: [ 4816.396695] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:37:59 will-laptop kernel: [ 4816.396698] ide: failed opcode was: unknown
Apr 24 16:37:59 will-laptop kernel: [ 4816.396701] hda: drive not ready for command
Apr 24 16:38:04 will-laptop kernel: [ 4821.398223] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:04 will-laptop kernel: [ 4821.398226] ide: failed opcode was: unknown
Apr 24 16:38:04 will-laptop kernel: [ 4821.398229] hda: drive not ready for command
Apr 24 16:38:09 will-laptop kernel: [ 4826.403743] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:09 will-laptop kernel: [ 4826.403747] ide: failed opcode was: unknown
Apr 24 16:38:09 will-laptop kernel: [ 4826.403749] hda: drive not ready for command
Apr 24 16:38:14 will-laptop kernel: [ 4831.405267] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:14 will-laptop kernel: [ 4831.405270] ide: failed opcode was: unknown
Apr 24 16:38:14 will-laptop kernel: [ 4831.405273] hda: drive not ready for command
Apr 24 16:38:19 will-laptop kernel: [ 4836.406793] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:19 will-laptop kernel: [ 4836.406797] ide: failed opcode was: unknown
Apr 24 16:38:19 will-laptop kernel: [ 4836.406799] hda: drive not ready for command
Apr 24 16:38:24 will-laptop kernel: [ 4841.408318] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:24 will-laptop kernel: [ 4841.408322] ide: failed opcode was: unknown
Apr 24 16:38:24 will-laptop kernel: [ 4841.408325] hda: drive not ready for command
Apr 24 16:38:29 will-laptop kernel: [ 4846.417840] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:29 will-laptop kernel: [ 4846.417847] ide: failed opcode was: unknown
Apr 24 16:38:29 will-laptop kernel: [ 4846.417852] hda: drive not ready for command
Apr 24 16:38:36 will-laptop kernel: [ 4853.434056] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:36 will-laptop kernel: [ 4853.434063] ide: failed opcode was: unknown
Apr 24 16:38:36 will-laptop kernel: [ 4853.434067] hda: drive not ready for command
Apr 24 16:38:41 will-laptop kernel: [ 4858.435576] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:41 will-laptop kernel: [ 4858.435580] ide: failed opcode was: unknown
Apr 24 16:38:41 will-laptop kernel: [ 4858.435583] hda: drive not ready for command
Apr 24 16:38:46 will-laptop kernel: [ 4863.437102] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:46 will-laptop kernel: [ 4863.437106] ide: failed opcode was: unknown
Apr 24 16:38:46 will-laptop kernel: [ 4863.437108] hda: drive not ready for command
Apr 24 16:38:51 will-laptop kernel: [ 4868.438626] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:51 will-laptop kernel: [ 4868.438631] ide: failed opcode was: unknown
Apr 24 16:38:51 will-laptop kernel: [ 4868.438634] hda: drive not ready for command
Apr 24 16:38:56 will-laptop kernel: [ 4873.440151] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:38:56 will-laptop kernel: [ 4873.440155] ide: failed opcode was: unknown
Apr 24 16:38:56 will-laptop kernel: [ 4873.440158] hda: drive not ready for command
Apr 24 16:39:03 will-laptop kernel: [ 4880.192373] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:03 will-laptop kernel: [ 4880.192381] ide: failed opcode was: unknown
Apr 24 16:39:03 will-laptop kernel: [ 4880.192386] hda: drive not ready for command
Apr 24 16:39:08 will-laptop kernel: [ 4885.193896] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:08 will-laptop kernel: [ 4885.193900] ide: failed opcode was: unknown
Apr 24 16:39:08 will-laptop kernel: [ 4885.193903] hda: drive not ready for command
Apr 24 16:39:09 will-laptop kernel: [ 4886.159868] APIC error on CPU0: 40(40)
Apr 24 16:39:13 will-laptop kernel: [ 4890.199417] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:13 will-laptop kernel: [ 4890.199420] ide: failed opcode was: unknown
Apr 24 16:39:13 will-laptop kernel: [ 4890.199423] hda: drive not ready for command
Apr 24 16:39:18 will-laptop kernel: [ 4895.208941] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:18 will-laptop kernel: [ 4895.208946] ide: failed opcode was: unknown
Apr 24 16:39:18 will-laptop kernel: [ 4895.208950] hda: drive not ready for command
Apr 24 16:39:23 will-laptop kernel: [ 4900.210463] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:23 will-laptop kernel: [ 4900.210467] ide: failed opcode was: unknown
Apr 24 16:39:23 will-laptop kernel: [ 4900.210470] hda: drive not ready for command
Apr 24 16:39:23 will-laptop kernel: [ 4900.271701] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 24 16:39:30 will-laptop kernel: [ 4907.210748] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:30 will-laptop kernel: [ 4907.210755] ide: failed opcode was: unknown
Apr 24 16:39:30 will-laptop kernel: [ 4907.210760] hda: drive not ready for command
Apr 24 16:39:35 will-laptop kernel: [ 4912.212270] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:35 will-laptop kernel: [ 4912.212274] ide: failed opcode was: unknown
Apr 24 16:39:35 will-laptop kernel: [ 4912.212277] hda: drive not ready for command
Apr 24 16:39:36 will-laptop kernel: [ 4914.061565] APIC error on CPU0: 40(40)
Apr 24 16:39:40 will-laptop kernel: [ 4917.213793] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:40 will-laptop kernel: [ 4917.213797] ide: failed opcode was: unknown
Apr 24 16:39:40 will-laptop kernel: [ 4917.213799] hda: drive not ready for command
Apr 24 16:39:45 will-laptop kernel: [ 4922.215320] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:45 will-laptop kernel: [ 4922.215324] ide: failed opcode was: unknown
Apr 24 16:39:45 will-laptop kernel: [ 4922.215326] hda: drive not ready for command
Apr 24 16:39:48 will-laptop kernel: [ 4925.609416] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 24 16:39:50 will-laptop kernel: [ 4927.216842] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:50 will-laptop kernel: [ 4927.216846] ide: failed opcode was: unknown
Apr 24 16:39:50 will-laptop kernel: [ 4927.216848] hda: drive not ready for command
Apr 24 16:39:57 will-laptop kernel: [ 4934.217073] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:39:57 will-laptop kernel: [ 4934.217079] ide: failed opcode was: unknown
Apr 24 16:39:57 will-laptop kernel: [ 4934.217085] hda: drive not ready for command
Apr 24 16:40:02 will-laptop kernel: [ 4939.226593] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:40:02 will-laptop kernel: [ 4939.226599] ide: failed opcode was: unknown
Apr 24 16:40:02 will-laptop kernel: [ 4939.226605] hda: drive not ready for command
Apr 24 16:40:07 will-laptop kernel: [ 4944.228117] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:40:07 will-laptop kernel: [ 4944.228120] ide: failed opcode was: unknown
Apr 24 16:40:07 will-laptop kernel: [ 4944.228123] hda: drive not ready for command
Apr 24 16:40:12 will-laptop kernel: [ 4949.229640] hda: status timeout: status=0xd0 { Busy }
Apr 24 16:40:12 will-laptop kernel: [ 4949.229644] ide: failed opcode was: unknown



I didn't paste all the error messages, it lasted for another 5 mins..then I had the chance to reboot it...the reboot took more than 3 minutes.....................................

---

### Post by kommaanda on 2007-04-24
I am experiencing the same thing. Slow system, even mouse movements are not keeping up. I reinstalled a couple of times (first time was online upgrade from 6.10). The last time I reinstalled it seemed to work just fine at first but my Internet connection (ethernet) wasn't working. So, I disconnected in the network manager application (top right of the screen) and after reconnecting and slowed down again. I have no idea if it had to do with the ethernet. 
Do you have Internet access?

---

### Post by snipe on 2007-04-24
I got the log problem but my my system is working normaly... execpt my writer isn't detected

```
Apr 25 02:17:03 thunar kernel: [  265.983057] hdd: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Apr 25 02:17:03 thunar kernel: [  265.983062] hdd: status error: error=0x00 { }
Apr 25 02:17:03 thunar kernel: [  265.983063] ide: failed opcode was: unknown
Apr 25 02:17:03 thunar kernel: [  265.983065] hdd: drive not ready for command
Apr 25 02:17:03 thunar kernel: [  265.983614] hdd: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Apr 25 02:17:03 thunar kernel: [  265.983618] hdd: status error: error=0x00 { }
Apr 25 02:17:03 thunar kernel: [  265.983620] ide: failed opcode was: unknown
Apr 25 02:17:03 thunar kernel: [  265.983622] hdd: drive not ready for command
```

Edit : My dvd writer is a  PLEXTOR DVDR PX-740A and it is working great under edgy but not anymore under feisty

Edit 2: Found sth : You can stop the kernel display those messages by doing "sudo hdparm -w /dev/hdX" for me it's hdd .... But try this at your own risk because in the man page of hdparm it's written -w option (reseting drive) is DANGEROUS.
Anyway for me it stops the messages but my writer isn't detect at all

---

### Post by snipe on 2007-05-11
**[SIZE="4"]TEMPORARY SOLUTION[/SIZE]**
 **[SIZE="3"]You can try(at your own risk because it reset IDE device)[/SIZE]**
```
sudo hdparm -w /dev/hdX  (replace X with the letter of your drive)
```

and after to SET DMA because the reset unset it
```
sudo hdparm -d 1 /dev/hdX (replace X with the letter of your drive)
```

After that i didn't get anymore errors but my drive wasn't detect by gnome( serpentine & brasero)

To perform a detection of your drive do (or invert i don't remember which one depends on the other)
```
sudo rmmod cdrom ide_cd
```   
```
sudo modprobe cdrom ide_cd
```

---

