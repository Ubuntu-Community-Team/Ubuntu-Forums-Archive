---
title: "Problem with external HDD"
date: 2009-11-08
forum: Hardware
---

### Post by rullingen on 2009-11-08
Just installed Ubuntu 9.10 64bit and it wont mount my External HDD at all, XP can and my girlfriends laptop also running 9.10 (32bit) but not mine. I can however see it in Disk Utility but I cannot delete or create any partitions, neither does it recognize any existing ones.

DMESG returns something rather nasty:

```
[  964.485924] sd 6:0:0:0: [sdb] Unhandled error code
[  964.485928] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.485932] end_request: I/O error, dev sdb, sector 0
[  964.485985] sd 6:0:0:0: [sdb] Unhandled error code
[  964.485988] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.485991] end_request: I/O error, dev sdb, sector 0
[  964.486053] sd 6:0:0:0: [sdb] Unhandled error code
[  964.486056] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.486059] end_request: I/O error, dev sdb, sector 0
[  964.909088] sd 6:0:0:0: [sdb] Unhandled error code
[  964.909093] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.909097] end_request: I/O error, dev sdb, sector 63
[  964.909161] sd 6:0:0:0: [sdb] Unhandled error code
[  964.909163] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.909166] end_request: I/O error, dev sdb, sector 63
[  964.911700] sd 6:0:0:0: [sdb] Unhandled error code
[  964.911705] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.911709] end_request: I/O error, dev sdb, sector 63
[  964.911825] sd 6:0:0:0: [sdb] Unhandled error code
[  964.911827] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.911830] end_request: I/O error, dev sdb, sector 303
[  964.913838] sd 6:0:0:0: [sdb] Unhandled error code
[  964.913843] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.913846] end_request: I/O error, dev sdb, sector 63
[  964.916710] sd 6:0:0:0: [sdb] Unhandled error code
[  964.916714] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.916718] end_request: I/O error, dev sdb, sector 0
[  964.922690] sd 6:0:0:0: [sdb] Unhandled error code
[  964.922696] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.922700] end_request: I/O error, dev sdb, sector 0
[  964.922899] sd 6:0:0:0: [sdb] Unhandled error code
[  964.922901] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  964.922905] end_request: I/O error, dev sdb, sector 0
[  967.150600] sd 6:0:0:0: [sdb] Unhandled error code
[  967.150605] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.150610] end_request: I/O error, dev sdb, sector 63
[  967.150614] __ratelimit: 622 callbacks suppressed
[  967.150617] Buffer I/O error on device sdb1, logical block 0
[  967.150621] Buffer I/O error on device sdb1, logical block 1
[  967.150624] Buffer I/O error on device sdb1, logical block 2
[  967.150627] Buffer I/O error on device sdb1, logical block 3
[  967.150632] Buffer I/O error on device sdb1, logical block 4
[  967.150635] Buffer I/O error on device sdb1, logical block 5
[  967.150638] Buffer I/O error on device sdb1, logical block 6
[  967.150641] Buffer I/O error on device sdb1, logical block 7
[  967.150644] Buffer I/O error on device sdb1, logical block 8
[  967.150647] Buffer I/O error on device sdb1, logical block 9
[  967.150700] sd 6:0:0:0: [sdb] Unhandled error code
[  967.150702] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.150706] end_request: I/O error, dev sdb, sector 63
[  967.153186] sd 6:0:0:0: [sdb] Unhandled error code
[  967.153191] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.153195] end_request: I/O error, dev sdb, sector 63
[  967.153316] sd 6:0:0:0: [sdb] Unhandled error code
[  967.153318] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.153321] end_request: I/O error, dev sdb, sector 303
[  967.153370] sd 6:0:0:0: [sdb] Unhandled error code
[  967.153372] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.153376] end_request: I/O error, dev sdb, sector 63
[  967.156566] sd 6:0:0:0: [sdb] Unhandled error code
[  967.156571] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.156575] end_request: I/O error, dev sdb, sector 0
[  967.158708] sd 6:0:0:0: [sdb] Unhandled error code
[  967.158713] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.158717] end_request: I/O error, dev sdb, sector 0
[  967.158939] sd 6:0:0:0: [sdb] Unhandled error code
[  967.158941] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  967.158944] end_request: I/O error, dev sdb, sector 0
[ 1395.095903] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.095910] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.095914] end_request: I/O error, dev sdb, sector 63
[ 1395.095920] __ratelimit: 148 callbacks suppressed
[ 1395.095923] Buffer I/O error on device sdb1, logical block 0
[ 1395.095926] lost page write due to I/O error on sdb1
[ 1395.095931] Buffer I/O error on device sdb1, logical block 1
[ 1395.095934] lost page write due to I/O error on sdb1
[ 1395.095937] Buffer I/O error on device sdb1, logical block 2
[ 1395.095939] lost page write due to I/O error on sdb1
[ 1395.095942] Buffer I/O error on device sdb1, logical block 3
[ 1395.095944] lost page write due to I/O error on sdb1
[ 1395.095957] Buffer I/O error on device sdb1, logical block 4
[ 1395.095960] lost page write due to I/O error on sdb1
[ 1395.095963] Buffer I/O error on device sdb1, logical block 5
[ 1395.095965] lost page write due to I/O error on sdb1
[ 1395.095968] Buffer I/O error on device sdb1, logical block 6
[ 1395.095971] lost page write due to I/O error on sdb1
[ 1395.095974] Buffer I/O error on device sdb1, logical block 7
[ 1395.095976] lost page write due to I/O error on sdb1
[ 1395.095980] Buffer I/O error on device sdb1, logical block 8
[ 1395.095982] lost page write due to I/O error on sdb1
[ 1395.095985] Buffer I/O error on device sdb1, logical block 9
[ 1395.095988] lost page write due to I/O error on sdb1
[ 1395.097949] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.097954] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.097958] end_request: I/O error, dev sdb, sector 303
[ 1395.098037] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.098039] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.098043] end_request: I/O error, dev sdb, sector 1953519809
[ 1395.098237] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.098239] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.098242] end_request: I/O error, dev sdb, sector 1953520049
[ 1395.109339] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.109345] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.109349] end_request: I/O error, dev sdb, sector 63
[ 1395.109466] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.109468] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.109471] end_request: I/O error, dev sdb, sector 303
[ 1395.111303] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.111309] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.111313] end_request: I/O error, dev sdb, sector 63
[ 1395.114205] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.114210] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.114213] end_request: I/O error, dev sdb, sector 0
[ 1395.114267] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.114269] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.114272] end_request: I/O error, dev sdb, sector 0
[ 1395.114337] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.114339] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.114342] end_request: I/O error, dev sdb, sector 0
[ 1395.139901] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.139907] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.139911] end_request: I/O error, dev sdb, sector 63
[ 1395.140096] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.140099] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.140102] end_request: I/O error, dev sdb, sector 303
[ 1395.142314] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.142320] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.142324] end_request: I/O error, dev sdb, sector 63
[ 1395.145213] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.145216] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.145220] end_request: I/O error, dev sdb, sector 0
[ 1395.146083] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.146085] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.146088] end_request: I/O error, dev sdb, sector 0
[ 1395.146192] sd 6:0:0:0: [sdb] Unhandled error code
[ 1395.146195] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1395.146198] end_request: I/O error, dev sdb, sector 0
[ 1484.931456] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.931462] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.931466] end_request: I/O error, dev sdb, sector 63
[ 1484.931471] __ratelimit: 522 callbacks suppressed
[ 1484.931475] Buffer I/O error on device sdb1, logical block 0
[ 1484.931477] lost page write due to I/O error on sdb1
[ 1484.931481] Buffer I/O error on device sdb1, logical block 1
[ 1484.931484] lost page write due to I/O error on sdb1
[ 1484.931487] Buffer I/O error on device sdb1, logical block 2
[ 1484.931489] lost page write due to I/O error on sdb1
[ 1484.931492] Buffer I/O error on device sdb1, logical block 3
[ 1484.931494] lost page write due to I/O error on sdb1
[ 1484.931498] Buffer I/O error on device sdb1, logical block 4
[ 1484.931501] lost page write due to I/O error on sdb1
[ 1484.931504] Buffer I/O error on device sdb1, logical block 5
[ 1484.931506] lost page write due to I/O error on sdb1
[ 1484.931509] Buffer I/O error on device sdb1, logical block 6
[ 1484.931511] lost page write due to I/O error on sdb1
[ 1484.931514] Buffer I/O error on device sdb1, logical block 7
[ 1484.931517] lost page write due to I/O error on sdb1
[ 1484.931520] Buffer I/O error on device sdb1, logical block 8
[ 1484.931522] lost page write due to I/O error on sdb1
[ 1484.931525] Buffer I/O error on device sdb1, logical block 9
[ 1484.931527] lost page write due to I/O error on sdb1
[ 1484.931655] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.931658] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.931661] end_request: I/O error, dev sdb, sector 303
[ 1484.931705] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.931708] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.931711] end_request: I/O error, dev sdb, sector 1953519809
[ 1484.931839] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.931841] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.931845] end_request: I/O error, dev sdb, sector 1953520049
[ 1484.945913] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.945919] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.945923] end_request: I/O error, dev sdb, sector 1953520051
[ 1484.953243] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.953248] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.953252] end_request: I/O error, dev sdb, sector 63
[ 1484.953386] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.953389] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.953392] end_request: I/O error, dev sdb, sector 303
[ 1484.954601] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.954603] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.954606] end_request: I/O error, dev sdb, sector 63
[ 1484.965675] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.965679] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.965683] end_request: I/O error, dev sdb, sector 0
[ 1484.965734] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.965736] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.965739] end_request: I/O error, dev sdb, sector 0
[ 1484.965804] sd 6:0:0:0: [sdb] Unhandled error code
[ 1484.965806] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1484.965809] end_request: I/O error, dev sdb, sector 0
[ 1485.147817] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.147822] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.147826] end_request: I/O error, dev sdb, sector 0
[ 1485.147884] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.147886] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.147890] end_request: I/O error, dev sdb, sector 0
[ 1485.148033] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.148035] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.148038] end_request: I/O error, dev sdb, sector 63
[ 1485.150526] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.150531] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.150535] end_request: I/O error, dev sdb, sector 63
[ 1485.150696] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.150698] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.150701] end_request: I/O error, dev sdb, sector 303
[ 1485.150745] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.150747] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.150750] end_request: I/O error, dev sdb, sector 63
[ 1485.160762] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.160766] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.160770] end_request: I/O error, dev sdb, sector 0
[ 1485.160821] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.160823] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.160826] end_request: I/O error, dev sdb, sector 0
[ 1485.160889] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.160891] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.160894] end_request: I/O error, dev sdb, sector 0
[ 1485.180318] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.180323] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.180327] end_request: I/O error, dev sdb, sector 63
[ 1485.180441] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.180443] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.180446] end_request: I/O error, dev sdb, sector 303
[ 1485.180538] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.180540] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.180543] end_request: I/O error, dev sdb, sector 63
[ 1485.183497] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.183501] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.183505] end_request: I/O error, dev sdb, sector 0
[ 1485.183557] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.183559] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.183562] end_request: I/O error, dev sdb, sector 0
[ 1485.183625] sd 6:0:0:0: [sdb] Unhandled error code
[ 1485.183627] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1485.183630] end_request: I/O error, dev sdb, sector 0
[ 1550.359005] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.359009] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.359013] end_request: I/O error, dev sdb, sector 63
[ 1550.359019] __ratelimit: 662 callbacks suppressed
[ 1550.359023] Buffer I/O error on device sdb1, logical block 0
[ 1550.359025] lost page write due to I/O error on sdb1
[ 1550.359030] Buffer I/O error on device sdb1, logical block 1
[ 1550.359032] lost page write due to I/O error on sdb1
[ 1550.359036] Buffer I/O error on device sdb1, logical block 2
[ 1550.359038] lost page write due to I/O error on sdb1
[ 1550.359041] Buffer I/O error on device sdb1, logical block 3
[ 1550.359043] lost page write due to I/O error on sdb1
[ 1550.359052] Buffer I/O error on device sdb1, logical block 4
[ 1550.359055] lost page write due to I/O error on sdb1
[ 1550.359058] Buffer I/O error on device sdb1, logical block 5
[ 1550.359060] lost page write due to I/O error on sdb1
[ 1550.359063] Buffer I/O error on device sdb1, logical block 6
[ 1550.359065] lost page write due to I/O error on sdb1
[ 1550.359068] Buffer I/O error on device sdb1, logical block 7
[ 1550.359070] lost page write due to I/O error on sdb1
[ 1550.359074] Buffer I/O error on device sdb1, logical block 8
[ 1550.359076] lost page write due to I/O error on sdb1
[ 1550.359079] Buffer I/O error on device sdb1, logical block 9
[ 1550.359081] lost page write due to I/O error on sdb1
[ 1550.359266] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.359269] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.359272] end_request: I/O error, dev sdb, sector 303
[ 1550.359321] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.359323] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.359326] end_request: I/O error, dev sdb, sector 1953519809
[ 1550.359476] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.359478] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.359481] end_request: I/O error, dev sdb, sector 1953520049
[ 1550.369249] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.369254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.369259] end_request: I/O error, dev sdb, sector 63
[ 1550.369366] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.369368] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.369371] end_request: I/O error, dev sdb, sector 303
[ 1550.370118] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.370125] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.370132] end_request: I/O error, dev sdb, sector 0
[ 1550.370300] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.370304] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.370310] end_request: I/O error, dev sdb, sector 0
[ 1550.370392] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.370396] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.370401] end_request: I/O error, dev sdb, sector 63
[ 1550.371728] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.371733] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.371737] end_request: I/O error, dev sdb, sector 63
[ 1550.375272] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.375276] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.375280] end_request: I/O error, dev sdb, sector 0
[ 1550.375331] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.375333] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.375337] end_request: I/O error, dev sdb, sector 0
[ 1550.375399] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.375401] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.375404] end_request: I/O error, dev sdb, sector 0
[ 1550.379571] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.379577] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.379581] end_request: I/O error, dev sdb, sector 63
[ 1550.379731] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.379734] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.379737] end_request: I/O error, dev sdb, sector 303
[ 1550.379776] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.379778] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.379782] end_request: I/O error, dev sdb, sector 63
[ 1550.382777] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.382784] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.382790] end_request: I/O error, dev sdb, sector 0
[ 1550.384650] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.384656] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.384660] end_request: I/O error, dev sdb, sector 0
[ 1550.385930] sd 6:0:0:0: [sdb] Unhandled error code
[ 1550.385933] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1550.385936] end_request: I/O error, dev sdb, sector 0
[ 1785.464817] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.464822] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.464827] end_request: I/O error, dev sdb, sector 0
[ 1785.464831] __ratelimit: 524 callbacks suppressed
[ 1785.464834] Buffer I/O error on device sdb, logical block 0
[ 1785.464838] Buffer I/O error on device sdb, logical block 1
[ 1785.464841] Buffer I/O error on device sdb, logical block 2
[ 1785.464844] Buffer I/O error on device sdb, logical block 3
[ 1785.464890] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.464892] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.464895] end_request: I/O error, dev sdb, sector 0
[ 1785.464898] Buffer I/O error on device sdb, logical block 0
[ 1785.464966] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.464968] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.464971] end_request: I/O error, dev sdb, sector 0
[ 1785.464973] Buffer I/O error on device sdb, logical block 0
[ 1785.465570] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.465573] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.465576] end_request: I/O error, dev sdb, sector 0
[ 1785.465580] Buffer I/O error on device sdb, logical block 0
[ 1785.465621] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.465623] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.465626] end_request: I/O error, dev sdb, sector 0
[ 1785.465629] Buffer I/O error on device sdb, logical block 0
[ 1785.466002] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466004] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466007] end_request: I/O error, dev sdb, sector 0
[ 1785.466010] Buffer I/O error on device sdb, logical block 0
[ 1785.466014] Buffer I/O error on device sdb, logical block 1
[ 1785.466054] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466056] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466059] end_request: I/O error, dev sdb, sector 0
[ 1785.466116] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466119] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466122] end_request: I/O error, dev sdb, sector 0
[ 1785.466167] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466170] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466173] end_request: I/O error, dev sdb, sector 0
[ 1785.466218] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466220] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466223] end_request: I/O error, dev sdb, sector 0
[ 1785.466268] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466270] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466273] end_request: I/O error, dev sdb, sector 0
[ 1785.466318] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466320] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466323] end_request: I/O error, dev sdb, sector 0
[ 1785.466368] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466371] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466374] end_request: I/O error, dev sdb, sector 0
[ 1785.466419] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466421] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466424] end_request: I/O error, dev sdb, sector 0
[ 1785.466469] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466471] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466474] end_request: I/O error, dev sdb, sector 0
[ 1785.466519] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466521] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466524] end_request: I/O error, dev sdb, sector 8
[ 1785.466569] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466571] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466574] end_request: I/O error, dev sdb, sector 8
[ 1785.466619] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466621] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466624] end_request: I/O error, dev sdb, sector 8
[ 1785.466668] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466671] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466674] end_request: I/O error, dev sdb, sector 8
[ 1785.466718] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466720] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466723] end_request: I/O error, dev sdb, sector 8
[ 1785.466768] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466770] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466773] end_request: I/O error, dev sdb, sector 8
[ 1785.466818] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466820] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466823] end_request: I/O error, dev sdb, sector 8
[ 1785.466868] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466870] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466873] end_request: I/O error, dev sdb, sector 8
[ 1785.466918] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466921] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466924] end_request: I/O error, dev sdb, sector 0
[ 1785.466969] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.466971] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.466974] end_request: I/O error, dev sdb, sector 0
[ 1785.467022] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467024] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467027] end_request: I/O error, dev sdb, sector 0
[ 1785.467075] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467078] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467081] end_request: I/O error, dev sdb, sector 1953525160
[ 1785.467129] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467131] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467134] end_request: I/O error, dev sdb, sector 0
[ 1785.467182] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467184] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467187] end_request: I/O error, dev sdb, sector 0
[ 1785.467235] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467237] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467240] end_request: I/O error, dev sdb, sector 0
[ 1785.467288] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467290] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467293] end_request: I/O error, dev sdb, sector 0
[ 1785.467339] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.467341] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.467344] end_request: I/O error, dev sdb, sector 0
[ 1785.471193] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.471198] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.471202] end_request: I/O error, dev sdb, sector 63
[ 1785.471303] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.471306] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.471309] end_request: I/O error, dev sdb, sector 303
[ 1785.471354] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.471356] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.471359] end_request: I/O error, dev sdb, sector 63
[ 1785.474133] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.474139] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.474145] end_request: I/O error, dev sdb, sector 0
[ 1785.474197] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.474200] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.474205] end_request: I/O error, dev sdb, sector 0
[ 1785.474269] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.474273] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.474278] end_request: I/O error, dev sdb, sector 0
[ 1785.519119] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.519125] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.519129] end_request: I/O error, dev sdb, sector 0
[ 1785.519187] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.519189] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.519192] end_request: I/O error, dev sdb, sector 240
[ 1785.519233] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.519235] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.519238] end_request: I/O error, dev sdb, sector 0
[ 1785.523458] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.523464] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.523471] end_request: I/O error, dev sdb, sector 0
[ 1785.523521] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.523525] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.523530] end_request: I/O error, dev sdb, sector 0
[ 1785.523587] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.523590] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.523595] end_request: I/O error, dev sdb, sector 0
[ 1785.528659] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.528665] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.528669] end_request: I/O error, dev sdb, sector 63
[ 1785.528784] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.528786] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.528789] end_request: I/O error, dev sdb, sector 303
[ 1785.531814] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.531819] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.531823] end_request: I/O error, dev sdb, sector 63
[ 1785.540410] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.540414] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.540418] end_request: I/O error, dev sdb, sector 0
[ 1785.540469] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.540472] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.540475] end_request: I/O error, dev sdb, sector 0
[ 1785.540537] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.540539] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.540542] end_request: I/O error, dev sdb, sector 0
[ 1785.546597] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.546602] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.546606] end_request: I/O error, dev sdb, sector 0
[ 1785.546666] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.546669] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.546672] end_request: I/O error, dev sdb, sector 240
[ 1785.546890] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.546892] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.546895] end_request: I/O error, dev sdb, sector 0
[ 1785.550572] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.550579] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.550585] end_request: I/O error, dev sdb, sector 0
[ 1785.550636] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.550639] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.550644] end_request: I/O error, dev sdb, sector 0
[ 1785.550702] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.550706] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.550710] end_request: I/O error, dev sdb, sector 0
[ 1785.561198] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.561204] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.561208] end_request: I/O error, dev sdb, sector 0
[ 1785.561267] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.561269] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.561272] end_request: I/O error, dev sdb, sector 240
[ 1785.563202] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.563206] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.563209] end_request: I/O error, dev sdb, sector 0
[ 1785.567043] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.567048] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.567052] end_request: I/O error, dev sdb, sector 0
[ 1785.567108] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.567111] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.567113] end_request: I/O error, dev sdb, sector 0
[ 1785.567172] sd 6:0:0:0: [sdb] Unhandled error code
[ 1785.567174] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1785.567177] end_request: I/O error, dev sdb, sector 0

```

Please help

---

### Post by teward on 2009-11-08
oh crap, an I/O error.

This happened to a flash drive of mine... nothing can read it.  If it's a true I/O error on the HDD, then it means your HDD is screwed up beyond repair.  I have tried multiple ways to repair this issue on my flash drive, but to no avail.  IT DIED.  And I tried it on 3 different computers.  It just died.

If the drive isn't dead, though, all those I/O errors mean that the drive isn't able to communicate with your computer.  Might be your computer, though, and it just can't read it due to some issue with your hardware (maybe).

---

