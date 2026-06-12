---
title: "HP Elitebook Folio 9470m Hardware Problems"
date: 2013-10-18
forum: Hardware
---

### Post by XpCA4NK on 2013-10-18
Hello,

I recently got my new ultrabook. It is Windows 7 preinstalled and I decided to install Ubuntu 13.10 with dual-boot. This works rather well, but I have a few small problems, I can't really find a good solution in the internet. The problems I still encounter are mainly hardware problems and that's why I posted it in the Hardware section. The things that don't work correct right now are: 

- Not working hardware wireless button
- No multitouch gestures & disabling-feature on the Touchpad
- Bluetooth always turned on at start-up

I hardly have any Linux experience, but I got really much Windows and programming experience. I would really appreciate, when you could give me maybe a simple "type in"-solution, if possible, or more likely a hint or steps towards the solution. Thanks for your help.

Sincerly, Nico

---

### Post by Toz on 2013-10-18
Hello and welcome to the forums.

I also have this laptop and quite like it. 
> - Not working hardware wireless button
In addition to the hardware wireless button not working, out-of-the box, the brightness adjustment keys weren't working for me as well. I fixed both of these by using the "acpi-osi= acpi_backlight=vendor" kernel boot parameters. Here is how:
1. Open a terminal window and run the following command:
```
sudo -i gedit /etc/default/grub
```
...and enter your password when prompted.
2. Change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi= acpi_backlight=vendor"
```
...and save the file.
3. To commit the change, run:
```
sudo update-grub
```
...and reboot the computer.



> - No multitouch gestures & disabling-feature on the Touchpad
I actually use Xubuntu and there is a Mouse and Touchpad control panel that allows me to setup multi-touch and disable features. But I'm sort of old-school and don't generally use that fancy mouse stuff (point and click works just fine for me). Have a look through the Ubuntu settings to see if there is a similar control panel item. [Here is a reference document]("https://wiki.ubuntu.com/Multitouch").

> - Bluetooth always turned on at start-up
You can turn it off during the boot process by:
1. Open a terminal window and run the following command:
```
sudo -i gedit /etc/rc.local
```
...and just above the *exit 0* command, type:
```
rfkill block bluetooth
```
2. Save the file and it should be disabled on the next boot.



The one problem that I have not been able to fix is that when you plug in headphones into the combo headphone/microphone slot, the sound is very tinny. The last time I checked, the sound card in this system isn't yet supported by alsa. Regular use through the internal speakers is fine.



EDIT: You might also want to look at optimizing the system to use the SSD drive. [Here is a link ]("http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html")with more information and tweaks.

---

### Post by XpCA4NK on 2013-10-22
Great thanks for your tips. Every solution worked perfectly :) 

Sadly there aren't more touchpad-gestures supported since HP doesn't publish the Synaptics Gesture Suite Linux... like nobody does...

The problem with the soundcard seems to be fixed for me. The complete soundsystem works perfectly well. Maybe I got another soundcard(newer version of this Elitebook released under same name) or you have to update your system somehow...

---

### Post by Toz on 2013-10-22
Thanks for the update. 

About the soundcard, can you run the following command in a terminal window, choose the upload option when prompted, and post back the link that is generated (it will upload all the information about your alsa install and soundcard info to the alsa-project website and I can review and compare our systems):
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
Maybe I'm missing a setting or something that will help me fix my sound.
Thanks.

---

### Post by XpCA4NK on 2013-10-22
Ok, I uploaded the information. Here's the link: [http://www.alsa-project.org/db/?f=68b4a40b5fadfb141a6c057d1593ebbe728c08e1](http://www.alsa-project.org/db/?f=68b4a40b5fadfb141a6c057d1593ebbe728c08e1)

Hopefully it will help you to fix your problem :)

---

### Post by filtrehotmail on 2013-12-04
Thanks ! Your solution fixed the trouble perfectly for me too.

---

### Post by mattlach on 2014-07-25
Some good information in this thread.   I have a 9470m folio as well. 

Trying the suggested fixes.

I have found that in 14.04, the battery life is abysmal compared to Win7, and it doesn't appear to go to sleep properly when the lid is closed, continuing to drain power when not in use.

I just installed TLP and I hope this will help.

---

### Post by willmunoz on 2015-05-21
I tried this fix for the Wifi not display available access points in my list of available networks. I wanted to comment that the fix worked on my HP Elitebook folio 9470m with Ubuntu 15.04. Thank you again for display this fix.

---

