---
title: "Samsung netbook brightness control(Again)"
date: 2013-07-18
forum: Hardware
---

### Post by Captain NFB on 2013-07-18
Hi
I Run Ubuntu on a Samsung N150+ netbook. 
I have recently updated Ubuntu (to 13.04) and now the backlight control doesn't work...
If I start up with the mains pluged in the screen comes up bright enough to see clearly, but if I start up on battery power the screen is so dim I can barely see what I am doing. Either way I cannot alter the screen brightness.

This is not an entirely new problem. When I first installed Ubuntu it didn't work and I found the following solution:

   
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-tools samsung-backlight
sudo reboot

   
So, I have tried this again. With no effect.

   I have discovered that under Settings/Software & Updates/Other software it says:

   
Disabled on upgrade to Oneric ([http://ppa.launchpad.net/voria/ppa](http://ppa.launchpad.net/voria/ppa))

   
So I guess that is why the above no longer works.

In addition, some of the other Hotkeys (Eg. wifi/bluetooth/sound/screen on/off) all work. 
This is currently causing big problems. I'm away from home, using my netbook  as my primary form of comunication in cafes etc. My ability to find a wifi connection with a power supply is limited.

   
**Work Around**: I have just discovered that if I start on a power supply and then 'Hibernate' I will have a bright screen if I restart on battery power. But still no brightness control.

   
Other than reverting to backup (My backups are at home) does anyone have a solution? 

I looked on the Ubuntu forums and found this thread:

   [URL="http://ubuntuforums.org/showthread.php?t=2163131&highlight=Samsung+Backlight"]
http://ubuntuforums.org/showthread.php?t=2163131&highlight=Samsung+Backlight[/URL]

   
Which might help me, if I understood it. I'm not very good with the technical side of Ubuntu, as it usually just works.

   I then found this thread:

   [URL="http://ubuntuforums.org/showthread.php?t=2162886"]
http://ubuntuforums.org/showthread.php?t=2162886[/URL]

   
Which asked for the some comands to be run (for Diagnostics?):

   
1 Your current kernel command line:
Code:

  ```

cat /proc/cmdline


```   
Produces:

  ```
 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=2a09def6-779f-4377-bf2d-72f44d877e5d ro quiet splash vt.handoff=7


```   
2 Your video card and driver:
Code:

  ```
 
sudo lspci -vnn | grep -A12 VGA


```   
Produces:

  ```
 
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])

 Subsystem: Samsung Electronics Co Ltd Notebook N150P [144d:c072]
Flags: bus master, fast devsel, latency 0, IRQ 46
Memory at f0300000 (32-bit, non-prefetchable) [size=512K]
I/O ports at 18d0 [size=8]
Memory at d0000000 (32-bit, prefetchable) [size=256M]
Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
Expansion ROM at <unassigned> [disabled]
Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
Capabilities: [d0] Power Management version 2
Kernel driver in use: i915

    00:02.1 Display controller [0380]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a012]


```   
3 Your backlight interfaces:
Code:

  ```
 
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done


```   
Produces:

  ```
 
/sys/class/backlight/intel_backlight
12421
12421
/sys/class/backlight/samsung
8
8


```   
So I have done likewise, in the hopes that they will be usefull...
I suspect that the first link above is probably the solution, if only I understood it.

---

### Post by Toz on 2013-07-18
Lets try the solution from [http://ubuntuforums.org/showthread.php?t=2163131]("http://ubuntuforums.org/showthread.php?t=2163131") and see if it works.

First, open a terminal window and enter the following command:
```
sudo modprobe -r samsung_laptop
```
...enter your password when prompted. This will unload the samsung_laptop module which may be interfering with the backlight. In the other thread, according to the OP, this was sufficient to make the backlight work again, so check your backlight.

The rest of the instructions were to make it permanent.

---

### Post by Captain NFB on 2013-08-20
Hi Toz

First thanks for your prompt reply, and sorry for not getting back to you sooner but with the hacking and me spending 20 days offshore in a small boat, its taken me some time to get back to this.


   I ran:


  ```
 sudo modprobe -r samsung_laptop



```   and after logging out and back in again the backlight works!


   I then used


  ```
 sudo gedit



```   to open gedit, located the file


  ```
  /etc/modprobe.d/blacklist.conf



```   added


  ```
 blacklist samsung_laptop



```   closed the file and ran


  ```
 sudo update-initramfs -u



```   I then rebooted the computer to...no brightness control.


   Since in the other thread you asked for the following to be run, I've done likewise:


  ```
 for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done



```   Gives:


  ```
 /sys/class/backlight/intel_backlight
12421
12421
/sys/class/backlight/samsung
6
8



```  ```
 lsmod | grep samsung



```   Gives


  ```
 samsung_backlight      13807  0 



```   and


  ```
 dmesg | grep samsung



```   Gives


   [```
   31.868811] samsung_laptop: Disabling ACPI video driver
[   31.908905] samsung_laptop: enabled workaround for brightness stepping quirk
[   31.920663] samsung_laptop: detected SABI interface: SwSmi@
[   31.928375] sysfs: cannot create duplicate filename '/class/backlight/samsung'
[   31.928380] Modules linked in: samsung_laptop(+) parport_pc(F) ppdev(F) rfcomm bnep binfmt_misc(F) coretemp hid_generic joydev(F) gpio_ich snd_hda_codec_realtek samsung_backlight(OF) microcode(F) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core snd_hda_intel videodev usbhid snd_hda_codec hid snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) lib80211_crypt_tkip i915 snd_rawmidi(F) wl(POF) snd_seq(F) snd_seq_device(F) video(F) snd_timer(F) lib80211 drm_kms_helper cfg80211 mac_hid drm psmouse(F) btusb snd(F) serio_raw(F) bluetooth lpc_ich i2c_algo_bit soundcore(F) lp(F) parport(F) ahci(F) libahci(F) sky2
[   31.928663]  [<ffffffffa0695562>] samsung_init+0x54c/0xfea [samsung_laptop]
[   31.928679]  [<ffffffffa0695016>] ? samsung_dmi_matched+0x16/0x16 [samsung_laptop]
```


   In addition, when I ran 


  ```
 sudo gedit



```   Terminal said:


  ```
 (gedit:4003): IBUS-WARNING **: The owner of /home/henry/.config/ibus/bus is not root!



```   In case that is relevent.

Thanks for your help so far.

---

### Post by Toz on 2013-08-20
Thats interesting. You still have a samsung backlight interface. What happens if you unload samsung_backlight as well:
```
sudo modprobe -r samsung_backlight
```
...and log out and back in again?

Maybe even try blacklisting it as well in /etc/modprobe.d/blacklist.conf along with the other one.

---

### Post by Captain NFB on 2013-08-29
Hi Toz,
I ran:


  ```
 sudo modprobe -r samsung_backlight



```   and got the reply:


  ```
 FATAL: Module samsung_backlight not found.



```   But the backlight control started working, so I added


  ```
 samsung_backlight



```   to


  ```
 /etc/modprobe.d/blacklist.conf 



```   ran


  ```
 sudo update-initramfs -u



```   and restarted the computer- to no backlight control.
I then discovered that if I turn on the computer, log in, log out and then log back in again the backlight control works.
Is there anyway of getting backlight control right from the start?

---

### Post by sbnwl on 2013-08-29
Upgrades sometimes become problems. Could you afford a fresh install, or atleast test your laptop backlight using a LIVE CD of Ubuntu 13.04. It will help you to compare the differences in configurations in fresh install vs your current system.

---

### Post by Toz on 2013-08-29
> **Captain NFB said:**
> Hi Toz,
I ran:


  ```
 sudo modprobe -r samsung_backlight



```   and got the reply:


  ```
 FATAL: Module samsung_backlight not found.



```   But the backlight control started working, so I added


  ```
 samsung_backlight



```   to


  ```
 /etc/modprobe.d/blacklist.conf 



```   ran


  ```
 sudo update-initramfs -u



```   and restarted the computer- to no backlight control.
I then discovered that if I turn on the computer, log in, log out and then log back in again the backlight control works.
Is there anyway of getting backlight control right from the start?
Can you post back:
```
lsmod
```
...to see whats running now? It would be interesting to compare this result from right after boot to after logout and back in again to see if something is changing.

---

### Post by Captain NFB on 2013-09-08
Hi Toz
I ran 

```
lsmod
```
       
Twice. After Start up I got:

   

    ```
 Module                                Size  Used by
michael_mic     12612  8 
arc4                                 12615  4 
samsung_laptop         14532  0 
parport_pc                   28152  0 
ppdev                              17073  0 
rfcomm                           42641  0 
bnep                                  18036  2 
binfmt_misc                 17500  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel            39619  3 
lib80211_crypt_tkip    17379  0 
snd_hda_codec         136498  2 snd_hda_codec_realtek,snd_hda_intel
wl                                 3074449  0 
i915                               600349  3 
snd_hwdep                   13602  1 snd_hda_codec
joydev                            17377  0 
uvcvideo                       80847  0 
snd_pcm                        97451  2 snd_hda_codec,snd_hda_intel
hid_generic      12540  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi             13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
usbhid                            47074  0 
videobuf2_vmalloc      13056  1 uvcvideo
coretemp                      13355  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
gpio_ich                         13476  0 
videodev                      129260  2 uvcvideo,videobuf2_core
hid                                  101002  2 hid_generic,usbhid
snd_rawmidi                30180  1 snd_seq_midi
drm_kms_helper         49394  1 i915
drm                                   286028  4 i915,drm_kms_helper
snd_seq                            61554  2 snd_seq_midi_event,snd_seq_midi
btusb                                  22474  0 
snd_seq_device           14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211                          14352  2 wl,lib80211_crypt_tkip
snd_timer                        29425  2 snd_pcm,snd_seq
cfg80211                        510937  1 wl
bluetooth                       228667  11 bnep,btusb,rfcomm
i2c_algo_bit                  13413  1 i915
psmouse             95905  0 
snd                                       68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw                        13215  0 
lp                                         17759  0 
soundcore                       12680  1 snd
microcode                        22881  0 
video                                  19390  2 i915,samsung_laptop
lpc_ich                               17061  0 
mac_hid                             13205  0 
parport                             46345  3 lp,ppdev,parport_pc
ahci                                      25731  2 
libahci                                31364  1 ahci
sky2                                     57977  0 



```   And after loging out and in again:


   ```
Module                                 Size  Used by
michael_mic                12612  4 
arc4                                            12615  2 
samsung_laptop                  14532  0 
parport_pc                  28152  0 
ppdev                                          17073  0 
rfcomm                                      42641  0 
bnep                                            18036  2 
binfmt_misc                          17500  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel                       39619  3 
lib80211_crypt_tkip      17379  0 
snd_hda_codec                   136498  2 snd_hda_codec_realtek,snd_hda_intel
wl                                           3074449  0 
i915                                          600349  3 
snd_hwdep                              13602  1 snd_hda_codec
joydev                                      17377  0 
uvcvideo                                  80847  0 
snd_pcm                                  97451  2 snd_hda_codec,snd_hda_intel
hid_generic                          12540  0 
snd_page_alloc                   18710  2 snd_pcm,snd_hda_intel
snd_seq_midi                       13324  0 
snd_seq_midi_event       14899  1 snd_seq_midi
usbhid                                      47074  0 
videobuf2_vmalloc            13056  1 uvcvideo
coretemp                                13355  0 
videobuf2_memops           13202  1 videobuf2_vmalloc
videobuf2_core                    40513  1 uvcvideo
gpio_ich                                  13476  0 
videodev                               129260  2 uvcvideo,videobuf2_core
hid                                            101002  2 hid_generic,usbhid
snd_rawmidi                          30180  1 snd_seq_midi
drm_kms_helper                49394  1 i915
drm                                          286028  4 i915,drm_kms_helper
snd_seq                                   61554  2 snd_seq_midi_event,snd_seq_midi
btusb                                         22474  0 
snd_seq_device                  14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211                                   14352  2 wl,lib80211_crypt_tkip
snd_timer                               29425  2 snd_pcm,snd_seq
cfg80211                                510937  1 wl
bluetooth                              228667  11 bnep,btusb,rfcomm
i2c_algo_bit                          13413  1 i915
psmouse                                   95905  0 
snd                            68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw                               13215  0 
lp                                                 17759  0 
soundcore                               12680  1 snd
microcode                                22881  0 
video                                          19390  2 i915,samsung_laptop
lpc_ich                                      17061  0 
mac_hid                                     13205  0 
parport                        46345  3 lp,ppdev,parport_pc
ahci                                             25731  2 
libahci                                        31364  1 ahci
sky2                                            57977  0 

```
I hope I haven't screwed up the formatting too much- it all went to pot with cut & paste

---

### Post by Toz on 2013-09-08
According to [https://help.ubuntu.com/community/Loadable_Modules]("https://help.ubuntu.com/community/Loadable_Modules"), the name of the blacklist file should be /etc/modprobe.d/blacklist (no .conf). Can you try adding:
```
blacklist samsung_laptop
```
...to that file instead? Remember to reboot afterwards.

---

