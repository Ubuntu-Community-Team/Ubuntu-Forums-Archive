---
title: "Toshiba Satellite C55-A5300: I actually (!) need the Fn key to be locked, how to?"
date: 2014-08-21
forum: Hardware
---

### Post by yaroslav-mudryy on 2014-08-21
Hello everybody,

My fiancee has a Toshiba Satellite C55-A5300 laptop and I am trying to switch her to Linux/Ubuntu. Everything works perfectly except only one thing. She has really gotten used to function keys (F1-F12) acting as HotKeys/Multimedia keys, i.e. she doesn't have to hold Fn key to change brightness, volume, etc (don't ask me why, lol, she just really likes it that way).

So I googled for days. I have found many posts where people are trying to achieve the opposite (F1-F12 act in a standard way, HotKeys require Fn to be pressed) and nobody seems to ever want F1-F12 keys acting as the HotKeys by default (including me, I hate it).

Details and what I've tried:
1) I'm installing Ubuntu 14.04 for her.
2) BIOS has an option for this specific feature ("Standard" and "Special Keys" modes), but changing it in the BIOS doesn't make Ubuntu act any different. With either option F1-F12 keys in Ubuntu act as normal F1-F12 keys.
3) I even re-installed windows on it one time by now to check if it does the same there. In windows the BIOS setting for the HotKeys is applied properly, i.e. setting it to "Special Keys" make pressing F10 increase volume without Fn, etc.
4) I tried updating the BIOS (in fact forced the same version update via bootable CD).
5) Tried resetting BIOS settings to default from the BIOS itself, no change in behavior.
6) Tried resetting BIOS settings to default from windows with a special Toshiba HWSettings utility, no luck.

So it seems to me that somehow Ubuntu ignores the setting in the BIOS and makes F1-F12 keys act as standard at all times. Maybe BIOS option doesn't change the keys behavior on the hardware  level, but just provides an option for the OS to read and act upon  accordingly? Is this possible? If so, can I change/reverse HotKeys behavior from Ubuntu on software level? Any help is highly appreciated, I'd really like to make one more person a Linux convert.

---

### Post by varunendra on 2014-08-25
Not much hopeful with a Lenovo (not that it is guaranteed to work on other brads either, but Lenovo's are particularly stubborn), but have you tried various acpi related boot options? In particular - "acpi=force", or acpi_osi="Linux".

A list of common (there are many more) boot options : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

The above page also includes instructions/links to show how to use these options in temporary mode or on an installed system.

Some extra info : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I may not be able to offer any better help on this, but posting the output of -
```
lsmod
```
..may give us clues to try something extra (like removing the 'wmi' related drivers or loading them with some parameters if available).

---

### Post by yaroslav-mudryy on 2014-08-27
Hello Varun and thank you for your kind help. I finally got a hold of my fiancee's laptop and tried adding acpi boot options (acpi=force and acpi="Linux", both at the same time and one-by-one), but that unfortunately didn't work.

So, here is the output of lsmod, maybe that will shed some light:

```
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
ip6t_REJECT            12939  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18894  8 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17717  10 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
xt_limit               12711  13 
xt_tcpudp              12884  18 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  16 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 21841  1 nf_nat_ftp
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           96976  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
rts5139               335409  0 
arc4                   12608  2 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
rtl8188ee              89580  0 
rtlwifi                77814  1 rtl8188ee
crct10dif_pclmul       14289  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
mac80211              630653  2 rtlwifi,rtl8188ee
joydev                 17381  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13462  0 
lpc_ich                21080  0 
cfg80211              484040  2 mac80211,rtlwifi
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
i915                  783805  3 
lp                     17759  0 
video                  19476  1 i915
parport                42348  3 lp,ppdev,parport_pc
mei_me                 18627  0 
drm_kms_helper         53081  1 i915
mei                    82276  1 mei_me
drm                   303102  4 i915,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106678  0 
ahci                   25819  3 
alx                    32452  0 
mdio                   13807  1 alx
libahci                32560  1 ahci


```

---

### Post by varunendra on 2014-08-27
No known culprits or 'wmi' drivers in lsmod, so no help there.

Please try the command -
```
acpi_listen
```
..in the terminal, then press F1 through F12 keys with/without Fn keys, and let us know which ones you see generating some characters in the terminal.

I have no personal experience with above 'acpi_listen' trick, so not sure how we can take advantage of this. But if we could get a full table of keys/combos with the respective signals they generate, we can probably map them reversibly so that their behaviour with/without Fn key is reversed.

If a key/combo doesn't produce any characters in the terminal when running 'acpi_listen', probably "key codes" generated by those keys can be used (they can be monitored by "xev" command instead of "acpi_listen").

However, the above two methods (acpi_listen and xev) are just to know what signals they send to the system. I am not familiar with how to map them to reverse the behaviour. You may have to search yourself on how key mapping is done in Ubuntu, or maybe someone familiar with key - mapping can join us to save us some time.

Sorry if I'm confusing you, consider these just pointers to the direction you may have to work in.

---

### Post by yaroslav-mudryy on 2014-08-27
I just ran acpi_listen and tried to press those keys with and without the Fn. Don't know if you wanted me to do it for all F-keys, but for example F10 produces:

```
^[[21~
``` without Fn, and
```
button/volumeup VOLUP 00000080 00000000 K
``` with the Fn key. The other ones have similar characters with/without Fn.

---

### Post by varunendra on 2014-08-28
If all the function keys, both with and without the Fn key combo, produce outputs, then I think you are close. I just don't yet know how to map the signals as we desire, but I do know that there are ways, and even wiki pages on how to do that.

My routine today is going to be a bit busy, so just search the net and I'm sure you'll find how to do key-mapping in Ubuntu.

---

### Post by yaroslav-mudryy on 2014-08-28
Thanks again, Varun! This sounds like a good plan. I've found some guides on how to re-map the keys. One of them says it's as simple as making a config file in ~/.xmodmap, which I will try later today or tomorrow when I'll get my hands again on her laptop and post back about the results.

---

### Post by yaroslav-mudryy on 2014-09-02
I finally got my hands again on the laptop and the original goal is pretty much reached. I was unable to swap all the multimedia keys with F-keys, but majority of them are now working without the Fn keys. I found that modern Ubuntu uses xkb driver to handle the input and so I had to modify /usr/share/x11/xkb/keycodes/evdev to re-map the keys. Some of the keys are impossible to remap (like brightness and wifi on/off) because they don't produce the key code (as checked with 'xev'). The most important were the volume keys and they now work without Fn keys, which makes my fiancee a happy Ubuntu user now. Varun, thank you once more for all your kind help!

---

### Post by varunendra on 2014-09-02
Thanks happily accepted... which by the way could actually be for giving you company rather than 'help' :p

I still don't understand the way some of the Fn+ key combos work, like the brightness control or wifi you mentioned. They behave as if they have nothing to do with the OS and they are talking directly to the hardware. Although we know that can't be true, at least not completely.

I wish I knew which parts of the OS interact/control the actions of these keys/combos, but so far I have absolutely no clues. So can't offer anything except pointless comments like above :-\"

---

### Post by yaroslav-mudryy on 2014-09-02
Yeah, I am now completely confused too about how the keys actually work because of those brightness and wifi on/off. It really does seem like they talk to hardware directly, unlike volume keys. But then again, why don't they obey the setting in the BIOS? Weird. I'm thinking maybe there's still some other way of making the keys (all at once) obey the BIOS setting, maybe it's something in grub or some of those ACPI kernel options you mentioned. For now remapping the volume and play/pause keys suffices, but out of curiosity I will still tinker more with this once I actually marry this girl and will have this laptop at home every day, hehe.

---

### Post by varunendra on 2014-09-03
> **yaroslav-mudryy said:**
> ....but out of curiosity I will still tinker more with this once I actually marry this girl and will have this laptop at home every day, hehe.

Such a noble cause for marrying the girl !! You just filled my eyes with tears of joy and pride....!!

I wish you all the best on behalf of the whole community of tinkerers. May God be with you on the quest, and help you marry the la... *[COLOR="#808080"]<oops>[/COLOR]* .. the Girl as soon as possible!

Amen! [-o<

---

