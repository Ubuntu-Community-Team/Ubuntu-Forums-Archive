---
title: "Debugging ACPI DSDT on HP Pavilion X2 10-n109"
date: 2015-12-25
forum: Hardware
---

### Post by tmshlvck on 2015-12-25
Hi! I just tried Ubuntu (15.10) on HP Pavilion X2 10-n109nc. Problems:


- With default kernel, there are lot of random hangs, no wifi NIC support, no sound, no camera and no battery indicator.


- With latest custom kernel (4.4-rc7) it seems to be more stable but still sound + battery indicator do not work. It looks like ACPI-related problem. The SST sound is based on some B&O-branded Conexant codec, which seems to have no support in Linux currently.


- ACPI DSDT table seems to be a bit Linux-unfriendly. Look below for more info about DSDT hacking. The point of interest is battery, sleep/wake (which doesn't work now) and I2C init.


- I2C channel, which is probably connected to the touch screen fails to probe. Most likely because of PUNIT-managed lock, which seems to be another ACPI related problem.


- I2S/I2C camera seems to be unsupported / not-probed at all but I haven't investigated much deeper than finding the ID in the DSDT table and greping through kernel sources (and I have found nothing).

Any help with the mentioned problems would be appreciated. Though I am putting off this laptop because there is too much problems to hack or work-around them it by myself.

Captured data:


[http://aule.elfove.cz/~brill/hpx2/dmesg.txt](http://aule.elfove.cz/~brill/hpx2/dmesg.txt)
[http://aule.elfove.cz/~brill/hpx2/dmidecode.txt](http://aule.elfove.cz/~brill/hpx2/dmidecode.txt)
[http://aule.elfove.cz/~brill/hpx2/dsdt.dsl](http://aule.elfove.cz/~brill/hpx2/dsdt.dsl)

---

### Post by tmshlvck on 2015-12-27
I have dumped available ACPI devices. It seems that 10EC5670 and 10EC5645 are present and therefore it should be compatible with SST. I'll look deeper into that...

```

[    6.698330] acpi_ns_get_device_callback hid->string=PNP0A08
[    6.698347] acpi_ns_get_device_callback hid->string=INT0800
[    6.698357] acpi_ns_get_device_callback hid->string=PNP0000
[    6.698367] acpi_ns_get_device_callback hid->string=PNP0C02
[    6.698376] acpi_ns_get_device_callback hid->string=PNP0100
[    6.698385] acpi_ns_get_device_callback hid->string=PNP0501
[    6.698422] acpi_ns_get_device_callback hid->string=HPQC0003
[    6.698460] acpi_ns_get_device_callback hid->string=INT3496
[    6.698475] acpi_ns_get_device_callback hid->string=GPTC0001
[    6.698489] acpi_ns_get_device_callback hid->string=INT33A4
[    6.698502] acpi_ns_get_device_callback hid->string=80860F14
[    6.698522] acpi_ns_get_device_callback hid->string=80860F14
[    6.698536] acpi_ns_get_device_callback hid->string=BCM43241
[    6.698559] acpi_ns_get_device_callback hid->string=80860F14
[    6.698573] acpi_ns_get_device_callback hid->string=80860F14
[    6.698588] acpi_ns_get_device_callback hid->string=INTL9C60
[    6.698599] acpi_ns_get_device_callback hid->string=80862286
[    6.698613] acpi_ns_get_device_callback hid->string=INTL9C60
[    6.698624] acpi_ns_get_device_callback hid->string=808622C0
[    6.698638] acpi_ns_get_device_callback hid->string=80862288
[    6.698654] acpi_ns_get_device_callback hid->string=80862289
[    6.698668] acpi_ns_get_device_callback hid->string=8086228A
[    6.698811] acpi_ns_get_device_callback hid->string=BCM2E1A
[    6.698825] acpi_ns_get_device_callback hid->string=BCM2E3A
[    6.698837] acpi_ns_get_device_callback hid->string=BCM2E64
[    6.698848] acpi_ns_get_device_callback hid->string=BCM2E7B
[    6.698858] acpi_ns_get_device_callback hid->string=INT33E1
[    6.698870] acpi_ns_get_device_callback hid->string=8086228A
[    6.698884] acpi_ns_get_device_callback hid->string=BCM47521
[    6.698895] acpi_ns_get_device_callback hid->string=BCM4752
[    6.698906] acpi_ns_get_device_callback hid->string=INT33A2
[    6.698917] acpi_ns_get_device_callback hid->string=8086228E
[    6.698931] acpi_ns_get_device_callback hid->string=AUTH2750
[    6.698942] acpi_ns_get_device_callback hid->string=8086228E
[    6.698955] acpi_ns_get_device_callback hid->string=8086228E
[    6.698969] acpi_ns_get_device_callback hid->string=808622C1
[    6.698986] acpi_ns_get_device_callback hid->string=INTCF1C
[    6.699000] acpi_ns_get_device_callback hid->string=IMPJ0003
[    6.699017] acpi_ns_get_device_callback hid->string=FUSB0300
[    6.699029] acpi_ns_get_device_callback hid->string=PI330532
[    6.699039] acpi_ns_get_device_callback hid->string=MAX17047
[    6.699054] acpi_ns_get_device_callback hid->string=SMB0349
[    6.699068] acpi_ns_get_device_callback hid->string=TXN27501
[    6.699082] acpi_ns_get_device_callback hid->string=TXN24292
[    6.699096] acpi_ns_get_device_callback hid->string=PNP0C0A
[    6.699110] acpi_ns_get_device_callback hid->string=808622C1
[    6.699124] acpi_ns_get_device_callback hid->string=10EC5640
[    6.699138] acpi_ns_get_device_callback hid->string=10EC5645
[    6.699152] acpi_ns_get_device_callback hid->string=10EC5670
[    6.699167] acpi_ns_get_device_callback hid->string=INT33F8
[    6.699181] acpi_ns_get_device_callback hid->string=14F10720
[    6.699196] acpi_ns_get_device_callback hid->string=10TI3100
[    6.699210] acpi_ns_get_device_callback hid->string=IMPJ0003
[    6.699224] acpi_ns_get_device_callback hid->string=808622C1
[    6.699239] acpi_ns_get_device_callback hid->string=OVTI9728
[    6.699254] acpi_ns_get_device_callback hid->string=INT33F0
[    6.699270] acpi_ns_get_device_callback hid->string=PNP0C14
[    6.699282] acpi_ns_get_device_callback hid->string=PNP0C0A
[    6.699294] acpi_ns_get_device_callback hid->string=808622C1
[    6.699308] acpi_ns_get_device_callback hid->string=INT33CF
[    6.699322] acpi_ns_get_device_callback hid->string=INT3477
[    6.699334] acpi_ns_get_device_callback hid->string=APTA0330
[    6.699348] acpi_ns_get_device_callback hid->string=OVTI8835
[    6.699362] acpi_ns_get_device_callback hid->string=APTA0330
[    6.699378] acpi_ns_get_device_callback hid->string=INT33BE
[    6.699392] acpi_ns_get_device_callback hid->string=INT33FB
[    6.699407] acpi_ns_get_device_callback hid->string=808622C1
[    6.699421] acpi_ns_get_device_callback hid->string=808622C1
[    6.699435] acpi_ns_get_device_callback hid->string=ATML1000
[    6.699449] acpi_ns_get_device_callback hid->string=NTRG0001
[    6.699465] acpi_ns_get_device_callback hid->string=SYNA7508
[    6.699479] acpi_ns_get_device_callback hid->string=808622C1
[    6.699494] acpi_ns_get_device_callback hid->string=INT33F4
[    6.699509] acpi_ns_get_device_callback hid->string=INT33F5
[    6.699525] acpi_ns_get_device_callback hid->string=INT34D3
[    6.699542] acpi_ns_get_device_callback hid->string=DMY0001
[    6.699557] acpi_ns_get_device_callback hid->string=INT33FD
[    6.699574] acpi_ns_get_device_callback hid->string=INT33FE
[    6.699590] acpi_ns_get_device_callback hid->string=INT33FE
[    6.699605] acpi_ns_get_device_callback hid->string=PNP0C0A
[    6.699633] acpi_ns_get_device_callback hid->string=808622D8
[    6.699649] acpi_ns_get_device_callback hid->string=808622A8
[    6.699663] acpi_ns_get_device_callback hid->string=ADMA22A8
[    6.699677] acpi_ns_get_device_callback hid->string=AMCR22A8
[    6.699690] acpi_ns_get_device_callback hid->string=HAD022A8
[    6.699704] acpi_ns_get_device_callback hid->string=PNP0C02
[    6.699716] acpi_ns_get_device_callback hid->string=BCM4356
[    6.699757] acpi_ns_get_device_callback hid->string=PNP0C02
[    6.699770] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699781] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699791] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699800] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699810] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699820] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699830] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699839] acpi_ns_get_device_callback hid->string=PNP0C0F
[    6.699849] acpi_ns_get_device_callback hid->string=PNP0B00
[    6.699858] acpi_ns_get_device_callback hid->string=PNP0103
[    6.699869] acpi_ns_get_device_callback hid->string=VIBR22A8
[    6.699884] acpi_ns_get_device_callback hid->string=PNP0C0C
[    6.699893] acpi_ns_get_device_callback hid->string=PNP0C0D
[    6.699904] acpi_ns_get_device_callback hid->string=INT0002
[    6.699922] acpi_ns_get_device_callback hid->string=INT33FF
[    6.699936] acpi_ns_get_device_callback hid->string=INT33FF
[    6.699950] acpi_ns_get_device_callback hid->string=INT33FF
[    6.699965] acpi_ns_get_device_callback hid->string=INT33FF
[    6.699979] acpi_ns_get_device_callback hid->string=INT33FF
[    6.700026] acpi_ns_get_device_callback hid->string=ID9001
[    6.700043] acpi_ns_get_device_callback hid->string=ACPI0011
[    6.700055] acpi_ns_get_device_callback hid->string=8086229C
[    6.700066] acpi_ns_get_device_callback hid->string=INTCFD9
[    6.700080] acpi_ns_get_device_callback hid->string=INT33BD
[    6.700096] acpi_ns_get_device_callback hid->string=ACPI000C
[    6.700110] acpi_ns_get_device_callback hid->string=ACPI0003
[    6.700120] acpi_ns_get_device_callback hid->string=MCD0001
[    6.700133] acpi_ns_get_device_callback hid->string=MCD0001
[    6.700147] acpi_ns_get_device_callback hid->string=MCD0001
[    6.700160] acpi_ns_get_device_callback hid->string=MCD0001
[    6.700173] acpi_ns_get_device_callback hid->string=MCD0001
[    6.700186] acpi_ns_get_device_callback hid->string=PNP0C14
[    6.700202] acpi_ns_get_device_callback hid->string=INT3400
[    6.700213] acpi_ns_get_device_callback hid->string=INT3407
[    6.700223] acpi_ns_get_device_callback hid->string=INT3403
[    6.700236] acpi_ns_get_device_callback hid->string=INT3403
[    6.700245] acpi_ns_get_device_callback hid->string=INT3403
[    6.700256] acpi_ns_get_device_callback hid->string=INT3403
[    6.700269] acpi_ns_get_device_callback hid->string=INT3409
[    6.700279] acpi_ns_get_device_callback hid->string=INT3409
[    6.700289] acpi_ns_get_device_callback hid->string=INT3406
[    6.700299] acpi_ns_get_device_callback hid->string=INT3403
[    6.700309] acpi_ns_get_device_callback hid->string=INT3408

```

---

### Post by tmshlvck on 2016-01-01
I have recompiled the original DSDT with Intel compiler. The trick was to fill the external functions from another tables. The current disassembled DSDT is here: [http://aule.elfove.cz/~brill/hpx2/dsdt.dsl](http://aule.elfove.cz/~brill/hpx2/dsdt.dsl) I tried to tweak the DSDT but honestly I do not know what I am doing. So, still no luck with sound, one i2c channel (probable the channel that connects to touchscreen, but the touchscreen works somehow, but no multitouch, no advanced settings, it seems it is also operating in some fallback mode but I haven't investigated deeper...) and battery. It looks like we need to wait for HP to release more Linux-friendly BIOS/UEFI/firmware or how do we call it.

Verdict on this laptop?: Doesn't work. Don't buy!

Is HP going to do something about it?:-)

---

### Post by Bucky Ball on 2016-01-01
Try 15.10 as a last resort. Ignore 15.04. It has less than a month's support. 16.04 might be worth a shot also, but it is not released until April so expect breakages at some stage. Have you tried the super-stable 14.04 LTS? That can upgrade directly to 16.04 when available. 

If the computer is VERY new model, then the newer the Ubuntu release the better. If this is the case, by the release of 16.04 this machine may work fine 'out of the box'. 

I've had two HPs and not an issue. Nothing to do with them. It is our responsibility to check the hardware we purchase is going to work with Linux. It is also no fault of Canonical if third-parties refuse to play nice with Linux. 

Simple solution: Don't buy hardware that doesn't work with Linux, email the manufacturer and tell them why you've made the decision not to purchase their hardware. :)

I would wait to see if you can get help (and make like a support request here rather than a HP bash, if you want support trying to fix this that is) before heading to the nearest rubbish bin with your device. One step toward that would be to edit your first post, Go Advanced, and change the title of the thread to something less generic, e.g. a title that describes the problem you are attempting to solve. 

If you just want a rant, I'll move this to a non-support area for you. Good luck. ;)

PS: Are you attempting a dual-boot with Windows on this machine, and if so, are you installing Ubuntu in the same mode as Win is installed, e.g. UEFI or BIOS mode?

---

### Post by tmshlvck on 2016-01-02
Regarding sound: Dissecting Windows drivers shows that the active ACPI ID should be the 14F10720 / 813E103C . It means that it is probably Conexant CX2072x chip. No Linux driver is available. Dead end.

---

### Post by tmshlvck on 2016-01-02
Hi!

Thanks for reading though this thread.

Nope, I have installed only 15.10 and removed Windows and I haven't tried anything older. Btw. this BIOS/UEFI doesn't have legacy mode and there is not much to tweak in the BIOS setup.

Then I compiled a new kernel 4.4-rc7, added some patches from ACPI mailing list (new ACPICA just hit the list but it hasn't been merged to the mainline yet). It helped with the Cherry Trail PM debug (at least I can see that the LPE power state that indicates ACPI/driver interaction).

Thanks for advice. I'll change the title and I think that moving this thread to "non-support area" is good option. I just wanted to make my findings public. Getting help with ACPI would be of course nice either globally from HP with the new BIOS or with hacking DSDT table.

Anyway, I'll write some summary on this laptop and link it here.
Thanks

---

### Post by Yellow Pasque on 2016-01-02
> **tmshlvck said:**
> It means that it is probably Conexant CX2072x chip. No Linux driver is available. Dead end.

Conexant HDA codecs are supported in the standard kernel ALSA modules (snd-hda-codec-conexant to be exact).
[https://github.com/torvalds/linux/commit/6ffc0898b29a2811a6c0569c5dd9b581980110df](https://github.com/torvalds/linux/commit/6ffc0898b29a2811a6c0569c5dd9b581980110df)
If the OP is lucky, it will simply be a matter of adding the 14f1:0720PCI ID and aliasing it to an existing codec.


@OP: If you are interested, you can file a bug here: [https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&list_id=700421&product=Drivers&resolution=---](https://bugzilla.kernel.org/buglist.cgi?component=Sound%28ALSA%29&list_id=700421&product=Drivers&resolution=---)
Be sure to include your ALSA info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
If you have a stable internet connection, run this before getting the ALSA info to make it a bit more human-readable:
```
sudo update-pciids; sudo update-usbids
```

---

### Post by tmshlvck on 2016-01-02
> **Temüjin said:**
> Conexant HDA codecs are supported in the standard kernel ALSA modules (snd-hda-codec-conexant to be exact).
[https://github.com/torvalds/linux/commit/6ffc0898b29a2811a6c0569c5dd9b581980110df](https://github.com/torvalds/linux/commit/6ffc0898b29a2811a6c0569c5dd9b581980110df)
If the OP is lucky, it will simply be a matter of adding the 14f1:0720PCI ID and aliasing it to an existing codec.


Oh sorry, I forgot to link the lspci and lsusb outputs:


[http://aule.elfove.cz/~brill/hpx2/lspci.txt](http://aule.elfove.cz/~brill/hpx2/lspci.txt)
[http://aule.elfove.cz/~brill/hpx2/lsusb.txt](http://aule.elfove.cz/~brill/hpx2/lsusb.txt)


This Conexant-related patch seems to be already in upstream (and I am working with 4.4-rc7). But the problem seems to be that on this board the codec is connected through SST via I2S with I2C control interface. Therefore there is no such PCI device, only HID in ACPI because the device is meant to be probed according to ACPI tables by snd_intel_sst_acpi module.


I tried to add the ID to the snd_hda_id_conexant array in sound/pci/hda/patch_conexant.c but nothing had happened even after I have loaded the module manually.


Am I still missing something?

---

