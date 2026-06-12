---
title: "Laptop screen dimming problem (hardy)"
date: 2008-04-23
forum: Hardware
---

### Post by treb0r on 2008-04-23
Hi All,

I upgraded to Hardy beta a few weeks ago after using Gutsy since release. I have a novatech rasor pro laptop ([http://www.novatech.co.uk/novatech/specpage.html?NNB-600](http://www.novatech.co.uk/novatech/specpage.html?NNB-600)) and most things are working nicely.

The one major problem that I've found is that my screen now dims to the lowest setting on reboot, and I have to manually adjust it every time. To make things worse, the brightness function keys no longer work. None of this was a problem in gutsy.

The laptop has an intel core 2 duo cpu and Intel GMA X3100 Graphics.

 I realise there are a few posts about similar issues on other laptops, but they all seem to be using different chipsets to mine.

Any help would be greatly appreciated.

treb0r

---

### Post by neonflx on 2008-04-25
i am having the same issue with an ASUS M50SV-A1 laptop, screen brightness is just too low to begin with, i tried using the nvidia panel after installing the drivers but it just don't work properly as the brightness is so low to begin with that adjusting brightness/contrast/gamma thru it does not work

---

### Post by arkalon on 2008-04-25
Same problem, 

Acer Aspire 5710
Moible Intel GraphicsMedia Accelerator 950 (256MB)
Hardy (Final release)


A problem I didn't have with 7.10

---

### Post by HunterThomson on 2008-04-25
I had the same problem that is why I went back to 7.10... However, I talked to some people on the Ideapad thread and they say they don't have the problem but they are using the 32bit OS I use the 64bit and the launchpad bug report said it is a bug in the 64bit kernel. It is not just Ubuntu but a lot of Distro's and has been confirmed and is on the fix list and has been assigned to a developer.

---

### Post by treb0r on 2008-04-25
Hi Chaps,

Well, as far as I know, I'm using the 32bit kernel.

I'm sure it is a kernel issue though, and I'm pleased to hear I'm not the only one seeing this.

Let's hope we get a fix soon. On a positive note, everything else seems just peachy - compiz is finally solid as a rock on this machine.

treb0r

---

### Post by haseeb on 2008-04-25
guys,

i have got a silly solution.

* set your screen saver activation time to minimum
* wait until your screen saver starts.
* wake your laptop up
* you will see your brightness just FINE.

:guitar: its kinda weird. but it seems this is the only solution by now.

---

### Post by treb0r on 2008-04-25
Hi Haseeb,

Ok, I'll check that out.

Still looking for a PROPER fix though ;)

---

### Post by smallerdemon on 2008-04-25
Just weighing in with yet another one it is happening on.

Mine happened after the Hardy Heron upgrade.

Dell Latitude D600

In addition to the screen dimming issue, mine makes a beautiful "pop" of "click" from the speakers randomly.

I see the brightness indicator coming and going all the time too.  Crazy.

---

### Post by smallerdemon on 2008-04-25
Aw. :( It did NOT work for mine.

Oh well.  Back to Gutsy Gibbon.

---

### Post by smallerdemon on 2008-04-25
Here is what I found with my D600.

Hardy Heron changed and left permanent the on board BIOS brightness settings.

Battery was set to about 1/3 brightness.
AC was set to ZERO brightness.

Changing it in the BIOS did get me back to full screen brightness on reboot.

The constant clicking/popping noise, however, has yet to go away.  Clearly something is going on in the background constantly.  All system sounds are turned all.

We'll see how this goes and if the clicking/popping goes away.  If not, then yes, back to Gutsy Gibbon.

---

### Post by jonallport on 2008-04-25
OK, here's my workaround for my HP nx6125:

CTRL-ALT-F1 to swith to a TTY, no need to login
Use hotkey to change brightness (fn-F9/F10)
CTRL-ALT-F7 to switch back to GDM

It'll to me until I work something better out!

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by neonflx on 2008-04-25
> **haseeb said:**
> guys,

i have got a silly solution.

* set your screen saver activation time to minimum
* wait until your screen saver starts.
* wake your laptop up
* you will see your brightness just FINE.

:guitar: its kinda weird. but it seems this is the only solution by now.


it does not work for me , i have tried another distro to see and i did not have any issues with screen, tho i must have ubuntu :lolflag: , no other distro will do :twisted:

---

### Post by neonflx on 2008-04-25
> **']Nbx*cmD[ said:**
> ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:



This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

thanks your findings solved my problem i have the M50SV, thanks again

---

### Post by haseeb on 2008-04-25
Yet another "Temporary solution"

Right click on the task bar (or top panel, i dont know the exact name :-( ). And select **Brightness Applet** and drag it to the task bar.

Click the brightness applet icon. And set your brightness.

The problem of this solution is, change of brightness is not permanent.Every time you start your laptop you have to set the brightness from the bar.

Thanks.

[IMG]http://farm3.static.flickr.com/2137/2441995210_0518169eed_o.png[/IMG]

---

### Post by dtgolder on 2008-04-27
> **smallerdemon said:**
> Just weighing in with yet another one it is happening on.

Mine happened after the Hardy Heron upgrade.

Dell Latitude D600

In addition to the screen dimming issue, mine makes a beautiful "pop" of "click" from the speakers randomly.

I see the brightness indicator coming and going all the time too.  Crazy.
I'm getting the same issue with a Dell B120--fine in Gutsy--upgrade to Hardy and now the screen changes brightness on its own (with the popping sound). VERY annoying.

---

### Post by ziofil on 2008-04-29
I found the solution for my MBP: right click on the battery indicator on the top right corner, then on 'properties'.
in the 'general' tab deselect the option 'use ambient light to set screen brightness'.
it worked for me.

---

### Post by nawitus on 2008-04-29
I'm having the same problem with HP laptop..

And I found a fix for it.
1. Locate a brightness file
ls /sys/class/backlight/*/brightness
You can then try "sudo echo 10 > <brightness file>" to see which one of them works.
2. Then just add the command to any boot script, I added it to the same file as the hard-drive fix:
/etc/acpi/start.d/99-hdd-spin-fix.sh, the hdparm line is obviously not required
```

#!/bin/sh
hdparm -B 255 /dev/sda
echo 10 > /sys/class/backlight/acpi_video0/brightness

```
The maxium brightness might not be 10, I read it can also be 7 so test it out.

---

### Post by jcrow on 2008-04-29
I have the same problem, but with a twist. On startup the screen is dim. I can use the function keys to increase brightness, but if I resize the window running virtualbox, the screen dims again. I have a dell D530 laptop with intel graphics.

---

### Post by suoko on 2008-04-30
same problem on acer 5715Z

---

### Post by ajv2003 on 2008-04-30
I have HP dv2500t with nVidia 8400M GS, 2.2 Core 2 duo, 3 Gig RAM, the works and that is not an issue. I did a clean install.

---

### Post by jcrow on 2008-05-01
I don't know what happened, but the problem solved itself. I have no idea other than everything is fine now.

---

### Post by lecter255 on 2008-05-01
> **nawitus said:**
> I'm having the same problem with HP laptop..

And I found a fix for it.
1. Locate a brightness file
ls /sys/class/backlight/*/brightness
You can then try "sudo echo 10 > <brightness file>" to see which one of them works.
2. Then just add the command to any boot script, I added it to the same file as the hard-drive fix:
/etc/acpi/start.d/99-hdd-spin-fix.sh, the hdparm line is obviously not required
```

#!/bin/sh
hdparm -B 255 /dev/sda
echo 10 > /sys/class/backlight/acpi_video0/brightness

```
The maxium brightness might not be 10, I read it can also be 7 so test it out.

hey i try your method, but the folder /sys/class/backling/*/brightness is empty! i have a hp dv2000 with nvidia graphics. basically, I can't adjust the birghtness of my screen at all. when it's plugged in, the screen is bright, when not, it's as dim. i tried the brightness adjustment knob and nothing happens. i also tried fn+f8 and still nothing happens. any idea?

---

### Post by g_damian on 2008-05-02
solution for startup brigtness:
[LIST=1]
[*]grab my script from [http://dmn.jogger.pl/2008/05/02/ubuntu-8-04-i-jasnosc-lcd-rozwiazanie/]("http://dmn.jogger.pl/2008/05/02/ubuntu-8-04-i-jasnosc-lcd-rozwiazanie/")
[*]save it
[*]check if line "DIR=..." is good for you, customize it
[*]add path to the script to /etc/rc.local before "exit 0"
[*]now startup brigtness is that from top of the script. you can change it if you want
[/LIST]
**BUT:** laptop keys doesn't work when you do this. to modify brightness go to terminal and type:
```
sudo /path/to/script x
```
where *x* is brightness, usually from 0 (min) to 13 or 15 (max).

---

### Post by omnibot on 2008-05-02
Sorry, a bit new to this but can I have step 4 of g_damian's post explained to me?

---

### Post by g_damian on 2008-05-02
go to terminal (applications/accesories/terminal), paste:
```
sudo gedit /etc/rc.local
```
type your password, put this line in it, then save. that's all :)

---

### Post by omnibot on 2008-05-02
type my password, put in the line to the directory from step 3? 

am i supposed to save the script from your link to any place particular?

I apoligize, I am less than 24 hours into Ubuntu and I'm rather confused

---

### Post by omnibot on 2008-05-04
bump?

---

### Post by treb0r on 2008-05-06
Thanks for posting that script, but I'm waiting for a *proper* fix (no offence ;) ).

I'm hoping that a kernel update in the not too distant future will sort us all out.

---

### Post by mahousaru on 2008-06-02
> **jcrow said:**
> I have the same problem, but with a twist. On startup the screen is dim. I can use the function keys to increase brightness, but if I resize the window running virtualbox, the screen dims again. I have a dell D530 laptop with intel graphics.

No solution from me, but just to let you know my Asus F9E with a x3100 GPU has the same problem with VBox too...

---

### Post by jovanie01 on 2008-06-03
hey, i installed ubuntu on my asus A8Eseries Duo T7100, the screen has become so dimmed. i tried to remove ubuntu from my notebook and return to my xp os but the problem was not resolved. im already on my xp sp2. please help me resolve my problem,, i know just a little on computers...

---

