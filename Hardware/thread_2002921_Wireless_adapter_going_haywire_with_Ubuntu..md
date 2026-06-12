---
title: "Wireless adapter going haywire with Ubuntu."
date: 2012-06-13
forum: Hardware
---

### Post by NCShaffer on 2012-06-13
I have a HP Pavilion dv7 Entertainment Laptop and i recently said goodbye to Vista and put on Ubuntu since ive used it on my desktops and it worked amazingly. 

My only problem is my wireless is slow <snip>. The homepage of this forum which took my desktop 1 second to load took the laptop 10 minutes to load. No other laptops in my house do this, they all load instantly.

When the computer was Vista, the wireless was perfect, just the OS itself dragged.

I notice that the indicator for the wireless adapter keeps flashing between on and off very rapidly. This is Ubuntu doing this because no other OS on this laptop has ever done this.

How do i fix it? I don't want to go back to vista but i may have to if wireless is this slow.

---

### Post by NCShaffer on 2012-06-13
Can anyone please help me with this?

I go on a roadtrip tomorrow and i need this laptop.

---

### Post by josephmills on 2012-06-13
open termianl (ctrl+alt+t)
enter in 
```
lspci -nn 
```
then 
```
lsmod
```
then paste here

---

### Post by NCShaffer on 2012-06-13
nickolas@nickolas-HP-Pavilion-dv7-Notebook-PC:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96 [GeForce 9600M GT] [10de:0649] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
06:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
06:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
06:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
06:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
06:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
nickolas@nickolas-HP-Pavilion-dv7-Notebook-PC:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
arc4                   12473  2 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
hp_wmi                 13652  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlwifi               291847  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 iwlwifi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10962290  43 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
cfg80211              178679  2 iwlwifi,mac80211
videodev               86588  1 uvcvideo
psmouse                72919  0 
jmb38x_ms              17406  0 
serio_raw              13027  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15857  1 jmb38x_ms
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
video                  19068  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
hp_accel               25728  0 
rc_rc6_mce             12454  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
ene_ir                 18019  0 
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
r8169                  56321  0 
nickolas@nickolas-HP-Pavilion-dv7-Notebook-PC:~$

---

### Post by typhoon_tip on 2012-06-13
I think your hardware is fine. I think the problem is your router settings, I have had this problem everywhere as well.

Try to change your Wireless router settings to WPA2/WEP encryption, and play around with mixed mode (G, B, N) and see how it goes.

---

### Post by ahallubuntu on 2012-06-13
You have an Intel wireless card:

> 02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]

I have a couple of laptops with this same card (though not the HP version you have).  The 5100 has been a great card for me - has worked out of the box in all the older versions of Ubuntu I've tried.  (What version are you using?)

Some people have had issues with this card, however, and have been forced to turn off the "N" speed and revert to "G" speed to get reliable connections.  I've not had to do this myself - I get fast downloads with my 5100 cards.  My current laptop doesn't have a wireless light; I'm not sure if the flickering has anything to do with connection speed, but you can modify some setting to set it to always be ON or OFF if it bothers you...

You're using the latest Ubuntu 12.04 LTS I take it?  If so, you can try the "G" workaround (disable N) listed here:

[http://www.mattkirwan.com/linux/slow-wireless-connection-ubuntu-12-04-lenovo-thinkpad-x200/](http://www.mattkirwan.com/linux/slow-wireless-connection-ubuntu-12-04-lenovo-thinkpad-x200/)

The 5100 card is the same for both HP and Lenovo (there's a different version of that card for non-HP/non-Lenovo laptops).

---

### Post by typhoon_tip on 2012-06-13
> **ahallubuntu said:**
> ..and have been forced to turn off the "N" speed and revert to "G" speed to get reliable connections.  I've not had to do this myself - I get fast downloads with my 5100 cards.  My current laptop doesn't have a wireless light; I'm not sure if the flickering has anything to do with connection speed, but you can modify some setting to set it to always be ON or OFF if it bothers you...

Correct, that's the key. Wireless handling is different than Windows in Ubuntu, and may try to connect at higher speed but failed. With my PC, I could reach a very unreliable 300 Mbps on mine, but it was always failing and slowing down due to router firmware badly made. Have to revert to 65 Mbps stable connection !

---

### Post by NCShaffer on 2012-06-14
Thankyou, it works perfectly now. The indicator still blinks wildly, but my internet is ok.

---

### Post by ahallubuntu on 2012-06-14
Good to hear.  You can probably fix the light (or disable it) by putting this:

```
options iwlwifi led_mode=1
```

in that same conf file you just created.

---

### Post by typhoon_tip on 2012-06-16
> **NCShaffer said:**
> Thankyou, it works perfectly now. The indicator still blinks wildly, but my internet is ok.

That might be correct. My ThinPad T400 does not flash in Windows, while it does signal activity with Ubuntu, flashing during transfer of packets.

---

