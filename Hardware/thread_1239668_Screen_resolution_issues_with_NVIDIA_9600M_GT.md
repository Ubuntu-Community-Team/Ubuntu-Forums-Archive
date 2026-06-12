---
title: "Screen resolution issues with NVIDIA 9600M GT"
date: 2009-08-13
forum: Hardware
---

### Post by Wintershade on 2009-08-13
I have a bit of a problem with my NVIDIA GeForce 9600M GT (a notebook graphics card) on Arch Linux, and was hoping that somebody here could help me.

Yes I know Arch Linux has their own forum, and I've been discussing this issue there as well; however I'd like to ask the same question here, since **it seems that Ubuntu configures my graphics card correctly, unlike other distros**.

I have a widescreen notebook computer, whose display can do 1440x900@60Hz. However, this is the only widescreen resolution available to me, as all the other listed available modes are the 4:3 ones (like 1024x768, 800x600 and 640x480).

I'm running Arch Linux, with all the packages up-to-date (as far as the repos are concerned). The xorg server I'm running is 1.6.3, and the nvidia driver version is 185.18.31 (again, the latest from the repo).

So, I know this behaviour is wrong. I also have Ubuntu installed on my notebook, and it has somehow correctly "autoconfigured" my graphics card - there is a wide (forgive the pun) variety of video modes available to me - among others there are 1360x768, 1152x864, 960x600, 960x540, 840x525, and so on. All of these modes work under Ubuntu flawlessly - so it shouldn't be a problem with either my hardware or the driver.

If anyone could shed some light on this issue, I'd be most grateful. I'd like to configure my Arch Linux so that I can use other video modes, just like I can under Ubuntu.

For the record, I am putting my Xorg.0.log for [Arch]("http://pastebin.com/m55756ef5") and [Ubuntu]("http://pastebin.com/m4791db4b") in the pastebin; they are mostly the same, since there's not much configuration inside either xorg.conf.

However, if I try to edit the "Device" section in my xorg.conf under Arch and manually add the desired resolutions, like this:
```
SubSection "Display"
 Depth     24
 Modes "1440x900" "1360x768" "1152x864" "1024x768" "960x600" "960x540" "840x525" "800x600" "720x450" "640x480" "640x384"
EndSubSection
```my xorg still doesn't want to use them, and complains about it in Xorg.0.log:```
(--) NVIDIA(0): Connected display device(s) on GeForce 9600M GT at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Mode Validation Overrides for Seiko (DFP-0):
(II) NVIDIA(0):     NoExtendedGpuCapabilitiesCheck
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1360x768"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(WW) NVIDIA(0): No valid modes for "960x600"; removing.
(WW) NVIDIA(0): No valid modes for "960x540"; removing.
(WW) NVIDIA(0): No valid modes for "840x525"; removing.
(WW) NVIDIA(0): No valid modes for "720x450"; removing.
(WW) NVIDIA(0): No valid modes for "640x384"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
```

There... this is what I've mostly been able to piece together. I'm thinking there's another configuration file under Ubuntu somewhere, something that Arch doesn't have (or didn't configure properly). If anyone knows where or what is there to configure beside xorg.conf, please do tell me.

I will be very grateful if anyone could shed some light on this.

Thanks in advance!

---

