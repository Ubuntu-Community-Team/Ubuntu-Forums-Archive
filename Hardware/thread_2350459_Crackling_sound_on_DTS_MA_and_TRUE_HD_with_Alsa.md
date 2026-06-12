---
title: "Crackling sound on DTS MA and TRUE HD with Alsa"
date: 2017-01-24
forum: Hardware
---

### Post by torrero007 on 2017-01-24
Hi, I recently got the pc above to use it as HTPC. 
[FONT=verdana]
Mobo:      ASROCK AM1B-ITX RETAIL
[/FONT][FONT=verdana]CPU: AMD Athlon 5350 AM1/2.05 GHz/2 MB
[/FONT]GPU: AMD R3 Series (integrated) - HD 8400 (integrated)

I experience crackling sound when I play DTS MA and TRUE HD. I though my problem was the AMD drivers, thus I installed Ubuntu 14.04.01 (this version supports the AMD drivers). But even with the correct drivers I still have crackling sound on DTS MA and TRUE HD.

In Alsamixer I see "HD Audio Generic" but with no bars to adjust the volumes., only two boxes with S/PDIF and S/PDF1. I have tried to play with Kodi settings but nothing worked. Does anyone has an idea why is this happening?

---

### Post by FrenchyFungus on 2017-01-24
Does this happen with headphones only/as well?

---

### Post by torrero007 on 2017-01-24
It does happen with headphones as well. My amplifier is Yamaha RXV565.

---

### Post by FrenchyFungus on 2017-01-24
Ah, I was going to suggest checking for dust in the headphone socket - this was causing me to have similar problems recently.

---

### Post by torrero007 on 2017-01-25
I won't worry about the haedphones. My problem is mainly to the speakers. I don't have any problem when running Win10. It must be a problem with drivers. Can anyone suggest something? 

Update: It doesn't happen with Openelec/Libreelec. They are both working perfectly.

---

### Post by mastablasta on 2017-01-25
what si the actual audio chip? does it give out any error messages regarding audipon in dmesg (type dmesg in temrinal or open log viewer and see it there)

i have Audio issues on one of Asrock motherboards as well and with chip supposedly supported under Linux. not sure what they are doing.

---

### Post by torrero007 on 2017-01-25
> **mastablasta said:**
> what si the actual audio chip? does it give out any error messages regarding audipon in dmesg (type dmesg in temrinal or open log viewer and see it there)

i have Audio issues on one of Asrock motherboards as well and with chip supposedly supported under Linux. not sure what they are doing.

I run dmesg and atteched the result (I broke it down in 3 files because it exceeded the limit). I don't see any errors. What do you think?


p.s. I installed again Openelec (Kodi+Alsa) and works perfect.

---

### Post by mastablasta on 2017-01-26
so what is actually the audio chip? Intel or realtek? it look slike for some reason the chip is not being recognised. hard to sday why not.

```
[   12.431786] hda-intel 0000:00:01.1: Using LPIB position fix
[   12.431846] snd_hda_intel 0000:00:01.1: irq 85 for MSI/MSI-X
[   12.441548] hda-intel 0000:00:01.1: Enable sync_write for stable communication
[   12.492462] input: HD-Audio Generic HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.1/sound/card0/input6
[   12.496674] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input5
[   12.497122] hda-intel 0000:00:14.2: Using LPIB position fix
[   12.502301] kvm: Nested Virtualization enabled
[   12.502304] kvm: Nested Paging enabled
[   12.502908] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   12.536202] SKU: Nid=0x1d sku_cfg=0x40a4c601
[   12.536208] SKU: port_connectivity=0x1
[   12.536210] SKU: enable_pcbeep=0x0
[   12.536213] SKU: check_sum=0x00000004
[   12.536214] SKU: customization=0x000000c6
[   12.536216] SKU: external_amp=0x0
[   12.536218] SKU: platform_type=0x0
[   12.536220] SKU: swap=0x0
[   12.536221] SKU: override=0x1
[   12.537258] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   12.537264]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.537271]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.537273]    mono: mono_out=0x0
[   12.537274]    inputs:
[   12.537277]      Front Mic=0x19
[   12.537280]      Rear Mic=0x18
[   12.537282]      Line=0x1a
[   12.537285] realtek: No valid SSID, checking pincfg 0x40a4c601 for NID 0x1d
[   12.537287] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0662
[   12.555696] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   12.556339] input: HD-Audio Generic Line Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   12.557385] input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[   12.559349] input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   12.559561] input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
```

---

### Post by torrero007 on 2017-01-26
The audio chip is Realtek. I am know it from the windows drivers. I will try a different OS, maybe linux mint and see if I have any success.

---

### Post by mastablasta on 2017-01-26
go for Mint, sure.

also if it works in openelec check the kernel version there, then check the chip it recognises (you can do it in terminal).

kernel version:
```

uname -a
```


chip will likely be here:
```
lshw -sanitize
```

-sanitize parameter will clean sensitive info from the list

or here if it's a PCI device or recognised as such:
```
lspci -v
```

-v parameter will add additional info


i think openelec is debian based, so it is a bit strange it would all work there but not ubunut. maybe a minor error or paramter is set wrong in one of the config files.

---

### Post by torrero007 on 2017-01-28
> **mastablasta said:**
> go for Mint, sure.

also if it works in openelec check the kernel version there, then check the chip it recognises (you can do it in terminal).

kernel version:
```

uname -a
```


chip will likely be here:
```
lshw -sanitize
```

-sanitize parameter will clean sensitive info from the list

or here if it's a PCI device or recognised as such:
```
lspci -v
```

-v parameter will add additional info


i think openelec is debian based, so it is a bit strange it would all work there but not ubunut. maybe a minor error or paramter is set wrong in one of the config files.

I send you a pm

---

### Post by torrero007 on 2017-01-30
I also tried Linux Mint and I have the same problem. Does anyone has any idea why is this happening?

---

### Post by slickymaster on 2017-01-30
*Thread moved to **Hardware**.*

---

### Post by mastablasta on 2017-01-30
> **torrero007 said:**
> I also tried Linux Mint and I have the same problem. Does anyone has any idea why is this happening?

not really on the forums during weekend... i Will have a look at the files maybe later today.

you should be able to post them here usign the code tags (the # icon). they are not that big.

if lshw is not installed it can be easilly installed. it's a neat & small tool.

as to why it is happening - i am not an audio hardware expert, but it sounds a bit as if wrong drivers are selected and loaded for the chip. it happens on my strange Asrock motherboard and until now i haven't found out what is triggering this. in my case all works well on live boot, but it doesn't always work as it should on normal boot. and often it can't reset it via software, but i need to take out the power from the PC completelly.

in essence think of kernel as one big blob with all drivers in it. when you boot it checks for hardaware and then it load drivers for whatever it autofinds. now sometimes it's scan is flawed or chips are strange or mirepresented to the OS. in that case it mgith happen that a wrong or slightly wrong driver is loaded. sometimes this can be resolved by identifying the wrongly loaded driver and then saying to system "do not load this driver". so next time it boots it Will see this and try to find the next best thing which could be the correct driver. at least that's how i understand it. then again maybe i am wrong... :)

---

### Post by torrero007 on 2017-02-02
> **mastablasta said:**
> not really on the forums during weekend... i Will have a look at the files maybe later today.

you should be able to post them here usign the code tags (the # icon). they are not that big.

if lshw is not installed it can be easilly installed. it's a neat & small tool.

as to why it is happening - i am not an audio hardware expert, but it sounds a bit as if wrong drivers are selected and loaded for the chip. it happens on my strange Asrock motherboard and until now i haven't found out what is triggering this. in my case all works well on live boot, but it doesn't always work as it should on normal boot. and often it can't reset it via software, but i need to take out the power from the PC completelly.

in essence think of kernel as one big blob with all drivers in it. when you boot it checks for hardaware and then it load drivers for whatever it autofinds. now sometimes it's scan is flawed or chips are strange or mirepresented to the OS. in that case it mgith happen that a wrong or slightly wrong driver is loaded. sometimes this can be resolved by identifying the wrongly loaded driver and then saying to system "do not load this driver". so next time it boots it Will see this and try to find the next best thing which could be the correct driver. at least that's how i understand it. then again maybe i am wrong... :)

I am still trying to troubleshoot it but with no luck. Mastablasta, on alsamixer I can't see any bars for volume up/down (like I see on HDMI Generic). Only SpDif [00] and SpDif1[00]. Is that normal?

---

