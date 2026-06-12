---
title: "Touchpad and Camera &quot;missing&quot;"
date: 2016-11-08
forum: Hardware
---

### Post by asearle on 2016-11-08
Hallo Everyone,

A couple of years ago I bought my girlfriend a "Terra" laptop (a "no-name" but apparently with high-quality components) but found that neither the camera nor the touchpad worked. I wasn't too worried because the touchpad had worked with a Windows live-CD and so I planned to wait until a new release "found" these components.  But now 16.04.1 is out and they are still not visible.

When I look on my laptop (same company but slightly different model) I see the touchpad and the camera listed in "Input Devices" in "System Profiler and Benchmark" but these are not visible on the other (problem) laptop. I also compared "PCI Devices" but there seemed to be no difference.

I thought I might need to check/change the BIOS but I have looked long and hard and can't see anything that might play a role. The BIOS is "American Megatrends X300V TR.07 x64". I also asked the vendor but the reply was (as expected) "we don't work with Linux".

If anyone has a tip to get me started with the diagnostics then please do let me know.

Many thanks,
Alan
in Cologne

PS: Could it be an issue with "Lubuntu" (LXDE)?  Should I maybe try another Distro? But this seems to be such a basic point that it probably doesn't make a difference?

---

### Post by mörgæs on 2016-11-09
16.04.1 is not the latest release. 16.10 is, and it's worth a try to do a live boot of this one. If you have already tried Lubuntu then I suggest Ubuntu for the test.

One doesn't need to use Linux to upgrade the BIOS, in fact most BIOS'es need Dos or Windows for upgrading.

---

### Post by asearle on 2016-11-22
At last I found a reference to the problem of the touchpad not being recognised ...

[http://www.linux-hardware-guide.com/2013-11-30-wortmann-terra-mobile-1450-ii-ultrabook-intel-core-i3-3217u-1-8ghz-14-non-glare-led-4gb-120gb-ssd](http://www.linux-hardware-guide.com/2013-11-30-wortmann-terra-mobile-1450-ii-ultrabook-intel-core-i3-3217u-1-8ghz-14-non-glare-led-4gb-120gb-ssd)

> Grub has to be adapted in order to use the touchpad. In the file “/etc/default/grub” the entry
GRUB_CMDLINE_LINUX=""
has to be adapted to	
GRUB_CMDLINE_LINUX="i8042.noloop"
Afterwards, the following command has to be executed in order to let grub take this change into account:	
sudo update-grub

with some other sources saying the grub line should be the following ...

```
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
```

So I tried this and update grub and rebooted ... but the touchpad remained unrecognised.

On other sites (in German) they recommended switching UEFI (in BIOS) to include legacy systems. So I opened BIOS ...

> Aptio American Megatrends X300V TR.07 x64

... but couldn't see where I could select legacy systems. Indeed, I scoured the options (including Secure boot) but couldn't see any OS-mode settings.

This is very frustrating because the problem has been recognised and registered but none of the solutions seesm to work for me.

Any tips would be a great help.

Many thanks,
Alan
Cologne

---

