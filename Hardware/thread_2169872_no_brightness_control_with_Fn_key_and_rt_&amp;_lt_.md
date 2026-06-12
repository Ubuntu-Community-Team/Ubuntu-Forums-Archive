---
title: "no brightness control with Fn key and rt &amp; lt arrow keys."
date: 2013-08-23
forum: Hardware
---

### Post by jlh68 on 2013-08-23
I have a new netbook: Acer Aspire One model 725.  I installed Ubuntu 12.04.2LTS.  The touch pad does not work (unless I push Ctrl + Fn + F7) and the Fn brightness does not work. I have tried several "fixes" but none have worked and one even "broke" my system and I had to reinstall Ubuntu.

I would like to get the Fn brightness control to work, as I often turn the brightness down to extend battery life.

---

### Post by Toz on 2013-08-23
Have you tries the **acpi_osi=** kernel parameter? Here's how:

[LIST=1]
[*]Open your grub configuration file for editing as root:
```
gksu gedit /etc/default/grub
```
[*]Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi="
```
[*]Save the file
[*]Update grub:
```
sudo update-grub
```
[*]Reboot
[*]
[/LIST]

If the brightness still doesn't work on reboot, can you post back the results of the following commands:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by jlh68 on 2013-08-23
I tried your solution.  I get the applet in the right upper part of screen, but no change in brightness. and the applet does strange things:the brightness symbol bilink and the bar goes back and forth.

> john@Osprey:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=fcd74ea2-fe7c-456c-aace-213fc0bce507 ro acpi_osi quiet splash vt.handoff=7 
john@Osprey:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done 
/sys/class/backlight/acpi_video0 
0 
9 
john@Osprey:~$ 

---

### Post by jlh68 on 2013-08-23
I am wondering about that netbook as I have some other issues with it.  The WiFi will not connect, the touchpad does not work unless Ctrl + Fn + F7 are pressed and I cannot get it to dual boot into Win7.  Maybe some other issues I have not discovered yet.  I just set it up last week, It cam with Win7 installed and I changed the partitions for an Ubuntu install.  I thought since the netbook HD was 320GB and my Laptop was 320GB and both have Win7 installed, that I could set them up the same.  Well dual boot did not work the same.

---

### Post by Toz on 2013-08-23
> **jlh68 said:**
> I tried your solution.  I get the applet in the right upper part of screen, but no change in brightness. and the applet does strange things:the brightness symbol bilink and the bar goes back and forth.

You mispelled the kernel parameter. It should be **acpi_osi=**. The equals sign needs to be there. Can you try it again?

---

### Post by Toz on 2013-08-23
> **jlh68 said:**
> I am wondering about that netbook as I have some other issues with it.  The WiFi will not connect, the touchpad does not work unless Ctrl + Fn + F7 are pressed and I cannot get it to dual boot into Win7.  Maybe some other issues I have not discovered yet.  I just set it up last week, It cam with Win7 installed and I changed the partitions for an Ubuntu install.  I thought since the netbook HD was 320GB and my Laptop was 320GB and both have Win7 installed, that I could set them up the same.  Well dual boot did not work the same.

What video card does it have?
```
lspci -k | grep -A3 VGA
```

---

### Post by jlh68 on 2013-08-24
Answer to your last post is it has an AMD GPU which has a Rathon 6290 chipset.

To the other I put the correct spelling in (=) and I am having trouble booting.  I may have to reinstall Ubuntu.  I an getting Some numbers then BUG: soft lockup -CPU#0 stuck for 22s! [kworker/u:0:5]  I have 9 such messages and it is adding another about every 50 seconds.

---

### Post by jlh68 on 2013-08-24
I would like to reinstall all of Unbuntu and see if I can correct the Win7 not booting.  I don't remember how I goit it to work on this laptop bet it boots either Ubuntu or Win7. The image is of this laptop partition table.  The subject netbook has a similar one, execpt some ot the partition sizes are slightly different.
Any suggestions on setting up dual boot?  I know that I have not made the windows loader mount in the correct place, but I don't know what it should be and how it should be done.

I want to get the AAO 725 (10.6 screen) setup, and then I will retire the AAO150 (8.9-in screen), actually give it to my grand daughter.

---

### Post by Toz on 2013-08-24
> **jlh68 said:**
> Answer to your last post is it has an AMD GPU which has a Rathon 6290 chipset.

To the other I put the correct spelling in (=) and I am having trouble booting.  I may have to reinstall Ubuntu.  I an getting Some numbers then BUG: soft lockup -CPU#0 stuck for 22s! [kworker/u:0:5]  I have 9 such messages and it is adding another about every 50 seconds.
If you are unable to boot into Ubuntu because of the kernel parameter, you can remove it during bootup following the instructions in the "Temporarily Add a Kernel Boot Parameter for Testing" section of [this page]("https://wiki.ubuntu.com/Kernel/KernelBootParameters"). Just reverse the process, instead of adding a parameter, you'll be removing the parameter. Once you have booted into Ubuntu, edit grub again to remove that parameter (remember to run "sudo update-grub" to make it permanent).

---

### Post by Toz on 2013-08-24
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2090982") for more information on setting up the 725 to run Ubuntu.

---

### Post by jlh68 on 2013-08-26
I updated Linux-headers and 300+ other updates and that corrected the brightness problem.  Still no fix or help in the WiFi problem.  I searched the Internet and I still have not found a solution.  I had to connect via ethernet cable to wireless router to update files.  I presume that the WiFi problem has a solution.  I tried using a WiFi dongle (Realteck chip) and it would not work either, so I feel that the problem is in the Operating System or associated files.

A couple of interesting hardware items: neither the CAPS ON or the NumLK have an indicator to let the user know if they have been toggled on or off.  This laptop has LED indicators for both but the 725 netbook does not.  It also does not have any indicator on the screen either.

---

### Post by Toz on 2013-08-26
Glad to hear that the brightness issue is solved. I would suggest creating a new thread in the Networking section for your wireless problem. There are some really knowledgeable people there that can help. That way its not buried here in a thread about brightness.

---

