---
title: "Xubuntu Dual boot Windows 10 - Toshiba Laptop Touchpad Not Working"
date: 2015-11-28
forum: Hardware
---

### Post by Josh_Buzz on 2015-11-28
Hello there!

I have a Toshiba U945 laptop running Xubuntu 14.04 (dual-booted with Win10). The problem, the touchpad won't work when running Xubuntu AT ALL.
It DOES work when inside Windows 10 though. USB mouse WORKS on BOTH OSs.

Here's what I've tried so far:
[LIST]
[*]uninstalling, and reinstalling ```
xserver-xorg-input-synaptics
``` to no avail. 
[*]the hardware on/off for the touchpad on this laptop is Fn + F5. Which does nothing. Also, if I press F5 alone, all it does is open the display settings window. 
[*]creating a new user, as one forum post suggested (maybe i messed up the config), but even the new user, and guest user doesn't have control. Even the login screen won't detect the touchpad. 
[*]```
synclient TouchpadOff=0
``` to no avail. the terminal shows that TouchpadOff is set to 0, but still touchpad does not function. 
[*]many other things, of which most of the variations were to uninstall and reinstall synaptics, or xserver-xorg... I lost count... 
[/LIST]

This wasn't always the case. There was a time when I could use it fine. I even created a script file to turn the touchpad on/off using a keyboard shortcut utilizing TouchpadOff=1/0 and tied it to a shortcut so I can turn it on/off as desired.
I forgot when this problem surfaced exactly, as I have let it alone for awhile, however, it is really getting to me now, not being able to work w/o a USB mouse.
If I do remember correctly though, I think this started after I refreshed my Win8, and upgraded it to Win10.

I hoping someone here can help. I would be very grateful, I have been on this for around 2 weeks now.

---

### Post by Josh_Buzz on 2015-11-29
Hey there! :)

I see a lot of people have viewed this post overnight, but no answers
I'm HAPPY (no,overjoyed) to announce that IT'S SOLVED! :)

After scouring the web some more. I found a post that is somewhat similar to my situation, here:
[http://ubuntuforums.org/showthread.php?t=2237259](http://ubuntuforums.org/showthread.php?t=2237259)

I followed the steps indicated in [**[COLOR=#000000]moboticdes[/COLOR]**]("http://ubuntuforums.org/member.php?u=1146088")' December 28th, 2014 post, with a slight modification.
His post was for a Lenovo laptop, but I have a Toshiba. So, i followed everything, except, instead of blacklisting "ideapad_laptop", i did "lsmod" in Terminal, and spotted an entry "toshiba_acpi", since this is an acpi issue, and it seemed the closest one, I took the chance. And lo, behold, after rebooting, I hit Fn + F5, and swiped the touchpad, and watched it GO! :)

It seems the core problem was that every time Xubuntu boots up, it automatically locks the touchpad. The toshiba_acpi driver seems to be in charge of controlling the Fn keys, hence the mixed up functionality when I hit them (as mentioned in orig. post). By black listing the acpi driver, I forced the OS to load an alternate and PROPER driver. Now, Fn keys work exactly and precisely as they should! :)
At least, that's how I understood the problem.

In case, something happens to the link, here's the instructions from 's orig. post.
> What I did was



[LIST=1]
[*]Add the acpi_backlight=vendor to the grub default command line by doing the following:
[/LIST]

    
sudo gedit /etc/default/grub
  You will find this line in the new opened window:

  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  
Change it to:

  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
  
Save and close the window. Then do the following:



[LIST=1]
[*]Run the update-grub command
[*]blacklist the ideapad_laptop by adding "blacklist ideapad_laptop" to your /etc/modprobe.d/blacklist.conf file.
[*]Reboot
[/LIST]


Anyway, I hope this helps the people going through the same/similar problem!
God bless!

---

