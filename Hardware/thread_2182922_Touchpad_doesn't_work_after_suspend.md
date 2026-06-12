---
title: "Touchpad doesn't work after suspend"
date: 2013-10-23
forum: Hardware
---

### Post by Michael_Peterson on 2013-10-23
I have just installed Ubuntu Gnome 13.10. When I put my laptop to suspend, and then wake it up again afterwords, my touchpad is disabled (even if it is enabled before it went to sleep).

I have found a few workarounds. I can type "sudo service gdm restart" in a command line, which is kind of annoying because it closes everything and logs me off.
The other solution is to use the keyboard to navigate to System Settings -> Mouse & Touchpad, then tabbing down to the on/off switch. Which again isn't very ideal...

I've tried googling this problem, and searched for quite a while, but I couldn't find an answer. Does anyone have any ideas?

Thanks.

---

### Post by NoBugs! on 2013-10-23
Is it a problem only in Gnome? What type of laptop?

---

### Post by Michael_Peterson on 2013-10-23
It may not be only in Gnome. I am coming from Windows, where it worked fine. I have an [MSI GT70 0NC]("http://www.msi.com/product/nb/GT70-0NC.html#/?div=Overview").

Should I remove the gnome tag?

---

### Post by Toz on 2013-10-23
With root privileges, try creating the file **/etc/pm/sleep.d/0000trackpad**. From a terminal window:
```
sudo -i gedit /etc/pm/sleep.d/0000trackpad
```
...enter you password when prompted and copy/paste this code into the gedit window:
```
#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su **USER** -c '/usr/bin/synclient TouchpaOff=0' ;;
esac
```
...and change the word **USER** (in the above code) with your actual username (the one that you use to log in to your computer).

Save the file, log out and back in again, and test the trackpad after a suspend/resume cycle.

---

### Post by Michael_Peterson on 2013-10-23
I'm assuming you meant: ```
sudo nano -i /etc/pm/sleep.d/0000trackpad
```

If I did exactly what you said, it made a file named gedit, then the file /etc/pm/sleep.d/000trackpad.

It did not work by the way.

---

### Post by Toz on 2013-10-23
Sorry about that, it should have been:
```
sudo -i gedit /etc/pm/sleep.d/0000trackpad
```
...(but "sudo nano /etc/pm/sleep.d/0000trackpad" should be ok). You can delete the file "gedit" if one was created.

To make sure, can you post back:
```
ls -l /etc/pm/sleep.d/0000trackpad
```
```
cat /etc/pm/sleep.d/0000trackpad
```
...and the contents of /var/log/pm-suspend.log either via copy/paste or
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated. Lets see what the log file says about that new file we created.

---

### Post by Toz on 2013-10-23
Sorry, I noticed a typo in the script as well. Not having a good typing day today. Try this version of the script:
```
#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su USER -c '/usr/bin/synclient TouchpadOff=0' ;;
esac
```

---

### Post by Michael_Peterson on 2013-10-23
Sadly this still didn't work. It seems to be working every other time though, which is better then before at least.

```

ls -l /etc/pm/sleep.d/0000trackpad
-rw-r--r-- 1 root root 113 Oct 23 21:19 /etc/pm/sleep.d/0000trackpad

```

```

cat /etc/pm/sleep.d/0000trackpad
#!/bin/sh
case "$1" in
    resume)
        DISPLAY=:0.0 su michael -c '/usr/bin/synclient TouchpadOff=0' ;;
esac

```

I don't have the file "[COLOR=#000000][FONT=Ubuntu Mono]/var/log/pm-suspend.log"[/FONT][/COLOR].

```

cat /var/log/pm-suspend.log
cat: /var/log/pm-suspend.log: No such file or directory

```

---

### Post by Toz on 2013-10-23
Can you run:
```
synclient
```
...before and after suspend and compare the results? Lets see exactly what's different.

> I don't have the file "/var/log/pm-suspend.log".
That's really odd. Where does Ubuntu Gnome log its suspend info? Is **pm-utils** installed?

---

### Post by Michael_Peterson on 2013-10-23
Before:

```


synclient                                                               ~  
Parameter settings:
    LeftEdge                = 1767
    RightEdge               = 5397
    TopEdge                 = 1637
    BottomEdge              = 4451
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 234
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -106
    HorizScrollDelta        = -106
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0374602
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 26
    VertHysteresis          = 26
    ClickPad                = 0




```

After:

```


synclient                                                               ~  
Parameter settings:
    LeftEdge                = 1767
    RightEdge               = 5397
    TopEdge                 = 1637
    BottomEdge              = 4451
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 234
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -106
    HorizScrollDelta        = -106
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0374602
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 26
    VertHysteresis          = 26
    ClickPad                = 0


```

And no, pm-utils was not installed, but it is now, and here is the file log you requested earlier.

```

cat /var/log/pm-suspend.log                                             ~  
Initial commandline parameters: 
Wed Oct 23 22:47:39 CDT 2013: Running hooks for suspend.
Running hook /etc/pm/sleep.d/0000trackpad suspend suspend:
/etc/pm/sleep.d/0000trackpad suspend suspend: not executable.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Michael-PC 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bbswitch               13943  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
joydev                 17377  0 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_realtek    51465  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431315  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12608  2 
iwldvm                237440  0 
mac80211              596969  1 iwldvm
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
iwlwifi               165398  1 iwldvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
btusb                  28267  0 
bluetooth             371874  22 bnep,btusb,rfcomm
rtsx_pci_ms            18151  0 
snd_rawmidi            30095  1 snd_seq_midi
memstick               16760  1 rtsx_pci_ms
cfg80211              479757  3 iwlwifi,mac80211,iwldvm
microcode              23518  0 
lpc_ich                21080  0 
psmouse                97626  0 
serio_raw              13413  0 
i915                  655752  4 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         52651  1 i915
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
drm                   296739  5 i915,drm_kms_helper
snd                    69141  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18421  0 
mei                    77692  1 mei_me
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
msi_wmi                13354  0 
sparse_keymap          13948  1 msi_wmi
mxm_wmi                13021  0 
wmi                    19070  2 msi_wmi,mxm_wmi
mac_hid                13205  0 
video                  19318  1 i915
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
rtsx_pci_sdmmc         23527  0 
ahci                   25819  2 
libahci                31898  1 ahci
sdhci_pci              18985  0 
alx                    32255  0 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
sdhci                  42630  1 sdhci_pci
mdio                   13807  1 alx
             total       used       free     shared    buffers     cached
Mem:      12200232    4887200    7313032          0     162524    2396700
-/+ buffers/cache:    2327976    9872256
Swap:            0          0          0
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend:
/usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
Unloading alx kernel module ...
Done.
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Wed Oct 23 22:47:39 CDT 2013: performing suspend
Wed Oct 23 22:47:49 CDT 2013: Awake.
Wed Oct 23 22:47:49 CDT 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
Reloading alx kernel module ...
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend:
Laptop mode 
enabled, not active
/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Running hook /etc/pm/sleep.d/0000trackpad resume suspend:
/etc/pm/sleep.d/0000trackpad resume suspend: not executable.


Wed Oct 23 22:47:49 CDT 2013: Finished.

```

---

### Post by Toz on 2013-10-24
From the log file:> Running hook /etc/pm/sleep.d/0000trackpad resume suspend:
/etc/pm/sleep.d/0000trackpad resume suspend: not executable.
...we need to:
```
sudo chmod +x /etc/pm/sleep.d/0000trackpad
```
...to make it executable. However, there is no change in the settings of synclient before and after suspend, so I'm not sure the file will help as it is written.

Can you try this version of the file instead:
```
cat /etc/pm/sleep.d/0000trackpad
#!/bin/sh
case "$1" in
    suspend|hibernate)
         modprobe -r psmouse ;;
    resume|thaw)
        modprobe psmouse ;;
esac
```
...don't forget to make the file executable.

---

### Post by Michael_Peterson on 2013-10-24
This seemed to have worked. I've successfully suspended/resumed several times and my touchpad has been enabled every time.

Thanks for the help.

---

### Post by Toz on 2013-10-24
Glad to hear. Can you please "Mark this thread as solved" using the "Thread Tools" link above? Thanks.

---

### Post by sanketmedhi on 2014-02-11
Great post. This worked on my Toshiba P55t-A5202 laptop. Thanks a ton!

---

