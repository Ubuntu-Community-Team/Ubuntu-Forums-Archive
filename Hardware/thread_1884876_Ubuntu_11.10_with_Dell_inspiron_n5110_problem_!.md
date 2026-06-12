---
title: "Ubuntu 11.10 with Dell inspiron n5110 problem !"
date: 2011-11-22
forum: Hardware
---

### Post by nemosucker on 2011-11-22
Hello guys,

I have a Dell inspiron n5110 laptop i installed a fresh ubuntu 11.10 Os

i have a small problem or it's a big one i dunno xD

my laptop have 2 vga card

[PHP]root@Ubuntu-Inspiron-N5110:/home/nemo# lspci | grep -i VGA 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) [/PHP]

now can any one show me how to suspend or make stop to the other vga "nvidia card" because it's make a lot of heat to my laptop and i don't need it anyway "not loving with games" 

some ppl told me i can put the nvidia drive in blacklist to not boot with it but i dunno how i can make that

"am still new on linux and am very noob as well xD"

so plz help guys !

---

### Post by dandnsmith on 2011-11-22
With that sort of problem, I'd be looking for a BIOS setting to disable the unwanted interface. Are there 2 external VGA ports as well?

You can find the loaded modules using *lsmod*, which also shows dependencies to help sort out what is used by what. I'm not sure what steps you need for blacklisting a module, never having done it, but have used *rmmod* to unload a module (which will have a similar effect, which doesn't survive a reboot).

---

### Post by nemosucker on 2011-11-22
Thanks [dandnsmith]("http://ubuntuforums.org/member.php?u=575770"),

i did searched about some setting in my BIOS to switch off the nvidia card but there no setting for that :(

i tried to put lsmod too and the output is : 

[php]
root@Ubuntu:/home/nemo# lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
rfcomm                 38408  0 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  4 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
ath9k                 112612  0 
mac80211              393459  1 ath9k
nouveau               667307  0 
ttm                    65224  1 nouveau
btusb                  18160  1 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13599  1 ath9k
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
ath9k_hw              293893  2 ath9k,ath9k_common
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505143  3 
drm_kms_helper         32889  2 nouveau,i915
ath                    19387  2 ath9k,ath9k_hw
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
cfg80211              172392  3 ath9k,mac80211,ath
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
bluetooth             148839  13 rfcomm,bnep,btusb
mei                    36466  0 
drm                   196322  6 nouveau,ttm,i915,drm_kms_helper
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
i2c_algo_bit           13199  2 nouveau,i915
video                  18908  2 nouveau,i915
dell_wmi               12601  0 
psmouse                63474  0 
sparse_keymap          13658  1 dell_wmi
serio_raw              12990  0 
mxm_wmi                12859  1 nouveau
wmi                    18744  2 dell_wmi,mxm_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
r8169                  47200  0 
xhci_hcd               77080  0 
[/php]

dunno what's that xD

any way my problem is the heat of my processor is to high

[php]
root@Ubuntu:/home/nemo# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +62.5°C 
[/php]

the normal heat when i use win 7 without any program running or gaming too 48°C, So ubuntu very much hot with my laptop some ppl told me that's cause ur nvidia card is loading and running !!

---

### Post by dandnsmith on 2011-11-22
I can't say I can recognise any of those modules as being for your video/vga output - tho' I can see lots which I can definitely exclude.

I don't know what the performance figures are for your particular processor, but I don't regard 62/63 degress as worryingly high as older ones could go to 70 or 80 degrees.
Another thing - are you sure there isn't a calibration difference between the methods you've used to measure in Win7 and Ubuntu? Does it actually feel a lot hotter for the latter?

---

### Post by nemosucker on 2011-11-22
Am very appreciate your help to me dandnsmith :)

And am really don't wanna to back for the ugly microsoft :(

for ur question about if i feeling hotter with ubuntu ? - yep it's much hotter cause when am in win7 i got 48deg max 52deg and fan stop working and i don't hear it any time just when am gonna to play something like pes 2012 xD

but with ubuntu i hear the fan working with full power and hearing a noise too and when i touch the down of my laptop i feeling hotter heat comes from the inside !

and yes it's maybe a normal deg 63/64 with now but that only okey with some ppl living in could weather like U.K. Or the other euro country's but here in Egypt when it start with 63/64 deg it's not stop it's up to the highest degree's like 80/85 deg so that's a big problem for me and that's why am looking for a solution :(

after 2h googling for my issue i find the model name for nvidia card it's called "nouveau", can you guess what's called fro the result for command lsmod !

or some step's how can i put it in blaclist or just prevent it to boot !

Thanks once again and have a nice day :)

---

### Post by dandnsmith on 2011-11-22
OK, I understand the situation - I remember just how hot it could get in Egypt when I visited some while back (when they swapped police uniforms from summer to winter).

You've found the module - it's in your list *nouveau*, and a number of modules call it.
There's a [forum thread which describes how to do it](http://ubuntuforums.org/showthread.php?t=166624)

Good luck.

---

### Post by nemosucker on 2011-11-23
Thanks Derek i guess i can't find word to thanks u with, and ur welcome any time in egypt :P

look now 

[php]
nemo@Ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.5°C 
[/php]

just comes low for 6/7 deg xD dunno if we actually stop the nvidia drive or there are something else making a high heat for my lap !

result for lsmod command :

[php]
nemo@Ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  4 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
mxm_wmi                12859  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  18160  1 
bluetooth             148839  13 bnep,rfcomm,btusb
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k                 112612  0 
nvidia              10590610  0 
mac80211              393459  1 ath9k
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  2 dell_wmi,mxm_wmi
psmouse                63474  0 
serio_raw              12990  0 
ath9k_common           13599  1 ath9k
ath9k_hw              293893  2 ath9k,ath9k_common
i915                  505143  3 
ath                    19387  2 ath9k,ath9k_hw
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  3 ath9k,mac80211,ath
drm_kms_helper         32889  1 i915
drm                   196322  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
xhci_hcd               77080  0 
r8169                  47200  0 
[/php]

i guess we did stop nouveau to boot up but i will give it 2 more day's or 3 then i will test if the heat comes higher or it will be normal like the old os win7 
thanks once again, nice to meet u :)

---

### Post by dandnsmith on 2011-11-24
I'm happy to hear the links got some sort of result - here's hoping that it contues to work.

---

### Post by shevek. on 2012-01-11
@nemosucker, I have same laptop and used to have same issue with the fan (and battery life). I did some steps to solve it through uninstalling the nvidia driver and other tweaks:
[http://ubuntuforums.org/showpost.php?p=11603104&postcount=28](http://ubuntuforums.org/showpost.php?p=11603104&postcount=28)

HTH

---

### Post by miz0ooo0 on 2012-04-13
i have this laptop and same problem here :D
Egyptian version "aywa ana 3ndy nfs el moshkelaaaaaaaaa :D"

---

