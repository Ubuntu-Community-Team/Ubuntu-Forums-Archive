---
title: "Aspire 3820TG Problems"
date: 2010-10-05
forum: Hardware
---

### Post by Magreet on 2010-10-05
Hi there,
I've been trying to get Ubuntu to run on my 3820TG but had little luck.
There were few posts already out there of which none helped.
Issues so far:
-Backlight does not adjust
-internal, descrete graphics card switching
-touchpad (I don't care about multitouch but I can't even scroll up)
-battery lifetime: supposed to run 8h, ubuntu predicts 1,5h...

I'd be very gratefull for any help. I've switched from a MacBook Pro to get linux to know better and for programming compatibility and now I'm stuck with windows :(

---

### Post by claude4 on 2010-10-07
Backlight does not ajust
As root edit /etc/default/grub
Change the line GRUB_CMDLINE_LINUX=""
by GRUB_CMDLINE_LINUX="acpi_osi=Linux"
save the file
and then sudo update-grub and reboot.

The system do not see the touchpad, he see this as PS/2 mouse
Make a file psmouse.conf with this text
options psmouse proto=imps
save as root in /etc/modprobe.d/
The vertical scrolling then will be OK

Discrete graphics card switching
You must have Kernel 2.6.35 for that (Ubuntu 10.10)
As root, sudo su
and type echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
This will switch off the discrete card, you save ~10 W of power
You can see that
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

Sorry for my english

---

### Post by Magreet on 2010-10-07
Thank you very much, I'll give it a try!

---

### Post by Rustybolts on 2010-10-07
Acer aspire 5332 here and your fix worked for my screen brightness so thank you very much.   :popcorn:

---

### Post by Magreet on 2010-10-07
Screen and mouse bugs are fixed! =)
How can I test which graphics card is active? If I use the switcheroo command the screen freezes in a colored dot picture...

EDIT:
I installed the ATI restricted driver as well and now it only boots to tty1.
if I try to start startx it says "No devices detectes"/"no screens found" =(

---

### Post by claude4 on 2010-10-07
Don't use ATI driver.
Uninstall the flgrx driver.

---

### Post by Magreet on 2010-10-07
I reinstalled Ubuntu 10.10RC and it seems fine. shows about 4-5h battery life. I do not see a difference if I use echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
but the screen goes black if I try to do the opposite
echo ON > /sys/kernel/debug/vgaswitcheroo/switch

Also tried to use the [B]switch_between_cards.sh from the site.
Does not seem to make a difference...

EDIT:
... at least in AC mode.

Is there a way to enable the multi touch? 10.10 was supposed to support that?
[/B]

---

### Post by karmila on 2010-10-09
@claude4: Thanks mate you saved my eyes :popcorn:

Oh, forgot to tell. Mine is Acer4741Z

---

### Post by fantom1210 on 2010-11-24
Thank You **claude4**, your solutions works for my acer 3820tg very well :popcorn:

---

### Post by kubco2 on 2010-12-12
hello,

is here some solution for enable switching cards on acer 3820tg? My system still freeze in colored screen :( when I use echo ON.

PLEASE

---

### Post by Magreet on 2010-12-12
Just leave it turned off, thats what I do. No need for the ATI card in linux anyway, 1080p runs fine on the Intel.

---

### Post by kubco2 on 2010-12-12
ok thanks, and one more question... is here some tweak for vga fan control? or critical/safe vga temperature? because my vga fan always runs.

Thanks for help.

---

### Post by Magreet on 2010-12-13
Which one is the vga fan? Mine are very quiet, sometimes even off. Yours might run because of the power draining ATI card.

---

### Post by kubco2 on 2010-12-14
Left fan is OK, right fan always run 

tested:

tlp(pm-tools):right fan always running, watt consuption >14W 

laptop-mode-tools: right fan OK can be switched to passive but watt consuption even more ... >16W

bt-off,eth0-off,brightness-30%,kernel 2.6.36,only writing this reply,nothing running

I use this manual to radeon off
[http://ubuntuforums.org/showthread.php?t=1242590&page=9](http://ubuntuforums.org/showthread.php?t=1242590&page=9) down

---

### Post by el-stefano on 2011-02-06
Hi there,

Just in case this is still an issue, the following link will give you some more information:

[http://forum.notebookreview.com/acer/544755-3820tg-linux-any-problems.html](http://forum.notebookreview.com/acer/544755-3820tg-linux-any-problems.html)

If you have some problems with the proprietary driver (as I had, too) and you want to properly uninstall it without reinstalling the entire system, follow this nice manual from the ubuntu wiki:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

cheers,

stefan

---

### Post by A.I. on 2011-05-10
How enable multitouch in touchpad to use two finger scrolling and open context menu by two finger tapping?

I know, that by default laptop saa touchpad as mouse and I fix this by /etc/modprobe.d/psmouse.conf. Vertical scrolling (by scroll in right part of touchpad) is now working, but I can’t found multitouch settings tab in Mouse app.

---

