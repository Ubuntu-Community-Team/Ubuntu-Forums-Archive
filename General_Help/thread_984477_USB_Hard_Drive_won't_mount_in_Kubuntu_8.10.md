---
title: "USB Hard Drive won't mount in Kubuntu 8.10"
date: 2008-11-16
forum: General Help
---

### Post by bennetfox on 2008-11-16
Hey gang,

I installed Kubuntu 8.10 on my computer and I have a 250gb external hard drive plugged in via USB. When Kubuntu 8.10 starts to boot, I hear the external drive start going ca-chunka ca-chunka ca-chunka. It keeps doing this until I unplug the drive from the computer.

I tailed the messages when I plugged in the drive and this is what I get:

Nov 16 21:46:46 ubuntu kernel: [ 2477.952135] usb 5-3: new high speed USB device using ehci_hcd and address 8                                                   
Nov 16 21:46:46 ubuntu kernel: [ 2478.255279] usb 5-3: configuration #1 chosen from 1 choice                                                                    
Nov 16 21:46:46 ubuntu kernel: [ 2478.256613] scsi6 : SCSI emulation for USB Mass Storage devices                                                               
Nov 16 21:46:51 ubuntu kernel: [ 2483.257540] scsi 6:0:0:0: Direct-Access     WDC WD25 00JB-55GVC0      08.0 PQ: 0 ANSI: 0                                      
Nov 16 21:46:51 ubuntu kernel: [ 2483.261651] sd 6:0:0:0: [sdc] 488397169 512-byte hardware sectors (250059 MB)                                                 
Nov 16 21:46:51 ubuntu kernel: [ 2483.268277] sd 6:0:0:0: [sdc] Write Protect is off                                                                            
Nov 16 21:46:51 ubuntu kernel: [ 2483.270931] sd 6:0:0:0: [sdc] 488397169 512-byte hardware sectors (250059 MB)                                                 
Nov 16 21:46:51 ubuntu kernel: [ 2483.272427] sd 6:0:0:0: [sdc] Write Protect is off                                                                            
Nov 16 21:46:51 ubuntu kernel: [ 2483.273632]  sdc: sdc1                        
Nov 16 21:46:51 ubuntu kernel: [ 2483.304776] sd 6:0:0:0: [sdc] Attached SCSI disk                                                                              
Nov 16 21:46:51 ubuntu kernel: [ 2483.305509] sd 6:0:0:0: Attached scsi generic sg3 type 0                                                                      
Nov 16 21:46:52 ubuntu kernel: [ 2483.834057] sd 6:0:0:0: [sdc] Sense Key : No Sense [current]                                                                  
Nov 16 21:46:52 ubuntu kernel: [ 2483.834079] sd 6:0:0:0: [sdc] Add. Sense: No additional sense information                                                     
Nov 16 21:46:52 ubuntu kernel: [ 2484.200309] sd 6:0:0:0: [sdc] Sense Key : No Sense [current]                                                                  
Nov 16 21:46:52 ubuntu kernel: [ 2484.200330] sd 6:0:0:0: [sdc] Add. Sense: No additional sense information 
Nov 16 21:46:56 ubuntu kernel: [ 2487.475002] usb 5-3: USB disconnect, address 8
Nov 16 21:46:56 ubuntu kernel: [ 2487.477300] scsi 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 16 21:46:56 ubuntu kernel: [ 2487.477333] __ratelimit: 117 callbacks suppressed

The drive works fine in Windows and Kubuntu 8.04.

Any ideas on how I can get my drive mounted in Kubuntu 8.10?

Take care,
Bennet

---

### Post by ilchymis on 2008-11-16
I haven't experienced this myself, but I think this is a "bug" in the version of Linux used in Ubuntu 8.10.  If you've upgraded from a previous version, try booting with the old kernel, if it is still available in your Grub menu, and see if that fixes the problem.

(I put "bug" in quotes because the root of the problem appears to be certain USB drives not conforming to standard behavior; the "bug" is that newer versions of Linux apparently aren't as good as recovering from these problems as previous Linux kernels were, or as Windows currently is.)

This Linux kernel patch, not yet integrated into Ubuntu 8.10, may address this issue:  [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8bfa24727087d7252f9ecfb5fea2dfc92d797fbd](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8bfa24727087d7252f9ecfb5fea2dfc92d797fbd)

---

### Post by ilchymis on 2008-11-16
Also see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

---

