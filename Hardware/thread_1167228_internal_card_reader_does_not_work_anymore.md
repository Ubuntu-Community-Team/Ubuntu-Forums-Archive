---
title: "internal card reader does not work anymore"
date: 2009-05-22
forum: Hardware
---

### Post by UeB on 2009-05-22
Hallo,

my internal card does not work anymore (it worked at least until I upgraded to 9.10)

when I plug in an SD card I get this message in dmesg:

```
mmc0: error -84 whilst initialising SD card
```

Does anybody know what I could try to get it to work again?

Thanks in advance!

Some hardware information:
```
           *-system:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:08:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci
           *-system:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.2
                bus info: pci@0000:08:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.3
                bus info: pci@0000:08:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.4
                bus info: pci@0000:08:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
```

---

### Post by PatrickMoore on 2009-05-24
what is your computer model. i have a dv4-1275mx and mine is working out of the box with a fresh kubuntu 8.10 install.

---

### Post by UeB on 2009-05-25
The model's name is dv7-1001eg.
But I also did not have any problems wile using 8.10.

It appeared AFTER the upgrade to 9.04

---

### Post by KeeperOfDreams on 2009-05-30
Tossing in my information
dv5z running 9.04, was running 8.04 (did not work)
upgraded to 8.10 (briefly, worked there) 
and then to 9.04 (stopped working again)
I have only needed it a couple of times though and it has not been high priority.

---

### Post by i_m_bobo on 2009-05-30
I also lost access to my card reader when I upgraded to Jaunty. It worked for a year with Hardy. The computer sees the reader attached to USB0. The reader sees the card - the LED comes on. But the computer seems completely unaware of the card. There's nothing in any log when I plug the card in or out. According to "Device Manager" (which I installed to help investigate this), the reader is from Realtek Semiconductor Corp.

---

### Post by UeB on 2009-06-07
Hallo I still have this problem with my internal card reader.

I got my hands on different flash cards and tried them. The problem seems to be more complex the I thought before:

As I already wrote here my Kingston 1 GB SD card leads to a error message
mmc0: error -84 whilst initialising SD card
that can be seen when the command dmesg is used.

A "ALLROUND" 2 GB SD-Card gives
mmc0: new high speed SD card at address 0007
mmcblk0: mmc0:0007 SD02G 1.90 GiB 
 mmcblk0: p1
**and gets automounted** and I can even copy data form this SD card to my hard drive. But when I what to copy a file to the card I get an error mesg in nautilus saying the card is full but it is not and after that I cannot do anything with it anymore until I unplug it wait a bit and stick it back in.

And finally I tried a Olympus xD card, were nothing at all happens no automaount not even ANY mesage in dmesg. Even the card reader is not blinking.


can anybody help me fixing my card reader?

as I said it used to work in Ubutu 8.10 at least with the Kingston card which is the only one I used regularly. And would like to do so again!

---

### Post by UeB on 2009-11-21
Hallo,

I hoped that maybe the upgrade to 9.10 will do something good. Well it did not...

Only the format of the error mesg is dmesg change (they are much more verbose now) but my SD card will still not be auto-mounted.

The "new" errors:

```
[14937.702001] mmc0: error -110 whilst initialising SD card
[15014.658627] mmc0: new SD card at address 0002
[15014.719726] mmcblk0: mmc0:0002 SD1GB 958 MiB 
[15014.719870]  mmcblk0: p1
[15014.840365] mmcblk0: retrying using single block read
[15014.840394] mmcblk0: error -123 sending status comand
[15014.840399] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840402] end_request: I/O error, dev mmcblk0, sector 1961855
[15014.840408] Buffer I/O error on device mmcblk0p1, logical block 1961600
[15014.840434] mmcblk0: error -123 sending status comand
[15014.840437] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840440] end_request: I/O error, dev mmcblk0, sector 1961856
[15014.840444] Buffer I/O error on device mmcblk0p1, logical block 1961601
[15014.840468] mmcblk0: error -123 sending status comand
[15014.840471] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840474] end_request: I/O error, dev mmcblk0, sector 1961857
[15014.840477] Buffer I/O error on device mmcblk0p1, logical block 1961602
[15014.840571] mmcblk0: error -123 sending status comand
[15014.840574] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840577] end_request: I/O error, dev mmcblk0, sector 1961858
[15014.840580] Buffer I/O error on device mmcblk0p1, logical block 1961603
[15014.840605] mmcblk0: error -123 sending status comand
[15014.840608] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840611] end_request: I/O error, dev mmcblk0, sector 1961859
[15014.840614] Buffer I/O error on device mmcblk0p1, logical block 1961604
[15014.840638] mmcblk0: error -123 sending status comand
[15014.840641] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840644] end_request: I/O error, dev mmcblk0, sector 1961860
[15014.840647] Buffer I/O error on device mmcblk0p1, logical block 1961605
[15014.840671] mmcblk0: error -123 sending status comand
[15014.840674] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840677] end_request: I/O error, dev mmcblk0, sector 1961861
[15014.840680] Buffer I/O error on device mmcblk0p1, logical block 1961606
[15014.840704] mmcblk0: error -123 sending status comand
[15014.840707] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840710] end_request: I/O error, dev mmcblk0, sector 1961862
[15014.840713] Buffer I/O error on device mmcblk0p1, logical block 1961607
[15014.840801] mmcblk0: retrying using single block read
[15014.840825] mmcblk0: error -123 sending status comand
[15014.840828] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840831] end_request: I/O error, dev mmcblk0, sector 1961720
[15014.840855] mmcblk0: error -123 sending status comand
[15014.840858] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840861] end_request: I/O error, dev mmcblk0, sector 1961721
[15014.840885] mmcblk0: error -123 sending status comand
[15014.840888] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840891] end_request: I/O error, dev mmcblk0, sector 1961722
[15014.840914] mmcblk0: error -123 sending status comand
[15014.840917] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840920] end_request: I/O error, dev mmcblk0, sector 1961723
[15014.840944] mmcblk0: error -123 sending status comand
[15014.840947] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840950] end_request: I/O error, dev mmcblk0, sector 1961724
[15014.840973] mmcblk0: error -123 sending status comand
[15014.840976] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.840979] end_request: I/O error, dev mmcblk0, sector 1961725
[15014.841003] mmcblk0: error -123 sending status comand
[15014.841006] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841009] end_request: I/O error, dev mmcblk0, sector 1961726
[15014.841032] mmcblk0: error -123 sending status comand
[15014.841035] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841038] end_request: I/O error, dev mmcblk0, sector 1961727
[15014.841042] Buffer I/O error on device mmcblk0, logical block 245215
[15014.841067] mmcblk0: error -123 sending status comand
[15014.841069] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841073] end_request: I/O error, dev mmcblk0, sector 1961728
[15014.841096] mmcblk0: error -123 sending status comand
[15014.841099] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841102] end_request: I/O error, dev mmcblk0, sector 1961729
[15014.841125] mmcblk0: error -123 sending status comand
[15014.841128] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841131] end_request: I/O error, dev mmcblk0, sector 1961730
[15014.841154] mmcblk0: error -123 sending status comand
[15014.841157] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841160] end_request: I/O error, dev mmcblk0, sector 1961731
[15014.841183] mmcblk0: error -123 sending status comand
[15014.841186] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841189] end_request: I/O error, dev mmcblk0, sector 1961732
[15014.841212] mmcblk0: error -123 sending status comand
[15014.841215] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841218] end_request: I/O error, dev mmcblk0, sector 1961733
[15014.841241] mmcblk0: error -123 sending status comand
[15014.841244] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841247] end_request: I/O error, dev mmcblk0, sector 1961734
[15014.841271] mmcblk0: error -123 sending status comand
[15014.841273] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841276] end_request: I/O error, dev mmcblk0, sector 1961735
[15014.841279] Buffer I/O error on device mmcblk0, logical block 245216
[15014.841303] mmcblk0: error -123 sending status comand
[15014.841306] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841309] end_request: I/O error, dev mmcblk0, sector 1961736
[15014.841333] mmcblk0: error -123 sending status comand
[15014.841336] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841339] end_request: I/O error, dev mmcblk0, sector 1961737
[15014.841362] mmcblk0: error -123 sending status comand
[15014.841365] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841368] end_request: I/O error, dev mmcblk0, sector 1961738
[15014.841392] mmcblk0: error -123 sending status comand
[15014.841395] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841398] end_request: I/O error, dev mmcblk0, sector 1961739
[15014.841421] mmcblk0: error -123 sending status comand
[15014.841424] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841427] end_request: I/O error, dev mmcblk0, sector 1961740
[15014.841451] mmcblk0: error -123 sending status comand
[15014.841453] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841457] end_request: I/O error, dev mmcblk0, sector 1961741
[15014.841480] mmcblk0: error -123 sending status comand
[15014.841483] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841486] end_request: I/O error, dev mmcblk0, sector 1961742
[15014.841510] mmcblk0: error -123 sending status comand
[15014.841512] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841515] end_request: I/O error, dev mmcblk0, sector 1961743
[15014.841540] mmcblk0: error -123 sending status comand
[15014.841543] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841546] end_request: I/O error, dev mmcblk0, sector 1961744
[15014.841569] mmcblk0: error -123 sending status comand
[15014.841572] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841575] end_request: I/O error, dev mmcblk0, sector 1961745
[15014.841599] mmcblk0: error -123 sending status comand
[15014.841601] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841604] end_request: I/O error, dev mmcblk0, sector 1961746
[15014.841628] mmcblk0: error -123 sending status comand
[15014.841631] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841634] end_request: I/O error, dev mmcblk0, sector 1961747
[15014.841657] mmcblk0: error -123 sending status comand
[15014.841660] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841663] end_request: I/O error, dev mmcblk0, sector 1961748
[15014.841687] mmcblk0: error -123 sending status comand
[15014.841690] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841693] end_request: I/O error, dev mmcblk0, sector 1961749
[15014.841716] mmcblk0: error -123 sending status comand
[15014.841719] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841722] end_request: I/O error, dev mmcblk0, sector 1961750
[15014.841746] mmcblk0: error -123 sending status comand
[15014.841748] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.841751] end_request: I/O error, dev mmcblk0, sector 1961751
[15014.856859] mmcblk0: retrying using single block read
[15014.856885] mmcblk0: error -123 sending status comand
[15014.856889] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.856892] end_request: I/O error, dev mmcblk0, sector 1961720
[15014.856916] mmcblk0: error -123 sending status comand
[15014.856919] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.856922] end_request: I/O error, dev mmcblk0, sector 1961721
[15014.856946] mmcblk0: error -123 sending status comand
[15014.856949] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.856952] end_request: I/O error, dev mmcblk0, sector 1961722
[15014.856975] mmcblk0: error -123 sending status comand
[15014.856978] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.856981] end_request: I/O error, dev mmcblk0, sector 1961723
[15014.857004] mmcblk0: error -123 sending status comand
[15014.857007] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857010] end_request: I/O error, dev mmcblk0, sector 1961724
[15014.857033] mmcblk0: error -123 sending status comand
[15014.857036] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857039] end_request: I/O error, dev mmcblk0, sector 1961725
[15014.857063] mmcblk0: error -123 sending status comand
[15014.857065] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857068] end_request: I/O error, dev mmcblk0, sector 1961726
[15014.857092] mmcblk0: error -123 sending status comand
[15014.857095] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857098] end_request: I/O error, dev mmcblk0, sector 1961727
[15014.857126] mmcblk0: retrying using single block read
[15014.857150] mmcblk0: error -123 sending status comand
[15014.857153] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857156] end_request: I/O error, dev mmcblk0, sector 1961855
[15014.857181] mmcblk0: error -123 sending status comand
[15014.857184] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857187] end_request: I/O error, dev mmcblk0, sector 1961856
[15014.857211] mmcblk0: error -123 sending status comand
[15014.857214] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857217] end_request: I/O error, dev mmcblk0, sector 1961857
[15014.857242] mmcblk0: error -123 sending status comand
[15014.857244] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857247] end_request: I/O error, dev mmcblk0, sector 1961858
[15014.857272] mmcblk0: error -123 sending status comand
[15014.857275] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857278] end_request: I/O error, dev mmcblk0, sector 1961859
[15014.857302] mmcblk0: error -123 sending status comand
[15014.857305] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857308] end_request: I/O error, dev mmcblk0, sector 1961860
[15014.857333] mmcblk0: error -123 sending status comand
[15014.857335] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857338] end_request: I/O error, dev mmcblk0, sector 1961861
[15014.857363] mmcblk0: error -123 sending status comand
[15014.857366] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857369] end_request: I/O error, dev mmcblk0, sector 1961862
[15014.857545] mmcblk0: retrying using single block read
[15014.857586] mmcblk0: error -123 sending status comand
[15014.857594] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857602] end_request: I/O error, dev mmcblk0, sector 1961967
[15014.857644] mmcblk0: error -123 sending status comand
[15014.857650] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857656] end_request: I/O error, dev mmcblk0, sector 1961968
[15014.857692] mmcblk0: error -123 sending status comand
[15014.857697] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857704] end_request: I/O error, dev mmcblk0, sector 1961969
[15014.857739] mmcblk0: error -123 sending status comand
[15014.857744] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857750] end_request: I/O error, dev mmcblk0, sector 1961970
[15014.857786] mmcblk0: error -123 sending status comand
[15014.857794] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857803] end_request: I/O error, dev mmcblk0, sector 1961971
[15014.857841] mmcblk0: error -123 sending status comand
[15014.857849] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857858] end_request: I/O error, dev mmcblk0, sector 1961972
[15014.857895] mmcblk0: error -123 sending status comand
[15014.857903] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857912] end_request: I/O error, dev mmcblk0, sector 1961973
[15014.857950] mmcblk0: error -123 sending status comand
[15014.857958] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.857967] end_request: I/O error, dev mmcblk0, sector 1961974
[15014.858018] mmcblk0: retrying using single block read
[15014.858054] mmcblk0: error -123 sending status comand
[15014.858062] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858071] end_request: I/O error, dev mmcblk0, sector 1961920
[15014.858109] mmcblk0: error -123 sending status comand
[15014.858117] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858126] end_request: I/O error, dev mmcblk0, sector 1961921
[15014.858163] mmcblk0: error -123 sending status comand
[15014.858171] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858180] end_request: I/O error, dev mmcblk0, sector 1961922
[15014.858217] mmcblk0: error -123 sending status comand
[15014.858225] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858234] end_request: I/O error, dev mmcblk0, sector 1961923
[15014.858271] mmcblk0: error -123 sending status comand
[15014.858279] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858288] end_request: I/O error, dev mmcblk0, sector 1961924
[15014.858325] mmcblk0: error -123 sending status comand
[15014.858333] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858342] end_request: I/O error, dev mmcblk0, sector 1961925
[15014.858379] mmcblk0: error -123 sending status comand
[15014.858387] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858396] end_request: I/O error, dev mmcblk0, sector 1961926
[15014.858433] mmcblk0: error -123 sending status comand
[15014.858441] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858450] end_request: I/O error, dev mmcblk0, sector 1961927
[15014.858494] mmcblk0: error -123 sending status comand
[15014.858502] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858511] end_request: I/O error, dev mmcblk0, sector 1961928
[15014.858548] mmcblk0: error -123 sending status comand
[15014.858556] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858565] end_request: I/O error, dev mmcblk0, sector 1961929
[15014.858602] mmcblk0: error -123 sending status comand
[15014.858610] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858619] end_request: I/O error, dev mmcblk0, sector 1961930
[15014.858656] mmcblk0: error -123 sending status comand
[15014.858665] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858674] end_request: I/O error, dev mmcblk0, sector 1961931
[15014.858711] mmcblk0: error -123 sending status comand
[15014.858719] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858728] end_request: I/O error, dev mmcblk0, sector 1961932
[15014.858765] mmcblk0: error -123 sending status comand
[15014.858773] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858782] end_request: I/O error, dev mmcblk0, sector 1961933
[15014.858819] mmcblk0: error -123 sending status comand
[15014.858826] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858835] end_request: I/O error, dev mmcblk0, sector 1961934
[15014.858872] mmcblk0: error -123 sending status comand
[15014.858880] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.858889] end_request: I/O error, dev mmcblk0, sector 1961935
[15014.859004] mmcblk0: retrying using single block read
[15014.859041] mmcblk0: error -123 sending status comand
[15014.859049] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859058] end_request: I/O error, dev mmcblk0, sector 1961967
[15014.859097] mmcblk0: error -123 sending status comand
[15014.859105] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859114] end_request: I/O error, dev mmcblk0, sector 1961968
[15014.859152] mmcblk0: error -123 sending status comand
[15014.859160] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859169] end_request: I/O error, dev mmcblk0, sector 1961969
[15014.859207] mmcblk0: error -123 sending status comand
[15014.859215] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859224] end_request: I/O error, dev mmcblk0, sector 1961970
[15014.859262] mmcblk0: error -123 sending status comand
[15014.859270] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859279] end_request: I/O error, dev mmcblk0, sector 1961971
[15014.859316] mmcblk0: error -123 sending status comand
[15014.859324] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859333] end_request: I/O error, dev mmcblk0, sector 1961972
[15014.859371] mmcblk0: error -123 sending status comand
[15014.859379] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859388] end_request: I/O error, dev mmcblk0, sector 1961973
[15014.859425] mmcblk0: error -123 sending status comand
[15014.859433] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859442] end_request: I/O error, dev mmcblk0, sector 1961974
[15014.859535] mmcblk0: error -123 sending status comand
[15014.859543] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859552] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.859607] mmcblk0: error -123 sending status comand
[15014.859615] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859624] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.859687] mmcblk0: retrying using single block read
[15014.859724] mmcblk0: error -123 sending status comand
[15014.859732] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859741] end_request: I/O error, dev mmcblk0, sector 1961975
[15014.859779] mmcblk0: error -123 sending status comand
[15014.859787] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859796] end_request: I/O error, dev mmcblk0, sector 1961976
[15014.859834] mmcblk0: error -123 sending status comand
[15014.859842] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859851] end_request: I/O error, dev mmcblk0, sector 1961977
[15014.859889] mmcblk0: error -123 sending status comand
[15014.859897] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859906] end_request: I/O error, dev mmcblk0, sector 1961978
[15014.859944] mmcblk0: error -123 sending status comand
[15014.859951] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.859960] end_request: I/O error, dev mmcblk0, sector 1961979
[15014.859998] mmcblk0: error -123 sending status comand
[15014.860006] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860015] end_request: I/O error, dev mmcblk0, sector 1961980
[15014.860289] mmcblk0: error -123 sending status comand
[15014.860297] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860307] end_request: I/O error, dev mmcblk0, sector 1961981
[15014.860346] mmcblk0: error -123 sending status comand
[15014.860354] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860363] end_request: I/O error, dev mmcblk0, sector 1961982
[15014.860429] mmcblk0: error -123 sending status comand
[15014.860437] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860446] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.860505] mmcblk0: error -123 sending status comand
[15014.860511] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860520] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.860581] mmcblk0: error -123 sending status comand
[15014.860589] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860598] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.860653] mmcblk0: retrying using single block read
[15014.860690] mmcblk0: error -123 sending status comand
[15014.860698] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860707] end_request: I/O error, dev mmcblk0, sector 1961975
[15014.860745] mmcblk0: error -123 sending status comand
[15014.860753] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860762] end_request: I/O error, dev mmcblk0, sector 1961976
[15014.860800] mmcblk0: error -123 sending status comand
[15014.860807] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860816] end_request: I/O error, dev mmcblk0, sector 1961977
[15014.860854] mmcblk0: error -123 sending status comand
[15014.860862] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860871] end_request: I/O error, dev mmcblk0, sector 1961978
[15014.860909] mmcblk0: error -123 sending status comand
[15014.860916] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860925] end_request: I/O error, dev mmcblk0, sector 1961979
[15014.860963] mmcblk0: error -123 sending status comand
[15014.860971] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.860980] end_request: I/O error, dev mmcblk0, sector 1961980
[15014.861017] mmcblk0: error -123 sending status comand
[15014.861025] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861034] end_request: I/O error, dev mmcblk0, sector 1961981
[15014.861071] mmcblk0: error -123 sending status comand
[15014.861079] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861088] end_request: I/O error, dev mmcblk0, sector 1961982
[15014.861150] mmcblk0: retrying using single block read
[15014.861187] mmcblk0: error -123 sending status comand
[15014.861195] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861204] end_request: I/O error, dev mmcblk0, sector 1961919
[15014.861242] mmcblk0: error -123 sending status comand
[15014.861250] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861259] end_request: I/O error, dev mmcblk0, sector 1961920
[15014.861297] mmcblk0: error -123 sending status comand
[15014.861304] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861314] end_request: I/O error, dev mmcblk0, sector 1961921
[15014.861351] mmcblk0: error -123 sending status comand
[15014.861359] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861368] end_request: I/O error, dev mmcblk0, sector 1961922
[15014.861406] mmcblk0: error -123 sending status comand
[15014.861414] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861423] end_request: I/O error, dev mmcblk0, sector 1961923
[15014.861460] mmcblk0: error -123 sending status comand
[15014.861468] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861477] end_request: I/O error, dev mmcblk0, sector 1961924
[15014.861515] mmcblk0: error -123 sending status comand
[15014.861523] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861531] end_request: I/O error, dev mmcblk0, sector 1961925
[15014.861569] mmcblk0: error -123 sending status comand
[15014.861577] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861586] end_request: I/O error, dev mmcblk0, sector 1961926
[15014.861645] mmcblk0: retrying using single block read
[15014.861681] mmcblk0: error -123 sending status comand
[15014.861689] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861698] end_request: I/O error, dev mmcblk0, sector 1961967
[15014.861737] mmcblk0: error -123 sending status comand
[15014.861744] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861753] end_request: I/O error, dev mmcblk0, sector 1961968
[15014.861791] mmcblk0: error -123 sending status comand
[15014.861799] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861808] end_request: I/O error, dev mmcblk0, sector 1961969
[15014.861845] mmcblk0: error -123 sending status comand
[15014.861853] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861862] end_request: I/O error, dev mmcblk0, sector 1961970
[15014.861900] mmcblk0: error -123 sending status comand
[15014.861907] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861916] end_request: I/O error, dev mmcblk0, sector 1961971
[15014.861954] mmcblk0: error -123 sending status comand
[15014.861962] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.861971] end_request: I/O error, dev mmcblk0, sector 1961972
[15014.862009] mmcblk0: error -123 sending status comand
[15014.862017] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862026] end_request: I/O error, dev mmcblk0, sector 1961973
[15014.862063] mmcblk0: error -123 sending status comand
[15014.862071] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862080] end_request: I/O error, dev mmcblk0, sector 1961974
[15014.862140] mmcblk0: error -123 sending status comand
[15014.862148] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862157] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.862216] mmcblk0: error -123 sending status comand
[15014.862223] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862232] end_request: I/O error, dev mmcblk0, sector 1961983
[15014.862308] mmcblk0: retrying using single block read
[15014.862345] mmcblk0: error -123 sending status comand
[15014.862353] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862362] end_request: I/O error, dev mmcblk0, sector 735
[15014.862400] mmcblk0: error -123 sending status comand
[15014.862408] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862417] end_request: I/O error, dev mmcblk0, sector 736
[15014.862455] mmcblk0: error -123 sending status comand
[15014.862462] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862471] end_request: I/O error, dev mmcblk0, sector 737
[15014.862509] mmcblk0: error -123 sending status comand
[15014.862517] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862526] end_request: I/O error, dev mmcblk0, sector 738
[15014.862575] mmcblk0: error -123 sending status comand
[15014.862583] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862592] end_request: I/O error, dev mmcblk0, sector 739
[15014.862629] mmcblk0: error -123 sending status comand
[15014.862637] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862646] end_request: I/O error, dev mmcblk0, sector 740
[15014.862683] mmcblk0: error -123 sending status comand
[15014.862691] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862700] end_request: I/O error, dev mmcblk0, sector 741
[15014.862737] mmcblk0: error -123 sending status comand
[15014.862745] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862754] end_request: I/O error, dev mmcblk0, sector 742
[15014.862884] mmcblk0: retrying using single block read
[15014.862921] mmcblk0: error -123 sending status comand
[15014.862928] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862937] end_request: I/O error, dev mmcblk0, sector 783
[15014.862976] mmcblk0: error -123 sending status comand
[15014.862983] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.862992] end_request: I/O error, dev mmcblk0, sector 784
[15014.863030] mmcblk0: error -123 sending status comand
[15014.863038] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863047] end_request: I/O error, dev mmcblk0, sector 785
[15014.863085] mmcblk0: error -123 sending status comand
[15014.863092] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863101] end_request: I/O error, dev mmcblk0, sector 786
[15014.863139] mmcblk0: error -123 sending status comand
[15014.863147] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863155] end_request: I/O error, dev mmcblk0, sector 787
[15014.863193] mmcblk0: error -123 sending status comand
[15014.863200] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863209] end_request: I/O error, dev mmcblk0, sector 788
[15014.863247] mmcblk0: error -123 sending status comand
[15014.863254] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863263] end_request: I/O error, dev mmcblk0, sector 789
[15014.863300] mmcblk0: error -123 sending status comand
[15014.863308] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863317] end_request: I/O error, dev mmcblk0, sector 790
[15014.863371] mmcblk0: retrying using single block read
[15014.863408] mmcblk0: error -123 sending status comand
[15014.863416] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863425] end_request: I/O error, dev mmcblk0, sector 783
[15014.863463] mmcblk0: error -123 sending status comand
[15014.863471] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863480] end_request: I/O error, dev mmcblk0, sector 784
[15014.863518] mmcblk0: error -123 sending status comand
[15014.863526] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863535] end_request: I/O error, dev mmcblk0, sector 785
[15014.863572] mmcblk0: error -123 sending status comand
[15014.863580] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863589] end_request: I/O error, dev mmcblk0, sector 786
[15014.863626] mmcblk0: error -123 sending status comand
[15014.863634] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863643] end_request: I/O error, dev mmcblk0, sector 787
[15014.863681] mmcblk0: error -123 sending status comand
[15014.863688] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863697] end_request: I/O error, dev mmcblk0, sector 788
[15014.863735] mmcblk0: error -123 sending status comand
[15014.863743] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863752] end_request: I/O error, dev mmcblk0, sector 789
[15014.863789] mmcblk0: error -123 sending status comand
[15014.863797] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863806] end_request: I/O error, dev mmcblk0, sector 790
[15014.863874] mmcblk0: retrying using single block read
[15014.863910] mmcblk0: error -123 sending status comand
[15014.863918] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863927] end_request: I/O error, dev mmcblk0, sector 767
[15014.863965] mmcblk0: error -123 sending status comand
[15014.863973] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.863982] end_request: I/O error, dev mmcblk0, sector 768
[15014.864020] mmcblk0: error -123 sending status comand
[15014.864053] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.864061] end_request: I/O error, dev mmcblk0, sector 769
[15014.864100] mmcblk0: error -123 sending status comand
[15014.864107] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.864116] end_request: I/O error, dev mmcblk0, sector 770
[15014.864154] mmcblk0: error -123 sending status comand
[15014.864161] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.864171] end_request: I/O error, dev mmcblk0, sector 771
[15014.864208] mmcblk0: error -123 sending status comand
[15014.864216] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.864225] end_request: I/O error, dev mmcblk0, sector 772
[15014.864262] mmcblk0: error -123 sending status comand
[15014.864270] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.864278] end_request: I/O error, dev mmcblk0, sector 773
[15014.864315] mmcblk0: error -123 sending status comand
[15014.864323] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.864332] end_request: I/O error, dev mmcblk0, sector 774
[15014.878182] mmcblk0: retrying using single block read
[15014.878211] mmcblk0: error -123 sending status comand
[15014.878215] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878220] end_request: I/O error, dev mmcblk0, sector 1961920
[15014.878247] mmcblk0: error -123 sending status comand
[15014.878250] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878253] end_request: I/O error, dev mmcblk0, sector 1961921
[15014.878278] mmcblk0: error -123 sending status comand
[15014.878281] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878284] end_request: I/O error, dev mmcblk0, sector 1961922
[15014.878308] mmcblk0: error -123 sending status comand
[15014.878311] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878314] end_request: I/O error, dev mmcblk0, sector 1961923
[15014.878340] mmcblk0: error -123 sending status comand
[15014.878343] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878346] end_request: I/O error, dev mmcblk0, sector 1961924
[15014.878372] mmcblk0: error -123 sending status comand
[15014.878375] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878378] end_request: I/O error, dev mmcblk0, sector 1961925
[15014.878403] mmcblk0: error -123 sending status comand
[15014.878405] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878408] end_request: I/O error, dev mmcblk0, sector 1961926
[15014.878433] mmcblk0: error -123 sending status comand
[15014.878436] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878439] end_request: I/O error, dev mmcblk0, sector 1961927
[15014.878893] mmcblk0: retrying using single block read
[15014.878919] mmcblk0: error -123 sending status comand
[15014.878922] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878925] end_request: I/O error, dev mmcblk0, sector 528
[15014.878950] mmcblk0: error -123 sending status comand
[15014.878953] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878956] end_request: I/O error, dev mmcblk0, sector 529
[15014.878981] mmcblk0: error -123 sending status comand
[15014.878983] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.878986] end_request: I/O error, dev mmcblk0, sector 530
[15014.879010] mmcblk0: error -123 sending status comand
[15014.879013] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879016] end_request: I/O error, dev mmcblk0, sector 531
[15014.879041] mmcblk0: error -123 sending status comand
[15014.879043] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879046] end_request: I/O error, dev mmcblk0, sector 532
[15014.879071] mmcblk0: error -123 sending status comand
[15014.879074] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879077] end_request: I/O error, dev mmcblk0, sector 533
[15014.879101] mmcblk0: error -123 sending status comand
[15014.879104] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879107] end_request: I/O error, dev mmcblk0, sector 534
[15014.879132] mmcblk0: error -123 sending status comand
[15014.879135] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879138] end_request: I/O error, dev mmcblk0, sector 535
[15014.879167] mmcblk0: error -123 sending status comand
[15014.879170] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879173] end_request: I/O error, dev mmcblk0, sector 536
[15014.879198] mmcblk0: error -123 sending status comand
[15014.879201] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879204] end_request: I/O error, dev mmcblk0, sector 537
[15014.879228] mmcblk0: error -123 sending status comand
[15014.879231] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879234] end_request: I/O error, dev mmcblk0, sector 538
[15014.879259] mmcblk0: error -123 sending status comand
[15014.879262] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879265] end_request: I/O error, dev mmcblk0, sector 539
[15014.879289] mmcblk0: error -123 sending status comand
[15014.879292] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879295] end_request: I/O error, dev mmcblk0, sector 540
[15014.879319] mmcblk0: error -123 sending status comand
[15014.879322] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879325] end_request: I/O error, dev mmcblk0, sector 541
[15014.879350] mmcblk0: error -123 sending status comand
[15014.879353] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879356] end_request: I/O error, dev mmcblk0, sector 542
[15014.879380] mmcblk0: error -123 sending status comand
[15014.879383] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879386] end_request: I/O error, dev mmcblk0, sector 543
[15014.879410] mmcblk0: retrying using single block read
[15014.879434] mmcblk0: error -123 sending status comand
[15014.879437] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879440] end_request: I/O error, dev mmcblk0, sector 528
[15014.879463] mmcblk0: error -123 sending status comand
[15014.879466] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879469] end_request: I/O error, dev mmcblk0, sector 529
[15014.879493] mmcblk0: error -123 sending status comand
[15014.879495] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879498] end_request: I/O error, dev mmcblk0, sector 530
[15014.879522] mmcblk0: error -123 sending status comand
[15014.879524] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879527] end_request: I/O error, dev mmcblk0, sector 531
[15014.879551] mmcblk0: error -123 sending status comand
[15014.879553] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879556] end_request: I/O error, dev mmcblk0, sector 532
[15014.879580] mmcblk0: error -123 sending status comand
[15014.879583] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879586] end_request: I/O error, dev mmcblk0, sector 533
[15014.879609] mmcblk0: error -123 sending status comand
[15014.879612] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879615] end_request: I/O error, dev mmcblk0, sector 534
[15014.879638] mmcblk0: error -123 sending status comand
[15014.879641] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.879644] end_request: I/O error, dev mmcblk0, sector 535
[15014.882448] mmcblk0: retrying using single block read
[15014.882477] mmcblk0: error -123 sending status comand
[15014.882484] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882490] end_request: I/O error, dev mmcblk0, sector 528
[15014.882517] mmcblk0: error -123 sending status comand
[15014.882521] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882526] end_request: I/O error, dev mmcblk0, sector 529
[15014.882552] mmcblk0: error -123 sending status comand
[15014.882556] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882561] end_request: I/O error, dev mmcblk0, sector 530
[15014.882587] mmcblk0: error -123 sending status comand
[15014.882591] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882596] end_request: I/O error, dev mmcblk0, sector 531
[15014.882622] mmcblk0: error -123 sending status comand
[15014.882626] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882632] end_request: I/O error, dev mmcblk0, sector 532
[15014.882657] mmcblk0: error -123 sending status comand
[15014.882661] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882666] end_request: I/O error, dev mmcblk0, sector 533
[15014.882692] mmcblk0: error -123 sending status comand
[15014.882696] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882702] end_request: I/O error, dev mmcblk0, sector 534
[15014.882727] mmcblk0: error -123 sending status comand
[15014.882732] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.882737] end_request: I/O error, dev mmcblk0, sector 535
[15014.892102] mmcblk0: retrying using single block read
[15014.892128] mmcblk0: error -123 sending status comand
[15014.892132] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892137] end_request: I/O error, dev mmcblk0, sector 512
[15014.892161] mmcblk0: error -123 sending status comand
[15014.892164] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892167] end_request: I/O error, dev mmcblk0, sector 513
[15014.892191] mmcblk0: error -123 sending status comand
[15014.892194] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892197] end_request: I/O error, dev mmcblk0, sector 514
[15014.892220] mmcblk0: error -123 sending status comand
[15014.892222] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892225] end_request: I/O error, dev mmcblk0, sector 515
[15014.892249] mmcblk0: error -123 sending status comand
[15014.892251] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892254] end_request: I/O error, dev mmcblk0, sector 516
[15014.892277] mmcblk0: error -123 sending status comand
[15014.892280] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892283] end_request: I/O error, dev mmcblk0, sector 517
[15014.892306] mmcblk0: error -123 sending status comand
[15014.892309] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892312] end_request: I/O error, dev mmcblk0, sector 518
[15014.892335] mmcblk0: error -123 sending status comand
[15014.892337] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[15014.892340] end_request: I/O error, dev mmcblk0, sector 519
[15015.037791] mmc0: card 0002 removed
```

anybody any idea what to do?

---

### Post by dday1 on 2009-12-07
I have a similar problem. My internal card reader worked fine in Jaunty, but now while using Karmic, whenever I insert and remove my sd card I get this in my syslog with no sign of it being mounted:

```
Dec  7 22:48:25 Wakizashi-ni kernel: [ 7714.126212] tifm_core: MMC/SD card detected in socket 0:1
Dec  7 22:49:24 Wakizashi-ni kernel: [ 7772.727742] tifm0 : demand removing card from socket 0:1
```

If I remove and reinsert the card, i eventually get this and the card is mounted:

```
Dec  7 22:50:50 Wakizashi-ni kernel: [ 7859.089829] tifm_core: MMC/SD card detected in socket 0:1
Dec  7 22:50:51 Wakizashi-ni kernel: [ 7859.274840] mmc0: new SD card at address 4d39
Dec  7 22:50:51 Wakizashi-ni kernel: [ 7859.277682] mmcblk0: mmc0:4d39 SD02G 1.83 GiB (ro)
Dec  7 22:50:51 Wakizashi-ni kernel: [ 7859.277817]  mmcblk0: p1
Dec  7 22:50:51 Wakizashi-ni kernel: [ 7859.300618] mmcblk0: retrying using single block read
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300044] tifm_sd0:1 : card failed to respond for a long period of time (11, 2)
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300071] tifm0 : demand removing card from socket 0:1
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300153] mmc0: card 4d39 removed
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300883] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300891] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300901] mmcblk0: error -84 transferring data, sector 0, nr 256, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300909] end_request: I/O error, dev mmcblk0, sector 0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300930] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300936] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300943] end_request: I/O error, dev mmcblk0, sector 1
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300955] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300961] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300968] end_request: I/O error, dev mmcblk0, sector 2
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300980] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300986] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.300993] end_request: I/O error, dev mmcblk0, sector 3
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301010] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301016] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301023] end_request: I/O error, dev mmcblk0, sector 4
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301035] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301041] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301048] end_request: I/O error, dev mmcblk0, sector 5
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301059] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301066] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301073] end_request: I/O error, dev mmcblk0, sector 6
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301084] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301091] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301098] end_request: I/O error, dev mmcblk0, sector 7
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301106] __ratelimit: 6 callbacks suppressed
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301113] Buffer I/O error on device mmcblk0, logical block 0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301134] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301141] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301148] end_request: I/O error, dev mmcblk0, sector 8
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301159] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301166] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301173] end_request: I/O error, dev mmcblk0, sector 9
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301184] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301191] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301198] end_request: I/O error, dev mmcblk0, sector 10
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301209] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301216] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301223] end_request: I/O error, dev mmcblk0, sector 11
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301234] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301240] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301248] end_request: I/O error, dev mmcblk0, sector 12
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301259] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301265] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301272] end_request: I/O error, dev mmcblk0, sector 13
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301284] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301290] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301297] end_request: I/O error, dev mmcblk0, sector 14
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301309] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301315] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301322] end_request: I/O error, dev mmcblk0, sector 15
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301329] Buffer I/O error on device mmcblk0, logical block 1
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301341] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301348] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301355] end_request: I/O error, dev mmcblk0, sector 16
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301366] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301373] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301380] end_request: I/O error, dev mmcblk0, sector 17
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301391] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301398] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301405] end_request: I/O error, dev mmcblk0, sector 18
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301416] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301422] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301429] end_request: I/O error, dev mmcblk0, sector 19
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301441] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301447] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301454] end_request: I/O error, dev mmcblk0, sector 20
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301465] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301472] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301479] end_request: I/O error, dev mmcblk0, sector 21
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301490] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301497] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301504] end_request: I/O error, dev mmcblk0, sector 22
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301515] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301521] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301529] end_request: I/O error, dev mmcblk0, sector 23
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301535] Buffer I/O error on device mmcblk0, logical block 2
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301548] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301554] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301561] end_request: I/O error, dev mmcblk0, sector 24
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301573] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301579] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301586] end_request: I/O error, dev mmcblk0, sector 25
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301597] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301604] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301611] end_request: I/O error, dev mmcblk0, sector 26
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301622] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301628] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301636] end_request: I/O error, dev mmcblk0, sector 27
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301647] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301653] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301660] end_request: I/O error, dev mmcblk0, sector 28
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301671] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301678] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301685] end_request: I/O error, dev mmcblk0, sector 29
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301696] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301703] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301710] end_request: I/O error, dev mmcblk0, sector 30
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301721] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301727] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301734] end_request: I/O error, dev mmcblk0, sector 31
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301741] Buffer I/O error on device mmcblk0, logical block 3
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301753] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301760] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301767] end_request: I/O error, dev mmcblk0, sector 32
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301778] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301784] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301791] end_request: I/O error, dev mmcblk0, sector 33
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301802] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301809] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301816] end_request: I/O error, dev mmcblk0, sector 34
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301827] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301833] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301841] end_request: I/O error, dev mmcblk0, sector 35
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301852] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301858] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301865] end_request: I/O error, dev mmcblk0, sector 36
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301876] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301883] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301890] end_request: I/O error, dev mmcblk0, sector 37
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301901] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301907] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301914] end_request: I/O error, dev mmcblk0, sector 38
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301925] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301932] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301939] end_request: I/O error, dev mmcblk0, sector 39
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301946] Buffer I/O error on device mmcblk0, logical block 4
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301958] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301964] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301971] end_request: I/O error, dev mmcblk0, sector 40
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301982] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301989] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.301996] end_request: I/O error, dev mmcblk0, sector 41
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302007] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302013] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302020] end_request: I/O error, dev mmcblk0, sector 42
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302031] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302038] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302045] end_request: I/O error, dev mmcblk0, sector 43
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302056] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302062] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302069] end_request: I/O error, dev mmcblk0, sector 44
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302080] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302087] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302094] end_request: I/O error, dev mmcblk0, sector 45
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302105] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302111] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302118] end_request: I/O error, dev mmcblk0, sector 46
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302129] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302136] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302143] end_request: I/O error, dev mmcblk0, sector 47
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302150] Buffer I/O error on device mmcblk0, logical block 5
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302162] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302168] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302175] end_request: I/O error, dev mmcblk0, sector 48
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302186] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302193] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302200] end_request: I/O error, dev mmcblk0, sector 49
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302211] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302217] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302224] end_request: I/O error, dev mmcblk0, sector 50
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302235] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302242] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302249] end_request: I/O error, dev mmcblk0, sector 51
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302260] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302266] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302275] end_request: I/O error, dev mmcblk0, sector 52
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302285] MMC: killing requests for dead queue
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302293] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302302] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302321] end_request: I/O error, dev mmcblk0, sector 0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302329] Buffer I/O error on device mmcblk0, logical block 0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302346] end_request: I/O error, dev mmcblk0, sector 53
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302358] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302365] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302372] end_request: I/O error, dev mmcblk0, sector 54
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302385] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302391] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302399] end_request: I/O error, dev mmcblk0, sector 55
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302405] Buffer I/O error on device mmcblk0, logical block 6
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302418] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302425] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302432] end_request: I/O error, dev mmcblk0, sector 56
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302443] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302449] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302456] end_request: I/O error, dev mmcblk0, sector 57
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302467] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302473] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302481] end_request: I/O error, dev mmcblk0, sector 58
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302491] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302498] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302505] end_request: I/O error, dev mmcblk0, sector 59
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302516] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302522] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302529] end_request: I/O error, dev mmcblk0, sector 60
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302540] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302546] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302553] end_request: I/O error, dev mmcblk0, sector 61
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302564] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302571] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302578] end_request: I/O error, dev mmcblk0, sector 62
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302588] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302595] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302602] end_request: I/O error, dev mmcblk0, sector 63
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302609] Buffer I/O error on device mmcblk0, logical block 7
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302627] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302633] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302640] end_request: I/O error, dev mmcblk0, sector 64
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302651] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302658] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302665] end_request: I/O error, dev mmcblk0, sector 65
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302676] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302682] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302689] end_request: I/O error, dev mmcblk0, sector 66
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302700] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302706] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302713] end_request: I/O error, dev mmcblk0, sector 67
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302724] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302730] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302737] end_request: I/O error, dev mmcblk0, sector 68
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302748] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302754] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302762] end_request: I/O error, dev mmcblk0, sector 69
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302772] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302779] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302786] end_request: I/O error, dev mmcblk0, sector 70
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302797] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302803] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302810] end_request: I/O error, dev mmcblk0, sector 71
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302817] Buffer I/O error on device mmcblk0, logical block 8
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302833] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302840] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302847] end_request: I/O error, dev mmcblk0, sector 72
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302858] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302864] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302871] end_request: I/O error, dev mmcblk0, sector 73
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302882] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302888] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302895] end_request: I/O error, dev mmcblk0, sector 74
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302906] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302912] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302919] end_request: I/O error, dev mmcblk0, sector 75
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302930] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302936] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302943] end_request: I/O error, dev mmcblk0, sector 76
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302954] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302960] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302967] end_request: I/O error, dev mmcblk0, sector 77
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302978] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302984] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.302991] end_request: I/O error, dev mmcblk0, sector 78
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303002] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303008] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303016] end_request: I/O error, dev mmcblk0, sector 79
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303032] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303038] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303045] end_request: I/O error, dev mmcblk0, sector 80
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303056] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303063] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303070] end_request: I/O error, dev mmcblk0, sector 81
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303080] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303086] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303094] end_request: I/O error, dev mmcblk0, sector 82
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303104] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303110] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303117] end_request: I/O error, dev mmcblk0, sector 83
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303128] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303134] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303141] end_request: I/O error, dev mmcblk0, sector 84
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303152] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303158] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303165] end_request: I/O error, dev mmcblk0, sector 85
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303176] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303182] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303189] end_request: I/O error, dev mmcblk0, sector 86
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303200] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303206] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303213] end_request: I/O error, dev mmcblk0, sector 87
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303229] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303236] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303243] end_request: I/O error, dev mmcblk0, sector 88
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303254] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303260] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303267] end_request: I/O error, dev mmcblk0, sector 89
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303277] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303284] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303291] end_request: I/O error, dev mmcblk0, sector 90
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303301] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303308] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303315] end_request: I/O error, dev mmcblk0, sector 91
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303325] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303332] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303339] end_request: I/O error, dev mmcblk0, sector 92
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303349] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303356] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303363] end_request: I/O error, dev mmcblk0, sector 93
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303373] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303379] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303387] end_request: I/O error, dev mmcblk0, sector 94
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303397] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303403] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303410] end_request: I/O error, dev mmcblk0, sector 95
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303427] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303433] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303440] end_request: I/O error, dev mmcblk0, sector 96
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303451] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303457] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303464] end_request: I/O error, dev mmcblk0, sector 97
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303475] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303481] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303488] end_request: I/O error, dev mmcblk0, sector 98
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303498] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303505] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303512] end_request: I/O error, dev mmcblk0, sector 99
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303522] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303529] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303536] end_request: I/O error, dev mmcblk0, sector 100
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303546] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303552] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303560] end_request: I/O error, dev mmcblk0, sector 101
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303570] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303576] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303583] end_request: I/O error, dev mmcblk0, sector 102
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303594] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303600] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303607] end_request: I/O error, dev mmcblk0, sector 103
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303623] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303630] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303637] end_request: I/O error, dev mmcblk0, sector 104
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303647] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303654] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303661] end_request: I/O error, dev mmcblk0, sector 105
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303671] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303677] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303684] end_request: I/O error, dev mmcblk0, sector 106
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303695] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303701] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303708] end_request: I/O error, dev mmcblk0, sector 107
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303718] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303725] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303732] end_request: I/O error, dev mmcblk0, sector 108
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303742] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303748] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303755] end_request: I/O error, dev mmcblk0, sector 109
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303766] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303772] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303779] end_request: I/O error, dev mmcblk0, sector 110
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303789] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303796] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303803] end_request: I/O error, dev mmcblk0, sector 111
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303819] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303825] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303832] end_request: I/O error, dev mmcblk0, sector 112
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303842] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303849] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303856] end_request: I/O error, dev mmcblk0, sector 113
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303866] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303873] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303880] end_request: I/O error, dev mmcblk0, sector 114
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303890] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303896] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303903] end_request: I/O error, dev mmcblk0, sector 115
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303913] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303920] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303927] end_request: I/O error, dev mmcblk0, sector 116
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303937] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303943] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303950] end_request: I/O error, dev mmcblk0, sector 117
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303960] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303967] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303974] end_request: I/O error, dev mmcblk0, sector 118
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303984] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303991] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.303998] end_request: I/O error, dev mmcblk0, sector 119
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304043] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304050] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304057] end_request: I/O error, dev mmcblk0, sector 120
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304067] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304074] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304081] end_request: I/O error, dev mmcblk0, sector 121
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304091] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304097] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304104] end_request: I/O error, dev mmcblk0, sector 122
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304114] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304121] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304128] end_request: I/O error, dev mmcblk0, sector 123
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304138] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304144] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304151] end_request: I/O error, dev mmcblk0, sector 124
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304161] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304168] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304175] end_request: I/O error, dev mmcblk0, sector 125
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304185] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304191] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304198] end_request: I/O error, dev mmcblk0, sector 126
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304208] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304215] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304222] end_request: I/O error, dev mmcblk0, sector 127
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304239] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304245] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304252] end_request: I/O error, dev mmcblk0, sector 128
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304262] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304269] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304276] end_request: I/O error, dev mmcblk0, sector 129
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304286] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304292] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304300] end_request: I/O error, dev mmcblk0, sector 130
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304309] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304316] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304323] end_request: I/O error, dev mmcblk0, sector 131
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304333] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304339] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304346] end_request: I/O error, dev mmcblk0, sector 132
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304356] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304363] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304370] end_request: I/O error, dev mmcblk0, sector 133
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304380] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304386] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304393] end_request: I/O error, dev mmcblk0, sector 134
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304403] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304409] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304417] end_request: I/O error, dev mmcblk0, sector 135
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304433] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304439] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304446] end_request: I/O error, dev mmcblk0, sector 136
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304456] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304463] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304470] end_request: I/O error, dev mmcblk0, sector 137
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304479] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304486] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304493] end_request: I/O error, dev mmcblk0, sector 138
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304503] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304509] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304516] end_request: I/O error, dev mmcblk0, sector 139
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304526] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304533] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304540] end_request: I/O error, dev mmcblk0, sector 140
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304549] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304556] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304563] end_request: I/O error, dev mmcblk0, sector 141
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304573] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304579] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304586] end_request: I/O error, dev mmcblk0, sector 142
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304596] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304602] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304610] end_request: I/O error, dev mmcblk0, sector 143
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304625] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304631] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304639] end_request: I/O error, dev mmcblk0, sector 144
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304648] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304655] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304662] end_request: I/O error, dev mmcblk0, sector 145
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304672] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304678] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304685] end_request: I/O error, dev mmcblk0, sector 146
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304695] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304701] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304709] end_request: I/O error, dev mmcblk0, sector 147
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304726] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304732] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304739] end_request: I/O error, dev mmcblk0, sector 148
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304749] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304755] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304762] end_request: I/O error, dev mmcblk0, sector 149
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304772] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304779] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304786] end_request: I/O error, dev mmcblk0, sector 150
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304795] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304802] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304809] end_request: I/O error, dev mmcblk0, sector 151
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304825] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304831] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304838] end_request: I/O error, dev mmcblk0, sector 152
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304848] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304854] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304862] end_request: I/O error, dev mmcblk0, sector 153
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304871] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304878] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304885] end_request: I/O error, dev mmcblk0, sector 154
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304894] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304901] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304908] end_request: I/O error, dev mmcblk0, sector 155
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304917] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304924] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304931] end_request: I/O error, dev mmcblk0, sector 156
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304940] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304947] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304954] end_request: I/O error, dev mmcblk0, sector 157
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304964] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304970] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304977] end_request: I/O error, dev mmcblk0, sector 158
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304987] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.304993] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305000] end_request: I/O error, dev mmcblk0, sector 159
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305021] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305027] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305035] end_request: I/O error, dev mmcblk0, sector 160
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305044] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305051] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305058] end_request: I/O error, dev mmcblk0, sector 161
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305067] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305074] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305081] end_request: I/O error, dev mmcblk0, sector 162
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305090] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305097] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305104] end_request: I/O error, dev mmcblk0, sector 163
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305113] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305120] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305127] end_request: I/O error, dev mmcblk0, sector 164
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305136] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305143] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305150] end_request: I/O error, dev mmcblk0, sector 165
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305159] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305166] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305173] end_request: I/O error, dev mmcblk0, sector 166
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305182] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305189] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305196] end_request: I/O error, dev mmcblk0, sector 167
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305212] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305219] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305226] end_request: I/O error, dev mmcblk0, sector 168
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305235] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305242] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305249] end_request: I/O error, dev mmcblk0, sector 169
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305258] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305265] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305272] end_request: I/O error, dev mmcblk0, sector 170
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305281] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305288] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305295] end_request: I/O error, dev mmcblk0, sector 171
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305304] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305311] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305318] end_request: I/O error, dev mmcblk0, sector 172
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305327] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305333] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305341] end_request: I/O error, dev mmcblk0, sector 173
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305350] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305356] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305363] end_request: I/O error, dev mmcblk0, sector 174
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305373] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305379] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305386] end_request: I/O error, dev mmcblk0, sector 175
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305402] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305408] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305415] end_request: I/O error, dev mmcblk0, sector 176
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305425] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305431] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305438] end_request: I/O error, dev mmcblk0, sector 177
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305447] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305454] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305461] end_request: I/O error, dev mmcblk0, sector 178
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305470] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305477] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305484] end_request: I/O error, dev mmcblk0, sector 179
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305493] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305500] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305507] end_request: I/O error, dev mmcblk0, sector 180
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305516] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305522] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305530] end_request: I/O error, dev mmcblk0, sector 181
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305539] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305545] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305552] end_request: I/O error, dev mmcblk0, sector 182
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305562] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305568] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305575] end_request: I/O error, dev mmcblk0, sector 183
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305590] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305597] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305604] end_request: I/O error, dev mmcblk0, sector 184
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305613] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305620] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305627] end_request: I/O error, dev mmcblk0, sector 185
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305636] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305642] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305650] end_request: I/O error, dev mmcblk0, sector 186
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305659] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305665] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305672] end_request: I/O error, dev mmcblk0, sector 187
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305681] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305688] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305695] end_request: I/O error, dev mmcblk0, sector 188
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305704] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305711] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305718] end_request: I/O error, dev mmcblk0, sector 189
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305727] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305733] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305740] end_request: I/O error, dev mmcblk0, sector 190
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305750] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305756] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305763] end_request: I/O error, dev mmcblk0, sector 191
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305778] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305785] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305792] end_request: I/O error, dev mmcblk0, sector 192
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305801] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305808] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305815] end_request: I/O error, dev mmcblk0, sector 193
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305824] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305830] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305837] end_request: I/O error, dev mmcblk0, sector 194
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305846] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305853] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305860] end_request: I/O error, dev mmcblk0, sector 195
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305869] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305876] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305883] end_request: I/O error, dev mmcblk0, sector 196
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305892] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305898] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305905] end_request: I/O error, dev mmcblk0, sector 197
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305914] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305921] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305928] end_request: I/O error, dev mmcblk0, sector 198
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305937] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305943] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305951] end_request: I/O error, dev mmcblk0, sector 199
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305965] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305972] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305979] end_request: I/O error, dev mmcblk0, sector 200
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305988] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.305995] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306002] end_request: I/O error, dev mmcblk0, sector 201
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306011] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306017] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306024] end_request: I/O error, dev mmcblk0, sector 202
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306033] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306040] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306047] end_request: I/O error, dev mmcblk0, sector 203
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306056] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306062] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306069] end_request: I/O error, dev mmcblk0, sector 204
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306078] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306085] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306092] end_request: I/O error, dev mmcblk0, sector 205
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306101] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306107] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306114] end_request: I/O error, dev mmcblk0, sector 206
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306123] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306130] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306137] end_request: I/O error, dev mmcblk0, sector 207
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306151] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306158] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306165] end_request: I/O error, dev mmcblk0, sector 208
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306174] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306181] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306188] end_request: I/O error, dev mmcblk0, sector 209
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306197] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306203] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306210] end_request: I/O error, dev mmcblk0, sector 210
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306219] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306225] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306233] end_request: I/O error, dev mmcblk0, sector 211
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306241] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306248] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306255] end_request: I/O error, dev mmcblk0, sector 212
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306264] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306270] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306277] end_request: I/O error, dev mmcblk0, sector 213
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306286] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306293] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306300] end_request: I/O error, dev mmcblk0, sector 214
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306309] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306315] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306322] end_request: I/O error, dev mmcblk0, sector 215
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306337] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306343] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306350] end_request: I/O error, dev mmcblk0, sector 216
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306359] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306366] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306373] end_request: I/O error, dev mmcblk0, sector 217
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306382] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306388] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306395] end_request: I/O error, dev mmcblk0, sector 218
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306404] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306411] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306418] end_request: I/O error, dev mmcblk0, sector 219
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306435] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306442] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306449] end_request: I/O error, dev mmcblk0, sector 220
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306457] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306464] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306471] end_request: I/O error, dev mmcblk0, sector 221
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306480] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306486] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306493] end_request: I/O error, dev mmcblk0, sector 222
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306502] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306509] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306516] end_request: I/O error, dev mmcblk0, sector 223
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306531] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306537] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306544] end_request: I/O error, dev mmcblk0, sector 224
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306553] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306560] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306567] end_request: I/O error, dev mmcblk0, sector 225
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306575] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306582] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306589] end_request: I/O error, dev mmcblk0, sector 226
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306598] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306604] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306611] end_request: I/O error, dev mmcblk0, sector 227
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306620] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306626] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306633] end_request: I/O error, dev mmcblk0, sector 228
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306642] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306649] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306656] end_request: I/O error, dev mmcblk0, sector 229
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306664] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306671] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306678] end_request: I/O error, dev mmcblk0, sector 230
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306686] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306693] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306700] end_request: I/O error, dev mmcblk0, sector 231
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306714] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306721] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306728] end_request: I/O error, dev mmcblk0, sector 232
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306737] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306743] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306750] end_request: I/O error, dev mmcblk0, sector 233
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306759] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306765] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306772] end_request: I/O error, dev mmcblk0, sector 234
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306781] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306787] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306795] end_request: I/O error, dev mmcblk0, sector 235
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306803] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306810] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306817] end_request: I/O error, dev mmcblk0, sector 236
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306825] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306832] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306839] end_request: I/O error, dev mmcblk0, sector 237
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306848] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306854] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306861] end_request: I/O error, dev mmcblk0, sector 238
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306870] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306876] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306883] end_request: I/O error, dev mmcblk0, sector 239
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306898] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306904] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306911] end_request: I/O error, dev mmcblk0, sector 240
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306920] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306926] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306934] end_request: I/O error, dev mmcblk0, sector 241
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306942] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306948] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306956] end_request: I/O error, dev mmcblk0, sector 242
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306964] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306970] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306978] end_request: I/O error, dev mmcblk0, sector 243
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306986] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.306992] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307000] end_request: I/O error, dev mmcblk0, sector 244
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307008] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307015] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307022] end_request: I/O error, dev mmcblk0, sector 245
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307030] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307037] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307044] end_request: I/O error, dev mmcblk0, sector 246
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307052] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307059] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307066] end_request: I/O error, dev mmcblk0, sector 247
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307080] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307087] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307094] end_request: I/O error, dev mmcblk0, sector 248
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307102] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307109] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307116] end_request: I/O error, dev mmcblk0, sector 249
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307124] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307131] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307138] end_request: I/O error, dev mmcblk0, sector 250
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307146] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307153] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307160] end_request: I/O error, dev mmcblk0, sector 251
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307168] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307175] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307182] end_request: I/O error, dev mmcblk0, sector 252
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307190] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307197] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307204] end_request: I/O error, dev mmcblk0, sector 253
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307212] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307219] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307226] end_request: I/O error, dev mmcblk0, sector 254
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307234] mmcblk0: error -123 sending status comand
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307241] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.307248] end_request: I/O error, dev mmcblk0, sector 255
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.356717] tifm_core: MMC/SD card detected in socket 0:1
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.538844] mmc0: new SD card at address 4d39
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.539231] mmcblk0: mmc0:4d39 SD02G 1.83 GiB (ro)
Dec  7 22:50:52 Wakizashi-ni kernel: [ 7860.539350]  mmcblk0: p1

```

I wonder what is causing this and how do I get my card reader to work reliably?:confused:

---

### Post by dday1 on 2009-12-07
By the way I'm using a Sony Vaio N250E which has a built-in sd card reader

---

### Post by UeB on 2009-12-08
The problems were not there before a distro upgrade so I think we have every right to call this a software problems and demand a software solution.

> As matters stand, you internal card reader is not compatible with your hardware

Well it works with windows and it worked with older Ubuntu versions, so I do not think you can say that in this absolute manner.

kind regards

---

### Post by UeB on 2010-01-03
At the moment my internal card reader works again. I have no idea why. I did not try anything. Just plugged in for the first time since 6 weeks or so. And now it magically works.


This is the dmesg output. Errors are gone
[ 8959.682988] mmc0: new SD card at address 0002
[ 8959.745455] mmcblk0: mmc0:0002 SD1GB 958 MiB 
[ 8959.745592]  mmcblk0: p1

---

