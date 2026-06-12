---
title: "no backlight on laptop, black screen"
date: 2009-04-04
forum: Hardware
---

### Post by d-osprey on 2009-04-04
My laptop screen is black, no backlight. 

Newbie successfully running Ubuntu 8.1 Intrepid for two months,
on laptop Toshiba Tecra A8-S8414, 
display 15.4" TruBrite TFT LCD 128x800 wxga,
Intel Graphic Media Accelerator 950, 8MB graphics memory.

Externally shining a bright light into the laptop screen, reveals that the text is there, but no backlight. 
Just before it failed, the screen was flashing intermittantly.
Also on power-up, the screen WAS illuminating for about three seconds.

Is it something I did? A few days ago, I made some changes via System/Preferences/Power Management.
Under tab "On AC Power": I moved the slider switches to different times,
and checked the box "Dim Display when idle."
Under tab "On Battery Power: Also moved the slider switches,
and checked both boxes to:"Reduce backlight brightness" and  
"Dim Display when idle".

For a couple of days, it seemed to be working with those changes, but then, flashing, and then black.

As a result of the black laptop screen, I connected an external monitor to the system, and the external monitor works ok. 
I have also removed the checks on System/Preferences/PowerManagement boxes: "Dim Display when idle" and "Reduce backlight brightness" boxes. 

Boxes unchecked, however, the problem persists on the laptop monitor.

The function key to increase brightness [Fn]+[F7] does not change the black screen.

I saw a post ([http://linuxhappy.wordpress.com/2007/12/17/bright](http://linuxhappy.wordpress.com/2007/12/17/bright)...) that said to try  Ctrl+Alt+F1 and then Ctrl+Alt+f7. 
That sequence of keys gave me three seconds viewable on my laptop screen, 
although the color was red and washed out. Then it went black again.

In terminal mode, 
sudo gconf-editor /apps/gnome-power-manager/backlight
and unchecked idle_dim_battery. 
That didn't make any difference to the dark screen problem.

Yet another post ([http://ubuntuforums.org/archive/index.php/t-75678.html](http://ubuntuforums.org/archive/index.php/t-75678.html)), 
said to try adding a second line to /etc/acpi/resume.sh, 
adding /usr/bin/toshset -bl on
Again on powerup, that made no difference either.
So, not knowing what I'm doing, I removed the line I added.

And from info on another post ([http://ubuntuforums.org/archive/index.php/t-976384.html](http://ubuntuforums.org/archive/index.php/t-976384.html)), I ran lspci to obtain video info:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

From this [http://ubuntuforums.org/showthread.php?t=1115429](http://ubuntuforums.org/showthread.php?t=1115429)
I followed the directions,
esc on bootup into -11 generic (recovery)
Then selected xfix Try to fix X server
then, resume  Resume normal boot
However, I still have a black laptop screen.

But I don't know what to do next.

Are these symptoms indicating a software problem or a hardware problem? And what do I do?

---

### Post by Zimmer on 2009-04-10
Try a Live CD as that will have a 'vanilla' default display setting and I would guess if you still get a black screen then it is a hardware problem...

---

### Post by d-osprey on 2009-04-17
Thanks, Zimmer. 
I tried a live cd of PuppyLinux and had the same black screen result, so I'll buy an inverter and hope it fixes the problem. 
But, before I install an inverter - is there any way to restore the power management settings back to the original default settings?

---

### Post by d-osprey on 2009-05-13
Oh no. 
I purchased and replaced the backlight inverter.
The laptop screen is still black.

But if I put a bright light against the laptop screen, I can see the contents of the screen dimly (same contents as on my auxilliary monitor).

I'm going to do a clean install of the latest Ubuntu 9.04 to see if that has any impact.

Laptop is Toshiba Tecra A8
display 15.4" TruBrite TFT LCD 128x800 wxga,
Intel Graphic Media Accelerator 950, 8MB graphic memory

---

### Post by bagyolatamas on 2011-05-14
I have this problem too ;) your notebook is good the problem is whit Ubuntu :(

---

### Post by sanderd17 on 2011-05-14
[I]> **Zimmer said:**
> Try a Live CD as that will have a 'vanilla' default display setting and I would guess if you still get a black screen then it is a hardware problem...

I have seen that the problem is in the kernel, so a vanilla install will not work. Trying an older kernel from the grub list will probably work.

Setting the boot options "nomodeset" or "acpi_osi=" also worked for the most. I had the backlight problem too, and for me, the only thing that worked was switching to 32-bit.

Check my sig to get info about setting boot options[/I]

[B]EDIT:

I did't notice the year. @bagyolatamas: Ubuntu 11.04 is a lot different from 9.04. following instructions written for 9.04 will probably not work. I was talking about 11.04.[/B]

---

### Post by Firezap on 2011-05-14
Remember, there is more to a back light display then an inverter board...When the screen is pinkish it might mean that the light itself is faulty, not the inverter board. Did you try to hook up the laptop to a different screen? Also, a cable could be bad as well. I am just throwing out ideas though. But the fact that even Puppy Linux has the same problem makes me lean to a hardware problem. A laptop lamp burning out is not unheard of.:-k Although I may be wrong.


I just realized that this is an old forum lol...

---

