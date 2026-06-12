---
title: "Cannot change screen brightness with 10.4"
date: 2010-05-06
forum: Hardware
---

### Post by toogooda on 2010-05-06
I have just installed Ubuntu 10.4 on my laptop (Toshiba Qosmio G40) It recomended I install the new Nvidia driver version 195.36.15 after rebooting the picture was much better but know I can't change the screen brightness. Under the default screen driver on the live CD it was working.
My graphics card is NVidia GeForce 8600M GT using Nvidia.
The hot keys work as it shows the image in the top right that looks like it is altering the back-light but nothing actually changes.

Is there an easy fix for this? It doesn't sound like a big deal but is very annoying.

---

### Post by strikoo on 2010-05-06
I'm having the same problem.

[http://ubuntuforums.org/showthread.php?t=1474494](http://ubuntuforums.org/showthread.php?t=1474494)

Toshiba u500 nvidia g210m

On windows to enable brightness control, in driver inf is added registry dword key EnableBrightnessControl=1, if that key doesn't exist, the brightness control doesn't work so,
I find that there is no EnableBrightnessControl in /proc/drivers/nvidia/registry. My thinking is if I manage to add it there that brightness will work, the problem is that I don't know how to add it there.

---

### Post by toogooda on 2010-05-06
> **strikoo said:**
> I'm having the same problem.

[http://ubuntuforums.org/showthread.php?t=1474494](http://ubuntuforums.org/showthread.php?t=1474494)

Toshiba u500 nvidia g210m

On windows to enable brightness control, in driver inf is added registry dword key EnableBrightnessControl=1, if that key doesn't exist, the brightness control doesn't work so,
I find that there is no EnableBrightnessControl in /proc/drivers/nvidia/registry. My thinking is if I manage to add it there that brightness will work, the problem is that I don't know how to add it there.

That file seems to be locked, I tried [alt]+[ctrl]+f1 then sudo nano /proc/nvidia/driver/registry but when I tried to write out the file I got IO error.

must be another way to set this.

---

### Post by strikoo on 2010-05-06
> **toogooda said:**
> That file seems to be locked, I tried [alt]+[ctrl]+f1 then sudo nano /proc/nvidia/driver/registry but when I tried to write out the file I got IO error.

must be another way to set this.

This cannot be edited because it is created every time system boots.

---

### Post by toogooda on 2010-05-07
Bump,

Anyone else having this issue?

---

### Post by toogooda on 2010-05-07
This issue specifically related to the Nvidia 195.36.15 driver as it only happens when installed.

---

### Post by Semus4 on 2010-05-08
Similar problem here. Today I did update to 10.04.

My laptop is HP ProBook 4710s. 

Shortcuts for volume control, web browser etc. are working fine. But not brightness control (nothing showing when pressed).

My graphic card is ATI Mobility Radeon HD 4330, so problem doesn't seem to be related with nVidia in my case.

Hope this will be solved somehow, changing brightness on laptop is a normal functionality used every day.

---

### Post by strikoo on 2010-05-10
[http://ubuntuforums.org/showthread.php?t=1474494](http://ubuntuforums.org/showthread.php?t=1474494)

Here is a solution for toshiba laptops.

---

### Post by thecondordb on 2010-05-10
Hi friends.

I cannot change the **brightness** on a custom **Sony Vaio VGN-FW4** series laptop (model *PCG-3H1M*) running a fully updated **Ubuntu 10.04** (64 bit), too. It has an *ATI Mobility Radeon HD 4650* graphic chip. When i try the Fn+F5 and Fn+F6 buttons, **nothing happens at all** - no OSD and no brightness change. Using the (somehow jumpy) gnome brightness applet, doesn't change anything either. :(

The strange thing is, that brightness control **was working perfectly with Ubuntu 9.10** (64 bit) on this Sony laptop, so my distribution update to 10.04 somehow broke it. Maybe it's a kernel thing (brightness control working with 2.6.31-21.59 amd_64, not working with 2.6.32-22.33 amd_64). Maybe I shouldn't forget to tell you that I have some things installed here, that might also *interfere* somehow with ACPI/brightness control... the *lm-sensors* and *gnome-sensors* stuff to display CPU and HDD temperatures (currently working), *compiz extra animations* (currently working), *ATI fglrx driver* (currently working).

It seems to me like an *ACPI* and/or *sony-laptop module* problem? :confused:

There is an **old** blog post, providing a DSDT patch (unfortunately not confirmed working with Lucid Lynx) for Jaunty and Karmic here: [http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/](http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/) - I *can't test that patch* again because there are "no free download slots" when trying to download it. :(

There is an **old and archived** (and therefore unfortunately a READ ONLY) thread in these forums ("Calling all Vaio owners"), see here: [http://ubuntuforums.org/showthread.php?t=465491](http://ubuntuforums.org/showthread.php?t=465491)

That thread starter provided a script that automatically gathers information (*DSDT dump* etc.) that the he wished to have posted there. Because of the READ ONLY status, I ran his script and posted the generated *.tar.gz file* as an attachment here. I will also try to inform that thread starter in a few minutes by PM, if possible. :rolleyes:

In my */var/log/messages* file I found these interesting lines..
[COLOR=Gray][..]
 May 10 17:29:05 linuropa kernel: [    0.000000]
[COLOR=DarkOrange] AMI BIOS detected: BIOS may corrupt low RAM, working around it.[/COLOR]
[..]
 May 10 17:29:05 linuropa kernel: [    0.334591]
[COLOR=Red] [Firmware Bug]: ACPI: **ACPI brightness control misses _BQC function**[/COLOR]
[..]
 May 10 17:29:05 linuropa kernel: [    0.447243]
[COLOR=DarkOrange] Marking TSC unstable due to TSC halts in idle[/COLOR]
[..]
 May 10 17:29:05 linuropa kernel: [   13.543325]
[COLOR=Red] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS[/COLOR]
[..]
 May 10 17:29:05 linuropa kernel: [   13.705675]
[COLOR=DarkOrange] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors[/COLOR]
 May 10 17:29:05 linuropa kernel: [   13.707517]
[COLOR=SeaGreen] sony-laptop: Sony Notebook Control Driver v0.6.[/COLOR]
[..]
 May 10 17:29:05 linuropa kernel: [   13.765221]
[COLOR=SeaGreen] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input5[/COLOR]
 May 10 17:29:05 linuropa kernel: [   13.765311]
[COLOR=SeaGreen] input: Sony Vaio Jogdial as /devices/virtual/input/input6[/COLOR]
 May 10 17:29:05 linuropa kernel: [   13.766419]
[COLOR=Red] sony-laptop: **brightness ignored, must be controlled by ACPI video driver**[/COLOR]
[..][/COLOR]

Does anybody have an idea how to get the brightness controls working again? :roll:

Thanks.


Condor

---

### Post by toogooda on 2010-05-11
I think you have a different issue to us as we all have OSD working when we hit the hot keys but it just doesn't change the brightness. Also both of us only got the issue after the new Nvidia driver was installed. If I remove it my brightness works (but I lose the 3d stuff)

---

### Post by sams9 on 2010-05-11
Same problem here, pressing keys pops up indicator but doesn't change brightness. 
Same video driver but different card mine is a GeForce 310M.
Laptop is a Dell Vostro 3500.
Hope will find a solution soon.

---

### Post by rwarden3522 on 2010-05-12
I have the same problem with the brightness applet not allowing me to increase or decrease the brightness of my screen. HOWEVER, if I use the Gnome Power Mangement applet (Perference -> Power Management) I can change the brightness of the screen, for both on AC and on Battery Power, by using the sliders in the power management applet.

I hope this helps resolve this problem.

---

### Post by MisterEwok on 2010-05-12
I'm having the same problem. [fn]+[f5] puts the computer to sleep as it is supposed to but [fn]+[f7] and [fn]+[f8] are supposed to adjust the screen brightness down and up respectively. But they do nothing.

---

### Post by low-res on 2010-05-12
Got the same problem.

Franseco's patch gave me a brightness bar ut still nothing happens while the bar slides. When I go to powermanager and slide the bar there nothing happens.

Still looking for a solution...

---

### Post by xshadowspherex on 2010-05-15
Hello there

I recently installed Ubuntu 10.04 dual boot with Windows 7.
I also found it very annoying that I couldn't change the screen brightness on my laptop using the Fn+F6 and F7 keys. Messing around with Ubuntu for a bit (and I'm quite proud of myself since I'm a total Linux n00b) I found that it was my graphics driver that was messing it up. 

I don't know the actual solution to activate the nVidia driver and still manage to change the screen brightness, but if the screen brightness is really grinding your gears just remove your driver and restart your laptop. If anything at least your eyeballs won't be hurting. 

*I just finished reading that someone else who practically said the same thing lol. From what I'm going with, I'll just stick to 3D rendering with Windows 7 until the driver gets fixed.*

If someone finds a way to fix this let me know!
TIA

---

### Post by sams9 on 2010-05-25
Found a temp workaround online...
Change the brightness using the function keys at the grub menu.
Works for me, not ideal but better than not at all.

---

### Post by landymann on 2010-05-25
I know that it's not related to the nVidia drivers on my eee pc (its intel!) but I have the brightness applet on the pannel as my Fn keys don't work. (right click on panel, add to panel... and select screen brightness applet.)

---

### Post by Toci on 2010-06-01
I had the same issue, in my case it turned out to be something extremely basic:

 Whenever I clicked on the brightness icon it would close, and the only way to return the brightness to normal after hibernating (when the brightness went down permanently) was through Power Management.
 So I clicked on it again (the icon) and this time I scrolled through the mouse wheel, and that's how it changes.

---

### Post by PowerKiKi on 2010-06-08
I have a Vostro 3500 as well and I just found out there is an option in "NVIDIA X Server Settings" dialog. Go to "X Screen 0" > "X Server Color Correction" and adjust brightness on the fly (don't forget to confirm your change at the bottom).

That's no quite a perfect solution, but still a bit more convenient than grub workaround ;-)

---

### Post by kantu on 2010-07-07
I have a Dell Studio with ATI 5470 card i have no issues in adjusting screen brightness with function keys but ,
The power management option in System->Administration is very bad. 
It does not remember the settings , every time the screen brightness will be reset to high when i log in

---

### Post by Novarg on 2010-07-15
Dell vostro 3500 with nvidia 310m. Backlight not working, does anybody found solution?

---

### Post by Mick54 on 2010-07-25
Their is a tip to adjust the brightness.
Edit your xorg.conf :
> $ sudo gedit /etc/X11/xorg.conf 
add this line in the device section :
> Option "RegistryDwords" "EnableBrightnessControl=1"
Log out then log in, it should work

I test this tip on a Dell Vostro 3500 whith ubuntu 10.04 using nvidia driver 195.36.24 and it's working.

---

### Post by xpluto on 2010-07-25
try to adjust with smartdimmer program


type in console  :
```
smartdimmer -s 90

```for 90% of brightness

minimum is 15  maximum is 100

---

### Post by JackSchnippes on 2010-09-26
this worked for me: it's the same solution as from Mick54. Thanks mick! It's an issue with the proprietary NVIDIA drivers.

from [http://ubuntuforums.org/showthread.php?t=1515079#post9494941](http://ubuntuforums.org/showthread.php?t=1515079#post9494941)

> **BennBuntu said:**
>  
[...] Have to add 
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```to your  /etc/X11/**xorg.conf** under **devices** section. Make sure the quotation marks  are the same as if you type them.

---

### Post by toogooda on 2010-10-21
Solved when I installed 10.10

---

