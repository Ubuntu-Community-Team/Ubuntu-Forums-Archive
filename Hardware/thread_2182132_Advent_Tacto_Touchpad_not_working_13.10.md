---
title: "Advent Tacto Touchpad not working 13.10"
date: 2013-10-20
forum: Hardware
---

### Post by Gareth_Rogers on 2013-10-20
Greetings.

I have recently purchased an advent tacto laptop that came with windows 8, i immediately deleted it and installed ubuntu, everything works fine, including the touchscreen, apart from the touchpad. im currently using a combination of the touchscreen and a USB mouse. Im unsure where to start to try and either diagnose or fix this problem, ive searched this forum and have been unable to find any other reference to this particular machine. 

Any advice/help would be much appreciated.

---

### Post by varunendra on 2013-10-22
Welcome to the forums Gareth!

A good starting point may be looking at the model of your touchpad, and the drivers that are currently loaded. Please open a terminal (Ctrl-Alt-T) and post back the outputs of these commands -
```
xinput
lsmod
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by Gareth_Rogers on 2013-10-22
Hi there.

Thanks for the reply, here are the outputs to those commands, please bear in mind i currently have a wireless mouse plugged in which i am using.

xinput

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=11    [slave  pointer  (2)]
&#9116;   &#8627; SONiX USB Device                            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; USB Video Device                            id=10    [slave  keyboard (3)]
    &#8627; SONiX USB Device                            id=14    [slave  keyboard (3)]

```

lsmod

```

Module                  Size  Used byparport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431315  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
joydev                 17377  0 
cryptd                 20329  1 ghash_clmulni_intel
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_realtek    51465  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
arc4                   12608  2 
ath9k                 151173  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
cfg80211              479757  3 ath,ath9k,mac80211
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
i915                  655752  4 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath3k                  13318  0 
btusb                  28267  0 
psmouse                97626  0 
microcode              23518  0 
hid_multitouch         17407  0 
bluetooth             371874  13 bnep,ath3k,btusb,rfcomm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13413  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
drm_kms_helper         52651  1 i915
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm                   296739  5 i915,drm_kms_helper
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19318  1 i915
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
mei_me                 18421  0 
mei                    77692  1 mei_me
lpc_ich                21080  0 
mac_hid                13205  0 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ext2                   72832  1 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  3 hid_multitouch,hid_generic,usbhid
ahci                   25819  3 
libahci                31898  1 ahci
r8169                  67341  0 
mii                    13934  1 r8169

```

Hope this is helpful and correct.

---

### Post by varunendra on 2013-10-22
> **Gareth_Rogers said:**
> 
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=11    [slave  pointer  (2)]
&#9116;   &#8627; SONiX USB Device                            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
...

```

The touchpad isn't even registered there. Is it enabled from BIOS? Please check that.
Does it have any hardware switch (a button or a touchpoint, or a Key combo etc.) to enable/disable the touchpad? Please also try it.

As per your current output of 'xinput', the system can't even 'see' the touchpad, while as per lsmod, the drivers usually necessary to make it work are loaded.

And please also post back the outputs of :
```
lsusb
usb-devices
cat /proc/bus/input/devices
```

---

### Post by Gareth_Rogers on 2013-10-22
Hi.

I have had a look through the BIOS and there is no mention of a mouse or trackpad etc that i can see, only webcam and wake on LAN in the hardware section.

lsusb

```

Bus 002 Device 003: ID 0c45:0520 Microdia 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03eb:8433 Atmel Corp. 
Bus 001 Device 004: ID 13d3:3362 IMC Networks 
Bus 001 Device 005: ID 090c:37c0 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Silicon Motion Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

usb-devices

```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=090c ProdID=37c0 Rev=03.13
S:  Product=USB Video Device
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3362 Rev=00.02
S:  Manufacturer=Atheros Communications
S:  Product=Bluetooth USB Host Controller
S:  SerialNumber=Alaska Day 2006
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=03eb ProdID=8433 Rev=13.21
S:  Manufacturer=Atmel
S:  Product=Atmel maXTouch Digitizer
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.11
S:  Manufacturer=Linux 3.11.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0c45 ProdID=0520 Rev=00.01
S:  Manufacturer=SONiX
S:  Product=USB Device
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

```

cat /proc/bus/input/devices

```

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=0c45 Product=0520 Version=0100
N: Name="SONiX USB Device"
P: Phys=usb-0000:00:1d.0-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event5 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f


I: Bus=0003 Vendor=0c45 Product=0520 Version=0100
N: Name="SONiX USB Device"
P: Phys=usb-0000:00:1d.0-1.1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input6
U: Uniq=
H: Handlers=kbd mouse0 event6 
B: PROP=0
B: EV=17
B: KEY=1f0000 2020000 3878d801d001 1e000000000000 0
B: REL=103
B: MSC=10


I: Bus=0003 Vendor=03eb Product=8433 Version=0111
N: Name="Atmel Atmel maXTouch Digitizer"
P: Phys=usb-0000:00:1a.0-1.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=260800000000003


I: Bus=0003 Vendor=090c Product=37c0 Version=0313
N: Name="USB Video Device"
P: Phys=usb-0000:00:1a.0-1.2/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=10



```


thanks.

---

### Post by varunendra on 2013-10-22
I can see no traces of any other pointing device in above and don't know where else to look.

You didn't say anything about a hardware switch or something like a Fn+ key combo to enable/disable it. Does it have one? Does it have any indication of working?

I see a few modules in lsmod that I have never seen (or noticed) before. Besides, some known ones may also be associated with more than one device at a time. I don't know yet a decent way to trace them back to the device they are working for.

So instead of going on possibly a wild-goose-chase, could you please try a live cd/usb of 12.4.3 to see if it works there or not? If you choose to try that, I'd recommend to download the ISO via torrent, as it is not only fast, but ensures the integrity of the ISO too. Choose the 12.04.3 Desktop (64 bit) torrent from here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

And in the meanwhile let's try this ugly code to try tracing back some drivers to the devices they may have been loaded for -
```
find -L /sys/module/{joydev,uvcvideo,btusb,psmouse,hid_multitouch,serio_raw,mac_hid,hid_generic,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
```
This should trace all the drivers within the curly braces back to the device names they are loaded for, along with the full path which may also help relating them to the input devices found in "/proc/bus/input/devices" file.

These paths as well as their depths sometimes can change on different systems, so not sure if it will work for you the same way as it does here. Anyway, this is all I could conjure so far, and I would once again recommend trying 12.04.3 to see if the touchpad works with it. Even if nothing else works well but the touchpad does, at least it will give us something solid to work upon.

---

### Post by Gareth_Rogers on 2013-10-23
Hi there. 

Thanks for that, i will try a live boot off a USB when i arrive home from work tonight and report back. I apologise for neglecting to mention about the function key for the tra kpad. it does indeed have one, fn+esc to be precise, but i have tried it several times, and ran all sets of commands before and after using it and nothing appears to change.

Here is the output for that string of code, i will report back once i have tried the live USB. Thankyou for your help so far.

> 
/sys/module/uvcvideo/drivers/usb:uvcvideo/1-1.2:1.0/input/input15/name	USB Video Device
/sys/module/uvcvideo/drivers/usb:uvcvideo/1-1.2:1.0/video4linux/video0/name	USB Video Device
/sys/module/btusb/drivers/usb:btusb/1-1.3:1.0/bluetooth/hci0/name	gaz-Tacto-0
/sys/module/btusb/drivers/usb:btusb/1-1.3:1.0/bluetooth/hci0/rfkill2/name	hci0
/sys/module/usbhid/drivers/usb:usbhid/1-1.4:1.0/input/input5/name	Atmel Atmel maXTouch Digitizer
/sys/module/usbhid/drivers/usb:usbhid/2-1.1:1.0/input/input13/name	SONiX USB Device
/sys/module/usbhid/drivers/usb:usbhid/2-1.1:1.1/input/input14/name	SONiX USB Device


---

### Post by Gareth_Rogers on 2013-10-23
Hi Varun.

I have tried the live USB you suggested and everything appears to be the same, everything working ok apart from the trackpad which doesn't seem to exist :(

---

### Post by varunendra on 2013-10-23
> **Gareth_Rogers said:**
> it does indeed have one, fn+esc to be precise, but i have tried it several times, and ran all sets of commands before and after using it and nothing appears to change.
Do other Fn+ combinations work?

> **Gareth_Rogers said:**
> Here is the output for that string of code, i will report back once i have tried the live USB.
```
/sys/module/uvcvideo/drivers/usb:uvcvideo/1-1.2:1.0/input/input15/name	USB Video Device
/sys/module/uvcvideo/drivers/usb:uvcvideo/1-1.2:1.0/video4linux/video0/name	USB Video Device
/sys/module/btusb/drivers/usb:btusb/1-1.3:1.0/bluetooth/hci0/name	gaz-Tacto-0
/sys/module/btusb/drivers/usb:btusb/1-1.3:1.0/bluetooth/hci0/rfkill2/name	hci0
/sys/module/usbhid/drivers/usb:usbhid/1-1.4:1.0/input/input5/name	Atmel Atmel maXTouch Digitizer
/sys/module/usbhid/drivers/usb:usbhid/2-1.1:1.0/input/input13/name	SONiX USB Device
/sys/module/usbhid/drivers/usb:usbhid/2-1.1:1.1/input/input14/name	SONiX USB Device
```
It is strange that the "psmouse" driver is loaded, but is not associated with any device. It makes me wonder if the touchpad was detected initially, then got lost at some point during the boot process. But this assumption may be wrong, especially considering your later experience -
> **Gareth_Rogers said:**
> I have tried the live USB you suggested and everything appears to be the same, everything working ok apart from the trackpad which doesn't seem to exist :(
Was it 12.04.3?

I hate to throw wild guesses, but we don't have anything substantial to work with yet. So.... umm.. could you try an even older version? Like the original release of 12.04 (not 12.04.1,2 or 3). It uses kernel 3.2 series, and if even that can't detect the touchpad (assuming there *might be* some bug in 13.8+ kernels), then almost definitely it is either a hardware/firmware issue, or a BIOS setting.

You can get 12.04 original release here : [http://old-releases.ubuntu.com/releases/12.04.0/](http://old-releases.ubuntu.com/releases/12.04.0/) *(scroll down to the list below, it seems the .iso is working, torrent is not, but try it first anyway)*.

As another hopeless attempt to find some hint of when and for what the "psmouse" driver was loaded, please check the logs that may contain messages about it -
```
grep -iR psmouse /var/log 2>/dev/null
```
This will return all the lines from all the files (within /var/log) that contain "psmouse" in them, prefixed with the filenames.

To get Only the filenames (in case the above list gets too long) of the files that contain that word -
```
grep -iRl psmouse /var/log 2>/dev/null
```

Unless someone else with a better idea to investigate/troubleshoot the issue jumps in and join us here, I'd suggest you to also contact the vendor asking if there is some hidden setting or a 'special' way to make it work.

---

### Post by nigelclegg on 2014-02-20
Hi,

I have the same laptop with exactly the same problem. 
I've added the code for the log to see if that helps you to see what the problem may be.

```
sudo grep -iR psmouse /var/log 2>/dev/null/var/log/syslog.1:Feb 17 23:16:13 mollie-PC kernel: [   13.868371] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/syslog.1:Feb 17 23:16:13 mollie-PC kernel: [   13.883526] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/syslog.1:Feb 17 23:39:05 mollie-PC kernel: [   16.931716] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/syslog.1:Feb 17 23:39:05 mollie-PC kernel: [   16.947086] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/syslog.1:Feb 18 01:05:05 mollie-PC kernel: [   18.539242] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/syslog.1:Feb 18 01:05:05 mollie-PC kernel: [   18.554075] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/udev:KERNEL[19.101189] add      /module/psmouse (module)
/var/log/udev:DEVPATH=/module/psmouse
/var/log/udev:KERNEL[19.111781] add      /bus/serio/drivers/psmouse (drivers)
/var/log/udev:DEVPATH=/bus/serio/drivers/psmouse
/var/log/udev:UDEV  [19.929716] add      /module/psmouse (module)
/var/log/udev:DEVPATH=/module/psmouse
/var/log/udev:UDEV  [19.931638] add      /bus/serio/drivers/psmouse (drivers)
/var/log/udev:DEVPATH=/bus/serio/drivers/psmouse
/var/log/installer/syslog:Feb 17 21:37:03 ubuntu kernel: [   20.977074] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/installer/syslog:Feb 17 21:37:03 ubuntu kernel: [   20.992221] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/kern.log:Feb 17 23:16:13 mollie-PC kernel: [   13.868371] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/kern.log:Feb 17 23:16:13 mollie-PC kernel: [   13.883526] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/kern.log:Feb 17 23:39:05 mollie-PC kernel: [   16.931716] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/kern.log:Feb 17 23:39:05 mollie-PC kernel: [   16.947086] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/kern.log:Feb 18 01:05:05 mollie-PC kernel: [   18.539242] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
/var/log/kern.log:Feb 18 01:05:05 mollie-PC kernel: [   18.554075] psmouse serio1: elantech: Synaptics capabilities query result 0x11, 0x16, 0x0c.
/var/log/auth.log:Feb 20 21:14:25 mollie-PC sudo:   mollie : TTY=pts/1 ; PWD=/home/mollie ; USER=root ; COMMAND=/bin/grep -iRl psmouse /var/log
/var/log/auth.log:Feb 20 21:15:08 mollie-PC sudo:   mollie : TTY=pts/1 ; PWD=/home/mollie ; USER=root ; COMMAND=/bin/grep -iR psmouse /var/log
/var/log/pm-suspend.log:psmouse                97655  0 
/var/log/pm-suspend.log:psmouse                97655  0 
/var/log/pm-suspend.log:psmouse                97655  0 
/var/log/pm-suspend.log:psmouse                97655  0 



```

I'm sure the touchpad worked the day I installed Ubuntu but I may be wrong.

---

