---
title: "Sound card problem in Gigabyte motherboard"
date: 2010-11-08
forum: Hardware
---

### Post by toufiqueimam on 2010-11-08
Hi, I have installed ubuntu 10.10 in my friend's new pc (Gigabyte G41MT-ES2L motherboard with built in sound card). Everything was ok but I could not hear any sound.
Not only ubunuu, I have tried some other linux distros lke mandriva, linux mint, puppy linux etc but no sound.
after installation ubuntu detected it's sound card but i could not listen sound so i have installed alsa. but after installing alsa, no soundcard is detecting.u can see it.[IMG]http://img42.imageshack.us/img42/3453/screenshotcp.jpg[/IMG]

some output,
```
lspci
```>```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
```

```
lspci
```>```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
```

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```>```
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:654: audio open error: No such device
```

```
sudo aplay -l
```>```
aplay: device_list:235: no soundcards found...
```

```
find /lib/modules/`uname -r` | grep snd
```>```
find /lib/modules/`uname -r` | grep snd
```

```
lspci -v | less
```>```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
        Subsystem: Giga-byte Technology Device 5000
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: Giga-byte Technology Device d000
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at fd800000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at ff00 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 12
:
```

I have mailed to gigabyte, they replied > Dear Toufique,
Thank you for your kindly mail and inquiry. As we mentioned on the driver download page of GIGABYTE website, due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website. Since we do not receive proper driver from chipset vender, we cannot guarantee Linux to work on our system. Sorry if there is any inconvenience.
Regards,
GIGABYTE TECHNOLOGY

**Some people told me that this is may not a soundcard problem. Probably I have to change some setting in bios**

---

### Post by toufiqueimam on 2010-11-19
That problem still not solved. Waiting for help. Thank you

---

### Post by toufiqueimam on 2010-11-30
None helping here. Leaving

---

### Post by mastablasta on 2010-11-30
goodbye.
 
how did you install ALSA? did you performa upgrade?:[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
did you do the sudo alsa config command and then select the propper card?
 
Did you check your alsamixer ?
 
solution could also be buy and use one of the cheap SB compatible cards.

---

### Post by toufiqueimam on 2011-06-26
Hi!! that problem solved in new kernel. We can here sound automaticaliy in ubuntu 11.04,linux mint 11, knoppix 6.4

---

### Post by Geek4096 on 2012-01-03
I don't think the problem is solved.  I'm seeing this in 11.10 (i386).  Seems to cause apps to hang (darken) then wake up minutes later.

Is anyone else having this problem?

Thanks

---

