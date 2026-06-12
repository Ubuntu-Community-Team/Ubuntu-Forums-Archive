---
title: "Ubuntu 9.04 &#1080; AverMedia 507"
date: 2009-05-02
forum: Hardware
---

### Post by AlexKar on 2009-05-02
I updated my favorite Ubuntu 8.04 and installed 9.04 version. All hardware work correct with the exception of TV-tunner (Aver Media 507).
I execute standard installation steps - create saa7134.conf file in /etc/modprobe.d with the following content:
alias char-major-81 videodev
options i2c-algo-bit bit_test=1
options saa7134 card=45 tuner=38 i2c_scan=1 radio_nr=1
options tuner secam=d port2=0 port1=1

alias char-major-81-0 saa7134
alias char-major-81-1 off
alias char-major-81-2 off
alias char-major-81-3 off

After this manipulations "dmesg | grep 'saa'" command shows:
[   11.849530] saa7130/34: v4l2 driver version 0.2.14 loaded
[   11.849844] saa7134 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   11.849851] saa7133[0]: found at 0000:01:06.0, rev: 209, irq: 18, latency: 32, mmio: 0xfdeff000
[   11.849857] saa7133[0]: subsystem: 1461:a11b, board: Avermedia AVerTV Studio 507 [card=102,insmod option]
[   11.849985] saa7133[0]: board init: gpio is d8
[   11.850106] input: saa7134 IR (Avermedia AVerTV St as /devices/pci0000:00/0000:00:09.0/0000:01:06.0/input/input6
[   12.038054] saa7133[0]: i2c eeprom 00: 61 14 1b a1 ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038064] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038072] saa7133[0]: i2c eeprom 20: ff f1 f7 ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038079] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038086] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038093] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038100] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038107] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038114] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038121] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038128] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038135] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038142] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038149] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038156] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.038163] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.052404] saa7133[0]: i2c scan: found device @ 0x86  [tda9887]
[   12.060034] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[   12.068037] saa7133[0]: i2c scan: found device @ 0xc2  [[IMG]http://forum.ubuntu.ru/Smileys/webby/huh.gif[/IMG]]
[   12.166672] saa7133[0]: registered device video0 [v4l2]
[   12.166726] saa7133[0]: registered device vbi0
[   12.166773] saa7133[0]: registered device radio1
[   12.229365] saa7134 ALSA driver for DMA sound loaded
[   12.229402] saa7133[0]/alsa: saa7133[0] at 0xfdeff000 irq 18 registered as card -2

It's normal log and driver is initialized but tvtime program doesn't work and 
tvtime-scanner doesn't find any channels. In Ubuntu 8.04 it worked correct.
Content of tvtime.xml file is correct too:
<tvtime xmlns="[http://tvtime.sourceforge.net/DTD/](http://tvtime.sourceforge.net/DTD/)">

  <!--
    Default $HOME/.tvtime/tvtime.xml configuration file.
    Do not edit this config file while tvtime is running, it
    will be overwritten during runtime to update program settings.
  -->


  <!--
    The verbose setting indicates that we should print full
    informational and warning messages to stderr while running tvtime.
    Otherwise, only fatal errors will be printed to the output.
  -->
  <option name="Verbose" value="0"/>


  <!-- This sets the default capture device to use. -->
  <option name="V4LDevice" value="/dev/video0"/>

  <!--
    This sets the default capture card input to be opened by tvtime.
    For example, for my WinTV card has the tuner as source 0, and
    its composite input as source 1.  Sources can be changed at runtime
    using the "toggle_input" command, which is key command "i" by
    default.
  -->
  <option name="V4LInput" value="0"/>

  <!--
    This sets the default TV norm.  Valid options are:
       NTSC
       NTSC-JP
       SECAM
       PAL
       PAL-Nc
       PAL-M
       PAL-N
       PAL-60
  -->
  <option name="Norm" value="PAL"/>

  <!--
    This sets the default frequency table to use for any tuners found.
    Possibilities are:
       us-cable
       us-broadcast
       japan-cable
       japan-broadcast
       europe
       australia
       australia-optus
       newzealand
       france
       russia
  -->
  <!--
  <option name="Frequencies" value="europe"/>
  -->

  <!--
    There are two special NTSC cable standards in the US: IRC and HRC.
    In IRC, channels 5 and 6 are on different frequencies, and HRC mode
    shifts all frequencies up by 1.25MHz (and is also weird on channels
    5 and 6).  Use this option to set the cable mode to "Standard",
    "IRC", or "HRC".  It is very rare that you will see cable systems
    that use IRC or HRC cable.
  -->
  <option name="NTSCCableMode" value="Standard"/>

  <!--
    Toggle whether tvtime should check if there is a signal present
    when changing channels etc.  If your card doesn't suck, you
    shouldn't need to shut this off.  Disabling this feature will also
    disable the channel scanner.
  -->
  <option name="CheckForSignal" value="1"/>

  <!--
    This sets how many pixels per scanline to request from the capture
    card.  A higher setting gives better quality, while a lower setting
    means we do less work, and so tvtime will run faster.  If you have
    a slower CPU (like, less than 500Mhz or so), maybe values of 480
    or 400 might suit you best.  For best quality, choose a high value
    like 720 or 768.  Most capture cards cannot sample higher than 768
    pixels per scanline.
  -->
  <option name="InputWidth" value="720"/>

  <!--
    Set this to a filename to get show listings from an xmltv file.
    Set to "none" if you do not wish to use xmltv.
  -->
  <option name="XMLTVFile" value="none"/>

  <!--
    Set this to a two-letter language code to set the language to use
    for entries in the XMLTV file (for example, use "de" for German).
    Set to "none" if you wish to use the default language of the file.
  -->
  <option name="XMLTVLanguage" value="none"/>

  <!--
    Set this to 1 to enable XDS channel information decoding.  This
    option is specific to NTSC regions.  XDS is used to send information
    about the channel including the network name and call letters, and
    sometimes information about the current show.  This information is
    then shown on the OSD and saved to the stationlist.xml file.
  -->
  <option name="UseXDS" value="0"/>

  <!--
    This sets which device to use for VBI decoding.
  -->
  <option name="VBIDevice" value="/dev/vbi0"/>

  <!--
    This sets the mixer device and channel to use.  The format is device
    name:channel name.  Valid channels are:
      vol, bass, treble, synth, pcm, speaker, line, mic, cd, mix, pcm2,
      rec, igain, ogain, line1, line2, line3, dig1, dig2, dig3, phin,
      phout, video, radio, monitor
   -->
  <option name="MixerDevice" value="/dev/mixer:line"/>

  <!--
    This option enables 16:9 aspect ratio mode by default on startup.
  -->
  <option name="Widescreen" value="0"/>

  <!--
    Disabling this option tells tvtime to use the X server DPI to determine
    pixel shape.  By default, tvtime assumes pixels are square.  Set this
    to 0 if you have a 4:3 monitor but run it at 1280x1024 and want tvtime
    to do the right thing.
  -->
  <option name="SquarePixels" value="1"/>

  <!--
    Sets the geometry of the window.  A width value of 0 signifies
    that the appropriate width for the given height will be used.
    For 4:3 content on a square pixel display, this defaults to a
    768x576 window.
  -->
  <option name="WindowGeometry" value="0x576"/>

  <!--
    This sets the percent of the sides to leave to the overscan, that
    is, don't show them at all.  Safe action area on a television is 10%
    in the overscan, but that's a bit restrictive.  If you want tvtime
    to look like a TV, a good value would be about 6-8%.  The value is
    in percent, so for 8%, use 8.0.
  -->
  <option name="Overscan" value="3.5"/>

Please, give me some advices - How I can make tvtunner to work!

---

