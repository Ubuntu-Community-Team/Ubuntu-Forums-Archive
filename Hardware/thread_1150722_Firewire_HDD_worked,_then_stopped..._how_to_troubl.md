---
title: "Firewire HDD worked, then stopped... how to troubleshoot?"
date: 2009-05-06
forum: Hardware
---

### Post by inspired on 2009-05-06
Hi folks,
I have a 1tb external disk that I connect with Firewire. It worked fine for a few days. Then after using it on a windows install for a day or so, I plugged it back into the linux install and it no go.

I am not sure what I can do to get it going. I know it CAN work... because it was fine before.

Here is some log info from when I plug the drive in:
From kern.log
```
May  6 09:17:05 jonathan-ubuntu kernel: [ 1941.592413] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
May  6 09:17:05 jonathan-ubuntu kernel: [ 1941.869361] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00402602190118e2]
May  6 09:17:05 jonathan-ubuntu kernel: [ 1941.869419] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
May  6 09:17:05 jonathan-ubuntu kernel: [ 1941.895421] scsi2 : SBP-2 IEEE-1394
May  6 09:17:06 jonathan-ubuntu kernel: [ 1942.951143] ieee1394: sbp2: Logged into SBP-2 device
May  6 09:17:06 jonathan-ubuntu kernel: [ 1942.951961] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
May  6 09:17:12 jonathan-ubuntu kernel: [ 1949.000030] ieee1394: sbp2: aborting sbp2 command
May  6 09:17:12 jonathan-ubuntu kernel: [ 1949.000035] scsi 2:0:0:0: CDB: Inquiry: 12 00 00 00 24 00
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000029] ieee1394: sbp2: aborting sbp2 command
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000035] scsi 2:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000049] ieee1394: sbp2: hpsb_node_write failed.
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000051] 
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000061] ieee1394: sbp2: reset requested
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000063] ieee1394: sbp2: generating sbp2 fetch agent reset
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000066] ieee1394: sbp2: hpsb_node_write failed.
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000067] 
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000071] ieee1394: sbp2: Bus reset in progress - rejecting command
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000076] scsi 2:0:0:0: Device offlined - not ready after error recovery
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000120] ieee1394: sbp2: scsi_add_device failed
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.008041] scsi3 : SBP-2 IEEE-1394
May  6 09:17:43 jonathan-ubuntu kernel: [ 1980.012061] ieee1394: sbp2: Error logging into SBP-2 device - timed out
May  6 09:17:43 jonathan-ubuntu kernel: [ 1980.021352] sbp2: probe of 00402602190118e2-0 failed with error -16
May  6 09:17:44 jonathan-ubuntu kernel: [ 1980.499269] scsi4 : SBP-2 IEEE-1394
May  6 09:17:45 jonathan-ubuntu kernel: [ 1981.559375] ieee1394: sbp2: Logged into SBP-2 device
May  6 09:17:45 jonathan-ubuntu kernel: [ 1981.560631] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
May  6 09:17:51 jonathan-ubuntu kernel: [ 1988.000079] ieee1394: sbp2: aborting sbp2 command
May  6 09:17:51 jonathan-ubuntu kernel: [ 1988.000090] scsi 4:0:0:0: CDB: Inquiry: 12 00 00 00 24 00
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000077] ieee1394: sbp2: aborting sbp2 command
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000088] scsi 4:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000116] ieee1394: sbp2: hpsb_node_write failed.
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000120] 
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000135] ieee1394: sbp2: reset requested
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000141] ieee1394: sbp2: generating sbp2 fetch agent reset
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000148] ieee1394: sbp2: hpsb_node_write failed.
```
That error output keeps repeating each time the OS tries to access the drive.

And from Messages log:
```
May  6 09:17:05 jonathan-ubuntu kernel: [ 1941.895421] scsi2 : SBP-2 IEEE-1394
May  6 09:17:06 jonathan-ubuntu kernel: [ 1942.951143] ieee1394: sbp2: Logged into SBP-2 device
May  6 09:17:06 jonathan-ubuntu kernel: [ 1942.951961] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
May  6 09:17:12 jonathan-ubuntu kernel: [ 1949.000030] ieee1394: sbp2: aborting sbp2 command
May  6 09:17:12 jonathan-ubuntu kernel: [ 1949.000035] scsi 2:0:0:0: CDB: Inquiry: 12 00 00 00 24 00
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000029] ieee1394: sbp2: aborting sbp2 command
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000035] scsi 2:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000061] ieee1394: sbp2: reset requested
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000063] ieee1394: sbp2: generating sbp2 fetch agent reset
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.000076] scsi 2:0:0:0: Device offlined - not ready after error recovery
May  6 09:17:22 jonathan-ubuntu kernel: [ 1959.008041] scsi3 : SBP-2 IEEE-1394
May  6 09:17:43 jonathan-ubuntu kernel: [ 1980.021352] sbp2: probe of 00402602190118e2-0 failed with error -16
May  6 09:17:44 jonathan-ubuntu kernel: [ 1980.499269] scsi4 : SBP-2 IEEE-1394
May  6 09:17:45 jonathan-ubuntu kernel: [ 1981.559375] ieee1394: sbp2: Logged into SBP-2 device
May  6 09:17:45 jonathan-ubuntu kernel: [ 1981.560631] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
May  6 09:17:51 jonathan-ubuntu kernel: [ 1988.000079] ieee1394: sbp2: aborting sbp2 command
May  6 09:17:51 jonathan-ubuntu kernel: [ 1988.000090] scsi 4:0:0:0: CDB: Inquiry: 12 00 00 00 24 00
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000077] ieee1394: sbp2: aborting sbp2 command
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000088] scsi 4:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000135] ieee1394: sbp2: reset requested
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000141] ieee1394: sbp2: generating sbp2 fetch agent reset
May  6 09:18:01 jonathan-ubuntu kernel: [ 1998.000170] scsi 4:0:0:0: Device offlined - not ready after error recovery
May  6 09:18:02 jonathan-ubuntu kernel: [ 1998.500081] scsi5 : SBP-2 IEEE-1394
May  6 09:18:03 jonathan-ubuntu kernel: [ 1999.557448] ieee1394: sbp2: Logged into SBP-2 device
May  6 09:18:03 jonathan-ubuntu kernel: [ 1999.558441] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
May  6 09:18:09 jonathan-ubuntu kernel: [ 2006.000113] ieee1394: sbp2: aborting sbp2 command
May  6 09:18:09 jonathan-ubuntu kernel: [ 2006.000124] scsi 5:0:0:0: CDB: Inquiry: 12 00 00 00 24 00
May  6 09:18:19 jonathan-ubuntu kernel: [ 2016.000055] ieee1394: sbp2: aborting sbp2 command
May  6 09:18:19 jonathan-ubuntu kernel: [ 2016.000060] scsi 5:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  6 09:18:19 jonathan-ubuntu kernel: [ 2016.000085] ieee1394: sbp2: reset requested
May  6 09:18:19 jonathan-ubuntu kernel: [ 2016.000087] ieee1394: sbp2: generating sbp2 fetch agent reset
May  6 09:18:19 jonathan-ubuntu kernel: [ 2016.000100] scsi 5:0:0:0: Device offlined - not ready after error recovery
May  6 09:18:20 jonathan-ubuntu kernel: [ 2016.509078] scsi6 : SBP-2 IEEE-1394
May  6 09:18:21 jonathan-ubuntu kernel: [ 2017.568732] ieee1394: sbp2: Logged into SBP-2 device
May  6 09:18:21 jonathan-ubuntu kernel: [ 2017.569534] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
May  6 09:18:27 jonathan-ubuntu kernel: [ 2024.000069] ieee1394: sbp2: aborting sbp2 command
May  6 09:18:27 jonathan-ubuntu kernel: [ 2024.000076] scsi 6:0:0:0: CDB: Inquiry: 12 00 00 00 24 00
May  6 09:18:37 jonathan-ubuntu kernel: [ 2034.000100] ieee1394: sbp2: aborting sbp2 command
```
I am on 9.04 Ubuntu.

Any help is greatly appreciated.
Thanks,

Jonathan

---

### Post by inspired on 2009-05-12
Issue seems to have resolved itself. Drive has started appearing and mounting via firewire... for now.

---

### Post by inspired on 2009-05-15
Well... it crapped out again and Ubuntu is doing the same thing.
Would love to know how to troubleshoot this if anyone can advise.
:popcorn:
Cheers,
Jonathan

---

