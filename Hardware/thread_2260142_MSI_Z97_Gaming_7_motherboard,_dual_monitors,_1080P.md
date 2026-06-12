---
title: "MSI Z97 Gaming 7 motherboard, dual monitors, 1080P and 4K, Killer Ethernet"
date: 2015-01-09
forum: Hardware
---

### Post by dogatemycomputer on 2015-01-09
Greetings All,

Hardware compatibility is always an issue with Linux.  If you're considering buying the "latest and greatest" then you can generally expect something to have problems.  I was looking to buy a new computer.  I wanted a dual monitor setup with at least 1 of the monitors being 4K (3840 x 2160).  I also wanted a decked out motherboard (lots of USB 3 ports, lots of SATA III ports) and something fast. The last requirement was that surfing the web, YouTube and XXX should be fast and responsive.  I may not be using the computer for gaming but that doesn't mean it should stutter.

I ended up with:

- MSI Z97 Gaming 7 motherboard:  [http://www.amazon.com/MSI-DDR3-2600-Motherboards-GAMING/dp/B00K23BZTA](http://www.amazon.com/MSI-DDR3-2600-Motherboards-GAMING/dp/B00K23BZTA)  ($179)
- Core i5-4690K [http://www.amazon.com/gp/product/B00KPRWB9G/ref=oh_aui_detailpage_o00_s02?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00KPRWB9G/ref=oh_aui_detailpage_o00_s02?ie=UTF8&psc=1) ($235)
- NZXT Source 210 Case White [http://www.amazon.com/gp/product/B005869IUY/ref=oh_aui_detailpage_o00_s03?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B005869IUY/ref=oh_aui_detailpage_o00_s03?ie=UTF8&psc=1) ($43)
- 16GB of RAM   [http://www.amazon.com/gp/product/B00J8E910Y/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00J8E910Y/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1) ($149)
- Antec 750W pSU [http://www.amazon.com/gp/product/B00DUV01EQ/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00DUV01EQ/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1) ($104)
- Add your monitor, SATA DVD burner and HD of your choice

I installed Kubuntu 14.10.   Everything on this build worked right out of the box.   The Killer NIC (my main concern) and audio worked without a problem.  The integrated graphics required that you enabled dual monitor in the BIOS but Kubuntu detected both the 4K monitor (3840x2160@30hz) and the 1080P monitors. The desktop was setup properly using the open source drivers without adjusting any of the resolution or refresh settings.   The monitors work perfectly without any lag, hanging or other problems including HD Youtube video.  Hardware rendering works fine in Chrome.

 I am told the integrated graphics can power dual 4K monitors if I wanted to add a second one.  

The PSU and 16GB of RAM is overkill.  The fact that Kubuntu 14.10 with a 64GB SSD boots in about 7 seconds tells me the CPU is probably way overkill too.   I could have probably even gone with a i3-3220 and the machine would still perform well.

Oh.. I also ordered a Creative HS-1200 for VoIP apps.  It works great with SFL phone with Pulseaudio without affecting ALSA.  

I hope this helps the next guy.   Have a great day!

---

### Post by pqwoerituytrueiwoq on 2015-01-09
member to always compare prices
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130773](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130773) 153.99 ($133.99 after $20.00 rebate card)
```
05:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 10)
```
does not work with WOL

```
sudo moprobe nct6775
``` will enable your sensors

just get a 300-430 PSU for that, unless you have a monster GPU or SLI/Crossfire you have no need for a 750w unit

---

### Post by liutianxiao on 2015-08-02
hi, how could you install kubuntu 14.10 with using MSI Z97 gaming 7 motherboard?
when I install linux system, It stops with small rectangle in upper left of the screen and goes no further.  MSI seems to have a bad attitude towards Linux.

---

### Post by oldfred on 2015-08-03
@liutianxiao    

Did you add a video card, if so what one. You may need boot parameters for video. Nomodeset for AMD or nVidia or other boot options for Intel.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)



This was older model, but z97 are only slightly different than z87.
 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

---

### Post by liutianxiao on 2015-08-25
i have tried all the thing that you told me. but i still couldn't install kubuntu 14.04.maybe the problem is not about vedio card.
when I install with a liveCD , there will be a "MCE:Hardware Error"
my motherboard is MSI z97 gaming 7, CPU is Intel 4790k and my video card is Intel's integrated graphics.
the error is as follow:

[LIST]
[*][FONT=Courier New]MCE:[Hardware Error]: CPU 2:Machine Check Exception:5 bank 4, be00000000800400[/FONT]
[*][FONT=Courier New]MCE:[Hardware Error[/FONT][FONT=Courier New]][/FONT][FONT=Courier New]: RIP! INEXACT! 10: [/FONT]:<ffffffff810f5720> {Multi_cpu_stop+0x70/0xf0}
[*][FONT=Courier New]MCE:[Hardware Error[/FONT][FONT=Courier New]][/FONT][FONT=Courier New]: TSC 60d4299bac ADDR [/FONT]ffffffff81371c80 MISC ffffffff81371c80
[*][FONT=Courier New]MCE:[Hardware Error[/FONT][FONT=Courier New]][/FONT][FONT=Courier New]: PROCESSOR 0 :306C3 TIME 1358821009 SOCKET 0 APIC 6 microcode 1a[/FONT]
[*][FONT=Courier New][/FONT][FONT=Courier New]MCE:[Hardware Error[/FONT][FONT=Courier New]][/FONT][FONT=Courier New]: [/FONT]Run the above through "mcelog --ascii"
[*][FONT=Courier New]MCE:[Hardware Error[/FONT][FONT=Courier New]][/FONT][FONT=Courier New]: Some CPUs didn't answer in [/FONT]synchronization
[*][FONT=Courier New]MCE:[Hardware Error[/FONT][FONT=Courier New]][/FONT][FONT=Courier New]: machine check: Invalid[/FONT]
[/LIST]
[FONT=Courier New]Could you give me some other advice to solve this problem?[/FONT]

---

### Post by oldfred on 2015-08-25
My system is:
 Asus Z97-AR
Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz
      
 8GB as 2 - 4GB DIMM DDR3 Synchronous 1600 MHz
    
I just updated UEFI/BIOS with newest version and it reset all my settings. Have you updated?

I do not change any memory timings or try to overclock. Are you overclocking? If so remove or reduce it?

Did you use too much or too little thermal paste on CPU when installing it?

[http://www.advancedclustering.com/act-kb/what-are-machine-check-exceptions-or-mce/](http://www.advancedclustering.com/act-kb/what-are-machine-check-exceptions-or-mce/)

---

