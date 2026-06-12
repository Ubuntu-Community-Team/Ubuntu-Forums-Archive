---
title: "No sound via speakers on Zenbook UP6502ZD - the old cirrus amplifier classic issue"
date: 2023-12-03
forum: Hardware
---

### Post by staropram on 2023-12-03
Hello fellow computer enthusiasts,

I recently purchased a used Zenbook flip 15.6 OLED (UP6502ZD) with a 12th gen intel CPU. Naturally the first thing I did was install Ubuntu (in this case Lubuntu 23.10 as I've got minimalist OCD).

To my surprise (shame on you Asus) the laptop speakers do not work out-of-the-box so to speak. Why is this?

Well, for some inexplicable reason Asus decided to omit the `_DSD` (Device Specific Data) section from the ACPI table entry in the BIOS for the Cirrus Logic CSC3551 ADC. Without this `_DSD` section it cannot manage the two CS35L41 amplifiers which drive the speakers and hence there is no sound output from the speakers. 

I'm sure it is complete coincidence, and nothing to do any kind of vendor obfuscation or colluding between Asus, Cirrus, and Microsoft that the Windows drivers hardcode the `_DSD` parameters. Asus doesn't appear to be in the mood to update the BIOS on the myriad devices this problem effects either.

People experiencing this issue will usually have correctly working headphone, HDMI, and microphone interfaces as it is just the speaker driver initialisation that is broken.

The Linux community is very aware of this Asus speaker issue as are the Kernel developers. There is currently an almost [daily submission of patches]([https://lore.kernel.org/lkml/?q=Asus+cs35l41](https://lore.kernel.org/lkml/?q=Asus+cs35l41)) on the kernel mailing list mentioning Asus, speakers and the CS35L41's. Support for many Asus laptops is being incrementally added.

Unfortunately the UP6502ZD is not one which has yet received attention so I am attempting to get it working myself by patching the kernel and adding `_DSD` section to the ACPI table.

I've been following [this tutorial]([https://asus-linux.org/wiki/cirrus-amps/](https://asus-linux.org/wiki/cirrus-amps/)). The old method was to dump the ACPI tables, find the CSC3551 section and then use information there to construct a custom `_DSD` section which is then loaded at boot time to override the tables before the kernel is loaded.

The new method (since the patches have become available) is to patch the kernel which provides the `_DSD` information directly to the cs35l41 structure.

I patched 6.6.3 as that was the stable until today but that's immaterial here. The function added to ` cs35l41_hda_property.c
` in the patch shown [here]([https://asus-linux.org/wiki/cirrus-amps/](https://asus-linux.org/wiki/cirrus-amps/)) is called `asus_rog_2023_spkr_id2` and manually populates the `_DSD` info:


```
/*
 * The CSC3551 is used in almost the entire ASUS ROG laptop range in 2023, this is likely to
 * also include many non ROG labelled laptops. It is also used with either I2C connection or
 * SPI connection. The SPI connected versions may be missing a chip select GPIO and require
 * an DSD table patch.
 */
static int asus_rog_2023_spkr_id2(struct cs35l41_hda *cs35l41, struct device *physdev, int id,
            const char *hid)
{
   struct cs35l41_hw_cfg *hw_cfg = &cs35l41->hw_cfg;

   /* check SPI or I2C address to assign the index */
   cs35l41->index = (id == 0 || id == 0x40) ? 0 : 1;
   cs35l41->channel_index = 0;
   cs35l41->speaker_id = cs35l41_get_speaker_id(physdev, 0, 0, 2);
   hw_cfg->spk_pos = cs35l41->index;
   hw_cfg->bst_type = CS35L41_EXT_BOOST;
   hw_cfg->gpio1.func = CS35l41_VSPK_SWITCH;
   hw_cfg->gpio1.valid = true;
   hw_cfg->gpio2.func = CS35L41_INTERRUPT;
   hw_cfg->gpio2.valid = true;


   if (strcmp(cs35l41->acpi_subsystem_id, "10431473") == 0
      || strcmp(cs35l41->acpi_subsystem_id, "10431483") == 0
      || strcmp(cs35l41->acpi_subsystem_id, "10431493") == 0
      || strcmp(cs35l41->acpi_subsystem_id, "10431DA2") == 0) {
      cs35l41->reset_gpio = gpiod_get_index(physdev, NULL, 1, GPIOD_OUT_HIGH);
   } else {
      cs35l41->reset_gpio = gpiod_get_index(physdev, NULL, 0, GPIOD_OUT_HIGH);
   }

   hw_cfg->valid = true;

   return 0;
}
```


The subsystem ID `10431DA2` corresponds to the UP6502ZD (I've added this in). Note the `asus_rog_2023_spkr_id2` function is called from this table which contains various Asus models:


```
static const struct cs35l41_prop_model cs35l41_prop_model_table[] = {
   { "CLSA0100", NULL, lenovo_legion_no_acpi },
   { "CLSA0101", NULL, lenovo_legion_no_acpi },
   { "CSC3551", "103C89C6", hp_vision_acpi_fix },
...
   { "CSC3551", "10431493", asus_rog_2023_spkr_id2 }, // ASUS GV601V - spi, reset gpio 1
   { "CSC3551", "10431573", asus_rog_2023_spkr_id2 }, // ASUS GZ301V - spi, reset gpio 0
...
   { "CSC3551", "10431DA2", asus_rog_2023_spkr_id2 }, // ASUS UP6502ZD - spi, reset gpio 0
   {}
};
```


What you can see from `asus_rog_2023_spkr_id2` that `cs35l41->reset_gpio` is hardcoded depending on the subsystem ID. It isn't clear how the author figured out which pin to choose for each model. Perhaps they have some additional information or access to the spec sheet.

In anycase I tried both 0 and 1 and discovered that 1 got me further along than 0 from the boot output.

This is my current output from `dmesg | grep CSC` :


```
$ sudo dmesg | grep CSC
[   11.706278] Serial bus multi instantiate pseudo device driver CSC3551:00: Instantiated 2 SPI devices.
[   12.412121] cs35l41-hda spi0-CSC3551:00-cs35l41-hda.0: Using extra _DSD properties, bypassing _DSD in ACPI
[   12.461060] cs35l41-hda spi0-CSC3551:00-cs35l41-hda.0: Cirrus Logic CS35L41 (35a40), Revision: B2
[   12.484874] cs35l41-hda spi0-CSC3551:00-cs35l41-hda.1: Using extra _DSD properties, bypassing _DSD in ACPI
[   12.484901] cs35l41-hda spi0-CSC3551:00-cs35l41-hda.1: Reset line busy, assuming shared reset
[   12.587890] cs35l41-hda spi0-CSC3551:00-cs35l41-hda.1: Failed waiting for OTP_BOOT_DONE: -110
[   12.599850] cs35l41-hda: probe of spi0-CSC3551:00-cs35l41-hda.1 failed with error -110

```

As you can see it would appear that the first amplifier is initialised, but not the second. But this might be a red-herring, perhaps both are initialised and the `OTP_BOOT_DONE` error is related something else.

In addition to the kernel patch I have an ACPI overwrite for the chip select pin:


```
DefinitionBlock ("", "SSDT", 1, "CUSTOM", "CSC3551", 0x00000001)
{
    External (_SB_.PC00.SPI1, DeviceObj)
    External (_SB_.PC00.SPI1.SPK1, DeviceObj)

   Scope (_SB.PC00.SPI1)
    {
        Name (_DSD, Package ()
        {
            ToUUID ("daffd814-6eba-4d8c-8a91-bc9bbf4aa301"),
            Package ()
            {
                Package () { "cs-gpios", Package () {
                    Zero,                    // Native CS
                    SPK1, Zero, Zero, Zero   // GPIO CS
                } }
            }
        })
    }
}

```

Note that `SPI1` and `SPK1` correctly match the `acpidump` parameters of my system.

What I do not understand is how these `cs-gpios` properties are supposed to be set: whether this is something that can be obtained from the system itself or if these are magic numbers from the spec sheet and HW configuration of the motherboard.

So I'm not really sure where to go next with this, other than trying random settings for the "cs-gpios" pins or further reading the kernel source code. Any help would be appreciated.

Cheers

Ashley

---

### Post by slonk on 2023-12-07
I might have the same problem on a LG Gram 15", also with a i7-1260p.

All sound chip detection works as expected, but no sound from the speakers no matter what I do in the mixer.

However, contrary to your situation my headphone out also doesn't work.

How can I tell if I have the same problem? My `dmesg` doesn't mention CSC or DSD.

---

### Post by staropram on 2023-12-09
Just to answer my own question, I got mine working, see answer here: [https://askubuntu.com/questions/1495037/no-sound-via-speakers-on-zenbook-up6502zd-the-old-cirrus-amplifier-classic-iss](https://askubuntu.com/questions/1495037/no-sound-via-speakers-on-zenbook-up6502zd-the-old-cirrus-amplifier-classic-iss)

---

### Post by staropram on 2023-12-09
It might be worth opening a new issue for this so it doesn't get confusing.

What does it say with `inxi -SMA` also what does `dmesg | grep ALC` show?

If I were to guess I would say that you need to add a quirk in `patch_realtek.c` and there might already be one, but we would need to search using the model string that `inxi -M` outputs.

---

### Post by slonk on 2023-12-09
> **staropram said:**
> It might be worth opening a new issue for this so it doesn't get confusing.

What does it say with `inxi -SMA` also what does `dmesg | grep ALC` show?

If I were to guess I would say that you need to add a quirk in `patch_realtek.c` and there might already be one, but we would need to search using the model string that `inxi -M` outputs.

```

% inxi -SMA
System:
  Host: gram Kernel: 6.5.0-13-generic arch: x86_64 bits: 64 Desktop: Penrose
    Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Convertible System: LG product: 16T90Q-K.AAC7U1 v: Type1Version
    serial: <superuser required>
  Mobo: LG model: 16T90Q v: Type2Version serial: <superuser required>
    UEFI: American Megatrends v: GP123 date: 05/13/2022
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    driver: sof-audio-pci-intel-tgl
  API: ALSA v: k6.5.0-13-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active

% dmesg | grep ALC
[   63.216795] snd_hda_codec_realtek ehdaudio0D0: autoconfig for ALC256: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker



```

---

