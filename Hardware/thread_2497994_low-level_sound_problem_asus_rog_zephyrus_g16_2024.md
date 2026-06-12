---
title: "low-level sound problem: asus rog zephyrus g16 2024 gu605m"
date: 2024-05-25
forum: Hardware
---

### Post by korklal on 2024-05-25
hello guys!! I need help with a problem: asus rog zephyrus g16 2024 gu605m: low-level sound.
Linux user-GU605MI 6.8.8-060808-generic #202404271536 SMP PREEMPT_DYNAMIC Sat Apr 27 15:54:17 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux Ubuntu 24.04
journalctl -b -g CSC3556 --output short-monotonic
[ 2.373898] user-GU605MI kernel: Serial bus multi instantiate pseudo device driver CSC3556:00: Instantiated 2 SPI devices.
[ 2.484345] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[ 2.493213] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Reset GPIO busy, assume shared reset
[ 2.500317] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[ 6122.443562] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: .bin file required but not found
[ 6122.443566] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: PM: dpm_run_callback(): cs35l56_hda_system_resume+0x0/0xd0 [snd_hda_scodec_cs35l56] returns -2
[ 6122.443583] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: PM: failed to resume: error -2
[ 6122.456528] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: .bin file required but not found
[ 6122.456532] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: PM: dpm_run_callback(): cs35l56_hda_system_resume+0x0/0xd0 [snd_hda_scodec_cs35l56] returns -2
[ 6122.456544] user-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: PM: failed to resume: error -2

---

### Post by Yellow Pasque on 2024-05-26
> .bin file required but not found
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062135](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062135)

Installing the firmware package from -proposed (and rebooting) should fix it:
```
cd ~/
wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb
sudo dpkg -i linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb
```

EDIT: Before rebooting, you probably should mute or turn your volume down if you had it cranked because of no amp.

---

### Post by Sever_Alexandru on 2024-05-26
[QUOTE=I need help with a problem: asus rog zephyrus g16 2024 gu605m: low-level sound.
[/QUOTE]

Have the exact same issue with the same laptop and tried the yellow pasque showed but unfortunately did not work

---

### Post by Yellow Pasque on 2024-05-26
> **Sever_Alexandru said:**
> Have the exact same issue with the same laptop and tried the yellow pasque showed but unfortunately did not work

Are you still getting this message?:
```
.bin file required but not found
```

---

### Post by Yellow Pasque on 2024-05-26
Okay, looks like you need kernel 6.9: [https://github.com/tiwai/sound/commit/0672b017324b1444f12d008a3ba8bc0c6c9384fa](https://github.com/tiwai/sound/commit/0672b017324b1444f12d008a3ba8bc0c6c9384fa)
Or maybe you can control the volume in alsamixer even if Master volume doesn't work. I don't know..

---

### Post by Sever_Alexandru on 2024-05-27
> **Yellow Pasque said:**
> Okay, looks like you need kernel 6.9: [https://github.com/tiwai/sound/commit/0672b017324b1444f12d008a3ba8bc0c6c9384fa](https://github.com/tiwai/sound/commit/0672b017324b1444f12d008a3ba8bc0c6c9384fa)


Thank you! can you please tell me how do I install kernel 6.9 from the website you provided?

---

### Post by Yellow Pasque on 2024-05-27
> **Sever_Alexandru said:**
> Thank you! can you please tell me how do I install kernel 6.9 from the website you provided?

The link I gave was just a reference. You do not "install the kernel" from it.  You can get many different newer kernels  in many different ways, such as: [https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa](https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa)

---

### Post by silviun93 on 2024-06-04
Hello! I tried the above with no success. What I did:
* Update to kernel 6.9.3 using mainline
* installed [COLOR=#000000][FONT=&quot]linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb[/FONT][/COLOR]
Output of `journalctl -b -g CSC3556 --output short-monotonic`
```
[   16.426897] user-ROGsdOG-Zephyrus-G16-GU605MI-GU605MI kernel: Serial bus multi instantiate pseudo device driver CSC3556:00: Instantiated 2 SPI devices.
[   17.005413] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[   17.012808] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP system name: '10431C63-spkid0', amp name: 'AMP1'
[   17.015152] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Reset GPIO busy, assume shared reset
[   17.021618] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[   17.029910] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: DSP system name: '10431C63-spkid0', amp name: 'AMP2'
[   18.872572] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: .bin file required but not found
[   18.872580] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: snd_hda_codec_realtek hdaudioC2D0: failed to bind spi0-CSC3556:00-cs35l56-hda.0 (ops cs35l56_hda_comp_ops [snd_hda_scodec_cs35l56]): -2


```

---

### Post by Yellow Pasque on 2024-06-04
It seems like Ubuntu did not upload all the relevant files, but you can  get them from linux-firmware (copy/paste all 4 lines as one command):
```
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp1.bin && /
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp2.bin && /
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid1-amp1.bin && /
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid1-amp2.bin
```

Then: 
```
sudo chown root:root cs35l56*
sudo mv cs35l56* /lib/firmware/cirrus
cd /lib/firmware/cirrus && sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63.wmfw.zst    
sudo update-initramfs -u -k all
```

Reboot and see if it works.

---

### Post by silviun93 on 2024-06-07
I did the above things. Still not working, my output now for journalctl -b -g CSC3556 --output short-monotonic
Kernel: 6.9.3-060903-generic

[   16.364056] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: Serial bus multi instantiate pseudo device driver CSC3556:00: Instantiated 2 SPI devices.
[   17.101324] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[   17.108724] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP system name: '10431C63-spkid0', amp name: 'AMP1'
[   17.111066] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Reset GPIO busy, assume shared reset
[   17.118318] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[   17.126670] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: DSP system name: '10431C63-spkid0', amp name: 'AMP2'
[   18.789861] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Firmware: 1a00d6 vendor: 0x2 v3.4.4, 37 algorithms
[   18.791963] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp1.bin: invalid coefficient magic
[   18.791979] user-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: snd_hda_codec_realtek hdaudioC1D0: failed to bind spi0-CSC3556:00-cs35l56-hda.0 (ops cs35l56_hda_comp_ops [snd_hda_scodec_cs35l56]): -22

LE: the mentioned URLs are pointing to a html, not to the actual binary

---

### Post by silviun93 on 2024-06-07
after changing 'tree' with 'plain' for all the mentioned URLs, and rerun the commands, now  my output of [COLOR=#000000] journalctl -b -g CSC3556 --output short-monotonic[/COLOR]

[   15.846794] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: Serial bus multi instantiate pseudo device driver CSC3556:00: Instantiated 2 SPI devices.
[   16.367337] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[   16.374506] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP system name: '10431C63-spkid0', amp name: 'AMP1'
[   16.376676] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Reset GPIO busy, assume shared reset
[   16.383296] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[   16.392683] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.1: DSP system name: '10431C63-spkid0', amp name: 'AMP2'
[   17.998494] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Firmware: 1a00d6 vendor: 0x2 v3.4.4, 37 algorithms
[   18.000673] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp1.bin: v3.11.16
[   18.000680] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: misc: C:\Users\gchen\Desktop\Asus_proj\CY24\GU605\240426\init\10431C63_240426_V0_A0-init.bin
[   18.000700] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 1.0.3 but expected 1.0.1
[   18.000718] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 3.2.0 but expected 3.1.0
[   18.000726] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 3.2.0 but expected 3.1.0
[   18.000766] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 6.1.1 but expected 13.0.0
[   18.000785] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 6.1.1 but expected 13.0.0
[   18.000790] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 6.1.1 but expected 13.0.0
[   18.000796] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 6.1.1 but expected 13.0.0
[   18.000804] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: No XM for algorithm 9f22f
[   18.000808] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: No YM for algorithm 9f22f
[   18.000815] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 3.11.16 but expected 3.4.4
[   18.000820] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 11.0.7 but expected 11.0.3
[   18.000829] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 4.0.0 but expected 3.0.0
[   18.000834] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 3.1.1 but expected 3.0.1
[   18.000841] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: Algorithm coefficient version 6.0.0 but expected 5.1.0

---

### Post by Yellow Pasque on 2024-06-07
Sorry about the plain/tree mixup.

The only thing i can think of is to try removing the extra firmware patch (the symlink you created)
```
sudo rm /lib/firmware/cirrus/cs35l56-b0-dsp1-misc-10431c63.wmfw.zst
```

---

### Post by silviun93 on 2024-06-08
I deleted and now I can see 1 more extra line the logs
[   17.965954] silviun-ROG-Zephyrus-G16-GU605MI-GU605MI kernel: cs35l56-hda spi0-CSC3556:00-cs35l56-hda.0: DSP1: No XM for algorithm 9f231

What else can I do?

---

### Post by Yellow Pasque on 2024-06-08
I was just guessing at the name of the symlink, but now I see that you should have 2 (one for each speaker ID). Reference: [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/?id=d3a655e22101d79c75cdc0c5b0e9e888de848d07](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/?id=d3a655e22101d79c75cdc0c5b0e9e888de848d07)

So:
```
cd /lib/firmware/cirrus
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63-spkid0.wmfw.zst
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63-spkid1.wmfw.zst
```

If that doesn't work, I would file a bug against linux-firmware on Launchpad.

---

### Post by silviun93 on 2024-06-10
Finally, it works now! Thanks a lot, this was killing me.

---

### Post by silviun93 on 2024-06-10
For the others, I composed a final solution with all the  required steps.

PRE: Kernel should be at least 6.9 (I have 6.9.3). Use mainline for this.


```
wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb
sudo dpkg -i linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb



wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp1.bin 
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp2.bin 
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid1-amp1.bin
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid1-amp2.bin
sudo chown root:root cs35l56*
sudo mv cs35l56* /lib/firmware/cirrus
cd /lib/firmware/cirrus 
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63.wmfw.zst    
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63-spkid0.wmfw.zst
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63-spkid1.wmfw.zst


sudo update-initramfs -u -k all
```


reboot
check with `journalctl -b -g CSC3556 --output short-monotonic`. There should not be any errors.

---

### Post by Yellow Pasque on 2024-06-10
> sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63.wmfw.zst

I don't think you need this one, but I guess it doesn't hurt. I'm glad we figured it out.

---

### Post by korklal on 2024-06-11
:)

---

### Post by korklal on 2024-06-11
> **silviun93 said:**
> For the others, I composed a final solution with all the  required steps.

PRE: Kernel should be at least 6.9 (I have 6.9.3). Use mainline for this.


```
wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb
sudo dpkg -i linux-firmware_20240318.git3b128b60-0ubuntu2.1_amd64.deb



wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp1.bin 
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid0-amp2.bin 
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid1-amp1.bin
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus/cs35l56-b0-dsp1-misc-10431c63-spkid1-amp2.bin
sudo chown root:root cs35l56*
sudo mv cs35l56* /lib/firmware/cirrus
cd /lib/firmware/cirrus 
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63.wmfw.zst    
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63-spkid0.wmfw.zst
sudo ln -s cs35l56/CS35L56_Rev3.11.16.wmfw.zst cs35l56-b0-dsp1-misc-10431c63-spkid1.wmfw.zst


sudo update-initramfs -u -k all
```


reboot
check with `journalctl -b -g CSC3556 --output short-monotonic`. There should not be any errors.

Thanks!!! It work with kernel 6.9.3

---

### Post by zubozrout on 2024-08-12
This is great, thanks a mil @silviun93. With only a few tweaks to that ^, changing to downloading similar files, but "cs35l56-b0-dsp1-misc-10431b13" from: [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/cirrus), sound finally works for me on Ubuntu with Asus ROG Zephyrus G14 GA403UI as well. Such a huge improvement and a game changer after all those months really suffering with the sound, poor speakers having to run at max on half capacity with subwoofers being dead all along.

Unfortunately, HW support is atm better with e.g. Fedora where the sound works for me just fine when testing a live cd (granted, the latest development release, but not even latest development Ubuntu supports that out of the box). I've been initially trying to run the mainline kernels, but to my surprise that didn't resolve my issues as these modules were still missing :(. Interesting the support was backported and I was not seeing any errors on the default kernel with `journalctl`: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062135](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062135), however the sound still didn't work for me.

Anyway, forks flawlessly now - I am not on the default kernel though, but atm I have manually installed Ubuntu's signed 6.10.0-15 Linux kernel from here: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux](http://archive.ubuntu.com/ubuntu/pool/main/l/linux) (and it would likely work with the mainline kernels too)

Thank you again for your help!

```

Serial bus multi instantiate pseudo device driver CSC3556:00: Instantiated 3 I2C devices.
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: DSP system name: '10431B13-spkid0', amp name: 'AMP1'
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: Reset GPIO busy, assume shared reset
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: DSP system name: '10431B13-spkid0', amp name: 'AMP2'
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: DSP1: Firmware version: 3
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: DSP1: cirrus/cs35l56-b0-dsp1-misc-10431b13-spkid0.wmfw: Tue 05 Mar 2024 01:07:08 GMT Standard Time
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: DSP1: Firmware: 1a00d6 vendor: 0x2 v3.11.16, 41 algorithms
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: DSP1: cirrus/cs35l56-b0-dsp1-misc-10431b13-spkid0-amp1.bin: v3.11.16
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: DSP1: misc: C:\Users\gchen\Desktop\Asus_proj\CY24\GA403\240426\init\10431B13_240426_V0_A0-init.bin
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.0: Calibration applied
snd_hda_codec_realtek hdaudioC2D0: bound i2c-CSC3556:00-cs35l56-hda.0 (ops cs35l56_hda_comp_ops [snd_hda_scodec_cs35l56])
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: DSP1: Firmware version: 3
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: DSP1: cirrus/cs35l56-b0-dsp1-misc-10431b13-spkid0.wmfw: Tue 05 Mar 2024 01:07:08 GMT Standard Time
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: DSP1: Firmware: 1a00d6 vendor: 0x2 v3.11.16, 41 algorithms
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: DSP1: cirrus/cs35l56-b0-dsp1-misc-10431b13-spkid0-amp2.bin: v3.11.16
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: DSP1: misc: C:\Users\gchen\Desktop\Asus_proj\CY24\GA403\240426\init\10431B13_240426_V0_A1-init.bin
cs35l56-hda i2c-CSC3556:00-cs35l56-hda.1: Calibration applied
snd_hda_codec_realtek hdaudioC2D0: bound i2c-CSC3556:00-cs35l56-hda.1 (ops cs35l56_hda_comp_ops [snd_hda_scodec_cs35l56])

```

---

