---
title: "Realtek ALC5672 not working on Dell Venue 10 Pro tablet"
date: 2020-06-23
forum: Hardware
---

### Post by krzysiek-jakobczyk on 2020-06-23
Dear Community,

I've recently switched from Windows 10 i386 to Xubuntu 20.04 LTS amd64  on my Dell Venue 10 Pro 5055 tablet. The device has 32-bit EFI so it was  a bit of a struggle to install 64-bit OS, but I've finally managed to  do it.

Everything is working fine except for the sound. The tablet has  Realtek ALC5672 sound card, but it's recognized in the OS as a 'dummy  output'. As far as my investigation lead me it's the problem of Alsa  that is not correctly recognizing the hardware during boot [1].

In the `dmesg` output I've found following issues related to the sound card (`dmesg | grep rt5`):

 ```
[   19.330695] rt5640 i2c-10EC5640:00: Device with ID register 0x6271 is not rt5640/39
[   19.357253] rt5645 i2c-10EC5640:00: i2c-10EC5640:00 supply avdd not found, using dummy regulator
[   19.357305] rt5645 i2c-10EC5640:00: i2c-10EC5640:00 supply cpvdd not found, using dummy regulator
[   19.789627] rt5645 i2c-10EC5640:00: Device with ID register 0x6271 is not rt5645 or rt5650
[   19.835085] rt5651 i2c-10EC5640:00: Device with ID register 0x6271 is not rt5651
[   21.287753] bytcr_rt5640 bytcr_rt5640: quirk IN3_MAP enabled
[   21.287759] bytcr_rt5640 bytcr_rt5640: quirk realtek,jack-detect-source 2
[   21.287762] bytcr_rt5640 bytcr_rt5640: quirk realtek,over-current-threshold-microamp 2000
[   21.287765] bytcr_rt5640 bytcr_rt5640: quirk realtek,over-current-scale-factor 1
[   21.287768] bytcr_rt5640 bytcr_rt5640: quirk DIFF_MIC enabled
[   21.287771] bytcr_rt5640 bytcr_rt5640: quirk SSP0_AIF2 enabled
[   21.287774] bytcr_rt5640 bytcr_rt5640: quirk MCLK_EN enabled
[   21.287803] bytcr_rt5640 bytcr_rt5640: ASoC: CODEC DAI rt5640-aif2 not registered
[   21.287811] bytcr_rt5640 bytcr_rt5640: devm_snd_soc_register_card failed -517
``` 

It seems that the Realtek ALC5672 is not being correctly recognized by Xubuntu and that the problem isn't new. I've found similar problem here in the Ubuntu Forums [3], but the OP didn't finish the topic and I decided to do it after many years. As @[**[COLOR=#0078C0][B]claydoh**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=12640") suggested in the last message in the above thread ([3]) it seems that I'm running on Atom/Baytrail SoC which has everything integrated.

I've already tried few tips found in the Internet [2], but nothing  helped me so far thus I decided to search for help here. My question is:  how to make Realtek ALC5672 sound card working under Xubuntu 20.04 with  kernel 5.4.0-29.generic.

Would you please help me to get my sound working?

[1] [https://bugzilla.kernel.org/show_bug.cgi?id=96691](https://bugzilla.kernel.org/show_bug.cgi?id=96691)
[2] [https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html)
[3] [https://ubuntuforums.org/showthread.php?t=2378142&page=2](https://ubuntuforums.org/showthread.php?t=2378142&page=2)

---

