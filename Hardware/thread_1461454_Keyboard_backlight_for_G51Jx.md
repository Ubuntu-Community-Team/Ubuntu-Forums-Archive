---
title: "Keyboard backlight for G51Jx"
date: 2010-04-24
forum: Hardware
---

### Post by allwitchesdance on 2010-04-24
**Greeting all,**
Everyone who wants to get keyboard back-light functioning under Ubuntu 9.10 listen up. Attached you will find an archive with a patched asus-laptop module which supports keyboard backlight. You will need to:

[LIST=1]
[*]Uncompress the tarball
[*]Run build.sh to build the module
[*]Remove the old asus_laptop module (sudo rmmod asus_laptop)
[*]Insert the newly build module (sudo insmod asus_laptop.ko)
[/LIST]

As root run:
echo NUMBER > /sys/class/leds/asus\:\:kbd_backlight/brightness, where number is between 0 and 3 depending in the desired brightness. This tar-ball also includes kdbd.c which simplifies the process. Simply build it using gcc -o kdbl kdbd.c and the run as root:
    ```
./kdbl up 
```
or
    ```
./kdbl down 
```
depending on if you are turning the brightness up or down. I tested this code on ubuntu x64 9.10, but with 10.04 around the corner I hope this will work out of the box. I will provide limited support for this code, welcome to open source ;)
Peace, Tusk.

---

### Post by exodus on 2010-07-15
thanks buddy..

excellent fix.. works on my asus laptop like a charm...

g51jx-a1 to be precise and i'm running ubuntu 9.10 64 bit...

---

### Post by kthakore on 2010-08-24
Is there a way I can add this to a init.d script? Also will this be added to the official asus-laptop kernel module up stream?

---

### Post by scifi1901 on 2010-09-06
worked great on G73JH running 10.4 x64.  thanks!

---

### Post by Berbe on 2010-10-05
Hello everyone,

I own an Asus G51J Laptop and I had the exactly same problem as you. I solved it since a few hours and I wanted to share the solution.

I have managed to reassociate the original keys to higher/lower the keyboard brightness (Fn+F3 to lower it & Fn+F4 to higher it).

[LIST=1]
[*]Download the joined archive and uncompress it
[*]Move both the "acpi/events/keyboard_brightness*" files into the /etc/acpi/events/  directory.```
sudo mv acpi/events/keyboard_brightnessup /etc/acpi/events/
``````
sudo  mv acpi/events/keyboard_brightnessdown /etc/acpi/events/
```
[*]Move both the "acpi/key_brightness*.sh" files into the /etc/acpi/  directory.```
sudo mv acpi/key_brightnessup.sh  /etc/acpi/
``````
sudo mv acpi/key_brightnessdown.sh  /etc/acpi/
```
[*]Apply chmod 755 to both the /etc/acpi/key_brightness*.sh```
sudo chmod 755 /etc/acpi/key_brightnessup.sh
``````
sudo chmod 755 /etc/acpi/key_brightnessdown.sh
```
[*]Reload the acpid module```
sudo reload acpid
```
[/LIST]
Job done!
You have now recovered the usual behavior of the Fn+F3 & Fn+F4 buttons!

If you wish to understand acpi interruptions, I followed the [LaptopSpecialKeys from the Ubuntu Documentation]("https://help.ubuntu.com/community/LaptopSpecialKeys").

If you wish to go even further and manage keyboard backlighting depending on the power state, I recommend you to read [that article, made for power savings with Ubuntu on a Mac Pro]("http://ubuntuforums.org/showthread.php?t=1215928&page=2") (pay attention to the 99-savings script).
Some customization is mandatory, but you'll be able to automatically activate/deactivate keyboard illumination when on battery or not, from the even start of Ubuntu.

Have fun!

---

### Post by bupe on 2010-10-12
Great job Berbe! I can confirm that his works on G73JH running 10.10 x64, however there aren't as many states as in Windows 7 - brightness up has two states (lighter and stronger) while brightness down always disables the backlight - does not step back to the previous level. If I recall correctly then the Windows version has 3 steps of lighting levels and pressing Fn+F3 and Fn+F4 always goes up and down only one level.

Anyway this is still much better than not being able to control the backlight at all!

Many thanks for your contribution!

Cheers,
Peter

---

### Post by Berbe on 2010-10-12
As far as I remember, there have always been 3 states of backlighting on my Laptop... I didn't really noticed under Windows, but I think everythink worked well on the 9.x version of Ubuntu.

There must be a problem if ***Fn+F3*** always shut down your keyboard backlights.
Have a look to the .sh files, you'll see that the script reads the value from ***/sys/class/leds/asus::kbd_backlight/brightness*** which represents the current state of your keyboard illumination.

Write all the different values you may encounter (and try to write down all of them). Modify the script to switch from one to another (it simply rewrites the new value to the same interface to change the state).

These value seems to be hardware-specific, so it doesn't surprise me if they are different for each type of laptop.

Keep me posted! :P

---

### Post by adn258 on 2010-10-22
> **Berbe said:**
> Hello everyone,

I own an Asus G51J Laptop and I had the exactly same problem as you. I solved it since a few hours and I wanted to share the solution.

I have managed to reassociate the original keys to higher/lower the keyboard brightness (Fn+F3 to lower it & Fn+F4 to higher it).

[LIST=1]
[*]Download the joined archive and uncompress it
[*]Move both the "acpi/events/keyboard_brightness*" files into the /etc/acpi/events/  directory.```
sudo mv acpi/events/keyboard_brightnessup /etc/acpi/events/
``````
sudo  mv acpi/events/keyboard_brightnessdown /etc/acpi/events/
```
[*]Move both the "acpi/key_brightness*.sh" files into the /etc/acpi/  directory.```
sudo mv acpi/key_brightnessup.sh  /etc/acpi/
``````
sudo mv acpi/key_brightnessdown.sh  /etc/acpi/
```
[*]Apply chmod 755 to both the /etc/acpi/key_brightness*.sh```
sudo chmod 755 /etc/acpi/key_brightnessup.sh
``````
sudo chmod 755 /etc/acpi/key_brightnessdown.sh
```
[*]Reload the acpid module```
sudo reload acpid
```
[/LIST]
Job done!
You have now recovered the usual behavior of the Fn+F3 & Fn+F4 buttons!

If you wish to understand acpi interruptions, I followed the [LaptopSpecialKeys from the Ubuntu Documentation]("https://help.ubuntu.com/community/LaptopSpecialKeys").

If you wish to go even further and manage keyboard backlighting depending on the power state, I recommend you to read [that article, made for power savings with Ubuntu on a Mac Pro]("http://ubuntuforums.org/showthread.php?t=1215928&page=2") (pay attention to the 99-savings script).
Some customization is mandatory, but you'll be able to automatically activate/deactivate keyboard illumination when on battery or not, from the even start of Ubuntu.

Have fun!


I just wanted to say thank you very much simple as moving over these terminal commands.  Awesome :) G51J is a great laptop I am using one as well. 

Peace  Had to say thanks!

---

### Post by delca85 on 2010-11-23
Hi!
I have an Asus G73JWA1, yesterday I installed Ubuntu 10.10 and the I follow the guide above to make fn key keyboard working. The keys worked immediately, but when I reboot the system give me this error: Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block (0,0) .
Now I have installed again and I don't know if make that thing again.
What do you suggest to me? Do you think it's possible the reason of kernel panic is this? 
Thank you very much!

---

### Post by nakednous on 2010-12-08
Hi all,

What about the new asus models? I'm planning to buy the G53JW-A1, but it depends a bit on this issue.  This model should be similar than the G73JWA1. @delca, did you find a workaround for your it? Please post on this.

Cheers

---

### Post by delca85 on 2010-12-08
Yes nakednous, I have followed the guide again ad everything works fine.

---

### Post by W29 on 2010-12-16
Hmm. Doesn't seem to work for me.
I unzipped the tar.gz file.
Then I put the files in /usr/bin. I ran build.sh (had to change the access rights).
But then it comes up with an error:
```
/usr/bin/asus-laptop.c:1371: error: too few arguments to function &#8216;backlight_device_register&#8217;
```What am I doing wrong?

w29

---

### Post by onewing on 2011-01-26
@ Berbe: Thank you! Simple, consise. Excellent instruction set. :KS

---

### Post by ramrom on 2011-02-23
thanks a lot... works like a charm...

---

### Post by piloto on 2011-03-07
Hello guys, sorry for my poor english.

I fixed my problem with this   [https://launchpad.net/asus-keyboard-backlight](https://launchpad.net/asus-keyboard-backlight)

The best part is that you can install the fix like a package with few clicks.
It is working very well in my asus G60Jx with Ubuntu 10.10 64 bits. 

I hope I've helped somebody.

---

### Post by jtr010 on 2011-06-25
Berbe, 

 Thanks for the great instructions! Works on G51J!

Jack

---

### Post by W29 on 2011-10-22
The problem is solved in the new Ubuntu (11.10).

---

### Post by Berbe on 2011-10-27
> **W29 said:**
> The problem is solved in the new Ubuntu (11.10).
I would hardly say that...

I just tested that new 11.10 and my keyboard backlight is one amongst a lot of things that work pretty badly!

I haven't tested my fix on this new 11.10 and I don't know if the ACPI management has been changed so far.

I am really considering moving out to Debian once again... Back to basics!
That Squeeze appeals me a lot.

---

### Post by riko121212 on 2012-10-16
hi :)
i have a small problem whit my G51jx. When i run the file key_brightness  up or down.sh  as root everytyng is ok. The brightness of keyboard is  working. But like user show me:
./key_brightnessdown.sh: line 15: /sys/class/leds/asus::kbd_backlight/brightness: Permission denied
anybody to know soothing about that. 
thanks in advance

---

