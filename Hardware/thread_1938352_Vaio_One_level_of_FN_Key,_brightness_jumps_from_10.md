---
title: "Vaio: One level of FN Key, brightness jumps from 100% to 20%"
date: 2012-03-09
forum: Hardware
---

### Post by articrain on 2012-03-09
Hello everyone! I'm new to the forums but I've been using Ubuntu for a few months now and I'm very happy with everything so far with the exception of this niggling problem.

My laptop is a Vaio F Series, the official product name is "VPCF14AHJ," with an Nvidia 310M video card. It's actually a Japanese model but a lot of troubleshooting that I've done with has followed advice of Vaio F11/F12 people so I am guessing they are very similar (the hardware specifications are at least, as far as I can tell).

The problem I have is that my FN keys for the brightness (and also for the slider in Power Management or any other place) makes my brightness jump extremely sharply. The computer will boot at full, blinding 100% brightness and when I try to turn it down with just one click of FN+F5 it jumps to around 5% (an approximate), with a very slight flicker that eventually stabilizes. If I try to go down further, it would appear that the brightness does decrease but by extremely minimal amounts (something like 0.5%) until the brightness bar below the clock is halfway through, by which the brightness just doesn't decrease. I compared this state with my Windows installation (in which the brightness works perfectly) and the halfway mark of my brightness slider in Ubuntu is effectively the lowest brightness setting in Windows.

Some information that may be needed:

I've actually been scouring the web for a few months now on a solution and I finally thought it was time to register on the forums and make a post! It was rather challenging for me to find the words to search for this issue on Google, but after reading many things here are some points that might be useful about my system:

[LIST=1]
[*]After installing Ubuntu (I'm running 11.04) and installing the closed-sourced drivers through the "Additional Drivers" section,so I didn't really do anything fancy like downloading the drivers off Nvidia and installing them. This didn't make a difference anyway as I tried to see if it would change things on a previous Ubuntu install but I ended up messing around with too many files and having to reinstall. After installing, I added "Option "RegistryDwords" "EnableBrightnessControl=1" as suggested by many in the forums to enable the FN keys/Brightness Control (if I didn't do this the brightness remains fixed at 100% no matter what I do).

[*]Here is a copy of my lsmod:
> 
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40283  1 
cryptd                 20510  0 
aes_x86_64             17208  2 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53610  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
dm_crypt               22993  0 
snd_hda_codec_hdmi     28167  4 
nvidia              10709116  44 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
arc4                   12529  2 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 118238  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
mac80211              294370  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
sony_laptop            39880  0 
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
psmouse                73535  0 
cfg80211              178528  3 ath9k,mac80211,ath
coretemp               13490  0 
btusb                  18600  2 
i7core_edac            27903  0 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
edac_core              53845  3 i7core_edac
lp                     17825  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46458  3 parport_pc,ppdev,lp
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550457  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
sky2                   58509  0 
sdhci_pci              13989  0 
xhci_hcd               77643  0 
firewire_ohci          40370  0 
ahci                   25951  12 
libahci                26642  1 ahci
firewire_core          62646  1 firewire_ohci
sdhci                  27387  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
video                  19438  0 
ramzswap               13408  0 
xvmalloc               13767  1 ramzswap


[*]Finally, the brightness changing does work normally while running nouveau. The reason I am wanting to use the nvidia drivers instead however is that nouveau runs my laptop up to a rather unbearable temperature over long periods of use even with an external cooler, probably due to the lack of power management support. So far, the nvidia driver doesn't appear to give me this problem.

[*]While I doubt this will be a Unity related matter, I almost never use Unity and exclusively log in into Gnome Classic.
[/LIST]

My sincerest apologies for the lengthy post, I'm often accused of verbosity in all forms of writing.

Thanks in advance!

---

### Post by articrain on 2012-03-12
Bump!

---

### Post by Basher101 on 2012-03-12
i could give you more detailed help, but i just got some free classes and have to go in 5 minutes to the other ones...i will be back in 2 hours or so...

anyways, try setting your brightness with a command > sudo setpci -s 00:02.0 F4.B=[HEX]

where [HEX] is you must type a hex number, you can lookup the values here [http://www.the-eggman.com/seminars/dec_hex.html](http://www.the-eggman.com/seminars/dec_hex.html)

note: the command works for my onboard graphics (intel 4 Mobile chipset family), but i am not sure if it will work on a nvidia card (it may have other values than 00:02.0 )

---

### Post by articrain on 2012-03-14
> **Basher101 said:**
> i could give you more detailed help, but i just got some free classes and have to go in 5 minutes to the other ones...i will be back in 2 hours or so...

anyways, try setting your brightness with a command 

where [HEX] is you must type a hex number, you can lookup the values here [http://www.the-eggman.com/seminars/dec_hex.html](http://www.the-eggman.com/seminars/dec_hex.html)

note: the command works for my onboard graphics (intel 4 Mobile chipset family), but i am not sure if it will work on a nvidia card (it may have other values than 00:02.0 )

Thanks for the suggestion! Unfortunately, I tried it out and none of the values seem to be doing anything for me.

I did a bit of searching and ran lspci in terminal to find out the serial number for my card which was:

> 
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)


But unfortunately, using that number didn't do much for me either. You mentioned however that you are running on your Intel graphics chip - is there a way that I might switch to that and see whether the heat is manageable? I don't really do a lot of heavy graphic stuff on Ubuntu anyway so I don't think I will miss the capabilities of the nvidia card.

Thanks again.

---

### Post by articrain on 2012-03-22
Bump!

---

