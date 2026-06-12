---
title: "usb smart card reader don't work"
date: 2014-01-20
forum: Hardware
---

### Post by fabritrento on 2014-01-20
i tryed to install a usb smart card reader, but don't work. here the output of lsusb:

lsusb -v

Bus 003 Device 003: ID 25dd:3111  
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x25dd 
  idProduct          0x3111 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           93
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass        11 Chip/SmartCard
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ChipCard Interface Descriptor:
        bLength                54
        bDescriptorType        33
        bcdCCID              1.00
        nMaxSlotIndex           0
        bVoltageSupport         7  5.0V 3.0V 1.8V 
        dwProtocols             3  T=0 T=1
        dwDefaultClock       4000
        dwMaxiumumClock      4000
        bNumClockSupported      0
        dwDataRate          10752 bps
        dwMaxDataRate      344100 bps
        bNumDataRatesSupp.      0
        dwMaxIFSD             247
        dwSyncProtocols  00000000 
        dwMechanical     00000000 
        dwFeatures       00010030
          Auto clock change
          Auto baud rate change
          TPDU level exchange
        dwMaxCCIDMsgLen       271
        bClassGetResponse      00
        bClassEnvelope         00
        wlcdLayout           none
        bPINSupport             0 
        bMaxCCIDBus*****s       1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              16
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0


i tryed to install the package libacr38u but after that this error in dmesg appear:

[   88.941391] pcscd[2696]: segfault at 0 ip 009f9021 sp bfc9315c error 4 in libc-2.15.so[97b000+1a4000]
[   89.027648] pcscd[2699]: segfault at 0 ip 0045e021 sp bfbf296c error 4 in libc-2.15.so[3e0000+1a4000]
[   89.042682] pcscd[2704]: segfault at 0 ip 0048d021 sp bfebf49c error 4 in libc-2.15.so[40f000+1a4000]
[   89.055035] pcscd[2707]: segfault at 0 ip 00509021 sp bfef875c error 4 in libc-2.15.so[48b000+1a4000]
[   90.075917] pcscd[2720]: segfault at 0 ip 0034e021 sp bf8bc1ec error 4 in libc-2.15.so[2d0000+1a4000]
[   91.088124] pcscd[2724]: segfault at 0 ip 00464021 sp bf81ff2c error 4 in libc-2.15.so[3e6000+1a4000]
[   92.100111] pcscd[2727]: segfault at 0 ip 007ca021 sp bfd557bc error 4 in libc-2.15.so[74c000+1a4000]
[   93.112259] pcscd[2730]: segfault at 0 ip 00d8b021 sp bfb1b96c error 4 in libc-2.15.so[d0d000+1a4000]
[   94.160403] pcscd[2804]: segfault at 0 ip 00b53021 sp bffe50fc error 4 in libc-2.15.so[ad5000+1a4000]
[   95.186914] pcscd[2979]: segfault at 0 ip 00da4021 sp bfafde6c error 4 in libc-2.15.so[d26000+1a4000]
[   96.205723] pcscd[2982]: segfault at 0 ip 001b3021 sp bff9a99c error 4 in libc-2.15.so[135000+1a4000]
[   97.222879] pcscd[2986]: segfault at 0 ip 0018e021 sp bfb7cb6c error 4 in libc-2.15.so[110000+1a4000]
[   98.247934] pcscd[2989]: segfault at 0 ip 0018e021 sp bfb90a9c error 4 in libc-2.15.so[110000+1a4000]
[   99.262823] pcscd[2993]: segfault at 0 ip 0018e021 sp bfa7abac error 4 in libc-2.15.so[110000+1a4000]
[  100.279847] pcscd[2997]: segfault at 0 ip 003eb021 sp bfe3f3fc error 4 in libc-2.15.so[36d000+1a4000]
[  101.303497] pcscd[3000]: segfault at 0 ip 009cc021 sp bffcff0c error 4 in libc-2.15.so[94e000+1a4000]
[  102.328617] pcscd[3003]: segfault at 0 ip 001d9021 sp bfc75e2c error 4 in libc-2.15.so[15b000+1a4000]
[  103.342244] pcscd[3006]: segfault at 0 ip 0018e021 sp bfb0b85c error 4 in libc-2.15.so[110000+1a4000]
[  104.361442] pcscd[3009]: segfault at 0 ip 002b4021 sp bfcdf2ac error 4 in libc-2.15.so[236000+1a4000]
[  105.377992] pcscd[3012]: segfault at 0 ip 00486021 sp bfc28c3c error 4 in libc-2.15.so[408000+1a4000]
[  106.392353] pcscd[3015]: segfault at 0 ip 0097a021 sp bfb8d8ec error 4 in libc-2.15.so[8fc000+1a4000]
[  107.422926] pcscd[3018]: segfault at 0 ip 00a0d021 sp bfedee8c error 4 in libc-2.15.so[98f000+1a4000]
[  108.448682] pcscd[3021]: segfault at 0 ip 00204021 sp bfcea1ac error 4 in libc-2.15.so[186000+1a4000]
[  109.470152] pcscd[3024]: segfault at 0 ip 008a2021 sp bfb637ac error 4 in libc-2.15.so[824000+1a4000]
[  110.487527] pcscd[3027]: segfault at 0 ip 0089d021 sp bfa0945c error 4 in libc-2.15.so[81f000+1a4000]
[  111.504679] pcscd[3030]: segfault at 0 ip 0018e021 sp bf9d4fac error 4 in libc-2.15.so[110000+1a4000]
[  112.518763] pcscd[3033]: segfault at 0 ip 00263021 sp bf94976c error 4 in libc-2.15.so[1e5000+1a4000]
[  113.533140] pcscd[3036]: segfault at 0 ip 00ad9021 sp bfe7ff0c error 4 in libc-2.15.so[a5b000+1a4000]
[  114.561578] pcscd[3039]: segfault at 0 ip 00363021 sp bfba9fdc error 4 in libc-2.15.so[2e5000+1a4000]
[  115.584649] pcscd[3283]: segfault at 0 ip 00e3c021 sp bfe99eac error 4 in libc-2.15.so[dbe000+1a4000]
[  116.598258] pcscd[3286]: segfault at 0 ip 00ed3021 sp bff477dc error 4 in libc-2.15.so[e55000+1a4000]
[  117.615263] pcscd[3289]: segfault at 0 ip 00bdb021 sp bfa25ecc error 4 in libc-2.15.so[b5d000+1a4000]
[  118.634751] pcscd[3294]: segfault at 0 ip 002bd021 sp bfce877c error 4 in libc-2.15.so[23f000+1a4000]
[  119.653291] pcscd[3297]: segfault at 0 ip 0018e021 sp bf9c2b7c error 4 in libc-2.15.so[110000+1a4000]
[  120.669035] pcscd[3300]: segfault at 0 ip 0018e021 sp bfb2997c error 4 in libc-2.15.so[110000+1a4000]
[  121.683361] pcscd[3303]: segfault at 0 ip 0018e021 sp bfc1fa7c error 4 in libc-2.15.so[110000+1a4000]
[  122.697330] pcscd[3306]: segfault at 0 ip 0018e021 sp bfbd386c error 4 in libc-2.15.so[110000+1a4000]
[  123.711376] pcscd[3309]: segfault at 0 ip 00bc3021 sp bf9aee4c error 4 in libc-2.15.so[b45000+1a4000]
[  124.728703] pcscd[3312]: segfault at 0 ip 00322021 sp bfee4f3c error 4 in libc-2.15.so[2a4000+1a4000]
[  125.746911] pcscd[3315]: segfault at 0 ip 00d24021 sp bfc8e2dc error 4 in libc-2.15.so[ca6000+1a4000]
[  126.763556] pcscd[3318]: segfault at 0 ip 00997021 sp bfd6b40c error 4 in libc-2.15.so[919000+1a4000]
[  127.785681] pcscd[3321]: segfault at 0 ip 007bf021 sp bfe6f86c error 4 in libc-2.15.so[741000+1a4000]
[  128.799465] pcscd[3324]: segfault at 0 ip 0018e021 sp bfc4493c error 4 in libc-2.15.so[110000+1a4000]
[  129.813584] pcscd[3327]: segfault at 0 ip 00e5b021 sp bfe49a8c error 4 in libc-2.15.so[ddd000+1a4000]
[  130.827556] pcscd[3330]: segfault at 0 ip 00300021 sp bfeb55ec error 4 in libc-2.15.so[282000+1a4000]
[  131.841568] pcscd[3333]: segfault at 0 ip 0018e021 sp bfc7268c error 4 in libc-2.15.so[110000+1a4000]
[  132.855505] pcscd[3336]: segfault at 0 ip 0099f021 sp bfb27e4c error 4 in libc-2.15.so[921000+1a4000]
[  133.870147] pcscd[3339]: segfault at 0 ip 0018e021 sp bf86a3fc error 4 in libc-2.15.so[110000+1a4000]
[  134.884458] pcscd[3342]: segfault at 0 ip 0018e021 sp bfebefbc error 4 in libc-2.15.so[110000+1a4000]
[  135.898344] pcscd[3345]: segfault at 0 ip 0018e021 sp bff5581c error 4 in libc-2.15.so[110000+1a4000]
[  136.913922] pcscd[3589]: segfault at 0 ip 002ba021 sp bfba329c error 4 in libc-2.15.so[23c000+1a4000]
[  137.928469] pcscd[3592]: segfault at 0 ip 0018e021 sp bfd72d9c error 4 in libc-2.15.so[110000+1a4000]
[  138.955490] pcscd[3595]: segfault at 0 ip 006b8021 sp bfd7326c error 4 in libc-2.15.so[63a000+1a4000]
[  139.969374] pcscd[3598]: segfault at 0 ip 00364021 sp bff1b6dc error 4 in libc-2.15.so[2e6000+1a4000]
[  140.997371] pcscd[3601]: segfault at 0 ip 004b7021 sp bfdfbd5c error 4 in libc-2.15.so[439000+1a4000]
[  142.011711] pcscd[3605]: segfault at 0 ip 0018e021 sp bfd29aec error 4 in libc-2.15.so[110000+1a4000]
[  143.026673] pcscd[3608]: segfault at 0 ip 00213021 sp bfa3c9ec error 4 in libc-2.15.so[195000+1a4000]
[  144.048710] pcscd[3613]: segfault at 0 ip 0060f021 sp bfb3153c error 4 in libc-2.15.so[591000+1a4000]
[  145.075221] pcscd[3616]: segfault at 0 ip 00227021 sp bffdc1ac error 4 in libc-2.15.so[1a9000+1a4000]
[  146.089670] pcscd[3619]: segfault at 0 ip 007e5021 sp bf86cd4c error 4 in libc-2.15.so[767000+1a4000]
[  147.104263] pcscd[3622]: segfault at 0 ip 004c1021 sp bf921b2c error 4 in libc-2.15.so[443000+1a4000]
[  148.118754] pcscd[3626]: segfault at 0 ip 0018e021 sp bfef667c error 4 in libc-2.15.so[110000+1a4000]
[  149.152977] pcscd[3630]: segfault at 0 ip 00b34021 sp bfb2e43c error 4 in libc-2.15.so[ab6000+1a4000]
[  150.166809] pcscd[3633]: segfault at 0 ip 0018e021 sp bf98e04c error 4 in libc-2.15.so[110000+1a4000]
[  151.180783] pcscd[3636]: segfault at 0 ip 006fc021 sp bfbc8bac error 4 in libc-2.15.so[67e000+1a4000]
[  152.194616] pcscd[3639]: segfault at 0 ip 0048b021 sp bff7e33c error 4 in libc-2.15.so[40d000+1a4000]
[  153.208728] pcscd[3642]: segfault at 0 ip 0030c021 sp bffa2dbc error 4 in libc-2.15.so[28e000+1a4000]
[  154.222839] pcscd[3645]: segfault at 0 ip 00b97021 sp bf9ff4bc error 4 in libc-2.15.so[b19000+1a4000]
[  155.255527] pcscd[3648]: segfault at 0 ip 005fa021 sp bfa733ac error 4 in libc-2.15.so[57c000+1a4000]
[  156.321393] pcscd[3832]: segfault at 0 ip 0019e021 sp bf8093ac error 4 in libc-2.15.so[120000+1a4000]
[  157.342020] pcscd[3896]: segfault at 0 ip 00886021 sp bfe6895c error 4 in libc-2.15.so[808000+1a4000]
[  158.366361] pcscd[3899]: segfault at 0 ip 0018e021 sp bf85046c error 4 in libc-2.15.so[110000+1a4000]
[  159.396301] pcscd[3902]: segfault at 0 ip 0018e021 sp bf9c96fc error 4 in libc-2.15.so[110000+1a4000]
[  160.432632] pcscd[3906]: segfault at 0 ip 0034f021 sp bf96540c error 4 in libc-2.15.so[2d1000+1a4000]
[  161.458596] pcscd[3910]: segfault at 0 ip 00261021 sp bfd3094c error 4 in libc-2.15.so[1e3000+1a4000]
[  162.474499] pcscd[3914]: segfault at 0 ip 0018e021 sp bfe497bc error 4 in libc-2.15.so[110000+1a4000]
[  163.508814] pcscd[3917]: segfault at 0 ip 002b1021 sp bfaf1dbc error 4 in libc-2.15.so[233000+1a4000]
[  164.529476] pcscd[3920]: segfault at 0 ip 0018e021 sp bfb4c33c error 4 in libc-2.15.so[110000+1a4000]
[  165.554303] pcscd[3923]: segfault at 0 ip 008dc021 sp bf93f54c error 4 in libc-2.15.so[85e000+1a4000]
[  166.570865] pcscd[3926]: segfault at 0 ip 00908021 sp bfd3a04c error 4 in libc-2.15.so[88a000+1a4000]
[  167.586829] pcscd[3929]: segfault at 0 ip 0018e021 sp bfe6d10c error 4 in libc-2.15.so[110000+1a4000]
[  168.602749] pcscd[3932]: segfault at 0 ip 003e9021 sp bfe47cfc error 4 in libc-2.15.so[36b000+1a4000]
[  169.618882] pcscd[3935]: segfault at 0 ip 00844021 sp bfa5d10c error 4 in libc-2.15.so[7c6000+1a4000]
[  170.637541] pcscd[3938]: segfault at 0 ip 00b0e021 sp bfb892cc error 4 in libc-2.15.so[a90000+1a4000]
[  171.662006] pcscd[3941]: segfault at 0 ip 002d2021 sp bf96c0cc error 4 in libc-2.15.so[254000+1a4000]
[  172.677729] pcscd[3944]: segfault at 0 ip 0019e021 sp bfda954c error 4 in libc-2.15.so[120000+1a4000]
[  173.695017] pcscd[3947]: segfault at 0 ip 00553021 sp bf845bdc error 4 in libc-2.15.so[4d5000+1a4000]
[  174.710578] pcscd[3950]: segfault at 0 ip 006a3021 sp bf9a2a9c error 4 in libc-2.15.so[625000+1a4000]
[  175.726753] pcscd[3953]: segfault at 0 ip 0074b021 sp bf9c334c error 4 in libc-2.15.so[6cd000+1a4000]
[  176.742616] pcscd[3956]: segfault at 0 ip 001ee021 sp bf81b5ec error 4 in libc-2.15.so[170000+1a4000]
[  177.759395] pcscd[4200]: segfault at 0 ip 00214021 sp bf92a60c error 4 in libc-2.15.so[196000+1a4000]
[  178.775608] pcscd[4203]: segfault at 0 ip 00370021 sp bfb3a11c error 4 in libc-2.15.so[2f2000+1a4000]
[  179.791526] pcscd[4206]: segfault at 0 ip 002d4021 sp bf904ebc error 4 in libc-2.15.so[256000+1a4000]
[  180.807465] pcscd[4209]: segfault at 0 ip 00220021 sp bfb6b9cc error 4 in libc-2.15.so[1a2000+1a4000]
[  181.828912] pcscd[4212]: segfault at 0 ip 001a9021 sp bff8419c error 4 in libc-2.15.so[12b000+1a4000]
[  182.844667] pcscd[4215]: segfault at 0 ip 00e93021 sp bfc93a3c error 4 in libc-2.15.so[e15000+1a4000]
[  183.860691] pcscd[4218]: segfault at 0 ip 00420021 sp bf913b6c error 4 in libc-2.15.so[3a2000+1a4000]
[  184.876742] pcscd[4221]: segfault at 0 ip 0018e021 sp bf874f6c error 4 in libc-2.15.so[110000+1a4000]
[  185.892797] pcscd[4224]: segfault at 0 ip 00d20021 sp bfa1702c error 4 in libc-2.15.so[ca2000+1a4000]
[  186.908733] pcscd[4227]: segfault at 0 ip 00432021 sp bf8de6ec error 4 in libc-2.15.so[3b4000+1a4000]
[  187.928605] pcscd[4230]: segfault at 0 ip 0018e021 sp bfbac1dc error 4 in libc-2.15.so[110000+1a4000]
[  188.944700] pcscd[4233]: segfault at 0 ip 0024d021 sp bf9fe40c error 4 in libc-2.15.so[1cf000+1a4000]
[  189.969742] pcscd[4236]: segfault at 0 ip 0018e021 sp bfb1e1dc error 4 in libc-2.15.so[110000+1a4000]
[  190.985689] pcscd[4239]: segfault at 0 ip 006a9021 sp bfef1aec error 4 in libc-2.15.so[62b000+1a4000]
[  192.002327] pcscd[4242]: segfault at 0 ip 00894021 sp bfad8afc error 4 in libc-2.15.so[816000+1a4000]
[  193.018628] pcscd[4245]: segfault at 0 ip 002ba021 sp bfd82e1c error 4 in libc-2.15.so[23c000+1a4000]
[  194.034611] pcscd[4248]: segfault at 0 ip 001b1021 sp bfa8534c error 4 in libc-2.15.so[133000+1a4000]
[  195.061580] pcscd[4251]: segfault at 0 ip 00296021 sp bfce346c error 4 in libc-2.15.so[218000+1a4000]
[  196.081900] pcscd[4256]: segfault at 0 ip 006ef021 sp bfa9357c error 4 in libc-2.15.so[671000+1a4000]
[  197.135796] pcscd[4315]: segfault at 0 ip 0018e021 sp bfe436cc error 4 in libc-2.15.so[110000+1a4000]
[  198.187716] pcscd[4503]: segfault at 0 ip 00b65021 sp bfd4268c error 4 in libc-2.15.so[ae7000+1a4000]
[  199.207831] pcscd[4506]: segfault at 0 ip 0018e021 sp bf9c685c error 4 in libc-2.15.so[110000+1a4000]
[  200.231068] pcscd[4509]: segfault at 0 ip 00646021 sp bf82b31c error 4 in libc-2.15.so[5c8000+1a4000]
[  201.255627] pcscd[4512]: segfault at 0 ip 008d5021 sp bff679bc error 4 in libc-2.15.so[857000+1a4000]
[  202.273140] pcscd[4515]: segfault at 0 ip 001bd021 sp bfeffc6c error 4 in libc-2.15.so[13f000+1a4000]
[  203.296746] pcscd[4518]: segfault at 0 ip 006d7021 sp bfa7bf4c error 4 in libc-2.15.so[659000+1a4000]
[  204.314728] pcscd[4521]: segfault at 0 ip 0032c021 sp bffeff7c error 4 in libc-2.15.so[2ae000+1a4000]
[  205.339007] pcscd[4524]: segfault at 0 ip 008b0021 sp bfd1db4c error 4 in libc-2.15.so[832000+1a4000]
[  206.374180] pcscd[4528]: segfault at 0 ip 0035e021 sp bf92616c error 4 in libc-2.15.so[2e0000+1a4000]
[  207.405994] pcscd[4531]: segfault at 0 ip 0032d021 sp bfc861dc error 4 in libc-2.15.so[2af000+1a4000]
[  208.435970] pcscd[4534]: segfault at 0 ip 00d05021 sp bfbd46cc error 4 in libc-2.15.so[c87000+1a4000]
[  209.466286] pcscd[4537]: segfault at 0 ip 00cde021 sp bfd0621c error 4 in libc-2.15.so[c60000+1a4000]
[  210.497883] pcscd[4540]: segfault at 0 ip 0018e021 sp bf99f3ec error 4 in libc-2.15.so[110000+1a4000]
[  211.526646] pcscd[4543]: segfault at 0 ip 001b6021 sp bfab98fc error 4 in libc-2.15.so[138000+1a4000]
[  212.562556] pcscd[4546]: segfault at 0 ip 0018e021 sp bf8840fc error 4 in libc-2.15.so[110000+1a4000]
[  213.579586] pcscd[4549]: segfault at 0 ip 00987021 sp bffa35dc error 4 in libc-2.15.so[909000+1a4000]
[  214.596100] pcscd[4552]: segfault at 0 ip 002d6021 sp bffccc7c error 4 in libc-2.15.so[258000+1a4000]
[  215.612455] pcscd[4555]: segfault at 0 ip 0018e021 sp bfb27c8c error 4 in libc-2.15.so[110000+1a4000]
[  216.637409] pcscd[4558]: segfault at 0 ip 001d9021 sp bfc6832c error 4 in libc-2.15.so[15b000+1a4000]
[  217.654273] pcscd[4561]: segfault at 0 ip 0092f021 sp bfc236cc error 4 in libc-2.15.so[8b1000+1a4000]
[  218.670794] pcscd[4805]: segfault at 0 ip 004c1021 sp bfc30a9c error 4 in libc-2.15.so[443000+1a4000]
[  219.686758] pcscd[4808]: segfault at 0 ip 00a89021 sp bfdb7d3c error 4 in libc-2.15.so[a0b000+1a4000]
[  220.702677] pcscd[4811]: segfault at 0 ip 0026b021 sp bfb6f30c error 4 in libc-2.15.so[1ed000+1a4000]
[  221.718805] pcscd[4814]: segfault at 0 ip 002cc021 sp bfbe213c error 4 in libc-2.15.so[24e000+1a4000]
[  222.734839] pcscd[4817]: segfault at 0 ip 00ecc021 sp bfc4871c error 4 in libc-2.15.so[e4e000+1a4000]
[  223.750758] pcscd[4820]: segfault at 0 ip 003d1021 sp bf860ffc error 4 in libc-2.15.so[353000+1a4000]
[  224.766688] pcscd[4823]: segfault at 0 ip 00ab0021 sp bfcd9acc error 4 in libc-2.15.so[a32000+1a4000]
[  225.782692] pcscd[4826]: segfault at 0 ip 0018e021 sp bf99c29c error 4 in libc-2.15.so[110000+1a4000]
[  226.798790] pcscd[4829]: segfault at 0 ip 0019e021 sp bf96664c error 4 in libc-2.15.so[120000+1a4000]
[  227.815702] pcscd[4832]: segfault at 0 ip 00464021 sp bfc7533c error 4 in libc-2.15.so[3e6000+1a4000]
[  228.831733] pcscd[4835]: segfault at 0 ip 00d1d021 sp bfab716c error 4 in libc-2.15.so[c9f000+1a4000]
[  229.847663] pcscd[4838]: segfault at 0 ip 0018e021 sp bfd4b5ec error 4 in libc-2.15.so[110000+1a4000]
[  230.863730] pcscd[4841]: segfault at 0 ip 004d3021 sp bfc64efc error 4 in libc-2.15.so[455000+1a4000]
[  231.879744] pcscd[4844]: segfault at 0 ip 00879021 sp bfe18adc error 4 in libc-2.15.so[7fb000+1a4000]
[  232.895670] pcscd[4847]: segfault at 0 ip 0063e021 sp bfb449fc error 4 in libc-2.15.so[5c0000+1a4000]
[  233.911694] pcscd[4850]: segfault at 0 ip 001ec021 sp bfbbdafc error 4 in libc-2.15.so[16e000+1a4000]
[  234.927683] pcscd[4853]: segfault at 0 ip 00dc7021 sp bfde874c error 4 in libc-2.15.so[d49000+1a4000]
[  235.943626] pcscd[4856]: segfault at 0 ip 001bb021 sp bfbd784c error 4 in libc-2.15.so[13d000+1a4000]
[  236.959600] pcscd[4859]: segfault at 0 ip 0019e021 sp bfa31f0c error 4 in libc-2.15.so[120000+1a4000]
[  237.976789] pcscd[4862]: segfault at 0 ip 001e1021 sp bfab32ac error 4 in libc-2.15.so[163000+1a4000]
[  238.992883] pcscd[5106]: segfault at 0 ip 0018e021 sp bfe5c77c error 4 in libc-2.15.so[110000+1a4000]
[  240.008853] pcscd[5109]: segfault at 0 ip 00391021 sp bf8da6dc error 4 in libc-2.15.so[313000+1a4000]
[  241.024903] pcscd[5112]: segfault at 0 ip 00be9021 sp bfde130c error 4 in libc-2.15.so[b6b000+1a4000]
[  242.040911] pcscd[5115]: segfault at 0 ip 0018e021 sp bfcd609c error 4 in libc-2.15.so[110000+1a4000]
[  243.056850] pcscd[5118]: segfault at 0 ip 00a23021 sp bfaaa54c error 4 in libc-2.15.so[9a5000+1a4000]
[  244.072947] pcscd[5121]: segfault at 0 ip 0023a021 sp bfe9e59c error 4 in libc-2.15.so[1bc000+1a4000]
[  245.088905] pcscd[5124]: segfault at 0 ip 00690021 sp bf9be98c error 4 in libc-2.15.so[612000+1a4000]
[  246.104887] pcscd[5127]: segfault at 0 ip 00d17021 sp bf9b63ac error 4 in libc-2.15.so[c99000+1a4000]
[  247.120832] pcscd[5130]: segfault at 0 ip 001dd021 sp bfcd73ac error 4 in libc-2.15.so[15f000+1a4000]
[  248.136811] pcscd[5133]: segfault at 0 ip 0026f021 sp bf9907ec error 4 in libc-2.15.so[1f1000+1a4000]
[  249.152847] pcscd[5136]: segfault at 0 ip 00238021 sp bfc975dc error 4 in libc-2.15.so[1ba000+1a4000]
[  250.168910] pcscd[5139]: segfault at 0 ip 008f3021 sp bfa0016c error 4 in libc-2.15.so[875000+1a4000]
[  251.184854] pcscd[5142]: segfault at 0 ip 00e40021 sp bff71d2c error 4 in libc-2.15.so[dc2000+1a4000]
[  252.200869] pcscd[5145]: segfault at 0 ip 00c32021 sp bf9ffc1c error 4 in libc-2.15.so[bb4000+1a4000]
[  253.216952] pcscd[5148]: segfault at 0 ip 00a31021 sp bf95aeac error 4 in libc-2.15.so[9b3000+1a4000]
[  254.232880] pcscd[5151]: segfault at 0 ip 0018e021 sp bff8de6c error 4 in libc-2.15.so[110000+1a4000]
[  255.248969] pcscd[5154]: segfault at 0 ip 0018e021 sp bfaf84fc error 4 in libc-2.15.so[110000+1a4000]
[  256.264910] pcscd[5157]: segfault at 0 ip 0029e021 sp bfa502dc error 4 in libc-2.15.so[220000+1a4000]
[  257.290008] pcscd[5160]: segfault at 0 ip 00307021 sp bfe77a0c error 4 in libc-2.15.so[289000+1a4000]
[  258.337239] pcscd[5404]: segfault at 0 ip 00276021 sp bffaef7c error 4 in libc-2.15.so[1f8000+1a4000]
[  259.353913] pcscd[5407]: segfault at 0 ip 00aea021 sp bf81c93c error 4 in libc-2.15.so[a6c000+1a4000]
[  260.369934] pcscd[5410]: segfault at 0 ip 0022c021 sp bff70ecc error 4 in libc-2.15.so[1ae000+1a4000]
[  261.386046] pcscd[5413]: segfault at 0 ip 0018e021 sp bfb4e1bc error 4 in libc-2.15.so[110000+1a4000]
[  262.401953] pcscd[5416]: segfault at 0 ip 001bc021 sp bff5ea0c error 4 in libc-2.15.so[13e000+1a4000]
[  263.418038] pcscd[5419]: segfault at 0 ip 0018e021 sp bfc9648c error 4 in libc-2.15.so[110000+1a4000]
[  264.434114] pcscd[5422]: segfault at 0 ip 00401021 sp bff6d79c error 4 in libc-2.15.so[383000+1a4000]
[  265.449885] pcscd[5425]: segfault at 0 ip 00ab3021 sp bfd6988c error 4 in libc-2.15.so[a35000+1a4000]
[  266.465899] pcscd[5428]: segfault at 0 ip 00536021 sp bfef064c error 4 in libc-2.15.so[4b8000+1a4000]
[  267.481857] pcscd[5431]: segfault at 0 ip 004af021 sp bfb4bb2c error 4 in libc-2.15.so[431000+1a4000]
[  268.498025] pcscd[5434]: segfault at 0 ip 003b1021 sp bfb28eec error 4 in libc-2.15.so[333000+1a4000]
[  269.513959] pcscd[5437]: segfault at 0 ip 00567021 sp bf9e800c error 4 in libc-2.15.so[4e9000+1a4000]
[  270.530034] pcscd[5440]: segfault at 0 ip 00a7c021 sp bfc90fbc error 4 in libc-2.15.so[9fe000+1a4000]
[  271.545976] pcscd[5443]: segfault at 0 ip 00c16021 sp bffb39bc error 4 in libc-2.15.so[b98000+1a4000]
[  272.561905] pcscd[5446]: segfault at 0 ip 00b6c021 sp bfe0f1ec error 4 in libc-2.15.so[aee000+1a4000]
[  273.577913] pcscd[5449]: segfault at 0 ip 00548021 sp bfcc1d8c error 4 in libc-2.15.so[4ca000+1a4000]
[  274.593940] pcscd[5452]: segfault at 0 ip 001a9021 sp bfb075ac error 4 in libc-2.15.so[12b000+1a4000]
[  275.610018] pcscd[5455]: segfault at 0 ip 0018e021 sp bf8b534c error 4 in libc-2.15.so[110000+1a4000]
[  276.625926] pcscd[5458]: segfault at 0 ip 00ea7021 sp bff36e0c error 4 in libc-2.15.so[e29000+1a4000]
[  277.641923] pcscd[5461]: segfault at 0 ip 002e8021 sp bfe0e9fc error 4 in libc-2.15.so[26a000+1a4000]
[  278.658086] pcscd[5464]: segfault at 0 ip 00a79021 sp bfb4070c error 4 in libc-2.15.so[9fb000+1a4000]
[  279.673953] pcscd[5708]: segfault at 0 ip 00cbd021 sp bfbd41dc error 4 in libc-2.15.so[c3f000+1a4000]
[  280.689968] pcscd[5711]: segfault at 0 ip 003aa021 sp bfe1162c error 4 in libc-2.15.so[32c000+1a4000]
[  281.706037] pcscd[5714]: segfault at 0 ip 00d7e021 sp bfdeac2c error 4 in libc-2.15.so[d00000+1a4000]
[  282.721944] pcscd[5717]: segfault at 0 ip 00436021 sp bf90d27c error 4 in libc-2.15.so[3b8000+1a4000]
[  283.737899] pcscd[5720]: segfault at 0 ip 0056e021 sp bfb48a1c error 4 in libc-2.15.so[4f0000+1a4000]
[  284.753863] pcscd[5723]: segfault at 0 ip 00cad021 sp bfd62c8c error 4 in libc-2.15.so[c2f000+1a4000]
[  285.769979] pcscd[5726]: segfault at 0 ip 0018e021 sp bfbbac7c error 4 in libc-2.15.so[110000+1a4000]
[  286.785841] pcscd[5729]: segfault at 0 ip 0023a021 sp bff7602c error 4 in libc-2.15.so[1bc000+1a4000]
[  287.801848] pcscd[5732]: segfault at 0 ip 0018e021 sp bfa08a7c error 4 in libc-2.15.so[110000+1a4000]
[  288.818624] pcscd[5735]: segfault at 0 ip 00e8c021 sp bff2770c error 4 in libc-2.15.so[e0e000+1a4000]
[  289.835298] pcscd[5738]: segfault at 0 ip 0018e021 sp bfc88a1c error 4 in libc-2.15.so[110000+1a4000]
[  290.851787] pcscd[5741]: segfault at 0 ip 0081b021 sp bf9781dc error 4 in libc-2.15.so[79d000+1a4000]
[  291.867827] pcscd[5744]: segfault at 0 ip 0095f021 sp bfc023cc error 4 in libc-2.15.so[8e1000+1a4000]
[  292.883810] pcscd[5747]: segfault at 0 ip 0019e021 sp bf8e419c error 4 in libc-2.15.so[120000+1a4000]
[  293.899936] pcscd[5750]: segfault at 0 ip 0018e021 sp bfb58b8c error 4 in libc-2.15.so[110000+1a4000]
[  294.917048] pcscd[5753]: segfault at 0 ip 00484021 sp bfdbbcfc error 4 in libc-2.15.so[406000+1a4000]
[  295.932934] pcscd[5756]: segfault at 0 ip 002db021 sp bffee4bc error 4 in libc-2.15.so[25d000+1a4000]
[  296.949073] pcscd[5759]: segfault at 0 ip 00304021 sp bf8b2e2c error 4 in libc-2.15.so[286000+1a4000]
[  297.965481] pcscd[5762]: segfault at 0 ip 0018f021 sp bfcc02bc error 4 in libc-2.15.so[111000+1a4000]
[  298.981955] pcscd[5765]: segfault at 0 ip 00974021 sp bfd12b3c error 4 in libc-2.15.so[8f6000+1a4000]
[  299.997955] pcscd[6009]: segfault at 0 ip 00d2d021 sp bfb62e6c error 4 in libc-2.15.so[caf000+1a4000]
[  301.013952] pcscd[6012]: segfault at 0 ip 00a95021 sp bf9e0dfc error 4 in libc-2.15.so[a17000+1a4000]
[  302.029897] pcscd[6015]: segfault at 0 ip 0018e021 sp bfe963dc error 4 in libc-2.15.so[110000+1a4000]
[  303.045890] pcscd[6018]: segfault at 0 ip 00c7a021 sp bf8cce0c error 4 in libc-2.15.so[bfc000+1a4000]
[  304.061890] pcscd[6021]: segfault at 0 ip 001a9021 sp bf8228fc error 4 in libc-2.15.so[12b000+1a4000]
[  304.656037] usb 3-1: USB disconnect, device number 2
[  305.077991] pcscd[6024]: segfault at 0 ip 0018e021 sp bfba5ddc error 4 in libc-2.15.so[110000+1a4000]
[  306.093880] pcscd[6027]: segfault at 0 ip 002cf021 sp bff21a6c error 4 in libc-2.15.so[251000+1a4000]
[  307.109963] pcscd[6030]: segfault at 0 ip 00aa5021 sp bfd04fac error 4 in libc-2.15.so[a27000+1a4000]
[  308.125999] pcscd[6033]: segfault at 0 ip 00abe021 sp bfc7c00c error 4 in libc-2.15.so[a40000+1a4000]
[  309.142046] pcscd[6036]: segfault at 0 ip 00ae5021 sp bfbfa51c error 4 in libc-2.15.so[a67000+1a4000]
[  309.344019] usb 3-1: new full-speed USB device number 3 using ohci_hcd
[  310.157911] pcscd[6042]: segfault at 0 ip 002cd021 sp bfe52c4c error 4 in libc-2.15.so[24f000+1a4000]
[  311.173954] pcscd[6045]: segfault at 0 ip 0046c021 sp bfe68e2c error 4 in libc-2.15.so[3ee000+1a4000]
[  312.189944] pcscd[6048]: segfault at 0 ip 0018e021 sp bfe3fadc error 4 in libc-2.15.so[110000+1a4000]
[  313.205988] pcscd[6051]: segfault at 0 ip 002c9021 sp bfba771c error 4 in libc-2.15.so[24b000+1a4000]
[  314.235496] pcscd[6054]: segfault at 0 ip 0034a021 sp bfec907c error 4 in libc-2.15.so[2cc000+1a4000]
[  315.271258] pcscd[6057]: segfault at 0 ip 0025b021 sp bfd714ac error 4 in libc-2.15.so[1dd000+1a4000]
[  316.298196] pcscd[6064]: segfault at 0 ip 00339021 sp bf81d95c error 4 in libc-2.15.so[2bb000+1a4000]
[  317.331337] pcscd[6067]: segfault at 0 ip 00313021 sp bfd8b4dc error 4 in libc-2.15.so[295000+1a4000]
[  318.350417] pcscd[6070]: segfault at 0 ip 00c7b021 sp bfe80f1c error 4 in libc-2.15.so[bfd000+1a4000]
[  319.375617] pcscd[6314]: segfault at 0 ip 00e2d021 sp bfbd09bc error 4 in libc-2.15.so[daf000+1a4000]
[  320.396079] pcscd[6317]: segfault at 0 ip 0018e021 sp bf952dbc error 4 in libc-2.15.so[110000+1a4000]
[  321.415169] pcscd[6320]: segfault at 0 ip 00332021 sp bff6cf7c error 4 in libc-2.15.so[2b4000+1a4000]
[  322.441393] pcscd[6323]: segfault at 0 ip 00271021 sp bfd39f9c error 4 in libc-2.15.so[1f3000+1a4000]
[  323.458191] pcscd[6326]: segfault at 0 ip 0052b021 sp bffa067c error 4 in libc-2.15.so[4ad000+1a4000]
[  324.487797] pcscd[6329]: segfault at 0 ip 001ea021 sp bfe2305c error 4 in libc-2.15.so[16c000+1a4000]
[  325.505163] pcscd[6332]: segfault at 0 ip 009b3021 sp bfbe0f0c error 4 in libc-2.15.so[935000+1a4000]
[  326.522208] pcscd[6335]: segfault at 0 ip 00b4b021 sp bffa670c error 4 in libc-2.15.so[acd000+1a4000]
[  327.539880] pcscd[6340]: segfault at 0 ip 00587021 sp bfc567ac error 4 in libc-2.15.so[509000+1a4000]
[  328.567704] pcscd[6343]: segfault at 0 ip 00c40021 sp bf96bf7c error 4 in libc-2.15.so[bc2000+1a4000]
[  329.585378] pcscd[6346]: segfault at 0 ip 005c6021 sp bfa7f91c error 4 in libc-2.15.so[548000+1a4000]
[  330.610509] pcscd[6349]: segfault at 0 ip 00a0f021 sp bf8c6f2c error 4 in libc-2.15.so[991000+1a4000]
[  331.639321] pcscd[6352]: segfault at 0 ip 0018e021 sp bffbbc8c error 4 in libc-2.15.so[110000+1a4000]
[  332.668356] pcscd[6355]: segfault at 0 ip 005e5021 sp bffc101c error 4 in libc-2.15.so[567000+1a4000]
[  333.686191] pcscd[6358]: segfault at 0 ip 00d60021 sp bfbc82dc error 4 in libc-2.15.so[ce2000+1a4000]
[  334.709625] pcscd[6361]: segfault at 0 ip 0088e021 sp bfc9ce1c error 4 in libc-2.15.so[810000+1a4000]
[  335.739944] pcscd[6365]: segfault at 0 ip 002df021 sp bfd1091c error 4 in libc-2.15.so[261000+1a4000]
[  336.766196] pcscd[6368]: segfault at 0 ip 0018e021 sp bff2e35c error 4 in libc-2.15.so[110000+1a4000]
[  337.783793] pcscd[6371]: segfault at 0 ip 0018e021 sp bfafadbc error 4 in libc-2.15.so[110000+1a4000]
[  338.804826] pcscd[6374]: segfault at 0 ip 00682021 sp bf89360c error 4 in libc-2.15.so[604000+1a4000]
[  339.822206] pcscd[6618]: segfault at 0 ip 007ef021 sp bfb9684c error 4 in libc-2.15.so[771000+1a4000]
[  340.850643] pcscd[6621]: segfault at 0 ip 00219021 sp bfbb3e0c error 4 in libc-2.15.so[19b000+1a4000]
[  341.887347] pcscd[6625]: segfault at 0 ip 0018e021 sp bf9718ac error 4 in libc-2.15.so[110000+1a4000]
[  342.915924] pcscd[6628]: segfault at 0 ip 0068a021 sp bff95adc error 4 in libc-2.15.so[60c000+1a4000]
[  343.955039] pcscd[6631]: segfault at 0 ip 00d38021 sp bfcb904c error 4 in libc-2.15.so[cba000+1a4000]
[  344.974406] pcscd[6634]: segfault at 0 ip 00416021 sp bfa0c02c error 4 in libc-2.15.so[398000+1a4000]
[  345.991017] pcscd[6637]: segfault at 0 ip 0019e021 sp bff06fac error 4 in libc-2.15.so[120000+1a4000]
[  347.007012] pcscd[6640]: segfault at 0 ip 0018e021 sp bfa9f85c error 4 in libc-2.15.so[110000+1a4000]
[  348.025015] pcscd[6643]: segfault at 0 ip 00c3b021 sp bf867dcc error 4 in libc-2.15.so[bbd000+1a4000]
[  349.042483] pcscd[6646]: segfault at 0 ip 0043d021 sp bf8cf70c error 4 in libc-2.15.so[3bf000+1a4000]
[  350.059039] pcscd[6649]: segfault at 0 ip 0018e021 sp bf9a249c error 4 in libc-2.15.so[110000+1a4000]
[  351.087037] pcscd[6652]: segfault at 0 ip 0018e021 sp bf93584c error 4 in libc-2.15.so[110000+1a4000]
[  352.105196] pcscd[6655]: segfault at 0 ip 0018e021 sp bfbc9fac error 4 in libc-2.15.so[110000+1a4000]
[  353.122975] pcscd[6658]: segfault at 0 ip 0018e021 sp bfaba7fc error 4 in libc-2.15.so[110000+1a4000]
[  354.141576] pcscd[6661]: segfault at 0 ip 0051f021 sp bfc557cc error 4 in libc-2.15.so[4a1000+1a4000]
[  355.168159] pcscd[6664]: segfault at 0 ip 006f6021 sp bf9dbe8c error 4 in libc-2.15.so[678000+1a4000]
[  356.187135] pcscd[6667]: segfault at 0 ip 00c4a021 sp bfb7c77c error 4 in libc-2.15.so[bcc000+1a4000]
[  357.221624] pcscd[6670]: segfault at 0 ip 0018e021 sp bfe5eedc error 4 in libc-2.15.so[110000+1a4000]
[  358.244884] pcscd[6673]: segfault at 0 ip 0037e021 sp bfcda5ec error 4 in libc-2.15.so[300000+1a4000]
[  359.294593] pcscd[6886]: segfault at 0 ip 00303021 sp bf9c6a5c error 4 in libc-2.15.so[285000+1a4000]
[  360.326820] pcscd[6920]: segfault at 0 ip 00869021 sp bfcfa66c error 4 in libc-2.15.so[7eb000+1a4000]
[  361.343690] pcscd[6923]: segfault at 0 ip 00c69021 sp bfd5465c error 4 in libc-2.15.so[beb000+1a4000]
[  362.362716] pcscd[6926]: segfault at 0 ip 001b8021 sp bfdf666c error 4 in libc-2.15.so[13a000+1a4000]
[  363.390166] pcscd[6929]: segfault at 0 ip 0018e021 sp bfa4f5ac error 4 in libc-2.15.so[110000+1a4000]
[  364.407183] pcscd[6932]: segfault at 0 ip 0018e021 sp bfe7d6fc error 4 in libc-2.15.so[110000+1a4000]
[  365.424176] pcscd[6935]: segfault at 0 ip 00200021 sp bfe0bfcc error 4 in libc-2.15.so[182000+1a4000]
[  366.440174] pcscd[6938]: segfault at 0 ip 00a2d021 sp bfe1e33c error 4 in libc-2.15.so[9af000+1a4000]
[  367.456401] pcscd[6941]: segfault at 0 ip 0045d021 sp bfd4431c error 4 in libc-2.15.so[3df000+1a4000]
[  368.473386] pcscd[6944]: segfault at 0 ip 0037e021 sp bf9ec53c error 4 in libc-2.15.so[300000+1a4000]
[  369.490357] pcscd[6947]: segfault at 0 ip 0018e021 sp bf8e04fc error 4 in libc-2.15.so[110000+1a4000]
[  370.507240] pcscd[6950]: segfault at 0 ip 00200021 sp bfa1babc error 4 in libc-2.15.so[182000+1a4000]
[  371.524234] pcscd[6954]: segfault at 0 ip 002c7021 sp bff6a6dc error 4 in libc-2.15.so[249000+1a4000]
[  372.554637] pcscd[6957]: segfault at 0 ip 0018e021 sp bf82c56c error 4 in libc-2.15.so[110000+1a4000]
[  373.573052] pcscd[6960]: segfault at 0 ip 009ce021 sp bfc8233c error 4 in libc-2.15.so[950000+1a4000]
[  374.589333] pcscd[6963]: segfault at 0 ip 00340021 sp bff95cac error 4 in libc-2.15.so[2c2000+1a4000]
[  375.606215] pcscd[6966]: segfault at 0 ip 003d4021 sp bf8abc7c error 4 in libc-2.15.so[356000+1a4000]
[  376.623330] pcscd[6969]: segfault at 0 ip 001ab021 sp bf8cabbc error 4 in libc-2.15.so[12d000+1a4000]
[  377.640202] pcscd[6972]: segfault at 0 ip 004e6021 sp bfe1b79c error 4 in libc-2.15.so[468000+1a4000]
[  378.657325] pcscd[6975]: segfault at 0 ip 001e2021 sp bfb9ad6c error 4 in libc-2.15.so[164000+1a4000]
[  379.674357] pcscd[6978]: segfault at 0 ip 006e0021 sp bf8de77c error 4 in libc-2.15.so[662000+1a4000]
[  380.691660] pcscd[7222]: segfault at 0 ip 0018e021 sp bfbf679c error 4 in libc-2.15.so[110000+1a4000]
[  381.709608] pcscd[7225]: segfault at 0 ip 007b6021 sp bfb3466c error 4 in libc-2.15.so[738000+1a4000]
[  382.726972] pcscd[7228]: segfault at 0 ip 00e40021 sp bf93a69c error 4 in libc-2.15.so[dc2000+1a4000]
[  383.743805] pcscd[7231]: segfault at 0 ip 00795021 sp bfc04b3c error 4 in libc-2.15.so[717000+1a4000]
[  384.767999] pcscd[7234]: segfault at 0 ip 003e6021 sp bf9f40ec error 4 in libc-2.15.so[368000+1a4000]
[  385.793171] pcscd[7237]: segfault at 0 ip 003a7021 sp bffe783c error 4 in libc-2.15.so[329000+1a4000]
[  386.819483] pcscd[7240]: segfault at 0 ip 0018e021 sp bfba096c error 4 in libc-2.15.so[110000+1a4000]
[  387.837451] pcscd[7243]: segfault at 0 ip 0018e021 sp bf96f95c error 4 in libc-2.15.so[110000+1a4000]
[  388.855961] pcscd[7246]: segfault at 0 ip 0018e021 sp bf8d4f8c error 4 in libc-2.15.so[110000+1a4000]
[  389.872268] pcscd[7249]: segfault at 0 ip 002c8021 sp bfeb3a0c error 4 in libc-2.15.so[24a000+1a4000]
[  390.889390] pcscd[7252]: segfault at 0 ip 002e0021 sp bf83b03c error 4 in libc-2.15.so[262000+1a4000]
[  391.906298] pcscd[7255]: segfault at 0 ip 0018e021 sp bf82265c error 4 in libc-2.15.so[110000+1a4000]
[  392.923292] pcscd[7258]: segfault at 0 ip 0023f021 sp bfa4fffc error 4 in libc-2.15.so[1c1000+1a4000]
[  393.940502] pcscd[7261]: segfault at 0 ip 0024a021 sp bfe50c5c error 4 in libc-2.15.so[1cc000+1a4000]
[  394.957427] pcscd[7264]: segfault at 0 ip 00eb8021 sp bfc87e3c error 4 in libc-2.15.so[e3a000+1a4000]
[  395.982578] pcscd[7267]: segfault at 0 ip 002e8021 sp bfc78d6c error 4 in libc-2.15.so[26a000+1a4000]
[  397.000608] pcscd[7270]: segfault at 0 ip 0040b021 sp bfe5561c error 4 in libc-2.15.so[38d000+1a4000]
[  398.030158] pcscd[7273]: segfault at 0 ip 0083a021 sp bfcdfdec error 4 in libc-2.15.so[7bc000+1a4000]
[  399.047913] pcscd[7276]: segfault at 0 ip 0018e021 sp bfae25ac error 4 in libc-2.15.so[110000+1a4000]
[  400.077133] pcscd[7279]: segfault at 0 ip 0018e021 sp bfa4adac error 4 in libc-2.15.so[110000+1a4000]
[  401.104272] pcscd[7342]: segfault at 0 ip 0018e021 sp bf9f50bc error 4 in libc-2.15.so[110000+1a4000]
[  402.132785] pcscd[7526]: segfault at 0 ip 003e0021 sp bf88e09c error 4 in libc-2.15.so[362000+1a4000]
[  403.165487] pcscd[7529]: segfault at 0 ip 00596021 sp bfd57edc error 4 in libc-2.15.so[518000+1a4000]
[  404.193175] pcscd[7532]: segfault at 0 ip 00277021 sp bfc6d5dc error 4 in libc-2.15.so[1f9000+1a4000]
[  405.212292] pcscd[7535]: segfault at 0 ip 00644021 sp bff44a4c error 4 in libc-2.15.so[5c6000+1a4000]
[  406.230261] pcscd[7538]: segfault at 0 ip 00388021 sp bf8d045c error 4 in libc-2.15.so[30a000+1a4000]
[  407.287923] pcscd[7541]: segfault at 0 ip 006fe021 sp bfbdcb0c error 4 in libc-2.15.so[680000+1a4000]
[  408.306527] pcscd[7544]: segfault at 0 ip 0018e021 sp bff8ff3c error 4 in libc-2.15.so[110000+1a4000]
[  409.323361] pcscd[7547]: segfault at 0 ip 0018e021 sp bff104bc error 4 in libc-2.15.so[110000+1a4000]
[  410.343304] pcscd[7550]: segfault at 0 ip 00c0c021 sp bfbe1cfc error 4 in libc-2.15.so[b8e000+1a4000]
[  411.364765] pcscd[7553]: segfault at 0 ip 001fa021 sp bfc4135c error 4 in libc-2.15.so[17c000+1a4000]
[  412.384563] pcscd[7556]: segfault at 0 ip 0018e021 sp bfdc6b1c error 4 in libc-2.15.so[110000+1a4000]
[  413.406028] pcscd[7559]: segfault at 0 ip 0024c021 sp bf93240c error 4 in libc-2.15.so[1ce000+1a4000]
[  414.430522] pcscd[7562]: segfault at 0 ip 0018e021 sp bfd77e6c error 4 in libc-2.15.so[110000+1a4000]
[  415.448153] pcscd[7565]: segfault at 0 ip 0018e021 sp bffeca0c error 4 in libc-2.15.so[110000+1a4000]
[  416.465209] pcscd[7568]: segfault at 0 ip 005cb021 sp bffd833c error 4 in libc-2.15.so[54d000+1a4000]
[  417.482508] pcscd[7571]: segfault at 0 ip 001b4021 sp bff44cec error 4 in libc-2.15.so[136000+1a4000]
[  418.505531] pcscd[7574]: segfault at 0 ip 0024d021 sp bfebb8dc error 4 in libc-2.15.so[1cf000+1a4000]
[  419.522842] pcscd[7577]: segfault at 0 ip 0018e021 sp bf96150c error 4 in libc-2.15.so[110000+1a4000]
[  420.549978] pcscd[7580]: segfault at 0 ip 00d6e021 sp bffe9c8c error 4 in libc-2.15.so[cf0000+1a4000]
[  421.582468] pcscd[7839]: segfault at 0 ip 0018e021 sp bfec20ac error 4 in libc-2.15.so[110000+1a4000]
[  422.708343] pcscd[7883]: segfault at 0 ip 00d2e021 sp bff2a6cc error 4 in libc-2.15.so[cb0000+1a4000]
[  423.725883] pcscd[7903]: segfault at 0 ip 00d78021 sp bf98723c error 4 in libc-2.15.so[cfa000+1a4000]
[  424.755872] pcscd[7906]: segfault at 0 ip 0018e021 sp bfa3d2ac error 4 in libc-2.15.so[110000+1a4000]
[  425.773420] pcscd[7909]: segfault at 0 ip 0018e021 sp bf8df63c error 4 in libc-2.15.so[110000+1a4000]
[  426.793613] pcscd[7912]: segfault at 0 ip 008f1021 sp bfc73c9c error 4 in libc-2.15.so[873000+1a4000]
[  427.810887] pcscd[7915]: segfault at 0 ip 00c62021 sp bfc6a2ac error 4 in libc-2.15.so[be4000+1a4000]
[  428.827814] pcscd[7918]: segfault at 0 ip 0018e021 sp bf9a9f6c error 4 in libc-2.15.so[110000+1a4000]
[  429.850279] pcscd[7921]: segfault at 0 ip 0018e021 sp bfa4b5ec error 4 in libc-2.15.so[110000+1a4000]
[  430.868254] pcscd[7924]: segfault at 0 ip 00520021 sp bfa5ad3c error 4 in libc-2.15.so[4a2000+1a4000]
[  431.902290] pcscd[7927]: segfault at 0 ip 0030f021 sp bf8778dc error 4 in libc-2.15.so[291000+1a4000]
[  432.920449] pcscd[7930]: segfault at 0 ip 0018e021 sp bfa157bc error 4 in libc-2.15.so[110000+1a4000]
[  433.938794] pcscd[7933]: segfault at 0 ip 002ad021 sp bfdf8f3c error 4 in libc-2.15.so[22f000+1a4000]
[  434.966059] pcscd[7936]: segfault at 0 ip 00441021 sp bfc4f71c error 4 in libc-2.15.so[3c3000+1a4000]
[  435.990303] pcscd[7939]: segfault at 0 ip 00499021 sp bfd109ec error 4 in libc-2.15.so[41b000+1a4000]
[  437.020829] pcscd[7942]: segfault at 0 ip 0018e021 sp bfff506c error 4 in libc-2.15.so[110000+1a4000]
[  438.083078] pcscd[7945]: segfault at 0 ip 00bde021 sp bfce834c error 4 in libc-2.15.so[b60000+1a4000]
[  439.106939] pcscd[7948]: segfault at 0 ip 004c0021 sp bff14b5c error 4 in libc-2.15.so[442000+1a4000]
[  440.123488] pcscd[7951]: segfault at 0 ip 002df021 sp bfbdd17c error 4 in libc-2.15.so[261000+1a4000]

here the versions:

$ apt-cache show opensc libccid libacr38u
Package: opensc
Priority: optional
Section: universe/utils
Installed-Size: 2322
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Eric Dorland <eric@debian.org>
Architecture: i386
Version: 0.12.2-2ubuntu1
Replaces: libopensc2 (<< 0.12.0)
Depends: pcscd, libc6 (>= 2.11), libltdl7 (>= 2.4.2), libreadline6 (>= 6.0), libssl1.0.0 (>= 1.0.0), zlib1g (>= 1:1.1.4)
Conflicts: libopensc2 (<< 0.12.0), mozilla-opensc
Filename: pool/universe/o/opensc/opensc_0.12.2-2ubuntu1_i386.deb
Size: 917692
MD5sum: d4a45f9a2bc8dd0b216ad2eea891a166
SHA1: 5f05fdce3fe3e9cc2646cabbe5d3314a31be7b3b
SHA256: 3b12040e121193a30bde37990bcce7ad74514d941a29a526a9e8c573b9b7d7fc
Description-en: Smart card utilities with support for PKCS#15 compatible cards
 OpenSC provides a set of libraries and utilities to access smart
 cards.  It mainly focuses on cards that support cryptographic
 operations. It facilitates their use in security applications such as
 mail encryption, authentication, and digital signature. OpenSC
 implements the PKCS#11 API. Applications supporting this API, such as
 Iceweasel and Icedove, can use it. OpenSC implements the PKCS#15
 standard and aims to be compatible with all software that does so as
 well.
 .
 Before purchasing any cards, please read carefully documentation in
 /usr/share/doc/opensc/html/wiki/index.html - only some cards are
 supported. Not only does card type matters, but also card version,
 card OS version and preloaded applet. Only a subset of possible
 operations may be supported for your card. Card initialization may
 require third party proprietary software.
Homepage: [http://www.opensc-project.org/](http://www.opensc-project.org/)
Description-md5: 0719d649dde173c24420e7f6ca8ce42d
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: libccid
Status: install ok installed
Priority: extra
Section: libs
Installed-Size: 313
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: ccid
Version: 1.4.12-1
Provides: pcsc-ifd-handler
Depends: libc6 (>= 2.15), libusb-1.0-0 (>= 2:1.0.8)
Suggests: pcmciautils
Conffiles:
 /etc/libccid_Info.plist 2954570f6efded7373fc709bf5af7b24
 /etc/reader.conf.d/libccidtwin 8e8aaa7efa4ac575ba218255bbf1ecbe
Description-en: PC/SC driver for USB CCID smart card readers
 This library provides a PC/SC IFD handler implementation for the USB smart
 card drivers compliant to the CCID protocol.
 .
 This package is needed to communicate with the CCID smartcard readers through
 the PC/SC Lite resource manager (pcscd).
 .
 For an exhaustive list of supported reader see
 [http://pcsclite.alioth.debian.org/section.html](http://pcsclite.alioth.debian.org/section.html)
 .
 This driver also supports the GemPC Twin connected to a serial port and
 the GemPC Card (PCMCIA, through the suggested pcmciautils package) and
 Gemplus GemPC Express (Express54 card).
Original-Maintainer: Ludovic Rousseau <rousseau@debian.org>
Homepage: [http://pcsclite.alioth.debian.org/ccid.html](http://pcsclite.alioth.debian.org/ccid.html)

Package: libccid
Priority: extra
Section: universe/libs
Installed-Size: 294
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Ludovic Rousseau <rousseau@debian.org>
Architecture: i386
Source: ccid
Version: 1.4.5-1
Provides: pcsc-ifd-handler
Depends: libc6 (>= 2.7), libusb-1.0-0 (>= 2:1.0.8)
Suggests: pcmciautils
Filename: pool/universe/c/ccid/libccid_1.4.5-1_i386.deb
Size: 107664
MD5sum: ae53d01c7a0bd6f16b88ca6310887218
SHA1: 8b7f17600e1b4455f01424835691e5b8e4afe703
SHA256: b11a930a346970ec9dc46c6fb5909e3d7fa0feda1dc0e428fc0e4ecf69b1cbbd
Description-en: PC/SC driver for USB CCID smart card readers
 This library provides a PC/SC IFD handler implementation for the USB smart
 card drivers compliant to the CCID protocol.
 .
 This package is needed to communicate with the CCID smartcard readers through
 the PC/SC Lite resource manager (pcscd).
 .
 For an exhaustive list of supported reader see
 [http://pcsclite.alioth.debian.org/section.html](http://pcsclite.alioth.debian.org/section.html)
 .
 This driver also supports the GemPC Twin connected to a serial port and
 the GemPC Card (PCMCIA, through the suggested pcmciautils package) and
 Gemplus GemPC Express (Express54 card).
Homepage: [http://pcsclite.alioth.debian.org/ccid.html](http://pcsclite.alioth.debian.org/ccid.html)
Description-md5: 0526431951af10123a8e2fba4694ad49
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: libacr38u
Priority: extra
Section: universe/libs
Installed-Size: 102
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Laurent Bigonville <bigon@debian.org>
Architecture: i386
Source: acr38
Version: 1.7.11-1
Provides: pcsc-ifd-handler
Depends: libc6 (>= 2.4), libusb-0.1-4 (>= 2:0.1.12)
Recommends: pcscd
Filename: pool/universe/a/acr38/libacr38u_1.7.11-1_i386.deb
Size: 21064
MD5sum: 5fc7bc654b99d6c553b2dd29441e30d6
SHA1: 1ce388a9185a85a81632d18870a9f3185da9a9b7
SHA256: 67c85581bcbb809dd82c355a03887285f04fa1e7a0760bd4b20c78d4f3ae3881
Description-en: PC/SC driver for the ACR38U smart card reader
 This library provides a PC/SC IFD handler implementation for the ACS
 ACR38U smart card readers. This driver is for the non-CCID version only.
 .
 This package is needed to communicate with the ACR38U smartcard
 readers through the PC/SC Lite resource manager (pcscd).
Homepage: [http://www.acs.com.hk/](http://www.acs.com.hk/)
Description-md5: ecee1412b8c0970b38311b7862321c95
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

$ uname -a
Linux docente-Aspire-X3810 3.2.0-55-generic-pae #85-Ubuntu SMP Wed Oct 2 14:03:15 UTC 2013 i686 i686 i386 GNU/Linux

---

### Post by mörgæs on 2014-01-21
It seems like you are using an old Ubuntu release.

As a general approach (admittedly I don't know the card reader you are talking of) when dealing with hardware support I would begin with trying 13.10 and 14.04.

---

