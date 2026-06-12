---
title: "Partition Misalignment by 1024 bytes"
date: 2015-02-10
forum: Hardware
---

### Post by alphaamanitin on 2015-02-10
Hello,

My Disk Utility says that my extended partition is misaligned by 1024 bytes.  I have in /dev/sda2 999gb with /dev/sda5/ (ext4, 35 gb) and /dev/sda6/ (ext4, 964 gb) inside it.  With a swap partition at the end, /dev/sda1.  

I had a motherboard death on this thing and bought a new motherboard after several months.  I never had this message before and am not sure when it appeared after the MOBO replacement.  Now, what I find really odd, is that now my supposed SWAP partition (/dev/sda1) is bootable?! What the heck is with that. 

If some one can tell me how to neatly post the output of the boot info script I will do so.  It was a mess when I just tried it.


I just cannot afford to reformat the drive and don't have the time to back up all the data on it in a way that wouldn't result in the same error (cloning the drive).  I am wrapping up a PhD and there is no way in hell I am going to bother with this unless I absolutely have to, but I am worried about it.  Should I be?

Thanks,

AlphaA

---

### Post by weatherman2 on 2015-02-11
What's the output of these commands:

```
sudo fdisk -lu
```
```
sudo parted -l
```

FYI, your Extended partition is not a "real" partition - it's a container partition, inside which other partitions (called "logical" partitions) exist.  The question is, are your logical partitions aligned?  Are your primary partitions aligned?

Partition alignment only matters if your drive is an "advanced format" type of drive (common within the last 3-4 years).  If a real partition isn't aligned to the right partition boundary on an advanced format drive, you could suffer performance loss.  

There are alignment tools that will re-align your existing partitions - available from the disk manufacturers.  But these would be slow if your partitions have a lot of data - because as I understand it each byte must be moved as part of the alignment.  A nearly empty partition would be aligned quickly because there's not much data to align.

But if only your extended partition is showing misaligned, it's probably a fake error and not meaningful.

---

### Post by alphaamanitin on 2015-02-11
Hello,

Yeah, I know the extended partition is just a holder, I just wanted to give you the picture of the whole setup.  In Disk Utility I'm pretty sure all the actual partitions were fine and the warning was on the extended partition.  However, why in the hell is the boot partitions on the end where swap normally gets created (or at least visually depicted) and the Disk Utility says that partition is swap and linux/solarix format?

I'll double check all of this and update this post including the bootinfo script output, but I am on a different computer right now.

Thanks,

AlphaA

---

### Post by oldfred on 2015-02-11
The first part of this is the bootinfoscript.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If using bootinfoscript use this one and post in code tags or # in Go Advanced editor:


 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by alphaamanitin on 2015-02-16
> **oldfred said:**
> [...]
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If I didn't say so earlier, I did have to replace the motherboard on this computer.  Oddly enough, the SD card reader on the old motherboard and on this one appears to be dead.  Not sure if this could be related in anyway, but I thought I would mention it.  I do mean dead.  Nothing happens when you put a SD card into it and the SD card reader does not appear in any of the locations I have been told to check from within Xubuntu, and it does not appear in the BIOS (or rather efi) of the motherboard as well.

Okay, I did the boot info stuff and here it is.  Link: [http://paste.ubuntu.com/10259560/](http://paste.ubuntu.com/10259560/)

```


[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
   2
   3
   4
   5
   6
   7
   8
   9
  10
  11
  12
  13
  14
  15
  16
  17
  18
  19
  20
  21
  22
  23
  24
  25
  26
  27
  28
  29
  30
  31
  32
  33
  34
  35
  36
  37
  38
  39
  40
  41
  42
  43
  44
  45
  46
  47
  48
  49
  50
  51
  52
  53
  54
  55
  56
  57
  58
  59
  60
  61
  62
  63
  64
  65
  66
  67
  68
  69
  70
  71
  72
  73
  74
  75
  76
  77
  78
  79
  80
  81
  82
  83
  84
  85
  86
  87
  88
  89
  90
  91
  92
  93
  94
  95
  96
  97
  98
  99
 100
 101
 102
 103
 104
 105
 106
 107
 108
 109
 110
 111
 112
 113
 114
 115
 116
 117
 118
 119
 120
 121
 122
 123
 124
 125
 126
 127
 128
 129
 130
 131
 132
 133
 134
 135
 136
 137
 138
 139
 140
 141
 142
 143
 144
 145
 146
 147
 148
 149
 150
 151
 152
 153
 154
 155
 156
 157
 158
 159
 160
 161
 162
 163
 164
 165
 166
 167
 168
 169
 170
 171
 172
 173
 174
 175
 176
 177
 178
 179
 180
 181
 182
 183
 184
 185
 186
 187
 188
 189
 190
 191
 192
 193
 194
 195
 196
 197
 198
 199
 200
 201
 202
 203
 204
 205
 206
 207
 208
 209
 210
 211
 212
 213
 214
 215
 216
 217
 218
 219
 220
 221
 222
 223
 224
 225
 226
 227
 228
 229
 230
 231
 232
 233
 234
 235
 236
 237
 238
 239
 240
 241
 242
 243
 244
 245
 246
 247
 248
 249
 250
 251
 252
 253
 254
 255
 256
 257
 258
 259
 260
 261
 262
 263
 264
 265
 266
 267
 268
 269
 270
 271
 272
 273
 274
 275
 276
 277
 278
 279
 280
 281
 282
 283
 284
 285
 286
 287
 288
 289
 290
 291
 292
 293
 294
 295
 296
 297
 298
 299
 300
 301
 302
 303
 304
 305
 306
 307
 308
 309
 310
 311
 312
 313
 314
 315
 316
 317
 318
 319
 320
 321
 322
 323
 324
 325
 326
 327
 328
 329
 330
 331
 332
 333
 334
 335
 336
 337
 338
 339
 340
 341
 342
 343
 344
 345
 346
 347
 348
 349
 350
 351
 352
 353
 354
 355
 356
 357
 358
 359
 360
 361
 362
 363
 364
 365
 366
 367
 368
 369
 370
 371
 372
 373
 374
 375
 376
 377
 378
 379
 380
 381
 382
 383
 384
 385
 386
 387
 388
 389
 390
 391
 392
 393
 394
 395
 396
 397
 398
 399
 400
 401
 402
 403
 404
 405
 406
 407
 408
 409
 410
 411
 412
 413
 414
 415
 416
 417
 418
 419
 420
 421
 422
 423
 424
 425
 426
 427
 428
 429
 430
 431
 432
 433
 434
 435
 436
 437
 438
 439
 440
 441
 442
 443
 444
 445
 446
 447
 448
 449
 450
 451
 452
 453
 454
 455
 456
 457
 458
 459
 460
 461
 462
 463
 464
 465
 466
 467
 468
 469
 470
 471
 472
 473
 474
 475
 476
 477
 478
 479
 480
 481
 482
 483
 484
 485
 486
 487
 488
 489
 490
 491
 492
 493
 494
 495
 496
 497
 498
 499
 500
 501
 502
 503
 504
 505
 506
 507
 508
 509
 510
 511
 512
 513
 514
 515
 516
 517
 518
 519
 520
 521
 522
 523
 524
 525
 526
 527
 528
 529
 530
 531
 532
 533
 534
 535
 536
 537
 538
 539
 540
 541
 542
 543
 544
 545
 546
 547
 548
 549
 550
 551
 552
 553
 554
 555
 556
 557
 558
 559
 560
 561
 562
 563
 564
 565
 566
 567
 568
 569
 570
 571
 572
 573
 574
 575
 576
 577
 578
 579
 580
 581
 582
 583
 584
 585
 586
 587
 588
 589
 590
 591
 592
 593
 594
 595
 596
 597
 598
 599
 600
 601
 602
 603
 604
 605
 606
 607
 608
 609
 610
 611
 612
 613
 614
 615
 616
 617
 618
 619
 620
 621
 622
 623
 624
 625
 626
 627
 628
 629
 630
 631
 632
 633
 634
 635
 636
 637
 638
 639
 640
 641
 642
 643
 644
 645
 646
 647
 648
 649
 650
 651
 652
 653
 654
 655
 656
 657
 658
 659
 660
 661
 662
 663
 664
 665
 666
 667
 668
 669
 670
 671
 672
 673
 674
 675
 676
 677
 678
 679
 680
 681
 682
 683
 684
 685
 686
 687
 688
 689
 690
 691
 692
 693
 694
 695
 696
 697
 698
 699
 700
 701
 702
 703
 704
 705
 706
 707
 708
 709
 710
 711
 712
 713
 714
 715
 716
 717
 718
 719
 720
 721
 722
 723
 724
 725
 726
 727
 728
 729
 730
 731
 732
 733
 734
 735
 736
 737
 738
 739
 740
 741
 742
 743
 744
 745
 746
 747
 748
 749
 750
 751
 752
 753
 754
 755
 756
 757
 758
 759
 760
 761
 762
 763
 764
 765
 766
 767
 768
 769
 770
 771
 772
 773
 774
 775
 776
 777
 778
 779
 780
 781
 782
 783
 784
 785
 786
 787
 788
 789
 790
 791
 792
 793
 794
 795
 796
 797
 798
 799
 800
 801
 802
 803
 804
 805
 806
 807
 808
 809
 810
 811
 812
 813
 814
 815
 816
 817
 818
 819
 820
 821
 822
 823
 824
 825
 826
 827
 828
 829
 830
 831
 832
 833
 834
 835
 836
 837
 838
 839
 840
 841
 842
 843
 844
 845
 846
 847
 848
 849
 850
 851
 852
 853
 854
 855
 856
 857
 858
 859
 860
 861
 862
 863
 864
 865
 866
 867
 868
 869
 870
 871
 872
 873
 874
 875
 876
 877
 878
 879
 880
 881
 882
 883
 884
 885
 886
 887
 888
 889
 890
 891
 892
 893
 894
 895
 896
 897
 898
 899
 900
 901
 902
 903
 904
 905
 906
 907
 908
 909
 910
 911
 912
 913
 914
 915
 916
 917
 918
 919
 920
 921
 922
 923
 924
 925
 926
 927
 928
 929
 930
 931
 932
 933
 934
 935
 936
 937
 938
 939
 940
 941
 942
 943
 944
 945
 946
 947
 948
 949
 950
 951
 952
 953
 954
 955
 956
 957
 958
 959
 960
 961
 962
 963
 964
 965
 966
 967
 968
 969
 970
 971
 972
 973
 974
 975
 976
 977
 978
 979
 980
 981
 982
 983
 984
 985
 986
 987
 988
 989
 990
 991
 992
 993
 994
 995
 996
 997
 998
 999
1000
1001
1002
1003
1004
1005
1006
1007
1008
1009
1010
1011
1012
1013
1014
1015
1016
1017
1018
1019
1020
1021
1022
1023
1024
1025
1026
1027
1028
1029
1030
1031
1032
1033
1034
1035
1036
1037
1038
1039
1040
1041
1042
1043
1044
1045
1046
1047
1048
1049
1050
1051
1052
1053
1054
1055
1056
1057
1058
1059
1060
1061
1062
1063
1064
1065
1066
1067
1068
1069
1070
1071
1072
1073
1074
1075
1076
1077
1078
1079
1080
1081
1082
1083
1084
1085
1086
1087
1088
1089
1090
1091
1092
1093
1094
1095
1096
1097
1098
1099
1100
1101
1102
1103
1104
1105
1106
1107
1108
1109
1110
1111
1112
1113
1114
1115
1116
1117
1118
1119
1120
1121
1122
1123
1124
1125
1126
1127
1128
1129
1130
1131
1132
1133
1134
1135
1136
1137
1138
1139
1140
1141
1142
1143
1144
1145
1146
1147
1148
1149
1150
1151
1152
1153
1154
1155
1156
1157
1158
1159
1160
1161
1162
1163
1164
1165
1166
1167
1168
1169
1170
1171
1172
1173
1174
1175
1176
1177
1178
1179
1180
1181
1182
1183
1184
1185
1186
1187
1188
1189
1190
1191
1192
1193
1194
1195
1196
1197
1198
1199
1200
1201
1202
1203
1204
1205
1206
1207
1208
1209
1210
1211
1212
1213
1214
1215
1216
1217
1218
1219
1220
1221
1222
1223
1224
1225
1226
1227
1228
1229
1230
1231
1232
1233
1234
1235
1236
1237
1238
1239
1240
1241
1242
1243
1244
1245
1246
1247
1248
1249
1250
1251
1252
1253
1254
1255
1256
1257
1258
1259
1260
1261
1262
1263
1264
1265
1266
1267
1268
1269
1270
1271
1272
1273
1274
1275
1276
1277
1278
1279
1280
1281
1282
1283[/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 9Feb2015[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos5[COLOR=#666666])[/COLOR]/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *  1,951,571,968 1,953,523,711     1,951,744  82 Linux swap / Solaris
/dev/sda2               2,046 1,951,571,967 1,951,569,922   5 Extended
/dev/sda5               2,048    68,360,191    68,358,144  83 Linux
/dev/sda6          68,362,240 1,951,571,967 1,883,209,728  83 Linux


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 81bfb47e-c501-4cf0-95a7-de2742b8b74b   swap       
/dev/sda5        2438eb3f-c5a0-4481-b3ca-0467f425075a   ext4       
/dev/sda6        870a6b7b-586b-4795-add0-5afe82a30f2b   [COLOR=#B8860B]ext4[/COLOR]       

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -l /dev/disk/by-id"[/COLOR] output: [COLOR=#666666]======================[/COLOR]

total 0
lrwxrwxrwx 1 root root  9 Feb 16 13:12 ata-TOSHIBA_MQ01ABD100_X2NLFYVGS -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 16 11:58 ata-TOSHIBA_MQ01ABD100_X2NLFYVGS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 16 11:58 ata-TOSHIBA_MQ01ABD100_X2NLFYVGS-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 16 11:58 ata-TOSHIBA_MQ01ABD100_X2NLFYVGS-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 16 11:58 ata-TOSHIBA_MQ01ABD100_X2NLFYVGS-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Feb 16 11:58 ata-TSSTcorp_CDDVDW_SN-208AB_R8JT6GHC800C3D -> ../../sr0
lrwxrwxrwx 1 root root 10 Feb 16 13:12 dm-name-cryptswap1 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Feb 16 13:12 dm-uuid-CRYPT-PLAIN-cryptswap1_unformatted -> ../../dm-0
lrwxrwxrwx 1 root root  9 Feb 16 13:12 scsi-SATA_TOSHIBA_MQ01ABD_X2NLFYVGS -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 16 11:58 scsi-SATA_TOSHIBA_MQ01ABD_X2NLFYVGS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 16 11:58 scsi-SATA_TOSHIBA_MQ01ABD_X2NLFYVGS-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 16 11:58 scsi-SATA_TOSHIBA_MQ01ABD_X2NLFYVGS-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 16 11:58 scsi-SATA_TOSHIBA_MQ01ABD_X2NLFYVGS-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Feb 16 13:12 wwn-0x5000039457186186 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 16 11:58 wwn-0x5000039457186186-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 16 11:58 wwn-0x5000039457186186-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 16 11:58 wwn-0x5000039457186186-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 16 11:58 wwn-0x5000039457186186-part6 -> ../../sda6

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -R /dev/mapper/"[/COLOR] output: [COLOR=#666666]=========================[/COLOR]

/dev/mapper:
control
[COLOR=#B8860B]cryptswap1[/COLOR]

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/sda6        /home                    ext4       [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda5/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
[COLOR=#666666]}[/COLOR]

insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
[COLOR=#AA22FF]**if **[/COLOR]loadfont /usr/share/grub/unicode.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
  search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR]/boot/grub/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]-1
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_timeout_style[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]hidden
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]0
  [COLOR=#008800]*# Fallback hidden-timeout code in case the timeout_style feature is*[/COLOR]
  [COLOR=#008800]*# unavailable.*[/COLOR]
  [COLOR=#AA22FF]**elif **[/COLOR]sleep --interruptible 0 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]0
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${1}"[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${1}"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${linux_gfx_mode}"[/COLOR] ![COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"text"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]load_video; [COLOR=#AA22FF]**fi**[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-76-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-76-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-76-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-76-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-76-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-76-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-76-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]"Previous Linux versions"[/COLOR] [COLOR=#666666]{[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-75-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-75-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-75-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-75-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-75-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-75-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-75-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-74-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-74-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-74-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-74-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-74-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-74-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-74-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-72-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-72-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-72-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-72-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-72-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-72-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-72-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-70-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-70-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-70-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-70-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-70-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-70-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-70-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-69-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-69-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-69-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-69-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-69-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-69-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-69-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-60-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-60-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-60-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-60-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-60-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-60-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-60-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-59-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-59-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-59-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-59-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-59-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-59-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-59-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-58-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-58-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-58-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-58-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-58-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-58-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-58-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-57-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-57-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-57-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-57-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-57-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-57-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-57-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-56-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-56-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-56-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-56-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-56-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-56-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-56-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-55-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-55-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-55-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-55-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-55-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-54-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-54-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-54-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-54-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-54-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-54-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-54-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-53-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-53-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-53-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-53-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-53-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-53-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-53-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-52-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-52-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-52-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-52-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-52-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-52-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-52-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-51-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-51-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-51-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-51-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-51-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-51-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-51-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-49-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-49-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-49-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-49-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-49-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-49-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-49-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-48-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-48-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-48-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-48-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-48-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-48-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-48-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-45-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-45-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-45-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-45-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-45-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-45-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-45-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-44-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-44-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-44-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-44-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-44-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-44-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-44-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-43-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-43-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-43-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-43-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-43-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-43-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-43-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-41-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-41-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-41-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-41-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-41-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-41-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-41-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-40-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-40-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-40-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-40-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-40-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-40-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-39-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-39-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-39-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-39-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-39-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-39-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-39-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-38-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-38-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-38-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-38-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-38-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-38-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-37-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-37-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-37-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-37-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-37-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-37-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-36-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-36-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-36-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-36-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-36-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-36-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-35-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-35-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-35-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-35-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-35-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-35-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-34-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-34-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-34-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-34-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-34-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-34-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-29-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux    /boot/vmlinuz-3.2.0-29-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-29-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-29-generic ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-29-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-29-generic
[COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_memtest86+ ###*[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+)"[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux16    /boot/memtest86+.bin
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+, serial console 115200)"[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos5)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 2438eb3f-c5a0-4481-b3ca-0467f425075a
    linux16    /boot/memtest86+.bin [COLOR=#B8860B]console[/COLOR][COLOR=#666666]=[/COLOR]ttyS0,115200n8
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_memtest86+ ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_uefi-firmware ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sda5/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=#008800]*# / was on /dev/sda5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# /home was on /dev/sda6 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]870a6b7b-586b-4795-add0-5afe82a30f2b /home           ext4    defaults        0       2
[COLOR=#008800]*# swap was on /dev/sda1 during installation*[/COLOR]
[COLOR=#008800]*#UUID=822db774-3786-4257-9cf6-362c42ad6ab1 none            swap    sw              0       0*[/COLOR]
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

[COLOR=#666666]======================[/COLOR] sda5/boot/extlinux/extlinux.conf: [COLOR=#666666]=======================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*## /boot/extlinux/extlinux.conf*[/COLOR]
[COLOR=#008800]*##*[/COLOR]
[COLOR=#008800]*## IMPORTANT WARNING*[/COLOR]
[COLOR=#008800]*##*[/COLOR]
[COLOR=#008800]*## The configuration of this file is generated automatically.*[/COLOR]
[COLOR=#008800]*## Do not edit this file manually, use: extlinux-update*[/COLOR]


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda5: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

   4.952178955 [COLOR=#666666]=[/COLOR] 5.317361664    boot/grub/grub.cfg                             1
   4.708042145 [COLOR=#666666]=[/COLOR] 5.055221760    boot/grub/core.img                             1
   4.278175354 [COLOR=#666666]=[/COLOR] 4.593655808    boot/vmlinuz-3.2.0-29-generic                  1
   1.267322540 [COLOR=#666666]=[/COLOR] 1.360777216    boot/vmlinuz-3.2.0-34-generic                  2
   2.739978790 [COLOR=#666666]=[/COLOR] 2.942029824    boot/vmlinuz-3.2.0-35-generic                  2
   3.540763855 [COLOR=#666666]=[/COLOR] 3.801866240    boot/vmlinuz-3.2.0-36-generic                  2
   2.470451355 [COLOR=#666666]=[/COLOR] 2.652626944    boot/vmlinuz-3.2.0-37-generic                  1
  17.727539062 [COLOR=#666666]=[/COLOR] 19.034800128   boot/vmlinuz-3.2.0-38-generic                  2
  17.465820312 [COLOR=#666666]=[/COLOR] 18.753781760   boot/vmlinuz-3.2.0-39-generic                  2
  16.559570312 [COLOR=#666666]=[/COLOR] 17.780703232   boot/vmlinuz-3.2.0-40-generic                  2
   4.657955170 [COLOR=#666666]=[/COLOR] 5.001441280    boot/vmlinuz-3.2.0-41-generic                  1
  17.177486420 [COLOR=#666666]=[/COLOR] 18.444185600   boot/vmlinuz-3.2.0-43-generic                  2
   5.232173920 [COLOR=#666666]=[/COLOR] 5.618003968    boot/vmlinuz-3.2.0-44-generic                  2
  19.376705170 [COLOR=#666666]=[/COLOR] 20.805578752   boot/vmlinuz-3.2.0-45-generic                  2
   0.888427734 [COLOR=#666666]=[/COLOR] 0.953942016    boot/vmlinuz-3.2.0-48-generic                  2
  18.825927734 [COLOR=#666666]=[/COLOR] 20.214185984   boot/vmlinuz-3.2.0-49-generic                  2
  20.693115234 [COLOR=#666666]=[/COLOR] 22.219063296   boot/vmlinuz-3.2.0-51-generic                  2
   8.603271484 [COLOR=#666666]=[/COLOR] 9.237692416    boot/vmlinuz-3.2.0-52-generic                  1
  21.724365234 [COLOR=#666666]=[/COLOR] 23.326359552   boot/vmlinuz-3.2.0-53-generic                  1
  20.575927734 [COLOR=#666666]=[/COLOR] 22.093234176   boot/vmlinuz-3.2.0-54-generic                  2
   3.802494049 [COLOR=#666666]=[/COLOR] 4.082896896    boot/vmlinuz-3.2.0-55-generic                  1
  20.806400299 [COLOR=#666666]=[/COLOR] 22.340702208   boot/vmlinuz-3.2.0-56-generic                  2
   5.477539062 [COLOR=#666666]=[/COLOR] 5.881462784    boot/vmlinuz-3.2.0-57-generic                  2
  23.818119049 [COLOR=#666666]=[/COLOR] 25.574510592   boot/vmlinuz-3.2.0-58-generic                  2
  23.751712799 [COLOR=#666666]=[/COLOR] 25.503207424   boot/vmlinuz-3.2.0-59-generic                  2
   1.298587799 [COLOR=#666666]=[/COLOR] 1.394348032    boot/vmlinuz-3.2.0-60-generic                  2
  23.794685364 [COLOR=#666666]=[/COLOR] 25.549348864   boot/vmlinuz-3.2.0-69-generic                  1
  27.310310364 [COLOR=#666666]=[/COLOR] 29.324222464   boot/vmlinuz-3.2.0-70-generic                  2
  30.626720428 [COLOR=#666666]=[/COLOR] 32.885190656   boot/vmlinuz-3.2.0-72-generic                  1
  24.450939178 [COLOR=#666666]=[/COLOR] 26.253996032   boot/vmlinuz-3.2.0-74-generic                  2
   3.485351562 [COLOR=#666666]=[/COLOR] 3.742367744    boot/vmlinuz-3.2.0-75-generic                  2
  23.333751678 [COLOR=#666666]=[/COLOR] 25.054425088   boot/vmlinuz-3.2.0-76-generic                  1
  23.333751678 [COLOR=#666666]=[/COLOR] 25.054425088   vmlinuz                                        1
   3.485351562 [COLOR=#666666]=[/COLOR] 3.742367744    vmlinuz.old                                    2
   1.505352020 [COLOR=#666666]=[/COLOR] 1.616359424    boot/initrd.img-3.2.0-29-generic               2
  14.745185852 [COLOR=#666666]=[/COLOR] 15.832522752   boot/initrd.img-3.2.0-34-generic               2
   2.046707153 [COLOR=#666666]=[/COLOR] 2.197635072    boot/initrd.img-3.2.0-35-generic               2
   2.512866974 [COLOR=#666666]=[/COLOR] 2.698170368    boot/initrd.img-3.2.0-36-generic               3
   3.766277313 [COLOR=#666666]=[/COLOR] 4.044009472    boot/initrd.img-3.2.0-37-generic               3
  19.036613464 [COLOR=#666666]=[/COLOR] 20.440408064   boot/initrd.img-3.2.0-38-generic               2
  17.280162811 [COLOR=#666666]=[/COLOR] 18.554433536   boot/initrd.img-3.2.0-39-generic               3
  19.906177521 [COLOR=#666666]=[/COLOR] 21.374095360   boot/initrd.img-3.2.0-40-generic               3
   5.226074219 [COLOR=#666666]=[/COLOR] 5.611454464    boot/initrd.img-3.2.0-41-generic               2
  20.708534241 [COLOR=#666666]=[/COLOR] 22.235619328   boot/initrd.img-3.2.0-43-generic               2
  20.899414062 [COLOR=#666666]=[/COLOR] 22.440574976   boot/initrd.img-3.2.0-44-generic               3
  21.005405426 [COLOR=#666666]=[/COLOR] 22.554382336   boot/initrd.img-3.2.0-45-generic               2
   2.078006744 [COLOR=#666666]=[/COLOR] 2.231242752    boot/initrd.img-3.2.0-48-generic               2
  28.896030426 [COLOR=#666666]=[/COLOR] 31.026876416   boot/initrd.img-3.2.0-49-generic               1
   8.630409241 [COLOR=#666666]=[/COLOR] 9.266831360    boot/initrd.img-3.2.0-51-generic               2
  21.680603027 [COLOR=#666666]=[/COLOR] 23.279370240   boot/initrd.img-3.2.0-52-generic               2
  22.989784241 [COLOR=#666666]=[/COLOR] 24.685092864   boot/initrd.img-3.2.0-53-generic               2
  23.716346741 [COLOR=#666666]=[/COLOR] 25.465233408   boot/initrd.img-3.2.0-54-generic               1
   3.896034241 [COLOR=#666666]=[/COLOR] 4.183334912    boot/initrd.img-3.2.0-55-generic               3
   2.082561493 [COLOR=#666666]=[/COLOR] 2.236133376    boot/initrd.img-3.2.0-56-generic               2
   6.510120392 [COLOR=#666666]=[/COLOR] 6.990188544    boot/initrd.img-3.2.0-57-generic               3
  24.653877258 [COLOR=#666666]=[/COLOR] 26.471899136   boot/initrd.img-3.2.0-58-generic               2
  25.012550354 [COLOR=#666666]=[/COLOR] 26.857021440   boot/initrd.img-3.2.0-59-generic               2
  26.899414062 [COLOR=#666666]=[/COLOR] 28.883025920   boot/initrd.img-3.2.0-60-generic               2
  24.895938873 [COLOR=#666666]=[/COLOR] 26.731810816   boot/initrd.img-3.2.0-69-generic               2
  29.888248444 [COLOR=#666666]=[/COLOR] 32.092262400   boot/initrd.img-3.2.0-70-generic               1
  24.095886230 [COLOR=#666666]=[/COLOR] 25.872760832   boot/initrd.img-3.2.0-72-generic               3
  27.674400330 [COLOR=#666666]=[/COLOR] 29.715161088   boot/initrd.img-3.2.0-74-generic               3
   6.091373444 [COLOR=#666666]=[/COLOR] 6.540562432    boot/initrd.img-3.2.0-75-generic               3
  27.594081879 [COLOR=#666666]=[/COLOR] 29.628919808   boot/initrd.img-3.2.0-76-generic               3
  27.594081879 [COLOR=#666666]=[/COLOR] 29.628919808   initrd.img                                     3
   6.091373444 [COLOR=#666666]=[/COLOR] 6.540562432    initrd.img.old                                 [COLOR=#B8860B]3[/COLOR]

[COLOR=#666666]=================[/COLOR] sda5: Location of files loaded by Syslinux: [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

   4.226451874 [COLOR=#666666]=[/COLOR] 4.538118144    boot/extlinux/extlinux.conf                    1
  30.535850525 [COLOR=#666666]=[/COLOR] 32.787619840   boot/extlinux/chain.c32                        [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]==============[/COLOR] sda5: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 boot/extlinux/chain.c32            :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]


ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-info 2015-02-16__13h12 [COLOR=#666666]===================[/COLOR]
boot-info version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 4ppa33
boot-info is executed in installed-session [COLOR=#666666]([/COLOR]Ubuntu 12.04.5 LTS, precise, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/boot/vmlinuz-3.2.0-76-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2438eb3f-c5a0-4481-b3ca-0467f425075a ro quiet splash vt.handoff[COLOR=#666666]=[/COLOR]7
Disk /dev/mapper/cryptswap1 doesn[COLOR=#BB4444]'t contain a valid partition table[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda5:The OS now in use - Ubuntu 12.04.5 LTS CurrentSession:linux[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/sda5: UUID="2438eb3f-c5a0-4481-b3ca-0467f425075a" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sda6: UUID="870a6b7b-586b-4795-add0-5afe82a30f2b" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/mapper/cryptswap1: UUID="81bfb47e-c501-4cf0-95a7-de2742b8b74b" TYPE="swap"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Warning: extended partition does not start at a cylinder boundary.[/COLOR]
[COLOR=#BB4444]DOS and Linux will interpret the contents differently.[/COLOR]

[COLOR=#BB4444]=================== /etc/grub.d/ :[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root      4096 Oct 27 15:52 grub.d[/COLOR]
[COLOR=#BB4444]total 60[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7806 Dec  6  2013 00_header[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7877 Dec  6  2013 10_linux[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6449 Dec  6  2013 20_linux_xen[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6675 Dec  6  2013 30_os-prober[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 1388 Dec 10  2012 30_uefi-firmware[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  214 May 17  2012 40_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   95 May 17  2012 41_custom[/COLOR]
[COLOR=#BB4444]-rw-r--r-- 1 root root  483 May 17  2012 README[/COLOR]




[COLOR=#BB4444]=================== /etc/default/grub :[/COLOR]

[COLOR=#BB4444]# If you change this file, run '[/COLOR]update-grub[COLOR=#BB4444]' afterwards to update[/COLOR]
[COLOR=#BB4444]# /boot/grub/grub.cfg.[/COLOR]
[COLOR=#BB4444]# For full documentation of the options in this file, see:[/COLOR]
[COLOR=#BB4444]#   info -f grub -n '[/COLOR]Simple configuration[COLOR=#BB4444]'[/COLOR]

[COLOR=#BB4444]GRUB_DEFAULT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT_QUIET=true[/COLOR]
[COLOR=#BB4444]GRUB_TIMEOUT=10[/COLOR]
[COLOR=#BB4444]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX=""[/COLOR]

[COLOR=#BB4444]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR]
[COLOR=#BB4444]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR]
[COLOR=#BB4444]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR]
[COLOR=#BB4444]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/COLOR]

[COLOR=#BB4444]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR]
[COLOR=#BB4444]#GRUB_TERMINAL=console[/COLOR]

[COLOR=#BB4444]# The resolution used on graphical terminal[/COLOR]
[COLOR=#BB4444]# note that you can use only modes which your graphic card supports via VBE[/COLOR]
[COLOR=#BB4444]# you can see them in real GRUB with the command `vbeinfo'[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]




[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2046 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA TOSHIBA MQ01ABD1 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 1000GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
2      1048kB  999GB   999GB   extended
5      1049kB  35.0GB  35.0GB  logical   ext4
6      35.0GB  999GB   964GB   logical   ext4
1      999GB   1000GB  999MB   primary                boot


Model: Linux device-mapper [COLOR=#666666]([/COLOR]crypt[COLOR=#666666])[/COLOR] [COLOR=#666666]([/COLOR]dm[COLOR=#666666])[/COLOR]
Disk /dev/mapper/cryptswap1: 999MB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system     Flags
1      0.00B  999MB  999MB  linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA TOSHIBA MQ01ABD1;
2:1048kB:999GB:999GB:::;
5:1049kB:35.0GB:35.0GB:ext4::;
6:35.0GB:999GB:964GB:ext4::;
1:999GB:1000GB:999MB:::boot;

BYT;
/dev/mapper/cryptswap1:999MB:dm:512:4096:loop:Linux device-mapper [COLOR=#666666]([/COLOR]crypt[COLOR=#666666])[/COLOR];
1:0.00B:999MB:999MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

[COLOR=#666666]===================[/COLOR] lsblk:
KNAME TYPE  FSTYPE   SIZE LABEL MODEL       UUID
sda   disk         931.5G       TOSHIBA MQ0
sda1  part           953M
dm-0  crypt swap     953M                   81bfb47e-c501-4cf0-95a7-de2742b8b74b
sda2  part             1K
sda5  part  ext4    32.6G                   2438eb3f-c5a0-4481-b3ca-0467f425075a
sda6  part  ext4     898G                   870a6b7b-586b-4795-add0-5afe82a30f2b
sr0   rom           1024M       CDDVDW SN-2

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0
dm-0     1  0  0 running [COLOR=#666666][[/COLOR]SWAP[COLOR=#666666]][/COLOR]
sda2     1  0  0
sda5     1  0  0         /
sda6     1  0  0         /home
sr0      1  0  1 [COLOR=#B8860B]running[/COLOR]


[COLOR=#666666]===================[/COLOR] mount:
/dev/sda5 on / [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
/dev/sda6 on /home [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
binfmt_misc on /proc/sys/fs/binfmt_misc [COLOR=#AA22FF]type [/COLOR]binfmt_misc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
/home/user/.Private on /home/user [COLOR=#AA22FF]type [/COLOR]ecryptfs [COLOR=#666666]([/COLOR]ecryptfs_check_dev_ruid,ecryptfs_cipher[COLOR=#666666]=[/COLOR]aes,ecryptfs_key_bytes[COLOR=#666666]=[/COLOR]16,ecryptfs_unlink_sigs,ecryptfs_sig[COLOR=#666666]=[/COLOR]b43c4bba2577582f,ecryptfs_fnek_sig[COLOR=#666666]=[/COLOR]de1a3b54156366b3[COLOR=#666666])[/COLOR]
gvfs-fuse-daemon on /home/user/.gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfs-fuse-daemon [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]user[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/dm-0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dm-0 dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 v4l vboxdrv vboxdrvu vboxnetctl vboxusb vga_arbiter video0 zero
ls /dev/mapper:  control cryptswap1
ls: cannot access : No such file or directory
Disk /dev/mapper/cryptswap1 doesn't contain a valid partition [COLOR=#B8860B]table[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem          Type      Size  Used Avail Use% Mounted on
/dev/sda5           ext4       33G   17G   14G  55% /
udev                devtmpfs  7.8G   12K  7.8G   1% /dev
tmpfs               tmpfs     1.6G  896K  1.6G   1% /run
none                tmpfs     5.0M     0  5.0M   0% /run/lock
none                tmpfs     7.8G   27M  7.8G   1% /run/shm
/dev/sda6           ext4      884G  618G  222G  74% /home
/home/user/.Private ecryptfs  884G  618G  222G  74% /home/user

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: 0x0004b91b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *  1951571968  1953523711      975872   82  Linux swap / Solaris
/dev/sda2            2046  1951571967   975784961    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5            2048    68360191    34179072   83  Linux
/dev/sda6        68362240  1951571967   941604864   83  Linux

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 999 MB, 999292928 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1951744 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: [COLOR=#B8860B]0x4dc0fdb2[/COLOR]




[COLOR=#666666]===================[/COLOR] Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


[COLOR=#666666]===================[/COLOR] User settings
The settings chosen by the user will not act on the boot.[/COLOR][/TD]
[/TR]
[/TABLE]

```

Thanks,

AlphaA

---

### Post by oldfred on 2015-02-16
The issue may just be that your configuration of swap as sda1, but extended partition as first partition on drive starting before 2048. But the first partition you write to sda5, does start at the standard starting position of 2048. I do not think you have an issue.

But you do have too many kernels. Time to houseclean. I prefer synaptic.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

 Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Other housekeeping:

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by alphaamanitin on 2015-02-16
Hello,


Thanks.  Too many kernals, is that why my boot time has been seemingly getting longer and longer?  I don't know how the drive got configured like that.  I just made a separate partition for /home.  At least, I think I made a pretty vanilla install, cannot recall now.  


Oh, and I wanted to know, should I do the suggested actions? Thanks OldFred.

Thanks again,

AlphaA

---

