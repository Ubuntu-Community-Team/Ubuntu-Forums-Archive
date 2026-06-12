---
title: "[kubuntu] Monitor and graphics card driver failing -&gt; wrong resolution"
date: 2016-09-15
forum: Hardware
---

### Post by cheroka4 on 2016-09-15
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"] My new system is running Kubuntu 16.04, with kernel version  4.4.0-generic.
It is a custom built computer, running an external video  card, [EVGA 1060 GTX 3GB model]("http://www.evga.com/Products/Product.aspx?pn=03G-P4-6160-KR").

I installed the latest Nvidia drivers, ```
sudo apt-get install nvidia-370
```, and rebooted.

Problem is, the detected (maximum and only shown) resolution for my display is 1024x768, but the one from my monitor should be 1920x1080.
After reading  in askubuntu etc I figured that my ```
xrandr
``` output was strange:

```

adrian@CuboIndio:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 
  1920x1080_60.00 (0x28b) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz

```

Note that the above output is after trying to add the resolution, as explained [here]("https://wiki.archlinux.org/index.php/xrandr#Adding_undetected_resolutions"), with cvt.


The output of my /var/log/Xorg.0.log file is [http://pastebin.com/yEgzhV4f](http://pastebin.com/yEgzhV4f).
Note that at this point in time I am not dual booting Windows, but I will down the road for playing games
Any suggestions on what to try would be highly appreciated, thanks![URL="http://pastebin.com/yEgzhV4f"]

[/URL][/TD]
[/TR]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]

---

