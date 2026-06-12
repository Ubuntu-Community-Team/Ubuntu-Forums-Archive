---
title: "Clickpad not working on Dell Inspiron 13 7000 (Ububtu 14.04)"
date: 2014-09-25
forum: Hardware
---

### Post by dean14 on 2014-09-25
Hello, I recently installed Ubuntu 14.04 on a new Dell Inspiron 14.04, everything works perfectly well except from the clickpad.
The clickpad does not respond at all.

The laptop came pre-installed with Windows and the Clickpad works, so I can rule hardware failure out.

I followed several guides and searched the web but wasn't able to solve it.

```

dean@dean-Insp:~$ xinput
&#9121; Virtual core pointer                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen Pen                        id=11    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=12    [slave  pointer  (2)]
&#9116;   &#8627; DLL0674:00 06CB:75DB                        id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys     

```

I tried to run:
```

dean@dean-Insp:~$ xinput test 13

```
```

dean@dean-Insp:~$ xinput test 15

```
Using the clickpad showd no output on screen. Doing the same with 12 gives output.

**ver-xorg-input-synaptics** is installed and latest, system has been updated to the latest.

I didnt install synaptiks because I read that it's no longer maintained and it is unavailable.

```

dean@dean-Insp:~$ sudo lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
dm_crypt               23177  0 
rfcomm                 69160  8 
bnep                   19624  2 
hid_sensor_magn_3d     13209  0 
hid_sensor_als         13123  0 
hid_sensor_gyro_3d     13209  0 
hid_sensor_accel_3d    13221  0 
hid_sensor_trigger     12916  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
kfifo_buf              13379  1 industrialio_triggered_buffer
industrialio           54069  7 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_accel_3d,hid_sensor_als,kfifo_buf,hid_sensor_magn_3d
hid_sensor_iio_common    13755  4 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
hid_multitouch         17407  0 
hid_sensor_hub         19536  6 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_als,hid_sensor_magn_3d,hid_sensor_iio_common
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
intel_rapl             18773  0 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
x86_pkg_temp_thermal    14205  0 
arc4                   12608  2 
intel_powerclamp       14705  0 
coretemp               13435  0 
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
nls_iso8859_1          12713  1 
kvm_intel             143109  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  1245 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  625 ghash_clmulni_intel,aesni_intel,ablk_helper
btusb                  32412  0 
bluetooth             391136  22 bnep,btusb,rfcomm
iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
serio_raw              13462  0 
snd_hda_intel          56451  5 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
iwlwifi               169932  1 iwlmvm
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lpc_ich                21080  0 
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 18627  0 
mei                    82276  1 mei_me
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
i2c_hid                18860  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
i2c_designware_platform    12960  0 
i2c_designware_core    14768  1 i2c_designware_platform
mac_hid                13205  0 
usbhid                 52659  0 
hid                   106148  4 i2c_hid,hid_multitouch,hid_sensor_hub,usbhid
i915                  783805  5 
ahci                   25819  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
psmouse               106678  0 
libahci                32716  1 ahci
drm                   303102  4 i915,drm_kms_helper
wmi                    19177  1 dell_wmi
video                  19476  1 i915

```

I believe that because xinfo shows two devices:
```

&#9116;   &#8627; DLL0674:00 06CB:75DB                        id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]

```
the issue might be with the module.

Please advice :(

---

### Post by ajgreeny on 2014-09-25
Did you try the live system before installing; it is always worth doing so as it may point out future hardware problems after installation and allow you to search for solutions before getting to your current situation.

I presume a mouse works OK so you can use the machine?

Try running **synclient -l** in terminal to see if it is recognised by software, and it may show that it is disabled for some reason.
```
TouchpadOff             = 0
``` I think, is what you should see if the touchpad is fully working.

---

### Post by dean14 on 2014-09-26
I have an external mouse, plus there's a touchscreen. I wold have replaced that sorry excuse of an OS with Ubuntu anyhow, it's a UX nightmare.

I tried your suggestion and something is strange:
 ```

dean@dean-insp:~$ synclient -l | grep Off
    TouchpadOff             = 2

```
And in another try:
```

dean@dean-insp:~$ synclient -l | grep Off
    TouchpadOff             = 0

```

This behavior persists. Once it's 0 and another time it's 2.

---

### Post by foxy123 on 2014-10-24
I wonder if you have found a solution. i've got this problem too.

---

