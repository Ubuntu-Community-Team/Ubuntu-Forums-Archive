---
title: "Leadtek Winfast2000XP TV card - Video Yes, TV no"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by tristan on 2005-06-29
Greetings

After doing a hell of a lot of googling and forum searching I settled on a relatively cheap **Leadtek Winfast2000XP RM** TV card to try in my ubuntu box. This card has a conexant copy of the BT878 chip and is supposedly supported well under ubuntu.

I installed the card and connected up my VCR (which is normally connected to my TV via its RF out) to it via both the TV-in, and the composite video in. When I fired up tvtime (after giving it the appropriate settings for Australian TV), I was met by a blue screen, with** "no signal"** displayed prominently. I tried scanning through the channels (1-63 for Aussie TV) hoping that one of them would pick up the RF signal from the VCR - no luck. If I disabled  signal detection, then instead of the blue screen I got black and white static on all channels. No amount of manual fine tuning on any channel produces any results.

The thing is, if I switch it to use composite video as input instead of TV, I get a lovely crisp display of my VCR's output. So obviously the BTTV module is working, and creating  /dev/video0 . It just seems that the tuner is not doing its thing.

My dmesg output shows that the card is apparently properly detected:
```
Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 17, latency: 32, mmio: 0xef000000
bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
bttv0: using tuner=5
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
tuner: chip found at addr 0xc2 i2c-bus bt878 #0 [sw]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by bt878 #0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: registered device radio0
bttv0: PLL: 28636363 => 35468950 .. ok
bttv0: add subdevice "remote0"
```

The strange thing is, that I can remove bttv with **rmmod bttv**, reload it with any combination of card and tuner (eg modprobe bttv card=XX tuner=YY), and fire up tvtime with exactly the same results (ie no TV, but nice video in). I've also tried manually loading the bttv module with settings such as gbuffer=4, pll=0 etc, none of which have any effect. I've even tried removing bttv and loading in the cx8800 and/or saa7134 modules, which give me the same video output but no TV. What the...?

Basically I've tried every setting I know of to no effect, and have really given it a good go before posting here. I've no idea how to fix it, and hope that one of you legends has a bit of information that might help me. 

I just hope I haven't lucked out with the conexant chip lottery. I can't really afford to keep blowing $70+ until I find a working bloody card. ](*,)

---

### Post by emperor on 2005-06-29
see: [http://www.bttv-gallery.de/]("http://www.bttv-gallery.de/")

user reports: **Leadtek WinFast TV 2000 XP RM Edition**
card working under linux with card id=35 and tuner id=38

The vendors change chipsets all the time, perhaps the TV tuner is defined wrong in the v4l driver.

You can also check the v4l source files; search for your card in the source. You could also modify the source a bit and re-compile it. I did this once to get the FM radio to work on my Asus TV card.

The card id and tuner can be dynamicly set when the module is inserted. See the following documentation from the bttv source tarball. The info will need to be modified for modprobe compatiblity.

===============
Note: "modinfo <module>" prints various informations about a kernel
module, among them a complete and up-to-date list of insmod options.
This list tends to be outdated because it is updated manually ...

==========================================================================

bttv.o
    the bt848/878 (grabber chip) driver

    insmod args:
        card=n        card type, see CARDLIST for a list.
        tuner=n        tuner type, see CARDLIST for a list.
        radio=0/1    card supports radio
        pll=0/1/2    pll settings
            0: don't use PLL
            1: 28 MHz crystal installed
            2: 35 MHz crystal installed

        triton1=0/1     for Triton1 (+others) compatibility
        vsfx=0/1    yet another chipset bug compatibility bit
                see README.quirks for details on these two.

        bigendian=n    Set the endianness of the gfx framebuffer.
                Default is native endian.
        fieldnr=0/1    Count fields.  Some TV descrambling software
                needs this, for others it only generates
                50 useless IRQs/sec.  default is 0 (off).
        autoload=0/1    autoload helper modules (tuner, audio).
                default is 1 (on).
        bttv_verbose=0/1/2  verbose level (at insmod time, while
                looking at the hardware).  default is 1.
        bttv_debug=0/1    debug messages (for capture).
                default is 0 (off).
        irq_debug=0/1    irq handler debug messages.
                default is 0 (off).
        gbuffers=2-32    number of capture buffers for mmap'ed capture.
                default is 4.
        gbufsize=    size of capture buffers. default and
                maximum value is 0x208000 (~2MB)
        no_overlay=0    Enable overlay on broken hardware.  There
                are some chipsets (SIS for example) which
                are known to have problems with the PCI DMA
                push used by bttv.  bttv will disable overlay
                by default on this hardware to avoid crashes.
                With this insmod option you can override this.
        automute=0/1    Automatically mutes the sound if there is
                no TV signal, on by default.  You might try
                to disable this if you have bad input signal
                quality which leading to unwanted sound
                dropouts.
        chroma_agc=0/1    AGC of chroma signal, off by default.
        adc_crush=0/1    Luminance ADC crush, on by default.

        bttv_gpio=0/1
        gpiomask=
        audioall=
        audiomux=
                See Sound-FAQ for a detailed description.

    remap, card, radio and pll accept up to four comma-separated arguments
    (for multiple boards).

tuner.o
    The tuner driver.  You need this unless you want to use only
    with a camera or external tuner ...

    insmod args:
        debug=1        print some debug info to the syslog
        type=n        type of the tuner chip. n as follows:
                see CARDLIST for a complete list.
        pal=[bdgil]    select PAL variant (used for some tuners
                only, important for the audio carrier).

tvmixer.o
    registers a mixer device for the TV card's volume/bass/treble
    controls (requires a i2c audio control chip like the msp3400).

    insmod args:
        debug=1        print some debug info to the syslog.
        devnr=n        allocate device #n (0 == /dev/mixer,
                1 = /dev/mixer1, ...), default is to
                use the first free one.

tvaudio.o
    new, experimental module which is supported to provide a single
    driver for all simple i2c audio control chips (tda/tea*).

    insmod args:
        tda8425  = 1    enable/disable the support for the
        tda9840  = 1    various chips.
        tda9850  = 1    The tea6300 can't be autodetected and is
        tda9855  = 1    therefore off by default, if you have
        tda9873  = 1    this one on your card (STB uses these)
        tda9874a = 1    you have to enable it explicitly.
        tea6300  = 0    The two tda985x chips use the same i2c
        tea6420  = 1    address and can't be disturgished from
        pic16c54 = 1    each other, you might have to disable
                the wrong one.
        debug = 1    print debug messages

    insmod args for tda9874a:
        tda9874a_SIF=1/2    select sound IF input pin (1 or 2)
                    (default is pin 1)
        tda9874a_AMSEL=0/1    auto-mute select for NICAM (default=0)
                    Please read note 3 below!
        tda9874a_STD=n        select TV sound standard (0..8):
                    0 - A2, B/G
                    1 - A2, M (Korea)
                    2 - A2, D/K (1)
                    3 - A2, D/K (2)
                    4 - A2, D/K (3)
                    5 - NICAM, I
                    6 - NICAM, B/G
                    7 - NICAM, D/K (default)
                    8 - NICAM, L

    Note 1: tda9874a supports both tda9874h (old) and tda9874a (new) chips.
    Note 2: tda9874h/a and tda9875 (which is supported separately by
    tda9875.o) use the same i2c address so both modules should not be
    used at the same time.
    Note 3: Using tda9874a_AMSEL option depends on your TV card design!
        AMSEL=0: auto-mute will switch between NICAM sound
             and the sound on 1st carrier (i.e. FM mono or AM).
        AMSEL=1: auto-mute will switch between NICAM sound
             and the analog mono input (MONOIN pin).
    If tda9874a decoder on your card has MONOIN pin not connected, then
    use only tda9874_AMSEL=0 or don't specify this option at all.
    For example:
      card=65 (FlyVideo 2000S) - set AMSEL=1 or AMSEL=0
      card=72 (Prolink PV-BT878P rev.9B) - set AMSEL=0 only

msp3400.o
    The driver for the msp34xx sound processor chips. If you have a
    stereo card, you probably want to insmod this one.

    insmod args:
        debug=1/2    print some debug info to the syslog,
                2 is more verbose.
        simple=1    Use the "short programming" method.  Newer
                msp34xx versions support this.  You need this
                for dbx stereo.  Default is on if supported by
                the chip.
        once=1        Don't check the TV-stations Audio mode
                every few seconds, but only once after
                channel switches.
        amsound=1    Audio carrier is AM/NICAM at 6.5 Mhz.  This
                should improve things for french people, the
                carrier autoscan seems to work with FM only...

tea6300.o - OBSOLETE (use tvaudio instead)
    The driver for the tea6300 fader chip.  If you have a stereo
    card and the msp3400.o doesn't work, you might want to try this
    one.  This chip is seen on most STB TV/FM cards (usually from
    Gateway OEM sold surplus on auction sites).

    insmod args:
        debug=1        print some debug info to the syslog.

tda8425.o - OBSOLETE (use tvaudio instead)
    The driver for the tda8425 fader chip.  This driver used to be
    part of bttv.c, so if your sound used to work but does not
    anymore, try loading this module.

    insmod args:
        debug=1        print some debug info to the syslog.

tda985x.o - OBSOLETE (use tvaudio instead)
    The driver for the tda9850/55 audio chips.

    insmod args:
        debug=1        print some debug info to the syslog.
        chip=9850/9855    set the chip type.

---

### Post by tristan on 2005-06-29
Emperor you are a saviour, and better at googling than me obviously :)

I'll try a few of these things out and see how I go.

I love this forum!!!

---

### Post by tristan on 2005-06-30
Yahoo, got it working, thanks very much to you Emperor!

[B]rmmod bttv
modprobe bttv card=35 tuner=38[/B]

You don't know how I can force bttv to use these settings? I tried creating /etc/modutils/bttv and adding in the options there, but it doesn't work. 

Faling that, is there a script I can edit (similar to rc.local on other linuxes) where I can just add the above commands?

Thanks again.

---

### Post by stepper on 2005-06-30
[QUOTE=tristan]You don't know how I can force bttv to use these settings? I tried creating /etc/modutils/bttv and adding in the options there, but it doesn't work. [/QUOTE]
I think its now /etc/modprobe.d/bttv and  then listing it as one of the modules to be loaded at boot time in /etc/modules

---

### Post by emperor on 2005-06-30
[QUOTE=tristan]Yahoo, got it working, thanks very much to you Emperor!

[b]rmmod bttv
modprobe bttv card=35 tuner=38[/b]

You don't know how I can force bttv to use these settings? I tried creating /etc/modutils/bttv and adding in the options there, but it doesn't work. 

Faling that, is there a script I can edit (similar to rc.local on other linuxes) where I can just add the above commands?

Thanks again.[/QUOTE]

look at: "man modprobe.conf" 
 options modulename option...

This indicates that you may add an option statement in modprobe.conf as follows:

options bttv  card=35  tuner=38

Try this first, if it doesn't work as documented, then a end of boot script file can be created or a login script.

---

### Post by technochoc on 2005-11-17
Hi Guy's

Really new to linux, but am persisting !](*,) 

I also have a cheap xp 2000 rm card and have read the thread above, but a little lost when i try to 

modprobe bttv card=35 tuner=38 in the terminal i get 

ERROR: Module bttv is in use by bt878

Help !!

All i get is a faint picture behind the noise

Technochoc

---

### Post by kreso on 2005-11-19
Hi, I have the same card but no luck.

I rmmod bt878 and bttv, then modprobe bt878 and modprobe bttv card=35 tuner=38.

dmesg says it uses tuner=5 no matter what I type in.

Also, zapping, tvtime, xawtv, and kdetv dont work.

Sometimes when I start tvtime or kdetw X restarts?

---

### Post by korami on 2006-02-04
[QUOTE=technochoc]Hi Guy's

Really new to linux, but am persisting !](*,) 

I also have a cheap xp 2000 rm card and have read the thread above, but a little lost when i try to 

modprobe bttv card=35 tuner=38 in the terminal i get 

ERROR: Module bttv is in use by bt878

Help !!

All i get is a faint picture behind the noise

Technochoc[/QUOTE]

Technochoc, in case you haven't found the solution yet... I have the same card and had the same issue, and had to enter the commands as follows:

**sudo rmmod bt878**
sudo rmmod bttv
sudo rmmod tuner
sudo modprobe bttv card=**34** tuner=**38**.

---

### Post by TmP on 2006-04-25
Thanx! it worked:
If you bought a Winfast2000xp card (RM) do this:

1. open terminal 
2. go to /ect
3. type: "sudo gedit modprobe.conf"
4. add this line: "options bttv card=**34** tuner=38"
5. save in /ect
6. should work from the next restart

watch out for some of the other guides to this solution. They suggest adding stuff to modules. This is unnecesary.

Try tvtime. Get it of Synaptics. Type:"sudo tvtime-scanner".
If you prefare xawtv type: "scantv"
If you get an error, check where the tuner got mounted. In my case it was vbi0 instead of vbi.

In that case type:"scantv -C /dev/vbi0"

---

### Post by Spleenie on 2006-06-03
[QUOTE=korami]Technochoc, in case you haven't found the solution yet... I have the same card and had the same issue, and had to enter the commands as follows:

**sudo rmmod bt878**
sudo rmmod bttv
sudo rmmod tuner
sudo modprobe bttv card=**34** tuner=**38**.[/QUOTE]

These commands worked for me also. I have a Winfast 2000 XP RM. Thanks for all the help.

Just one other minor detail. Anyone got the remote to work? :)

It's such a shnazzy remote is all. 

I have installed lirc and obtained the config file for the Leadtek RM remote control.

I have been unable to get the remote working at all. Has anyone had some success here?

Here is my relevant dmesg output for the tuner card:

```

[4294691.208000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 5, latency: 32, mmio: 0xe6023000
[4294691.208000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[4294691.208000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[4294691.208000] bttv0: gpio: en=00000000, out=00000000 in=003ff102 [init]
[4294691.209000] bttv0: using tuner=38
[4294691.209000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294691.211000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294691.214000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294691.216000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294691.230000] sis900.c: v1.08.09 Sep. 19 2005
[4294691.230000] **** SET: Misaligned resource pointer: d85e88c2 Type 07 Len 0
[4294691.230000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294691.230000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294691.232000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[4294691.297000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294691.297000] eth0: SiS 900 PCI Fast Ethernet at 0xe800, IRQ 11, 00:01:6c:a7:8e:7f.
[4294691.392000] i2c-sis96x version 1.0.0
[4294691.392000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
[4294691.454000] Real Time Clock Driver v1.12
[4294691.459000] FDC 0 is a post-1991 82077
[4294691.488000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294691.488000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[4294691.554000] bttv0: registered device video0
[4294691.554000] bttv0: registered device vbi0
[4294691.554000] bttv0: registered device radio0
[4294691.554000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294691.585000] bttv0: add subdevice "remote0"
[4294691.612000] input: PC Speaker as /class/input/input1
[4294691.648000] bt878: AUDIO driver version 0.0.0 loaded
[4294691.648000] bt878: Bt878 AUDIO function found (0).

```

Here is my /etc/lircd/lircd.conf file

```

#
# this config file was automatically generated
# using WinLIRC 0.6.4 (LIRC 0.6.1pre3) on Sun Nov 03 14:25:14 2002
#
# modified by CB
#
# contributed by Erik Christiansson, aka Sci
# www.alphafish.com
# erik@alphafish.com
#
# brand:             Leadtek
# model:             RM-0010 (bundeled with TV2000 TV-card)
#
# modifications based on the config files from
# Juan Toledo <toledo@users.sourceforge.net> and
# Markus Lischka <mlischka@users.sourceforge.net>
# Reza Naima
#
# Only CH_UP, CH_DOWN, VOL_UP and VOL_DOWN will repeat. This seems to
# be a hardware limitation.
#


begin remote

  name  RM-0010
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            40
  aeps          100

  header       9000  4500
  one           563  1687
  zero          563   562
  ptrail        563
  repeat       9000  2250
  pre_data_bits   16
  pre_data       0xC03F
  gap          108000
  toggle_bit      0

  frequency    38000
  duty_cycle   33

      begin codes
          POWER                    0x00000000000000FF
          TV/FM                    0x00000000000040BF
          SCAN                     0x000000000000A857
          DISPLAY                  0x0000000000006897
          1                        0x000000000000A05F
          2                        0x000000000000609F
          3                        0x000000000000E01F
          4                        0x000000000000906F
          5                        0x00000000000050AF
          6                        0x000000000000D02F
          7                        0x000000000000B04F
          8                        0x000000000000708F
          9                        0x000000000000F00F
          0                        0x00000000000048B7
          RECALL                   0x0000000000008877
          ENTER                    0x000000000000C837
          CC                       0x000000000000F807
          MTS                      0x000000000000D827
          FINE_DOWN                0x0000000000009867
          FINE_UP                  0x00000000000018E7
          VIDEO                    0x0000000000007887
          MUTE                     0x00000000000028D7
          CH_UP                    0x00000000000030CF
          CH_DOWN                  0x00000000000008F7
          VOL_DOWN                 0x00000000000010EF
          VOL_UP                   0x00000000000020DF
          FULLSCREEN               0x000000000000C03F

# The following are only supported by the remote control bundled with
# the WinFast TV 2000 XP Deluxe card.

          SLEEP                    0x00000000000002FD
          BOSS_KEY                 0x000000000000926D
          RED                      0x000000000000D22D
          GREEN                    0x00000000000032CD
          YELLOW                   0x000000000000B24D
          BLUE                     0x000000000000728D
          PIP                      0x00000000000052AD
          .                        0x000000000000827D
          BACK                     0x00000000000042BD
          PLAY                     0x000000000000C23D
          NEXT                     0x00000000000022DD
          TIMESHIFT                0x000000000000A25D
          STOP                     0x000000000000629D
          REC                      0x000000000000E21D
          SNAPSHOT                 0x00000000000012ED

# Only found on CoolCommand remote

          REPEAT                   0x000000000000884B
          TELETEXT                 0x000000000000F807
          TV                       0x0000000000006A95
          FM                       0x000000000000EA15
          DVD                      0x0000000000001AE5
          CLEAR(C)                 0x0000000000000AF5
          MENU                     0x000000000000F20D
          CH_SURF                  0x0000000000008A75
          ENTER                    0x000000000000C837
          AUDIO                    0x000000000000D827
          CC                       0x0000000000004AB5
          REW                      0x0000000000002AD5
          STOP                     0x000000000000629D
          FFW                      0x000000000000AA55
      end codes

end remote

```

Is there anything more I needed to do?

Cheers, Spleenie

---

### Post by geko@g2k.dk on 2006-06-26
I have a similar problem, but none of the postings here helped me. My TV2000 XP **Expert** works perfectly under tvtime (without any modfications to the modules or anything) but it just wont work under MythTV. MythTV can show the channels all right, but only after tvtime has tuned them in. MythTV itself cannot change channels. Whenever I try to do so, the image just halts for a few seconds, and then resumes viewing whatever it is currently on.

Any ideas? I'm using the danish channel codes, and I've even tried to set up the correct freq's, but nothing seems to work... It is as if MythTV has no control over the tuner, wheras tvtime has perfect control.

---

### Post by Mellon on 2006-07-16
i have the same card GEKO, can you plz tell me the numbers you use to card and tuner.

or can someone help me to find them.

i already use card=5 tuner=43 with no luck

this is my card 

>           o Leadtek WinFast TV 2000 XP Expert

            01:08.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
                    Subsystem: LeadTek Research Inc.: Unknown device 6613

            cx88[0]: subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert[card=5,autodetected]
            cx88[0]: Leadtek Winfast 2000 XP config: tuner=43, eeprom[0]=0x01
            cx88[0]/0: found at 0000:01:08.0, rev: 5, irq: 3, latency: 32, mmio:0xee000000
            tuner: chip found at addr 0xc0 i2c-bus cx88[0]
            tuner: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F)) by cx88[0]
            tda9885/6/7: chip found @ 0x86

          o Leadtek WinFast TV 2000 XP Expert Edition

            chips: cx23881-19, 74hc4053d, hef4052bt, em78p156elm, ht24lc02, apa2308, ams1117, xtal 28.636c3, xtal4.000d3
            pcb: LR6611 (checked), LR6613 (not checked), Assy Rev: A, PCB Rev:C
            tuner: [x] PAL BG, PAL I, PAL DK, Secam L/L Secam DK, Secam BG, A2, Nicam;
                     [  ] NTSC-J, EIA-J
                     [  ] NTSC-M, PAL M PAL N, MTS
            tuner:FM1216ME (?)
            connectors: FM, TV, VI (9pol din), RM (remote)
            VI = Video In Fan-out cable: s_Video IN (black), Composite video in (yellow), left audio in (white), right audio in (red)
            onboard connector: audio out

                  PCB Rev C, Assy Rev B, NTSC. 

Pin 114, GPIO[13] = 4052 'B'
Pin 115, GPIO[12] = 4052 'A'
Pin 128, GPIO[02] = 4052 Inhibit. // This is probably the 'popping' pin
				  // Keep at logic level '0' for sound, 1 for mute.
4052 '1Y' is capacitively coupled to tuner pin 20, FM right.
4052 '1X' is capacitively coupled to tuner pin 21, FM left.

Tuner pin 25, AF, appears to go through a 33k resistor to 4053 pin cx.
Pin 129, GPIO[01] = 4053 'C'
Pin 130, GPIO[00] = 4053 'B'
4053 inhibit is tied to ground  

            00:11.0 Multimedia video controller: CONEXANT: Unknown device 8800 (rev 05)
                    Subsystem: LeadTek Research Inc.: Unknown device 6611
                    Flags: bus master, medium devsel, latency 32, IRQ 9
                    Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
                    Capabilities: [44] Vital Product Data
                    Capabilities: [4c] Power Management version 2

            # detect
            0x86: TDA9885/TDA9886/TDA9887 tv and sound demodulator
            0xa0: eeprom
            0xc0: tuner
            # eeprom
            0000   01 ff ff ff  7d 10 11 66  ff ff ff ff  ff ff ff ff   .......f........
            0010   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0020   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0030   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0040   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0050   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0060   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0070   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0080   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            0090   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            00a0   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            00b0   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            00c0   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            00d0   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            00e0   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................
            00f0   ff ff ff ff  ff ff ff ff  ff ff ff ff  ff ff ff ff   ................

            from INF:
            Leadtek]
            ; E4 TVFM 880 NTSC MK3
            ; Video Driver enabled
            ; Audio Driver disabled
            ; TS Driver disabled
            ; VIP Port disabled
            ; Host Port disabled
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8801&SUBSYS_6613107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8802&SUBSYS_6613107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8803&SUBSYS_6613107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8804&SUBSYS_6613107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8811&SUBSYS_6613107D

            ; E4 TVFM 880 PAL MK3
            ; Video Driver enabled
            ; Audio Driver disabled
            ; TS Driver disabled
            ; VIP Port disabled
            ; Host Port disabled
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8801&SUBSYS_6611107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8802&SUBSYS_6611107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8803&SUBSYS_6611107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8804&SUBSYS_6611107D
            ;%WF23880.null%=NullSection,        PCI\VEN_14F1&DEV_8811&SUBSYS_6611107D

            ;;#########################################################################################
            ;661X
            %WF23880.FM1216MK3.1%=WF23880.FM1216MK3    ,PCI\VEN_14F1&DEV_8800&SUBSYS_6611107D
            %WF23880.FM1236MK3.1%=WF23880.FM1236MK3    ,PCI\VEN_14F1&DEV_8800&SUBSYS_6613107D
            %WF23880.FM1286MK3.1%=WF23880.FM1286MK3    ,PCI\VEN_14F1&DEV_8800&SUBSYS_661A107D

            ;662X
            %WF23880.FM1216MK3.2%=WF23880.FM1216MK3.DV    ,PCI\VEN_14F1&DEV_8800&SUBSYS_6620107D
            %WF23880.FM1236MK3.2%=WF23880.FM1236MK3.DV    ,PCI\VEN_14F1&DEV_8800&SUBSYS_6621107D
            %WF23880.FM1286MK3.2%=WF23880.FM1286MK3.DV    ,PCI\VEN_14F1&DEV_8800&SUBSYS_662A107D

            [FM1216MK3.AddReg]
            HKR,"DriverData","VideoStandard",0x00010001, 0x10,0x00,0x00,0x00
            HKR,"DriverData","ColorKillEnable",0x00010001, 0x01,0x00,0x00,0x00
            HKR,"DriverData","4in1Tuner",0x00010001, 0x01,0x00,0x00,0x00
            ; Country code is Germany = 49
            HKR,"DriverData","WWAudioCountryCode",0x00010001, 0x31,0x00,0x00,0x00
            HKR,"DriverData","Pll27",0x00010001, 0x00, 0x00, 0x00, 0x00
            HKR,"ENUM\Device1",pnpid,,"wf88xbar.cnxt"
            HKR,"ENUM\Device2",pnpid,,"wftune.fm1216mk3"

            [FM1236MK3.AddReg]
            HKR,"DriverData","VideoStandard",0x00010001, 0x01,0x00,0x00,0x00
            HKR,"DriverData","ColorKillEnable",0x00010001, 0x01,0x00,0x00,0x00
            ; Country code is USA = 1
            HKR,"DriverData","WWAudioCountryCode",0x00010001, 0x01,0x00,0x00,0x00
            HKR,"ENUM\Device1",pnpid,,"wf88xbar.cnxt"
            HKR,"ENUM\Device2",pnpid,,"wftune.fm1236mk3"

            [FM1286MK3.AddReg]
            HKR,"DriverData","VideoStandard",0x00010001, 0x01,0x00,0x00,0x00
            HKR,"DriverData","ColorKillEnable",0x00010001, 0x01,0x00,0x00,0x00
            ; Country code is Japan = 81
            HKR,"DriverData","WWAudioCountryCode",0x00010001, 0x51,0x00,0x00,0x00
            HKR,"ENUM\Device1",pnpid,,"wf88xbar.cnxt"
            HKR,"ENUM\Device2",pnpid,,"wftune.fm1286mk3"

            WF23880.FM1216MK3.1    = "WinFast TV2000 XP Expert WDM Video Capture.(PAL)"
            WF23880.FM1236MK3.1    = "WinFast TV2000 XP Expert WDM Video Capture.(NTSC)"
            WF23880.FM1286MK3.1    = "WinFast TV2000 XP Expert WDM Video Capture.(NTSC-J)"
            ;;------------------------------------------------------------------------------
            WF23880.FM1216MK3.2    = "WinFast DV2000 WDM Video Capture.(PAL)"
            WF23880.FM1236MK3.2    = "WinFast DV2000 WDM Video Capture.(NTSC)"
            WF23880.FM1286MK3.2    = "WinFast DV2000 WDM Video Capture.(NTSC-J)"
            ;;------------------------------------------------------------------------------
            ;WF23880.null        = "WinFast TV2000 XP Expert WDM .(unused device function)"

---

### Post by kvonb on 2006-09-03
Hello,

Hopefully  someone is still reading this thread!

I have a  Leadtek WinFast 2000 XP which is all setup and works excellent with tvtime.

I am trying to record tv shows with VLC and I have got it to capture the video perfectly, but cannot for the life of me get any audio!

Any ideas?

This is from dmesg:

```
[17179590.296000] bttv: driver version 0.9.16 loaded
[17179590.296000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179590.296000] bttv: Bt8xx card found (0).
[17179590.296000] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 209, latency: 64, mmio: 0xcfffe000
[17179590.296000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[17179590.296000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[17179590.296000] bttv0: gpio: en=00000000, out=00000000 in=00bfff06 [init]
[17179590.296000] bttv0: using tuner=5
[17179590.296000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179590.300000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179590.304000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179590.304000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179590.452000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179590.484000] bttv0: registered device video0
[17179590.484000] bttv0: registered device vbi0
[17179590.484000] bttv0: registered device radio0
[17179590.484000] bttv0: PLL: 28636363 => 35468950 ..<6>input: PC Speaker as /class/input/input1
[17179590.520000] bttv0: add subdevice "remote0"
[17179590.620000] bt878: AUDIO driver version 0.0.0 loaded
[17179590.620000] bt878: Bt878 AUDIO function found (0).
[17179590.620000] bt878(0): Bt878 (rev 17) at 00:08.1, irq: 209, latency: 64, memory: 0xcffff000
```

This is from /dev:

```
kev@kev:~$ ls -hAlF /dev/ | grep vid
crw-rw---- 1 root video    10, 175 2006-09-03 14:22 agpgart
crw-rw---- 1 root video    29,   0 2006-09-03 22:22 fb0
crw-rw---- 1 root video    81,  64 2006-09-03 14:22 radio0
crw-rw---- 1 root video    81, 224 2006-09-03 14:22 vbi0
lrwxrwxrwx 1 root root           6 2006-09-03 14:22 video -> video0
crw-rw---- 1 root video    81,   0 2006-09-03 14:22 video0
kev@kev:~$ ls -hAlF /dev/ | grep audio
crw-rw---- 1 root audio    14,  14 2006-09-03 14:22 admmidi
crw-rw---- 1 root audio    14,  12 2006-09-03 14:22 adsp
crw-rw---- 1 root audio    14,  13 2006-09-03 14:22 amidi
crw-rw---- 1 root audio    14,   4 2006-09-03 14:22 audio
crw-rw---- 1 root audio    14,   9 2006-09-03 14:22 dmmidi
crw-rw---- 1 root audio    14,   3 2006-09-03 14:22 dsp
```

I've tried EVERY audio device, and every audio in channel is enabled in the mixer, but still no sound in VLC.

The audio works well in tvtime.

Regards,

Kev :)

---

### Post by insub2 on 2006-10-10
maybe a different program?  if you get audio in tvtime, it seems like your hardware isn't the problem.  but i'm just a noob.

---

### Post by toganet on 2006-11-06
Hey guys, I have a couple of these cards, and both of them use card=34 tuner=43.

My problem is I do not know the "right" place to put the kernel module options so that those parameters are used at bootup.  I have been doing the whole "rmmod bt878; rmmod bttv" thing after it boots, and then modprobing the bttv module with the correct options, but even though I only reboot once every several months or so, it is still not ideal.

Should I blacklist bt878 and then have it load later in the boot sequence?

---

### Post by emperor on 2006-11-06
> **toganet said:**
> Hey guys, I have a couple of these cards, and both of them use card=34 tuner=43.

My problem is I do not know the "right" place to put the kernel module options so that those parameters are used at bootup.

Have you tried making an entry in "/etc/modprobe.d/options:" 
options bttv card=34 tuner=43

---

### Post by tipping point on 2007-02-14
I want to thank everyone who contributed to getting the Leadtek Winfast 2000XP (RM) working. I followed the command lines and my card is working fine.

---

### Post by theorem_hunter on 2007-02-25
what command did you type to get that output mellon?

---

### Post by laffys on 2007-03-06
I got mine working but no sound..... :(

---

### Post by amiba on 2007-03-23
For programs like vlc and mythtv, you also need to load the module btaudio, to get the sound working
You can check the info at [http://www.linuxtv.org/v4lwiki/index.php/Btaudio_(bt878](http://www.linuxtv.org/v4lwiki/index.php/Btaudio_(bt878))

---

### Post by ewdij on 2007-04-03
Has the cofig. info as outlined here worked for anyone running a 64 bit edgy ?

---

### Post by TheRLG on 2007-06-03
Hi all, I also have this card and cannot get any TV input.

I set the options card=34 and tuner=2, but no difference

The card is recognised correctly, but when I try to use it in MythTV, I get the blue screen with "No Signal" even though the cable is in correctly and the settings are correct.

Any help?

---

### Post by DriftShin on 2007-06-04
Wow. Was thinking i wouldn't find anything on the 2000XP. I have the Deluxe version and after looking it up on the Leadtek site, found that it used the Fusion 878A chipset. I have it installed in the machine but not sure how to get it started, installed basically. 
The one i have was bought in Australia but i'm now back home in Zambia, Africa. Will it be able to scan for the local channels coz when i tried it under Win XP, it would not be able to get any channel, just external video from my PS2.

Cheers.

---

