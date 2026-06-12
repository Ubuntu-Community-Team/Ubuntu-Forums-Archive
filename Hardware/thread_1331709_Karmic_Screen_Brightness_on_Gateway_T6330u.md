---
title: "Karmic Screen Brightness on Gateway T6330u"
date: 2009-11-19
forum: Hardware
---

### Post by chessnerd on 2009-11-19
Well, I installed Karmic on my laptop a few days ago and immediately evaluated what was working and not working. The sound worked without a fix being needed (a big plus because of the amount of time I spent fixing it in Jaunty), but I was having screen brightness issues.

"Oh," I thought, "that's not a problem. I had the same issue in Jaunty and wrote down my fix in a text file that I backed up before installing. I'll just implement the same command and it will work and then I can go along my way." Evidently I thought wrong.

The fix I tried (which worked under Jaunty) was - ```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
``` I added that to the startup list so that it would run every time I rebooted and then went about re-installing all of my applications and working on learning Grub2 to customize my boot loader only to find out later that that fix did nothing.

Until I can get it working I'll be forced to boot into Vista or 7 during class because with maximum brightness set my battery doesn't last that long. Does anyone know of a way to get my brightness adjustment working?

---

### Post by chessnerd on 2009-11-20
Alright, after more searching I found a fix for my problem and, oddly enough, I did it by editing Grub 2 configuration files.

After reading this: [http://ubuntuforums.org/showthread.php?p=8295090](http://ubuntuforums.org/showthread.php?p=8295090) While the fix they gave at the end was for Grub 1 (also referred to as Grub Legacy) I was able to infer a possible Grub 2 solution that ended up working.

For Grub 2, here is how you get the backlight working:

Open the terminal.

Open the /etc/default/grub file as root -
```
sudo /etc/default/grub
```

Then add "nomodeset acpi_backlight=vendor" to the GRUB_CMDLINE_LINUX line.
```
GRUB_CMDLINE_LINUX="nomodeset acpi_backlight=vendor"
```

Save the file and close.

Finally, update Grub.
```
sudo update-grub
```

Reboot and your backlight should work now.

If you are still using Grub 1 under Karmic you can refer to that last post in the aforementioned thread - [http://ubuntuforums.org/showthread.php?p=8295090](http://ubuntuforums.org/showthread.php?p=8295090)

Hope this can help some other people. I know that a lot of people are having the same problem.

---

### Post by Eagle Knight on 2009-11-21
Thanks:D chessnerd, 
I have the same Gateway T6330U but upgraded from 9.04 to 9.10.
This is Grub 1 fix  

Open the terminal.

Open the /boot/grub/menu.lst file as root -

```
sudo gedit /boot/grub/menu.lst
```


edit
after ## ## End Default Options ##
on the desired Kernel line 

Title
uuid
**Kernel**.............at the end add "nomodeset acpi_backlight=vendor" 
initrid
quiet
 

```
kernel	/boot/vmlinuz-2.x.xx-xx-generic root=UUID=....... ro quiet splash **nomodeset acpi_backlight=vendor**
```

Restar and you're done.

Btw did you make a clean install from live cd?... 'cose my lap has problems running it.

appreciate your help

---

### Post by chessnerd on 2009-11-22
> **Eagle Knight said:**
> 
Btw did you make a clean install from live cd?... 'cose my lap has problems running it.

appreciate your help

Yeah, I did a clean install from the live CD without any issues. Didn't have any issues with Jaunty either and I regularly test other distros on this thing without live CD problems. I'm not sure why two virtually identical laptops would be different in this respect. 

The only issue with CDs on my laptop is that the CD tray occasionally (maybe 1 in 4 times) shakes violently when loading up content from a CD or DVD, but thankfully it doesn't damage the disk or stop the content from loading.

Anyway, I'm glad I was able to help. The Ubuntu Forums community has given me a lot of assistance over the last year so any time that I can give back feels good. :)

---

### Post by Eagle Knight on 2009-11-23
Hi Chessnerd,
Finally after burning the image in a dvd instead of a cd  with an old xp machine and nero8 at 4x write speed, my dvd player didn't shake like crazy and now I have a clean karmic install which is better than the upgraded, the brightness grub 2 fix works grate.

Thanks again:)

---

