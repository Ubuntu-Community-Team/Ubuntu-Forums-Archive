---
title: "How to Enable Brightness Controls for Samsung R610?"
date: 2009-02-17
forum: Hardware
---

### Post by JohnJackson on 2009-02-17
I have a Samsung R610 laptop, with an NVIDIA 9200M graphics card. The brightness function keys do not work, though the audio function keys do. Is there a way to enable this functionality? Currently I have to use the NVIDIA X Server Settings utility to alter the brightness levels.

---

### Post by xcell on 2009-02-22
> **JohnJackson said:**
> I have a Samsung R610 laptop, with an NVIDIA 9200M graphics card. The brightness function keys do not work, though the audio function keys do. Is there a way to enable this functionality? Currently I have to use the NVIDIA X Server Settings utility to alter the brightness levels.

Same problem here, also on a R610 FS02.. 

Someone, please....

---

### Post by ProNux on 2009-02-24
Not probably a solution, but you can try installing the brightness applet on the panel.  Here you can adjust the brightness using a button/applet, not the physical switch...

---

### Post by JohnJackson on 2009-02-25
Thanks, but the brightness applet doesn't have any effect for me

---

### Post by xcell on 2009-03-13
Same here with the brightness applet..

I´ve tried multiple general tutorials on how to get them keys workin´, with no result.. The frustrating thing is that when booting mint, during the startup bar/screen, the keys are actually working (FN+up/down)

---

### Post by loza on 2009-03-13
Hi there

Sorry for butting in - I don't have a solution for you but I have just bought an R610 a week ago and was wondering which ubuntu to install?

I've been using my trusty tosh satellite pro L-10 for years but unfortunately its showing its age and is a bit slow even though I have upgraded it to the max.

Could you please share your experiences of the R610 and ubuntu?

What are you finding that does not work (like the brightness)?
What workarounds have you discovered?

I took a gamble on the Samsung R610 but am glad I did - it seems like a very well put together laptop - I have to run XP for work but want to dual boot it with a more stable OS. Ibex? or Heron?

Any help, info and advice, gratefully received!

Thanks in advance

loza

---

### Post by xcell on 2009-03-15
I´m running Linux Mint 6 (Ubuntu 8.10) and besides the FN up/down brightness issues it´s working great. Everything works out of the box!

I only had to run envyng to get the best drivers for the GF 9200M GS.

---

### Post by d_liebscher on 2009-07-06
Hi,

same here! 
Laptop reboots while using Fn Key's to change brightness.

Here is an Idea for a Workaround:

if nvidia diver is installed, the brightness is adjustable by using smartdimmer
e.g. ```
smartdimmer -s 50
```next step: changing the Fn command to smartdimmer
here is the problem: 
in KDE 3.x it was possible to edit a pythonscript in /usr/share/python-support/guidance-powermanager/brightness or something like that

KDE 4.x use a plasmoid which is using solid for communication with hal
It's possible to change the Backend for energy control in the system settings dialog but there is only on installed.

Anyone there with another idea?

Thanks

---

### Post by del_diablo on 2009-07-06
Well, i am using these in a terminal(not in terminal however, but i do use the commands)
```
echo 30 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
echo 60 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
echo 100 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
```

Just mash a hotkey linking to ex:

```
xterm -e "echo 100 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness"
```
```
xterm -e "echo 60 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness"
```
```
xterm -e "echo 30 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness"
```

Which will blink up xterm which will be gone after doing the job(which takes 0.1 second)

In whatever desktop enviroment your using :P

PS: "cat /proc/acpi/video/VGA/LCD/brightness" to figur out the value range, for me its 30-100.

---

### Post by d_liebscher on 2009-07-07
Hi,

the dircetory /proc/acpi does not exist on my system. I think the reason is the acpi=no option in grub. If I try to use ACPI the system crashs while starting up. Maybe this is the real cause of the problem.
(By the way, I noticed same problem on Ubuntu 8.10)

How could I change the Hotkeys? I didn't found FN Key commands in Xmodmap.

Annoying is just the fact, that every time I try to change brightness (by using FN+UP consuetudinarily) my system reboots and I could ](*,)... ;)

Thanks
Daniel

---

### Post by titato on 2009-10-21
hi there, 

i bought a r610 half a year ago, i found it very anoying that the most functionkeys i pressed the system rebooted.
Giving the boot parameter acpi=off is half a solution, ubuntu will boot but still reboots on using the function keys (maybe some exceptions).
I use the boot parameter MEM=4096M, this prevents ubuntu from rebooting, it still boots, even a couple of functionkeys function like intended.
The downside is that the system only finds 3GB of RAM when more is installed (like mine 4GB), yes i have the 64bit version installed.
Don't know the behaviour if you have more or less ram installed, it is possible that you have to use different MEM size.

If it is not a problem, you could try it.

If somebody does have a better solution, let me know. Ow btw thanx for the smartdimmer option...Im soww happy now, that brightness is killing when it is dark.

---

### Post by d_liebscher on 2009-10-22
Hi,

thanks for this new Idea.

I hope this problem will be fixed with Ubuntu 9.10. In seven days, i will test it and report my experiences here ;) .

regards

Daniel

---

### Post by d_liebscher on 2009-10-30
hello everybody,

today I tested the Ubuntu 9.10 LiveCD today, and realized, that the System crashs while starting. I disabled the AHCPI and the liveCD started but while changing the Brightness, the System crashs :(((

btw: disabled AHCI also means no battery control

any Ideas out there?

regards

daniel

---

### Post by xcell on 2010-01-26
It's been a long time since I checked this thread. 'till Now I still had my screen at maximum brightness. Just tried smartdimmer and it's awesome! Finally full brightness-control.

I was just wondering if there is a fix already for the fn+up/down buttons? I have Kubuntu 9.10 installed.

---

### Post by d_liebscher on 2010-01-27
Hi xcell,

i did not found a solution up to now. 

Also I didn't found realy usefule informations about solid and HAL communications. When I tried to understand how the system communicats with the Hardware I realised, thad my knowlage about operating systems hardware abstraction is verry limited ;) 

At momend I hope, that the next AHCPI version in (K)Ubuntu 10.4 will support the motherboard and anything will work fine.

regards

Daniel

---

### Post by jayamohan on 2010-01-28
I too had this problem. After searching for more than 1 day I came across a post that suggested to append acpi_osi='Linux' to the kernel boot options in grub. Suggestions are to edit the grub screen (hitting the key 'e' when grub loads) for the corresponding kernel and append acpi_osi='Linux'. There are chances that bright and dim controls could be reversed (function-down arrow key combination could increase the brightness than dimming). Googling acpi_osi=Linux would give plenty of information. If it works dont forget to make it permanent by editing /etc/default/grub for grub2 or menu.lst for Grub. Hope this solves your issue (it did for me). Happy ubuntuing :o

---

### Post by d_liebscher on 2010-01-30
Hi,

I tried the solution with acpi_osi=Linux but the system (9.04) crashed while starting up (no error messages just reboot). What version of ubuntu do you use? What's your Kernel Version?

regards

Daniel

---

### Post by pipuntu on 2011-02-02
Hi,

I also have the samsung R610, I have been looking for a solution to this for a while now. The closest is gnome-smartdimmer - I have contacted TJ who wrote gnome-smartdimmer to see if he has plans to update it for 10.04 which I use - [http://ubuntuforums.org/showthread.php?t=451781&page=6](http://ubuntuforums.org/showthread.php?t=451781&page=6)

I have an additional problem - my Fn + Brightness combo is badly broken, I may have done this in the past fiddling trying to get brightness working, but not sure how to fix.

If I press Fn and the up or down arrow (which are my brightness adjustment keys) then the brightness bar appears on screen, flickers a lot then goes. The my keyboard stops working **completely** and though my mouse still works my menus strangely disappear - 'Applications' is highlighted but nothing is beneath it, same for power and the rest, so I have to press the power button and restart to get my keyboard back. :( I do have compiz running...

I installed xbindkeys and xbindkeys-config but the latter crashes when I try and capture the Fn + Brightness keys and then the same result as described above.

Would be great to bind Fn + arrow up/down to smartdimmer :D

Any pointers much appreciated,
Pip.

---

### Post by d_liebscher on 2011-02-03
> **pipuntu said:**
> 
[...]
If I press Fn and the up or down arrow (which are my brightness adjustment keys) then the brightness bar appears on screen, flickers a lot then goes. The my keyboard stops working **completely** and though my mouse still works my menus strangely disappear - 'Applications' is highlighted but nothing is beneath it, same for power and the rest, so I have to press the power button and restart to get my keyboard back. [...].

Hi,

same problem on my Ubuntu 10.10 (x64) ... no idea how to fix it
(it seems to me, that every ubuntu version become more complex respective such changes on system. I remember ubuntu 7.04 (or something like this), you had just to edit some pythonfiles... ) 

regards

Daniel

---

