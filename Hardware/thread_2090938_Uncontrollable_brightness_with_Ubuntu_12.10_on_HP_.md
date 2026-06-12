---
title: "Uncontrollable brightness with Ubuntu 12.10 on HP Pavilion g7-2220 Notebook"
date: 2012-12-03
forum: Hardware
---

### Post by Uncuddly on 2012-12-03
Hello! :)

I recently received a new HP Pavilion g7-2220 Notebook PC and have loaded Ubuntu 12.10 onto it as an alternative to its native Windows 8. The results are mostly good or at least tolerable but the display is always at full brightness while using Linux.

Neither the notebook's brightness keys nor the slider in Ubuntu's "Brightness and Lock" settings have any effect on it. Google reveals that users in similar situations have had success adding "acpi_backlight=vendor" to grub but this only results in the brightness slider vanishing from settings.

Although I'm not sure what influence it might have over the screen brightness, the system reports that an AMD Radeon HD 7520G is responsible for its graphics. For what it's worth, the laptop's other hardware buttons (volume, media pause, wireless on/off) work as expected. I can switch back to Windows 8 to verify that the brightness is normally changeable, so it's not that the display itself is unable to dim. Any advice or suggestions in this regard would be greatly appreciated!

Suppose I could just wear sunglasses. :)

---

### Post by Toz on 2012-12-04
Hello and welcome to the forums.

Have you installed the ATI proprietary graphics drivers? You can find them by opening up the Software Centre, navigating to Edit->Software Sources and looking on the Additional Drivers tab.

You might also want to try the **acpi_osi=Linux** kernel parameter instead of "acpi_backlight=vendor".

---

### Post by Uncuddly on 2012-12-04
Thank you for the reply! I had not installed any proprietary software so I selected the fglrx driver at your suggestion. A fglrx-updates driver was also available but I decided to try them from the top down. Unfortunately, the result is that the laptop does not make it to login. It displays the end of the boot sequence as white text on a black screen.

I'm not sure whether returning to the open driver is best accomplished by means of booting in recovery mode or with the live DVD. I can't spend time with it at the moment, but once I figure it out I'll try the other proprietary driver and the proposed parameter.

In the meantime, thanks again for the feedback. :)

---

### Post by Uncuddly on 2012-12-05
Ok, so recovering from the previous attempt ended up being a fair mess. I couldn't boot far enough to reach a command line to potentially uninstall the problem driver and try again, so I used the Ubuntu DVD in an attempt to reinstall to get default settings. Sadly, the option to reinstall over the existing Ubuntu installation apparently doesn't like skipping the partitioning portion of the install, even though it would seem that no partition changes would be needed. So that reinstall got stuck after erasing enough of the original install that it couldn't be recognised and I had to do another reinstall over the Ubuntu partition.

Once Ubuntu was reinstalled, I tried the option for the updated proprietary driver. This has the same result of making the system unresponsive, so I suppose I'll have to reinstall Ubuntu again unless there is a less aggressive way to manipulate the installation without access to the command line. Maybe text-editing files with the DVD's OS? I'm not sure it's less trouble overall.

I'm not up for another reinstall tonight (also not sure that I haven't made an even bigger mess with my previous reinstall follies), so I still haven't been able to test the suggested parameter. The proprietary drivers aren't getting us anywhere on the brightness issue, anyway! :)

---

### Post by Uncuddly on 2012-12-05
After another reinstall, I tried the acpi_osi=Linux parameter. This does not restore control over brightness and has the side effect of disabling the other hardware keys, which previously worked. It also seemed to make the keyboard entirely unresponsive a few times as I tried to test the hardware buttons, requiring a restart. Maybe that was a consequence of the button pressing itself, though.

I should note that by default, without any acpi additions to grub, pushing the brightness buttons does cause Ubuntu's brightness indicator to appear and shift in the appropriate direction. It just doesn't affect screen brightness.

In summary, the proprietary drivers and grub changes aren't getting us anywhere on the HP g7-2220's brightness. It's fairly recent hardware so I expected it to have trouble with Linux, but one is duty-bound to try it so that the next person with one of these systems has something to read. On the bright side, I'm getting used to the maxed out screen setting. :)

---

### Post by Toz on 2012-12-05
Can you open a terminal window, run the following command and post back the results (it will identify your backlight interfaces):
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Maybe we can manually manipulate the brightness.

---

### Post by Uncuddly on 2012-12-06
The output is:

/sys/class/backlight/acpi_video0
6
10

Changing the brightness setting in Ubuntu changes the middle number. Since I have removed the grub changes, pressing the button to reduce brightness changes the 6 to 4, for example. Screen brightness obviously remains much higher than that!

Thanks for the continued feedback! :)

---

### Post by Toz on 2012-12-06
Hmmm. Can you retry this with the **acpi_backlight=vendor** parameter?
And can you also post back the results of:
```
lspci | grep VGA
```

It always seems to take some time with newer hardware to get functional support in the Linux kernel. I want to see if we can get a workaround to dim your brightness in the meantime.

---

### Post by josvanr on 2012-12-07
I'm following this discussion with great interest as I have the same problem on my HP Envy 17 (1.5 year old hardware)....

josvanr

---

### Post by Uncuddly on 2012-12-07
Retrying the above for-loop with the backlight parameter yields:

```
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
```It's just an empty directory now that the parameter is set.

The result of lspci | grep VGA is:
```

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7520G]
```Thanks for the interest, josvanr! I'm sure a solution will arise eventually! :)

---

### Post by josvanr on 2012-12-07
I just did an update, kernel is now 3.2.0-35-generic, and the problem has gone for hp envy 17 2100ed.

One down, x to go ......

---

### Post by Toz on 2012-12-07
> **Uncuddly said:**
> Retrying the above for-loop with the backlight parameter yields:

```
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
```It's just an empty directory now that the parameter is set.

The result of lspci | grep VGA is:
```

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7520G]
```

Try these commands:
```
sudo setpci -s 00:01.0 F4.B=FF
sudo setpci -s 00:01.0 F4.B=0
sudo setpci -s 00:01.0 F4.B=80
```

If no luck, try removing the **acpi_backlight=vendor** parameter and trying those commands again.

---

### Post by Uncuddly on 2012-12-08
The above commands produce no discernible difference with or without the backlight parameter. It's good to hear that josvanr has resolved the issue with the HP Envy, however! :)

---

### Post by Toz on 2012-12-08
I can't seem to manipulate your backlight interface. I think you're next best bet would be to try to get the proprietary drivers to work on your laptop. 

According to this bug report ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488")), there is a problem with installing proprietary drivers because of a missing package. You might be suffering from this problem when you try to enable to proprietary drivers and end up with a blank screen on reboot.

If you want to try getting the proprietary drivers installed again, try installing **linux-headers-generic** before enabling the proprietary drivers.

If on restart you still get a blank screen, you should be able to regain access to the system by passing the **nomodeset** kernel parameter on startup. See "How to temporarily set kernel boot options on an installed OS (not wubi)" [here]("http://ubuntuforums.org/showthread.php?t=1613132") for info on how to set it on startup.

---

### Post by Uncuddly on 2012-12-09
The system states that linux-headers-generic is already installed. It dates to October so it must be from the DVD and therefore available during the previous attempts to use the proprietary drivers.

Thanks for the nomodeset suggestion, though. I will definitely try that next time things go belly-up.

---

### Post by ShubhN on 2013-07-20
> **Toz said:**
> Can you open a terminal window, run the following command and post back the results (it will identify your backlight interfaces):
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Maybe we can manually manipulate the brightness.

Thanks for that. It was really req, bacause i started planning to go back to win7 since my eyes started responding to that much brightness. **THANKS AGAIN IN BOLD**[IMG]http://ubuntuforums.org/images/icons/icon10.png[/IMG]

---

### Post by chris.rapson on 2013-11-03
just like josvanr I'm following this thread to see if a solution turns up for older Envy hardware. As I understand it, the OP still has maxed out brightness? I've also had no success with grub settings and proprietary drivers only created more problems.

I'm running kernel 3.11.0-12-generic with Kubuntu 13.10

---

### Post by Toz on 2013-11-03
> **chris.rapson said:**
> just like josvanr I'm following this thread to see if a solution turns up for older Envy hardware. As I understand it, the OP still has maxed out brightness? I've also had no success with grub settings and proprietary drivers only created more problems.

I'm running kernel 3.11.0-12-generic with Kubuntu 13.10
Hello @chris.rapson and welcome to the forums.
Do you have the same system with an ATI card? What does the following command return:
```
lspci -k | grep -iA2 VGA
```
Can you also run the following command so we can see your current backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

