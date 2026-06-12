---
title: "[SOLVED] Necesito sonido 5.1 en Hardy (a como de lugar)"
date: 2008-11-16
forum: Hardware
---

### Post by User21 on 2008-11-16
Como puedo obtener el sonido 5.1 en Hardy Heron? Tengo una motherboard **Asus M2N-VM DVI** con **chipset nForce 630a**. He googleado, pero o no he comprendido qué hacer, o simplemente no funciona. No sé como manejar lo de ALSA ni de lo de PulseAudio. Ya me quedé sin ideas...

Les emito la siguiente info y cualquier otro dato, me lo piden:

**lspci**
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
**00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)**
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)


**lsmod**
Module                  Size  Used by
binfmt_misc            12808  1 
tun                    12672  0 
vboxdrv                76736  0 
powernow_k8            16704  1 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
xt_TCPMSS               5504  1 
xt_limit                3584  8 
xt_tcpudp               4096  30 
nf_nat_irc              3712  0 
nf_nat_ftp              4352  0 
ipt_LOG                 7296  8 
ipt_MASQUERADE          4608  1 
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        7576  1 nf_nat_irc
nf_conntrack_ftp       10144  1 nf_nat_ftp
xt_state                3328  8 
ac                      6916  0 
it87                   20876  0 
hwmon_vid               4352  1 it87
lp                     12324  0 
af_packet              23812  2 
ipv6                  267780  22 
bt878                  11832  0 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
serio_raw               7940  0 
bttv                  175860  1 bt878
parport_pc             36260  1 
ir_common              36100  1 bttv
parport                37832  2 lp,parport_pc
psmouse                40336  0 
pcspkr                  4224  0 
evdev                  13056  3 
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7300  1 bttv
nvidia               6896812  30 
k8temp                  6656  0 
gspca                 643920  0 
videobuf_dma_sg        14980  1 bttv
videobuf_core          18820  2 bttv,videobuf_dma_sg
btcx_risc               5896  1 bttv
tveeprom               16656  1 bttv
i2c_core               24832  10 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,bttv,i2c_algo_bit,nvidia,tveeprom
agpgart                34760  1 nvidia
videodev               29440  2 bttv,gspca
v4l2_common            18304  3 tuner,bttv,videodev
wmi_acer                9644  0 
v4l1_compat            15492  2 bttv,videodev
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
iptable_nat             8324  1 
nf_nat                 20396  4 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  10 iptable_nat
nf_conntrack           66752  9 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  1 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  10 xt_TCPMSS,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  7 
usb_storage            73664  0 
libusual               19108  1 usb_storage
ahci                   28548  6 
ata_generic             8324  0 
pata_amd               14212  0 
floppy                 59588  0 
pata_acpi               8320  0 
libata                159344  4 ahci,ata_generic,pata_amd,pata_acpi
tulip                  53536  0 
forcedeth              51980  0 
scsi_mod              151436  5 sg,sr_mod,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
ohci_hcd               26640  0 
usbcore               146412  6 gspca,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              37384  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  7 


Como debo proceder para obtener el sonido 5.1 ? En ween, me funciona desde el arranque, todo OK,  con los drivers, pero agradecería poder solucionarlo en Ubuntu! 
No, no estoy testeando con un mp3 de 2 canales, ni con un archivo de video con audio MP3. 
Algun gurú del sonido en GNU/Linux y/o Ubuntu ? Desde ya, muchisimas gracias :)

---

### Post by User21 on 2008-11-16
Aparentemente, obtuve el sonido de 6 canales. 
No estoy muy seguro como lo hice, pero explico lo que hice! xD

Mi tarjeta de sonido es, segun lspci : nVidia Corporation MCP67 High Definition Audio 
Pero se identifica en la info de la motherboard como Realtek ALC662 High Definition Audio 6-Channel CODEC con soporte S/PDIF y detección de JACKs.

Me basé en [este tutorial]("http://joeb454.ubuntuforums.org/showthread.php?p=5144481") y en[** este otro**]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2"). Este último parece haber dado la solución. Lo traduzco al español por si alguien lo necesita.

Identifica tu codec:
```
aplay -l
cat /proc/asound/card0/codec#* | grep Codec
```Yo obtuve las siguientes salidas.
```
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: ALC662 Analog [ALC662 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 1: ALC662 Digital [ALC662 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

Codec: Realtek ALC662 rev1
```Ahora, edita /etc/modprobe.d/alsa-base con el siguiente comando:
     ```
gksudo gedit /etc/modprobe.d/alsa-base 
```Modifica (o agrega) la siguiente linea con el *modelname* = apropiado, de la lista que se muestra debajo.
     ```
options snd-hda-intel model=modelname 

```Lista de modelnames según tu CODEC:

 ```
Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
        ATI SB450, SB600, RS600,
        VIA VT8251/VT8237A,
        SIS966, ULI M5461

    [Multiple options for each card instance]
    model    - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = use LPIB, 2 = POSBUF)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    bdl_pos_adj    - Specifies the DMA IRQ timing delay in samples.
        Passing -1 will make the driver to choose the appropriate
        value based on the controller chip.
    
    [Single (global) options]
    single_cmd  - Use single immediate commands to communicate with
        codecs (for debugging only)
    enable_msi    - Enable Message Signaled Interrupt (MSI) (default = off)
    power_save    - Automatic power-saving timtout (in second, 0 =
        disable)
    power_save_controller - Reset HD-audio controller in power-saving mode
        (default = on)

    This module supports multiple cards and autoprobe.
    
    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

      Model name    Description
      ----------    -----------
    ALC880
      3stack    3-jack in back and a headphone out
      3stack-digout    3-jack in back, a HP out and a SPDIF out
      5stack    5-jack in back, 2-jack in front
      5stack-digout    5-jack in back, 2-jack in front, a SPDIF out
      6stack    6-jack in back, 2-jack in front
      6stack-digout    6-jack with a SPDIF out
      w810        3-jack
      z71v        3-jack (HP shared SPDIF)
      asus        3-jack (ASUS Mobo)
      asus-w1v    ASUS W1V
      asus-dig    ASUS with SPDIF out
      asus-dig2    ASUS with SPDIF out (using GPIO2)
      uniwill    3-jack
      fujitsu    Fujitsu Laptops (Pi1536)
      F1734        2-jack
      lg        LG laptop (m1 express dual)
      lg-lw        LG LW20/LW25 laptop
      tcl        TCL S700
      clevo        Clevo laptops (m520G, m665n)
      medion    Medion Rim 2150
      test        for testing/debugging purpose, almost all controls can be
            adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y
      auto        auto-config reading BIOS (default)

    ALC260
      hp        HP machines
      hp-3013    HP machines (3013-variant)
      fujitsu    Fujitsu S7020
      acer        Acer TravelMate
      will        Will laptops (PB V7900)
      replacer    Replacer 672V
      basic        fixed pin assignment (old default model)
      test        for testing/debugging purpose, almost all controls can
            adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y
      auto        auto-config reading BIOS (default)

    ALC262
      fujitsu    Fujitsu Laptop
      hp-bpc    HP xw4400/6400/8400/9400 laptops
      hp-bpc-d7000    HP BPC D7000
      hp-tc-t5735    HP Thin Client T5735
      hp-rp5700    HP RP5700
      benq        Benq ED8
      benq-t31    Benq T31
      hippo        Hippo (ATI) with jack detection, Sony UX-90s
      hippo_1    Hippo (Benq) with jack detection
      sony-assamd    Sony ASSAMD
      ultra        Samsung Q1 Ultra Vista model
      lenovo-3000    Lenovo 3000 y410
      basic        fixed pin assignment w/o SPDIF
      auto        auto-config reading BIOS (default)

    ALC267/268
      quanta-il1    Quanta IL1 mini-notebook
      3stack    3-stack model
      toshiba    Toshiba A205
      acer        Acer laptops
      dell        Dell OEM laptops (Vostro 1200)
      zepto        Zepto laptops
      test        for testing/debugging purpose, almost all controls can
            adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y
      auto        auto-config reading BIOS (default)

    ALC269
      basic        Basic preset

    ALC662/663
      3stack-dig    3-stack (2-channel) with SPDIF
      3stack-6ch     3-stack (6-channel)
      3stack-6ch-dig 3-stack (6-channel) with SPDIF
      6stack-dig     6-stack with SPDIF
      lenovo-101e     Lenovo laptop
      eeepc-p701    ASUS Eeepc P701
      eeepc-ep20    ASUS Eeepc EP20
      m51va        ASUS M51VA
      g71v        ASUS G71V
      h13        ASUS H13
      g50v        ASUS G50V
      auto        auto-config reading BIOS (default)

    ALC882/885
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack digital with SPDIF I/O
      arima        Arima W820Di1
      targa        Targa T8, MSI-1049 T8
      asus-a7j    ASUS A7J
      asus-a7m    ASUS A7M
      macpro    MacPro support
      mbp3        Macbook Pro rev3
      imac24    iMac 24'' with jack detection
      w2jc        ASUS W2JC
      auto        auto-config reading BIOS (default)

    ALC883/888
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack digital with SPDIF I/O
      3stack-6ch    3-jack 6-channel
      3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
      6stack-dig-demo  6-jack digital for Intel demo board
      acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
      acer-aspire    Acer Aspire 9810
      medion    Medion Laptops
      medion-md2    Medion MD2
      targa-dig    Targa/MSI
      targa-2ch-dig    Targs/MSI with 2-channel
      laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
      lenovo-101e    Lenovo 101E
      lenovo-nb0763    Lenovo NB0763
      lenovo-ms7195-dig Lenovo MS7195
      haier-w66    Haier W66
      3stack-hp    HP machines with 3stack (Lucknow, Samba boards)
      6stack-dell    Dell machines with 6stack (Inspiron 530)
      mitac        Mitac 8252D
      clevo-m720    Clevo M720 laptop series
      fujitsu-pi2515 Fujitsu AMILO Pi2515
      auto        auto-config reading BIOS (default)

    ALC861/660
      3stack    3-jack
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack with SPDIF I/O
      3stack-660    3-jack (for ALC660)
      uniwill-m31    Uniwill M31 laptop
      toshiba    Toshiba laptop support
      asus        Asus laptop support
      asus-laptop    ASUS F2/F3 laptops
      auto        auto-config reading BIOS (default)

    ALC861VD/660VD
      3stack    3-jack
      3stack-dig    3-jack with SPDIF OUT
      6stack-dig    6-jack with SPDIF OUT
      3stack-660    3-jack (for ALC660VD)
      3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
      lenovo    Lenovo 3000 C200 & ASUS X20SG, ASUS U1E
      dallas    Dallas laptops, Toshiba satellite L30-106
      hp        HP TX1000
      auto        auto-config reading BIOS (default)

    CMI9880
      minimal    3-jack in back
      min_fp    3-jack in back, 2-jack in front
      full        6-jack in back, 2-jack in front
      full_dig    6-jack in back, 2-jack in front, SPDIF I/O
      allout    5-jack in back, 2-jack in front, SPDIF out
      auto        auto-config reading BIOS (default)

    AD1882
      3stack    3-stack mode (default)
      6stack    6-stack mode

    AD1884A / AD1883 / AD1984A / AD1984B
      desktop    3-stack desktop (default)
      laptop    laptop with HP jack sensing
      mobile    mobile devices with HP jack sensing
      thinkpad    Lenovo Thinkpad X300

    AD1884
      N/A

    AD1981
      basic        3-jack (default)
      hp        HP nx6320
      thinkpad    Lenovo Thinkpad T60/X60/Z60
      toshiba    Toshiba U205

    AD1983
      N/A

    AD1984
      basic        default configuration
      thinkpad    Lenovo Thinkpad T61/X61
      dell        Dell T3400

    AD1986A
      6stack    6-jack, separate surrounds (default)
      3stack    3-stack, shared surrounds
      laptop    2-channel only (FSC V2060, Samsung M50)
      laptop-eapd    2-channel with EAPD (Samsung R65, ASUS A6J)
      laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
      ultra        2-channel with EAPD (Samsung Ultra tablet PC)

    AD1988/AD1988B/AD1989A/AD1989B
      6stack    6-jack
      6stack-dig    ditto with SPDIF
      3stack    3-jack
      3stack-dig    ditto with SPDIF
      laptop    3-jack with hp-jack automute
      laptop-dig    ditto with SPDIF
      auto        auto-config reading BIOS (default)
    
    Conexant 5045
      laptop-hpsense    Laptop with HP sense (old model laptop)
      laptop-micsense   Laptop with Mic sense (old model fujitsu)
      laptop-hpmicsense Laptop with HP and Mic senses
      benq        Benq R55E
      test        for testing/debugging purpose, almost all controls
            can be adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y

    Conexant 5047
      laptop    Basic Laptop config 
      laptop-hp    Laptop config for some HP models (subdevice 30A5)
      laptop-eapd    Laptop config with EAPD support
      test        for testing/debugging purpose, almost all controls
            can be adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y

    Conexant 5051
      laptop    Basic Laptop config (default)
      hp        HP Spartan laptop

    STAC9200
      ref        Reference board
      dell-d21    Dell (unknown)
      dell-d22    Dell (unknown)
      dell-d23    Dell (unknown)
      dell-m21    Dell Inspiron 630m, Dell Inspiron 640m
      dell-m22    Dell Latitude D620, Dell Latitude D820
      dell-m23    Dell XPS M1710, Dell Precision M90
      dell-m24    Dell Latitude 120L
      dell-m25    Dell Inspiron E1505n
      dell-m26    Dell Inspiron 1501
      dell-m27    Dell Inspiron E1705/9400
      gateway    Gateway laptops with EAPD control
      panasonic    Panasonic CF-74

    STAC9205/9254
      ref        Reference board
      dell-m42    Dell (unknown)
      dell-m43    Dell Precision
      dell-m44    Dell Inspiron

    STAC9220/9221
      ref        Reference board
      3stack    D945 3stack
      5stack    D945 5stack + SPDIF
      intel-mac-v1    Intel Mac Type 1
      intel-mac-v2    Intel Mac Type 2
      intel-mac-v3    Intel Mac Type 3
      intel-mac-v4    Intel Mac Type 4
      intel-mac-v5    Intel Mac Type 5
      macmini    Intel Mac Mini (equivalent with type 3)
      macbook    Intel Mac Book (eq. type 5)
      macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
      macbook-pro    Intel Mac Book Pro 2nd generation (eq. type 3)
      imac-intel    Intel iMac (eq. type 2)
      imac-intel-20    Intel iMac (newer version) (eq. type 3)
      dell-d81    Dell (unknown)
      dell-d82    Dell (unknown)
      dell-m81    Dell (unknown)
      dell-m82    Dell XPS M1210

    STAC9202/9250/9251
      ref        Reference board, base config
      m2-2        Some Gateway MX series laptops
      m6        Some Gateway NX series laptops
      pa6        Gateway NX860 series

    STAC9227/9228/9229/927x
      ref        Reference board
      3stack    D965 3stack
      5stack    D965 5stack + SPDIF
      dell-3stack    Dell Dimension E520
      dell-bios    Fixes with Dell BIOS setup

    STAC92HD71B*
      ref        Reference board
      dell-m4-1    Dell desktops
      dell-m4-2    Dell desktops

    STAC92HD73*
      ref        Reference board
      dell-m6    Dell desktops

    STAC9872
      vaio        Setup for VAIO FE550G/SZ110
      vaio-ar Setup for VAIO AR

    The model name "genric" is treated as a special case.  When this
    model is given, the driver uses the generic codec parser without
    "codec-patch".  It's sometimes good for testing and debugging.

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    power_save and power_save_controller options are for power-saving
    mode.  See powersave.txt for details.

    Note 2: If you get click noises on output, try the module option
        position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
        register value without FIFO size correction as the current
        DMA pointer.  position_fix=2 will make the driver to use
        the position buffer instead of reading SD_LPIB register.
        (Usually SD_LPLIB register is more accurate than the
        position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    MORE NOTES ON "azx_get_response timeout" PROBLEMS:
    On some hardwares, you may need to add a proper probe_mask option
    to avoid the "azx_get_response timeout" problem above, instead.
    This occurs when the access to non-existing or non-working codec slot
    (likely a modem one) causes a stall of the communication via HD-audio
    bus.  You can see which codec slots are probed by enabling
    CONFIG_SND_DEBUG_VERBOSE, or simply from the file name of the codec
    proc files.  Then limit the slots to probe by probe_mask option.
    For example, probe_mask=1 means to probe only the first slot, and
    probe_mask=4 means only the third slot.

    The power-management is supported.
```En mi caso particular, mi codec es **ALC662** , por lo cual, según el tipo, elegi el modelname "**3stack-6ch-dig**" :

```
options snd-hda-intel model=3stack-6ch-dig

```**Reiniciar Ubuntu **(seguramente no es necesario si se sabe reiniciar todos los servidores de sonido, los modulos implicados, y los procesos necesarios, pero como no lo se, simplemente reinicio)

Al reiniciar, al hacer doble clic en el CONTROL DE VOLUME de Gnome, tengo las opciones para activar los 6 canales. Mis películas codificadas en AC3 y DVDs comerciales, ya funcionan con sonido 5.1!!! :D

Para testear que todos los canales estén funcionando, desde terminal:
```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```Y a disfrutar..!

---

### Post by niko_3100 on 2008-11-17
que compu tenes capo?

---

### Post by User21 on 2008-11-17
Es un AMD Athlon 64 X2 4600+; Motherboard ASUS M2N-VM DVI chipset Nforce 630a; 2Gb RAM DDR2 800Mhz; Video Nvidia GT 8500GT 512 Mb RAM DDR2 y un gabinete "PICHINCHO". Por?

---

### Post by albertoguevara on 2008-12-01
Hey, muy útil tu post, tenía el mismo problema pero mi configuración es 4.0 y sirve el sonido perfecto en las cornetas traseras con la configuración de 6ch pero deja de funcionar la entrada del mic, y por consecuencia no tengo micrófono; me imagino que esto ocurre debido a que toma el jack del mic para las cornetas del medio (o que se yo). No sabes si existe una configuración de 4ch?

Saludos, Alberto Guevara

---

### Post by Yunow on 2008-12-04
Desde que tengo Ubuntu 8.10 me quedé sin sonido...

Probando el tutorial no puedo pasar de la primer linea

```

yunow@yunowPC:~$ aplay -l
aplay: device_list:215: no se encontraron tarjetas de sonido...

```

```

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

```

No puedo cargar ningún módulo, parecen no existir...

```
 
sudo modprobe snd-hda-intel
sudo: unable to resolve host yunowPC
FATAL: Module snd_hda_intel not found.

```

Sabes que puede ser???

---

### Post by Max_Aeternus on 2009-02-16
Hola gente antes que nada muchas gracias ^^ , entre al foro por q tenia un drama con mi placa de sonido (no se escuchaba nada xD) bueno este tuto me ayudo y esta completamente solucionado ^^ 

Tengo Ubuntu 8.10 un mother ASUS P5GD2-X, Chipset de sonido CMI 9880 (para este chipset no existen mas soporte ni drivers en al pagina oficial, me fue mas facil instalarlo con Ubuntu q con Vista XD)

Gracias!!!.

---

### Post by daikun on 2009-11-04
error abajo si esta lo q queria decir

---

### Post by daikun on 2009-11-04
Sabes tengo exactamente la misma tarjeta que tu, me sale la misma. y logro hacer estos pasos, modificando el alsa-base.conf o algo asi, lo pongo en la ultima linea 

  	 	 	 	 	 	  options snd-hda-intel model=3stack-6ch-dig y no sucede nada, pero ahora buscando mas posibilidades y probando aca y haya. desconfigure Alsa por que no me sale ninguna posibilidad de hardware, nada de nada

Por cierto estoy usando 9.10 y me encantaria poder usar mi tarjeta con todas sus funcionalidades ah! 

Alguien sabe si las tarjetas Genius 5.1 "basicas" son compatibles con Alsa?

Gracias

---

### Post by guillermolisi on 2009-11-04
> **daikun said:**
> Sabes tengo exactamente la misma tarjeta que tu, me sale la misma. y logro hacer estos pasos, modificando el alsa-base.conf o algo asi, lo pongo en la ultima linea 

                                 options snd-hda-intel model=3stack-6ch-dig y no sucede nada, pero ahora buscando mas posibilidades y probando aca y haya. desconfigure Alsa por que no me sale ninguna posibilidad de hardware, nada de nada

Por cierto estoy usando 9.10 y me encantaria poder usar mi tarjeta con todas sus funcionalidades ah! 

Alguien sabe si las tarjetas Genius 5.1 "basicas" son compatibles con Alsa?

Gracias
No se si te detuviste para leer el asunto de este thread pero lo que aqui se converso es sobre otra version mas antigua de Ubuntu: Hardy Heron 8.04

Esta solucion es especifica para esta version, no para la que estas usando porque hay cosas que han cambiado y mucho.

En todo caso, hay threads que hablan del problema con los sonidos en 9.10 en la seccion de software.

---

