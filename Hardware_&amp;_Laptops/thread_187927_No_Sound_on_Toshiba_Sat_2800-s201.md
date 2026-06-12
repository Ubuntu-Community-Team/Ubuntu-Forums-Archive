---
title: "No Sound on Toshiba Sat 2800-s201"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by Rikostan on 2006-06-03
I did not have sound on this device under breezy and it did not change with the dapper upgrade.

The board is listed as a yamaha DS-XG ymf754 so the ymfpci module should work for it.
 when I do a modprobe snd-ymfpci I do not get any errors and checking alsamixer shows that nothing is muted except for the eicxxx stuff.

When I do a lsmod | grep snd I get the following.

snd_ymfpci             63296  1
gameport               16744  1 snd_ymfpci
snd_ac97_codec         99808  1 snd_ymfpci
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm                96676  2 snd_ymfpci,snd_ac97_codec
snd_opl3_lib           11648  1 snd_ymfpci
snd_timer              26884  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9952  1 snd_opl3_lib
snd_page_alloc         11304  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         8640  1 snd_ymfpci
snd_rawmidi            26848  1 snd_mpu401_uart
snd_seq_device          9228  2 snd_opl3_lib,snd_rawmidi
snd                    60004  11 snd_ymfpci,snd_ac97_codec,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10784  1 snd


When I do a lspci | grep -i audio, I get the following.
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]

I also found aadebug. Here is the output from it.
ALSA Audio Debug v0.1.0 - Sat Jun  3 13:55:01 EDT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux abuntu 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_ymfpci             63296  1
snd_ac97_codec         99808  1 snd_ymfpci
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm                96676  2 snd_ymfpci,snd_ac97_codec
snd_opl3_lib           11648  1 snd_ymfpci
snd_timer              26884  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9952  1 snd_opl3_lib
snd_page_alloc         11304  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         8640  1 snd_ymfpci
snd_rawmidi            26848  1 snd_mpu401_uart
snd_seq_device          9228  2 snd_opl3_lib,snd_rawmidi
snd                    60004  11 snd_ymfpci,snd_ac97_codec,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
alias char-major-116    snd

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [YMF754         ]: YMF754 - Yamaha DS-XG (YMF754)
                     Yamaha DS-XG (YMF754) at 0xefdf0000, irq 11
 27: [0- 3]: digital audio capture
 18: [0- 2]: digital audio playback
 17: [0- 1]: digital audio playback
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
00-00: YMFPCI : YMFPCI : playback 32 : capture 1
00-01: YMFPCI - IEC958 : YMFPCI - IEC958 : playback 1
00-02: YMFPCI - Rear : YMFPCI - Rear PCM : playback 1
00-03: YMFPCI - PCM2 : YMFPCI - Direct Recording : capture 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  pcmC0D2p  pcmC0D3c  timer

CPU -------------------------------------------------------
model name      : Celeron (Coppermine)
cpu MHz         : 646.856

RAM -------------------------------------------------------
MemTotal:       190756 kB
SwapTotal:      562232 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]


Any clues? Please let me know if there is anything else I can post that will help diagnose this issue.

---

### Post by Rikostan on 2006-06-04
Bump from page 2. I'd hate for this one to get buried before that one person who knows how to help me out sees it! :)

---

### Post by Rikostan on 2006-06-05
No ideas on this one?

---

### Post by Rikostan on 2006-06-12
Okay last bump.

I bet this is a case of blacklisting the correct module, but I haven't found any info on what to blacklist.

---

### Post by Rikostan on 2006-06-19
An update. 

I decided to reinstall dapper on this machine. I had made so many changes, I lost track of what I had done.

After a reinstall, I thought I had it whipped.
The drums played as GDM booted up and then I was able to start an MP3. It played about 3 seconds of the song and then stopped.
Afterwards no sound would work again. It doesn't matter what format the file I first play is, it will start the first few seconds and then die.

I can't change the IRQ settings or DMA settings in the bios other than to shut off the parallel  port. Which I have done.

---

