---
title: "Acer Aspire 3820TG brightness regulation"
date: 2010-05-30
forum: Hardware
---

### Post by napetesy on 2010-05-30
Hello,
I am running fresh installation of 10.04 on Aspire 3820TG with switchable graphics (Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] and ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]).
I have two questions?
1) How to find out which graphic card is used?

2) Second question is regarding the brightness regulation. Hot keys for brightness regulation are working so that only the brightness indicator is changing its value but the real brightness of the LCD is not (it stays on maximum). Is there any way how to regulate brightness on this laptop? 

Thank you for any suggestions.
napets

---

### Post by fishbulb1022 on 2010-06-01
I'm having the same issue on an Acer Aspire 7740-6656, with the same Intel Integrated graphics mentioned above. If anyone has a solution, that'd be great...and since were both having the same issue, I would guess that you're probably using the intel graphics. I don't know how to check, but that would be my assumption, unless you have successfully been able to switch, and the problem persisted.

---

### Post by Scott Sherman on 2010-06-01
Hi,
 
My function keys do not work either...
 
All you need to do to adjust the brightness is.. Right click on the task bar and click add or something like, (doing this from memory as I'm in work!) it should open a box of gadgets to add, and if you scroll down the list one of them is the brightness adjuster. Add that and you'll be set.
 
Cheers

---

### Post by fishbulb1022 on 2010-06-01
The applet doesn't work for me, no does going to the power menu and adjusting it there.

---

### Post by jmcdougall on 2010-06-01
I have an Acer Aspire 7740 and also have this problem.  I have posted this elsewhere and have gotten no responses.  Interestingly, I have installed the Burg graphical front end to Grub and the controls DO work there, but once it gets to the logon splash screen, it no longer works and is at full brightness.  That sure doesn't help when running off the battery.

---

### Post by napetesy on 2010-06-02
> **napetesy said:**
> 
1) How to find out which graphic card is used?

Still I don't know how to check which card is used... :(

> **napetesy said:**
> 
2) Second question is regarding the brightness regulation. Hot keys for brightness regulation are working so that only the brightness indicator is changing its value but the real brightness of the LCD is not (it stays on maximum). Is there any way how to regulate brightness on this laptop? 

I found a workaround (not the best one but it is working). I just disabled switchable graphics in BIOS. After that only ATI graphics card is visible and then everything works.

Of course we are loosing ability to reduce power consumption...

---

### Post by napetesy on 2010-06-02
I would suggest to read this thread: [http://ubuntuforums.org/showthread.php?t=1242590&highlight=3820TG](http://ubuntuforums.org/showthread.php?t=1242590&highlight=3820TG)
There is post #11 ([http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)) which should allow to switch off ATI card i.e. more power save.

Moreover maybe this thread will help us: [http://ubuntuforums.org/showthread.php?t=1165087](http://ubuntuforums.org/showthread.php?t=1165087)

And it looks like in linux kernel 2.6.34 is switchable option so there will be some workaround available soon or later [http://asusm51ta-with-linux.blogspot.com/]("http://asusm51ta-with-linux.blogspot.com/")

---

### Post by webbertiger on 2010-07-31
I'm running Ubuntu 10.04 on Acer Aspiron 7740 with the same issue, too. The current workaround I use is:
1) edit "/boot/grub/grub.cfg" by
changing
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=ht"
```
This can force ACPI to enable only CPU hyper-threading support. So it will not intercept the hot key to adjust backlight.

2) run the following command and reboot
sudo update-grub

This workaround will affect the battery notification. I need to adjust the backlight more often than checking battery levels, so I find this is a trade off that I can accept, before the new kernel fixes this.

---

### Post by Darkhorse85 on 2010-09-21
I have the same problem, but changing the settings in grub renders the laptop unbootable. Then i have to live cd to change the grub settings back to what it was before. So to sum up, nothing works to change the brightness in the terminal or in GUI form. 
My battery is feeling the strain when im not close to a power source :???: , so then i have to boot into windows 7 #-o

---

### Post by worldsayshi on 2011-02-12
F4lkon's solution in [this]("http://ubuntuforums.org/showthread.php?t=1613547") thread helped with me to disable Radeon and to gain some significant battery life. Although I can still not control brightness.

---

### Post by mk.fg on 2011-04-13
While not using fedora or ubuntu I've found solution for my 3820/distro on fedoraforum, in [this thread]("http://www.fedoraforum.org/forum/showthread.php?p=1461012").

Basically, just adding "acpi_osi=Linux" (note the capital L) to kernel cmdline (in grub) works for me.
Another (worse) solution is to set brightness level and reboot afterwards, taking care either not to shift it down again or just write a script to set it to max via sysfs right before reboot.

Apologies for necropost, but the thread just lacked that answer ;)

---

### Post by kubco2 on 2011-05-26
Is some fix for brightness levels? I used "edit grub" fix, but this leveling is horrible, sometimes after click it doesnt changes backlight and another time it changes more then 2-3levels on one click

Thx

---

### Post by yepes76 on 2011-08-16
I had the same problem of the brightness fn keys not working. It was not a problem of the fn keys, there were no way to change brigthness even with commands like xbacklight. 

After days googling and trying very different solutions, none of which worked at all, I found one (finally!!! :D) that worked for me!! I am using ubuntu 11.04 in an Acer Aspire 5742 with Intel integrated graphics. I reckon it is the same that mk.fg posted here, but then I did not understand it very well :S Here is the solution step-by-step

You need to edit the grub file with root permissions. Type in a terminal

```
sudo gedit /etc/default/grub
```then change the line

```
GRUB_CMDLINE_LINUX=""
``` by ```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```save changes, go back to the terminal and type

```
sudo update-grub
```and restart.

Hope it helps!

---

### Post by ozi87 on 2012-02-23
> **yepes76 said:**
> I had the same problem of the brightness fn keys not working. It was not a problem of the fn keys, there were no way to change brigthness even with commands like xbacklight. 

After days googling and trying very different solutions, none of which worked at all, I found one (finally!!! :D) that worked for me!! I am using ubuntu 11.04 in an Acer Aspire 5742 with Intel integrated graphics. I reckon it is the same that mk.fg posted here, but then I did not understand it very well :S Here is the solution step-by-step

You need to edit the grub file with root permissions. Type in a terminal

```
sudo gedit /etc/default/grub
```then change the line

```
GRUB_CMDLINE_LINUX=""
``` by ```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```save changes, go back to the terminal and type

```
sudo update-grub
```and restart.

Hope it helps!

Now i have light! Thank's!

---

