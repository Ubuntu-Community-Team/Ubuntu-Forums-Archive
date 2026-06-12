---
title: "brightness settings for toshiba satellite on dapper"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by musikgoat on 2007-02-22
Hello all,  I think this a first post.   Been silently using it and reading alot on configurations and such, this is the first time I've needed help that I cant find.  

My Specs:  I installed and fully updated dapper on A105-S4004 Toshiba Satellite.  
I have the system dual-booting ubuntu and XP.

I'm trying to figure out a way to lower some of the power consumption in ubuntu, one way that I can think of is by lowering the lcd brightness.

I cannot use the Fn + F6/F7, and i haven't found anything in the general settings.  I think that its because I'm not running the right driver.  

[pre]>lspci
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
[/pre]

In windows, the device shows as an intel 945GM express chipset.

any recommendations?

---

### Post by nachotronics on 2007-02-28
I had the same problem, the best solution i found was blacklisting the "video" module, this can be done by typing the following into terminal:
```
echo 'blacklist video' | sudo tee -a /etc/modprobe.d/blacklist
```
This will prevent the "video" module from getting loaded on system startup, so you need to reboot for the changes to make effect.

I tried searching what that module was intended for, but couldn't find much information, i only know it has something to do with video and acpi. I have done this almost a month ago, and i haven't had any problems or noticed any other changes besides the ability for adjusting brightness.

Hope this helps.

---

### Post by musikgoat on 2007-02-28
Thank you very much.  I followed your code, and verified that it was in the blacklist, but I still cannot  get any settings.  

```
 tim@COMPY386L:~$ cat /etc/modprobe.d/blacklist
 # This file lists those modules which we don't want to be loaded by
 # alias expansion, usually so some other driver will be loaded for the
 # device instead.
 
 # evbug is a debug tool that should be loaded explicitly
 blacklist evbug
 
 # these drivers are very simple, the HID drivers are usually preferred
 blacklist usbmouse
 blacklist usbkbd
 
 # replaced by e100
 blacklist eepro100
 
 # replaced by tulip
 blacklist de4x5
 
 # causes no end of confusion by creating unexpected network interfaces
 blacklist eth1394
 
 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
 # hardware on its own (Ubuntu bug #2011, #6810)
 blacklist snd_intel8x0m
 
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
 blacklist i2c_i801
 blacklist video 
```

rebooted, and cannot Fn + F6/F7  or find anything anywhere.

was there something that I missed?


Again, thanks for your help.

---

### Post by krrh on 2007-03-09
Give this a shot:

First:

cat /proc/acpi/video/VGA/LCD/brightness

The output will be a series of numbers.  These represent brightness levels.  Next:

echo 10 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness

Replace "10" with one of the numbers listed via the first command.  

I found this trick [here]("http://www.orangegroove.net/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/"). 

Good luck!

---

### Post by musikgoat on 2007-03-14
Thanks for that suggestion.   I ran into an issue though of not having a video section in /proc/acpi

```
tim@COMPY386L:/home/tim# ls -a /proc/acpi
.           battery              event   info            sony
..          button               fadt    power_resource  thermal_zone
ac_adapter  dsdt                 fan     processor       wakeup
alarm       embedded_controller  hotkey  sleep           wmi

```

I’m up to date on BIOS revisions (Pheonix v5.10) from Toshiba, I have a Satallite A105-S4004.  I have 
root@COMPY386L:/home/tim# cat /proc/acpi/info 
version:                 20060707

getting versions, acpi is at 0.09-1,  acpid is at 1.0.4-5ubuntu4, and acpi-support is at 0.90.   I also installed acpitool and that sounded promising.

tim@COMPY386L:~$ acpitool -l 1
Changing LCD brightness level is only supported on Toshiba or Thinkpad laptops.

heh, well then why isn't it working.


I'm open to anyone's suggestions.  I'm fishing here.

-tim

---

### Post by Azilla on 2007-03-14
You might have to remove *video* from the blacklist file. Once you reboot, the folder should be there.


Also, you can try and type this command -> sudo modprobe video
Just to see if it will load for the time being without you having to reboot.


:)

---

### Post by xyz on 2007-03-14
Hi,
Back on Dapper, I went System > Pref > Power Management and used the slider to lower brightness. I really miss that now that I use Edgy!

Also, in a command line:
```
sudo echo "brightness:1" > /proc/acpi/toshiba/lcd
```
where  1  is what you want to change. I think highest was 8 if I remember right.

I have a Toshiba Satellite A 40 so this may also work for you....hopegully!

You may need to tun this as well:
```
sudo chmod 777 /proc/acpi/toshiba/brightness
```

---

### Post by musikgoat on 2007-03-14
> **Azilla said:**
> You might have to remove *video* from the blacklist file. Once you reboot, the folder should be there.

Sweet, your right.  Now I have full access!!  now to set up some scripts to auto adjust on battery levels.    

Yey!!   Thanks everyone.

---

### Post by jfhian on 2007-04-19
> **krrh said:**
> Give this a shot:
I found this trick [here]("http://www.orangegroove.net/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/"). 


The URL has changed, the link should be [this]("http://slu.ms/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/"). It redirects in the meantime. Cheers.

---

