---
title: "Freeze at startup with AMD fglrx drivers."
date: 2015-07-08
forum: Hardware
---

### Post by ibbles on 2015-07-08
Stops at the Kubuntu logo right after grub.

New driver installed using the Driver Manager in the settings. The dmesg output contains the line 

```

[FONT=monospace][COLOR=#000000][  516.889460] <3>[fglrx:cf_object_handle_cmd] *ERROR* Can not generate cf candidates[/COLOR]
[/FONT]
```

which is also mentioned in a bug report at [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1417952](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1417952). No solution there though.

I also tried following the steps outlined in [http://ubuntuforums.org/showthread.php?t=2276023&p=13305154#post13305154](http://ubuntuforums.org/showthread.php?t=2276023&p=13305154#post13305154), since by HD7950 is between HD5800 and HD8500, but with the same poor results.

Whenever I get the freeze I Ctrl+Alt+F1 to text-only console and do 

```

[FONT=monospace][COLOR=#000000]sudo apt-get remove --purge "fglrx*"[/COLOR]
[/FONT]s[FONT=monospace][COLOR=#000000]udo apt-get install --reinstall xserver-xorg-video-radeon
sudo shutdown now[/COLOR]
[/FONT]
```

and then I get my desktop back on the next reboot.

I would like to try the fglrx drivers because I cannot get OpenCL to work with the  default one, and I get frequent hard lock-ups while playing XCom.

Any ideas?

---

