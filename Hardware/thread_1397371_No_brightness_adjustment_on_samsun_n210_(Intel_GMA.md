---
title: "No brightness adjustment on samsun n210 (Intel GMA 3150)"
date: 2010-02-03
forum: Hardware
---

### Post by vimm on 2010-02-03
Hello folks,

I installed Ubuntu Remix on my netbook samsung n210. Most of features work fine (some don't OBVIOUSLY) but there is one annoying problem - BRIGHTNESS. I cannot adjust it and unfortunately it's default to the lowest. It's very difficult to work on it.
Of course problem is deeper then invalid key bindings. 

It looks like default video driver doesn't support brightness correction for my card. I have nothing related to it in my /proc/acpi or /sys/. "Randr" doesn't know brightness option as well.

My video card is: Intel GMA 3150

Does enybody know how to fix it? I just want to use 90% brightness do I have to look for different drivers or something?

Thank you.

---

### Post by mikewhatever on 2010-02-03
Check out this thread: [http://ubuntuforums.org/showthread.php?t=1313390](http://ubuntuforums.org/showthread.php?t=1313390).

Various options seem to have worked for some. The title is misleading in saying 'Dell laptops', as if Dell had some special hardware made only for it's products.

---

### Post by vimm on 2010-02-03
Thank you for this link it helped in a way... Amendments to grub config only ******** it up however I discover I can change my brightness on grub screen and it will persists for the whole ubuntu session :D

---

### Post by mikewhatever on 2010-02-03
Are you saying that brightness keys work at Grub menu, but not after?
It's always a good idea to backup any config file before editing, in this case /etc/default/grub. In case the change makes the system unbootable, you can restore the file to its default.

```
sudo cp /etc/default/grub /etc/default/grub-backup
```

---

### Post by vimm on 2010-02-03
I wouldn't say "it works in GRUB" it's rather "it works outside UBUNTU".

---

### Post by NB305 on 2010-02-05
I have a Toshiba NB305 with Intel GMA3150 and the screen brightness does not work when I install 9.10.

I've tried to install 9.04 and the screen brightness worked, but the resolution was screwed up (800x600).

Anyway I've gone thru most of the remedy that was posted in the forum already. Any help would be appreciate.

---

### Post by lucas.andion on 2010-02-20
+1 Same thing here.

Any other ideas on how to fix this other while we wait for a decent driver release?

---

### Post by lucas.andion on 2010-02-23
Tested new intel drivers [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) with 2.6.32 kernel and it doesn't work.

Tested Ubuntu Lucid daily build from 22/02/2010 and doesn't work either.

---

### Post by wcale on 2010-02-24
Hi,
you can adjust brightness level by sending values directly to device, by setpci:

setpci -s 00:02.0 f4.b=ff

where 00:02.0 is the device address returned by lspci,and ff is a hexadecimal value <0,ff>. I have n210 running Debian, works well :)

Because it wasn't easy to control brightness this way, I've written a program that adjusts brightness, you can download source from here:
[ftp://x.servebeer.com/bright.c](ftp://x.servebeer.com/bright.c)
//Edit: Port changed from 51300 to default ftp 21

or here:
[http://info.wsisiz.edu.pl/~sieluzyc/bright.c]("http://info.wsisiz.edu.pl/%7Esieluzyc/bright.c")

It's a _very simple_ program, but it allows you to increase/decrease brightness by predefinied step, check actual brightness level and set level to a specific value.
It uses the same method that setpci does (write to file in /sys), so plz remember this can be dangerous - use at your own risk.
App does not assign any key shourtcuts, you have to do this manually.

Wcale

---

### Post by lucas.andion on 2010-02-24
Works perfectly on Ubuntu netbook remix 9.10 & samsung n210, thank you very much!

PS: I still wonder why Fn + UP & DOWN keys are not mapped as Fn + RIGHT LEFT do :/ any clues?

---

### Post by calyth on 2010-02-25
I've tried that GRUB config and it doesn't work.

---

### Post by pramtung on 2010-02-28
[@wcale]("http://ohioloco.ubuntuforums.org/member.php?u=1024176")
Man, you really save me.. 
You are my hero. Your trick work on my laptop.. :p

by the way, what is the f4.b thing, I don`t quite understand what's that for..

---

### Post by wcale on 2010-03-02
thanks :D

f4 is register address (= /sys/devices.../config offset) in hexadecimal. As you can see in program source, it just alters 244th byte. (f4 in hex = 244 dec)
.b tells setpci to change only one byte.

@lucas.andion
As far as I know, Fn+UP/DOWN are mapped by acpi. Because acpi doesn't recognise our laptop's acpi interface properly, it blocks these keys.

@calyth
Have you tried setpci method?

---

### Post by mavdlind on 2010-03-09
Hi there,
I tried the setpci trick but I get the following message:
Cannot open /sys/bus/pci/devices/0000:00:02.1/config

Any clues what to do next?
Cheers
mavdlind

---

### Post by wcale on 2010-03-10
There can be many reasons. First, are you doing it as root? Try
```
sudo setpci -s 00:02.0 f4.b=ff
```
Second thing - are you sure 00:02.1 is proper device address? I've checked it on two n210 and it was 00:02:0...

---

### Post by mavdlind on 2010-03-12
You're right, I made a confusion between two related devices....
Works brilliantly (no bad punt intended) now
Thanks
mavdlind

---

### Post by fedira on 2010-04-21
> **wcale said:**
> Hi,
you can adjust brightness level by sending values directly to device, by setpci:

setpci -s 00:02.0 f4.b=ff

where 00:02.0 is the device address returned by lspci,and ff is a hexadecimal value <0,ff>. I have n210 running Debian, works well :)

Wcale


Hi @wcale:

Thanks for providing this solution which seems to work for a number of people. I'd love to try it, but I need a little more info.

1. When I run ```
lspci
```, which device address do I need? Display controller, or VGA-compatible controller?

2. I like to try to understand the commands I'm running before I run them. I get that ```
setpci -s 00:02.0
``` restricts the setpci utility to configure only devices within that domain. (I think.) What does ```
f4.b=ff
``` do? Is ff the brightest (like 00=black and ff=white)?

Thanks for your help!

---

### Post by wcale on 2010-05-03
Hi @fedira,
1. It's VGA compatible controller.
2. Yes. ff is the highest brightness level, 00 is brightness off. f4.b described in post #13

---

### Post by yoyobeni on 2010-05-04
@wcale
thanks a lot it was really helpful

---

### Post by Jan Pieter on 2010-05-29
Thanks wcale. The trick with
sudo setpci -s 00:02.0 f4.b=ff
worked for me too on my Samsung N210 with Ubuntu 10.4

---

### Post by Fred Ora on 2010-06-27
Here's another way for those still searching.  All of the setpci answers say use at your own risk, I'm not sure what the danger is, but after much experimenting I got mine working this way without that setpci script.  I have a N150, but it should be the same.

Here's what I did:

in synaptic package manager go to settings, go to settings>repositories and chose other software tab.  
Add the following repository:  ppa:voria/ppa
click reload on the main package manager screen then search for samsung
check the boxes by samsung-tools AND samsung-backlight
click apply and load the packages.  close package manager and reboot

in the terminal run:
sudo gedit /lib/udev/rules.d/95-keyboard-force-release.rules
in the samsung section you will see a line with *N130*|*N140* etc.  add |*N150* there
also do the same for:
sudo gedit /lib/udev/rules.d/95-keymap.rules

substitute your model for N150 above if it isnt already there.


The first part loads the samsung tools and backlight utility.  this will also get some of your other function keys working.  you can see the mappings in system>samsung tools preferences.  
The second part gets the mappings working for the fn-up and fn-down keys.  it also keeps the fn-keys from going crazy by forcing them to release after being pressed.

Hope this helps!

---

### Post by hellrazor4ever on 2010-07-12
> **wcale said:**
> Hi,
you can adjust brightness level by sending values directly to device, by setpci:

setpci -s 00:02.0 f4.b=ff

where 00:02.0 is the device address returned by lspci,and ff is a hexadecimal value <0,ff>. I have n210 running Debian, works well :)

Because it wasn't easy to control brightness this way, I've written a program that adjusts brightness, you can download source from here:
[ftp://x.servebeer.com/bright.c](ftp://x.servebeer.com/bright.c)
//Edit: Port changed from 51300 to default ftp 21

or here:
[http://info.wsisiz.edu.pl/~sieluzyc/bright.c]("http://info.wsisiz.edu.pl/%7Esieluzyc/bright.c")

It's a _very simple_ program, but it allows you to increase/decrease brightness by predefinied step, check actual brightness level and set level to a specific value.
It uses the same method that setpci does (write to file in /sys), so plz remember this can be dangerous - use at your own risk.
App does not assign any key shourtcuts, you have to do this manually.

Wcale

Worked perfectly for my Samsung N220 Mito under Ubuntu 10.04!
Thank you so much!!!

---

### Post by joyfox on 2010-07-17
> **wcale said:**
> Hi @fedira,
1. It's VGA compatible controller.
2. Yes. ff is the highest brightness level, 00 is brightness off. f4.b described in post #13

Very good information!
Thanks a lot.

Joy

---

### Post by alainjackson on 2010-07-17
@Fred Ora

Excellent advice!

The screen brightness function buttons on my Samsung N220 weren't working at all. 

I followed your instructions for my N220 and now the brightness keys are working and the majority of the other function keys too. 

The setpci method was also working.

Thanks!

---

### Post by Mawh on 2010-07-21
Worked perfectly on my N210. Thank you Fred ! :)

---

### Post by Tony221268 on 2010-08-04
Did this but for this step "check the boxes by samsung-tools" I got the error depends "xbindkeys but it is not installable". This is for an NC10 running 10.0.4 Netbook version. The backlight package installed OK and I can adjust the brightness.
 
Still bugs me though...any idea what this is?

---

### Post by utilitytrack on 2010-08-06
Hello all,

look in here: [http://ubuntuforums.org/showthread.php?p=9677094#post9677094]("http://ubuntuforums.org/showthread.php?p=9677094#post9677094")

PS
Don't forget that only root can do this.

---

### Post by postadelmaga on 2010-08-15
Try this ppa (Voria)
[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

It had support for hotkey on Samsung netbook:popcorn:

---

### Post by Kimasu on 2010-09-02
> **Fred Ora said:**
> Hope this helps!

Worked perfectly for my N230. Thank you so much!

---

### Post by highflyer100 on 2010-09-05
Installed Lucid Netbook on my Samsung N150. Had the same problem with the function keys.
Added the ppa:voria/ppa repository and followed the instructions in post #21. After reboot all function keys worked properly. I did not have to edit anything. Thanks Fred Ora! :D

---

### Post by pavolzetor on 2010-09-05
I think, PPA content to control backlight should be merged into ubuntu and upstream

---

### Post by OrangeGrey on 2010-10-01
Had the brightness control problem on my N150 under 10.04. Followed #21 post, found out with "sudo gedit ..." that samsung N150 was already set up and no changes at all were necessary, and after reboot brightness control with function key worked perfectly. Thanks

---

### Post by Shadyabhi on 2010-11-06
> **wcale said:**
> Hi,
you can adjust brightness level by sending values directly to device, by setpci:

setpci -s 00:02.0 f4.b=ff

where 00:02.0 is the device address returned by lspci,and ff is a hexadecimal value <0,ff>. I have n210 running Debian, works well :)

Because it wasn't easy to control brightness this way, I've written a program that adjusts brightness, you can download source from here:
[ftp://x.servebeer.com/bright.c](ftp://x.servebeer.com/bright.c)
//Edit: Port changed from 51300 to default ftp 21

or here:
[http://info.wsisiz.edu.pl/~sieluzyc/bright.c]("http://info.wsisiz.edu.pl/%7Esieluzyc/bright.c")

It's a _very simple_ program, but it allows you to increase/decrease brightness by predefinied step, check actual brightness level and set level to a specific value.
It uses the same method that setpci does (write to file in /sys), so plz remember this can be dangerous - use at your own risk.
App does not assign any key shourtcuts, you have to do this manually.

Wcale
Even works perfectly on my ArchLinux64.install. Thanks for sharing..

---

### Post by MASEngr on 2010-11-11
Awesome, awesome, awesome!  Fred's post gives brightness control to the NF210, the new dual-core one.  It also adds all Fn key functions!  

This fix adds all FN keys to Ubuntu and allows for release action, meaning the keyboard will no longer stay stuck.   It works on UNR 10.04 and 10.10.  You must reboot after editing the configuration lines. 

Keys that work are:
Sleep
Battery Life
Webcam toggle
Backlight toggle
Mute
Fan mode
Wifi antenna toggle
Touchpad toggle
Number Lock
Sound up / down
brightness up / down
home


You will have to add:
|*NF210*|

into the lines of models in
 /lib/udev/rules.d/95-keyboard-force-release.rules

and then add the line:
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="NF210", RUN+="keymap $name samsung-nf210"

(Copy and paste the line above it, then just change the model to NF210)

into /lib/udev/rules.d/95-keymap.rules

This does not yet fix the network resume after sleep, and no, turning off wireless with Fn-F9 doesn't do it. :(

---

### Post by glósóli on 2010-11-16
> **MASEngr said:**
> Awesome, awesome, awesome!  Fred's post gives brightness control to the NF210, the new dual-core one.  It also adds all Fn key functions!  

This fix adds all FN keys to Ubuntu and allows for release action, meaning the keyboard will no longer stay stuck.   It works on UNR 10.04 and 10.10.  You must reboot after editing the configuration lines. 

Keys that work are:
Sleep
Battery Life
Webcam toggle
Backlight toggle
Mute
Fan mode
Wifi antenna toggle
Touchpad toggle
Number Lock
Sound up / down
brightness up / down
home


You will have to add:
|*NF210*|

into the lines of models in
 /lib/udev/rules.d/95-keyboard-force-release.rules

and then add the line:
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="NF210", RUN+="keymap $name samsung-nf210"

(Copy and paste the line above it, then just change the model to NF210)

into /lib/udev/rules.d/95-keymap.rules

This does not yet fix the network resume after sleep, and no, turning off wireless with Fn-F9 doesn't do it. :(

totally agree, awesome solution _Fred Ora_!!

EVERYTHING as posted above works; the only problem (that was actually THE problem for which I was looking for a solution) is that the brightness controls still don't work and this is pissing me off. (and actually the Eur button disable/enable the webcam...I would use more often the EUR symbol than disabling my webcam, but whatever..)
At least now, as stated above, the keyboard doesn't hang if I press them by accident; but still I would like to control the brightness with the keys instead of doing sudo smartdimmer everytime...

but the network resume after sleep is charmingly working (though even before the patches :P)

any idea??
my samsung is a Q320

thanx!

---

### Post by lavanchy on 2010-11-18
Try this:

sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-tools samsung-backlight
sudo reboot

regards
carlos



> **vimm said:**
> Hello folks,

I installed Ubuntu Remix on my netbook samsung n210. Most of features work fine (some don't OBVIOUSLY) but there is one annoying problem - BRIGHTNESS. I cannot adjust it and unfortunately it's default to the lowest. It's very difficult to work on it.
Of course problem is deeper then invalid key bindings. 

It looks like default video driver doesn't support brightness correction for my card. I have nothing related to it in my /proc/acpi or /sys/. "Randr" doesn't know brightness option as well.

My video card is: Intel GMA 3150

Does enybody know how to fix it? I just want to use 90% brightness do I have to look for different drivers or something?

Thank you.

---

### Post by Dustin Bess on 2010-11-20
...wow i so dont know what that is ...   =( so i guess im stuck with a dark screen

---

### Post by Dustin Bess on 2010-11-20
Lavanchy you are my hero! lol thank you ,this worked perfectly for me

---

### Post by EricDP on 2010-12-26
> **MASEngr said:**
> This does not yet fix the network resume after sleep, and no, turning off wireless with Fn-F9 doesn't do it. :(
Resume from sleep actually works fine for me on my new NF210, and the brighness controls work when I boot from live USB, but they don't work when I boot from hard drive. I'm thinking a patch broke it since the only difference between the USB and hard drive is I patched the OS on the hard drive.

I'm torn between re-installing again (since it's a new machine) or just leaving it for a while - it's actually a Christmas present for my wife so I think I need to just leave it working almost 100% and let her play with it for a while.

---

### Post by EricDP on 2010-12-26
Well I went for the re-install, got it all working, then selected just security updates (no recommended updates) and that also broke brightness control... I guess I'll re-install again and start stepping through them one by one (over a hundred) and try to see which one breaks it. :(

---

### Post by EricDP on 2010-12-26
OK, I've narrowed this down to kernel version and samsung-backlight module. It works fine with 2.6.35-22-generic, but it stops working with 2.6.35-24-generic. I'm running the i686 version. I've confirmed the module builds and loads with -24, but it doesn't do anything.

Other than this one thing, this netbook (Samsung NF210) seems to be working perfectly with Ubuntu Netbook 10.10.

EDIT: Solved by the method in this thread: [http://www.voria.org/forum/viewtopic.php?f=3&t=625](http://www.voria.org/forum/viewtopic.php?f=3&t=625)

---

### Post by Mawh on 2010-12-27
Awesome man, I'm trying that fix right away. I'll tell you if it works for me (no reason that it does not though).

---

### Post by Mawh on 2011-01-01
Thank you, it works... almost ! I'm having a weird issue, which I detailed in this post on the same thread that you linked : [http://www.voria.org/forum/viewtopic.php?p=4465#p4465](http://www.voria.org/forum/viewtopic.php?p=4465#p4465)

---

### Post by popcornman on 2011-01-03
> **wcale said:**
> Hi,
you can adjust brightness level by sending values directly to device, by setpci:

setpci -s 00:02.0 f4.b=ff

where 00:02.0 is the device address returned by lspci,and ff is a hexadecimal value <0,ff>. I have n210 running Debian, works well :)

Because it wasn't easy to control brightness this way, I've written a program that adjusts brightness, you can download source from here:
[ftp://x.servebeer.com/bright.c](ftp://x.servebeer.com/bright.c)
//Edit: Port changed from 51300 to default ftp 21

or here:
[http://info.wsisiz.edu.pl/~sieluzyc/bright.c]("http://info.wsisiz.edu.pl/%7Esieluzyc/bright.c")

It's a _very simple_ program, but it allows you to increase/decrease brightness by predefinied step, check actual brightness level and set level to a specific value.
It uses the same method that setpci does (write to file in /sys), so plz remember this can be dangerous - use at your own risk.
App does not assign any key shourtcuts, you have to do this manually.

Wcale

Hi everyone. I too am having a problem adjusting brightness on my Toshiba A665D-S6059 laptop. I made a [_thread_]("http://ubuntuforums.org/showthread.php?t=1656997") recently, but it got no hits. However after reading that it was the VGA controller I needed, I ran these two commands...
```
root@John-Laptop:/home/john# setpci -s 01:05.0 f4.b=44
root@John-Laptop:/home/john# setpci -s 01:05.0 f4.b=00
root@John-Laptop:/home/john# setpci -s 01:05.0 f4.b=15
root@John-Laptop:/home/john# setpci -s 02:00.0 f4.b=12
root@John-Laptop:/home/john# setpci -s 02:00.0 f4.b=00

```
The two PCI addresses I used were from my lspci dump...
```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
```
The problem is that those commands failed to to anything. They obviously did something because it didn't return a fail, but the display neither dimmed nor brightened. I'm really at a loss here and I can't use my Linux OS unplugged because my brightness is permanently on max. Any advise would be really appreciated please.:popcorn:

---

### Post by EricDP on 2011-01-05
> **Mawh said:**
> Thank you, it works... almost ! I'm having a weird issue, which I detailed in this post on the same thread that you linked : [http://www.voria.org/forum/viewtopic.php?p=4465#p4465](http://www.voria.org/forum/viewtopic.php?p=4465#p4465)

Actually, I had this too. I think I fixed it by disabling "dim display when idle" both when on battery and plugged in.

---

### Post by Mawh on 2011-01-12
As I said on the other thread, my checkboxes were already unchecked...

---

### Post by sanurmi on 2011-01-12
> **Fred Ora said:**
> Here's another way for those still searching.  All of the setpci answers say use at your own risk, I'm not sure what the danger is, but after much experimenting I got mine working this way without that setpci script.  I have a N150, but it should be the same.

Here's what I did:

in synaptic package manager go to settings, go to settings>repositories and chose other software tab.  
Add the following repository:  ppa:voria/ppa
click reload on the main package manager screen then search for samsung
check the boxes by samsung-tools AND samsung-backlight
click apply and load the packages.  close package manager and reboot

in the terminal run:
sudo gedit /lib/udev/rules.d/95-keyboard-force-release.rules
in the samsung section you will see a line with *N130*|*N140* etc.  add |*N150* there
also do the same for:
sudo gedit /lib/udev/rules.d/95-keymap.rules

substitute your model for N150 above if it isnt already there.


The first part loads the samsung tools and backlight utility.  this will also get some of your other function keys working.  you can see the mappings in system>samsung tools preferences.  
The second part gets the mappings working for the fn-up and fn-down keys.  it also keeps the fn-keys from going crazy by forcing them to release after being pressed.

Hope this helps!


I made as you said, but nothing else than backlight on-off from Fn+F5 is working. I have Samsung N220 and there was N220 already in that first file. To the second file I just added line like that:

ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="*N220*", RUN+="keymap $name samsung-N220"

I am really newbie with Linux and Ubuntu so I have no idea what happesn and why :)

Thanks,
Sami

---

### Post by xheyther on 2011-01-21
Hi there,

I manage to get the backlight adjustment working on my N210 by simply installing samsung-backlight from voria ppa. I also installed samsung-tools to get the short-keys working. I didn't had to add anything nor alter in any way the udev keyboard-force-release and keymap rules.
Thank to all of you for the pointer to voria ppa.

The issue I've now is that my track pad no longer work. I have to use a usb mouse.

Does anybody encounter this issue before and should it be related to the tinkering I did to get fn keys and backlight ?

---

### Post by eveliendehoop on 2011-02-05
Hi,
I'm absolutely new to linux. I've opened the second link you mention ([http://info.wsisiz.edu.pl/~sieluzyc/bright.c](http://info.wsisiz.edu.pl/~sieluzyc/bright.c)) to try and solve the fact that the Fn up and down keys to adjust the screen brightness on my N120 don't work. However, I really don't know how to use your code to actually fix my problem... Can you, in a more detailed way, tell me (a total Linux newbie) what to do?
Thanks!

---

### Post by fossean on 2011-03-04
I fixed the brightness control on a Samsung N150 Plus following the info in this thread [http://to.ly/9H1x](http://to.ly/9H1x)

Good luck!

---

### Post by kgas on 2011-03-04
check the [samsung tools](https://launchpad.net/samsung-tools)

---

### Post by minj on 2011-03-25
> **MASEngr said:**
> Awesome, awesome, awesome!  Fred's post gives brightness control to the NF210, the new dual-core one.  It also adds all Fn key functions!  

This fix adds all FN keys to Ubuntu and allows for release action, meaning the keyboard will no longer stay stuck.   It works on UNR 10.04 and 10.10.  You must reboot after editing the configuration lines. 

Keys that work are:
Sleep
Battery Life
Webcam toggle
Backlight toggle
Mute
Fan mode
Wifi antenna toggle
Touchpad toggle
Number Lock
Sound up / down
brightness up / down
home


You will have to add:
|*NF210*|

into the lines of models in
 /lib/udev/rules.d/95-keyboard-force-release.rules

and then add the line:
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="NF210", RUN+="keymap $name samsung-nf210"

(Copy and paste the line above it, then just change the model to NF210)

into /lib/udev/rules.d/95-keymap.rules

This does not yet fix the network resume after sleep, and no, turning off wireless with Fn-F9 doesn't do it. :(

Awesome you guys! I have Ubuntu 10.10 on Samsung NF310. Samsung-tools worked. Force-release worked. Keymap didn't so I added "acpi_backlight=vendor" to GRUB config ([http://www.voria.org/forum/viewtopic.php?f=3&t=625](http://www.voria.org/forum/viewtopic.php?f=3&t=625)) and vualia!

EDIT: this introduced the screen flickering problem but [http://www.voria.org/forum/viewtopic.php?p=4750#p4750](http://www.voria.org/forum/viewtopic.php?p=4750#p4750) solved it.

Although after some fiddling around with power state, lid and suspend/hibernate cycles I managed to make plugging cable out cause 'closed lid' action, which is very annoying if it is set to suspend. After a proper reboot the glitch didn't repeat itself though.

---

### Post by EverRoyalt on 2011-04-07
> **Fred Ora said:**
> Here's another way for those still searching.  All of the setpci answers say use at your own risk, I'm not sure what the danger is, but after much experimenting I got mine working this way without that setpci script.  I have a N150, but it should be the same.

Here's what I did:

in synaptic package manager go to settings, go to settings>repositories and chose other software tab.  
Add the following repository:  ppa:voria/ppa
click reload on the main package manager screen then search for samsung
check the boxes by samsung-tools AND samsung-backlight
click apply and load the packages.  close package manager and reboot

in the terminal run:
sudo gedit /lib/udev/rules.d/95-keyboard-force-release.rules
in the samsung section you will see a line with *N130*|*N140* etc.  add |*N150* there
also do the same for:
sudo gedit /lib/udev/rules.d/95-keymap.rules

substitute your model for N150 above if it isnt already there.


The first part loads the samsung tools and backlight utility.  this will also get some of your other function keys working.  you can see the mappings in system>samsung tools preferences.  
The second part gets the mappings working for the fn-up and fn-down keys.  it also keeps the fn-keys from going crazy by forcing them to release after being pressed.

Hope this helps!

(I am newbie btw)
Hi,
I got the the bit when you eneter "sudo gedit /lib/udev/rules.d/95-keyboard-force-release.rules" in to Terminal but when the textdoc opens there is nothing inside of it, it is just blank and i am useing the root account. Any idea what i have done wronge?

---

### Post by Peter-E on 2011-04-24
> I have a N150, but it should be the same.On my N210 I tried all above. Most of the Fn keys work except the backlight. I got this working on an N150 bot _not_ on the N210 unfortunately. In the Grub menu it does work but it did that "out of the box" As soon as Maverick launches it's over. Anyone who can confirm that the backlight setting actually works on a N210?

Thanks,
Peter

And... since installing the Natty upgrade it works. Whether this is due to the installs and settings I did previously or just that Natty is able to do this out of the box I don't know... Case closed for me.
Cheers,
Peter

---

### Post by ivotkl on 2013-02-25
Ok, if what was suggested here and on Dell laptops' post, I'm installing this ppa and app suggested [here](http://elleestcrimi.me/2011/11/06/quick-tip-3-fix-screen-brightness-issue-samsung-netbooks-running-ubuntu/),

---

