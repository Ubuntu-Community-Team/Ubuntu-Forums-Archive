---
title: "Edimax EW-7711ULC working"
date: 2015-06-20
forum: Hardware
---

### Post by aardwolf2 on 2015-06-20
As I couldn't find any working instructions to get this adaptor working I just wanted to post this somewhere others can hopefully find it.

After bouncing around the web for days looking for a solution, and the Edimax drivers refusing to compile on newer kernels I eventually found that this adaptor, well the one I have anyway, uses the Mediatek MT7610u chip, I found that this lovely person had done the hard work and published these instructions for compiling a driver for an adaptor that uses that chip, and compiles on later kernels (I'm on 3.19.0.21 and it worked after the modification detailed below).

[http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)

 they didn't work :( Fortunately the instructions include the details on which files were changed to get it to work, a quick read and I realised the vendor and product ID were required in the config files, and as these instructions were written for a different adaptor they weren't included, so after doing the git clone instruction cd into the mediatek_mt7610u_sta_driver_linux-64bit/common directory, edit the rtusb_dev_id.c file and add the line

{USB_DEVICE(0x7392,0xa711)}, /* MT7610U */

after the other USB_DEVICE entries in the file, save the file,  go back to the mediatek_mt7610u_sta_driver_linux-64bit directory

then follow the original instructions from "make clean" and I had a working EW-7711ULC adaptor.

Note that I found on my router (RTN66U) that setting 20/40 mode meant that my wifi wasn't detected, I had to set either 20 or 40 mode.

<edit>Something to do with my router as changing any setting meant my wifi wasn't detected any more, the neighbours network was detected so I knew the adaptor was working, disabling wifi and re-enabling on the PC and it sees my network</edit>
 
Hope this helps others.

---

### Post by alfred7 on 2015-07-22
Great, your post make me think it should be working under Vivid; finally I find TLP auto-suspend it causing it not work properly.

---

### Post by george-bungarzescu on 2015-12-15
Are you shure is about the ULC version of the adapter ?

I have an ubuntu 15.10 (and a virtualbox with ubuntu14 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux ).

I have tried all drivers i have found: the single one that was builded (on virtualbox ) without "error" was the Tp-link Archer T1U driver from tp link site -> unfortunately the driver is somehow different i was unable to ifconfig ra0 up even the driver was (after id adding ) loaded.

On 3.16.0-30 generic stock kernel , folowing instructions from Archer site (doc for linux build), the "original" drivers from Edimax (both gpl 1.0 and linux 1.1 packages ) and mediatek driver fail to build with a complain about not able to cast from getssid to internal ssid struct and other "warning treating as errors"  error.

I don`t rememeber exactly what was the problem with the driver you have posted but i will check.

After all tests, i believe the patched driver (hprath) was the one i was able to load and see wifi networks but it freeze the computer. Not tested in vbox but i will give a try again.

So, any advice will be usefull.

George

After spending some time with my problem i can say the following:


On Ubuntu 16.04 x86_64 with kernel 3.16.0-30 - it works both edimax 1.1 (at this time on edimax site ) linux kernel (it seem to be identical with the 2.2. mediatek driver on mediatek site )  and [http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)

The main diferences are (and apply also to 4.x.xx kernels !) :
1. the edimax driver complain about not finding RT2870.dat file (not 2860.dat file that the driver provide ). Also, after feeding with correct file, it can be used somehow.
It require:
modprobe mt75xx.ko (load kernel module)
at this time if you issue 
ifconfig ra0 
you will see NO HWAddr (mac) on the ra0.
next 
ifconfig ra0 up
at this moment, it will complain about RT2870.dat (see dmesg complete path)
if you feed with hprath provided RT2870 config file but if succesfull you will see the mac on ifconfig ra0

in order to be able to build the driver without error you have to fix __DATE__ and __TIME__ macros and also a fs security struct  
which is defined fsuid /fsgid (just search for fsuid in the source tree )  and need be replaced
 from int to kgid_t (and also kuid_t for fsuid) like this (file include/os/rt_linux.h)

typedef struct _OS_FS_INFO_
{
    kuid_t                fsuid; // in original driver file is int
    kgid_t                fsgid; // in in original instead kgid_t
    mm_segment_t    fs;
} OS_FS_INFO;

2. with hprath will work from the begining and also 
3. Neither will work on vbox guest ubuntu 14.0.3 on windows host - both complain about not being able to load firmware.
ERROR!!! NICLoadFirmware failed, Status[=0x00000001]

You have to deal with os/linux/config.mk settings in order to find best build options in order the adapter to work with wpa_supplicant and NetworkManager. Do not forget to make clean before make ;)

Take a look also bellow (important).


On the 4.x.xx kernels (original kernels for 16.04) you can compile the 
but you have to deal with more problems:
like EEPROM 0x02 must be 0x01
also, neither drivers won`t load RT2870 file because of a strange error 
"no file read method"
([https://gist.github.com/moutend/cb35a37297910c99d3e2](https://gist.github.com/moutend/cb35a37297910c99d3e2) can provide more suggestion in order to fix this )

if you issue, after ra0 up, iwpriv command, the adapter will work, but the connection will be very slow

iwpriv ra0 set WirelessMode=8 //iwconfig will show 5Ghz after that instead on 2.5Ghz on 

some more NetworkManager restart may be required.



Please note that an ath9k will show IEEE8... on iwconfig - strings that are missing from iwconfig ra0

No need to restart

Note: if you feed the driver with wpa_supplicant -ira0 -c/some_wpa_config -Dwext some strange things happens including usb device disconnect... maybe more things to investigate

After some more research
 in cmm_cfg.c

```
static UCHAR CFG_WMODE_MAP[]={
    PHY_11BG_MIXED, (WMODE_B | WMODE_G), /* 0 => B/G mixed */
    PHY_11B, (WMODE_B), /* 1 => B only */
    PHY_11A, (WMODE_A), /* 2 => A only */
    PHY_11ABG_MIXED, (WMODE_A | WMODE_B | WMODE_G), /* 3 => A/B/G mixed */
    PHY_11G, WMODE_G, /* 4 => G only */
    PHY_11ABGN_MIXED, (WMODE_B | WMODE_G | WMODE_GN | WMODE_A | WMODE_AN), /* 5 => A/B/G/GN/AN mixed */
    PHY_11N_2_4G, (WMODE_GN), /* 6 => N in 2.4G band only */
    PHY_11GN_MIXED, (WMODE_G | WMODE_GN), /* 7 => G/GN, i.e., no CCK mode */
    PHY_11AN_MIXED, (WMODE_A | WMODE_AN), /* 8 => A/N in 5 band */
    PHY_11BGN_MIXED, (WMODE_B | WMODE_G | WMODE_GN), /* 9 => B/G/GN mode*/
    PHY_11AGN_MIXED, (WMODE_G | WMODE_GN | WMODE_A | WMODE_AN), /* 10 => A/AN/G/GN mode, not support B mode */
    PHY_11N_5G, (WMODE_AN), /* 11 => only N in 5G band */
#ifdef DOT11_VHT_AC
    PHY_11VHT_N_ABG_MIXED, (WMODE_B | WMODE_G | WMODE_GN |WMODE_A | WMODE_AN | WMODE_AC), /* 12 => B/G/GN/A/AN/AC mixed*/
    PHY_11VHT_N_AG_MIXED, (WMODE_G | WMODE_GN |WMODE_A | WMODE_AN | WMODE_AC), /* 13 => G/GN/A/AN/AC mixed , no B mode */
    PHY_11VHT_N_A_MIXED, (WMODE_A | WMODE_AN | WMODE_AC), /* 14 => A/AC/AN mixed */
    PHY_11VHT_N_MIXED, (WMODE_AN | WMODE_AC), /* 15 => AC/AN mixed, but no A mode */
#endif /* DOT11_VHT_AC */
    PHY_MODE_MAX, WMODE_INVALID /* default phy mode if not match */
};
```

---

### Post by cheetodust on 2016-08-16
Hey Im new to linux.  And I can not find a way to access the file rtusb_dev_id.c.  could you help me out

---

