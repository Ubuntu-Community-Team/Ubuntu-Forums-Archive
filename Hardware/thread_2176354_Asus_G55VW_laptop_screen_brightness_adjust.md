---
title: "Asus G55VW laptop screen brightness adjust"
date: 2013-09-23
forum: Hardware
---

### Post by miguel6 on 2013-09-23
hey, i'm trying to reduce brightness on my screen because it is currently stuck at 100% from day 1 of ubuntu use. I have FN + F keys to adjust brightness but they don't work, that was a given. I tried xbacklight but when I set the brightness either by directly setting or reducing it dosen't do anything it just says it did it in terminal.

I recently tried 
```

sudo gedit /etc/default/grub


```   
and placed

  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

```  Save and exit.


  ```
sudo update-grub


```  Restart. and it should make FN keys work but no good. Heres link to post on it.

 
[http://stackoverflow.com/questions/11523523/how-can-i-change-the-screen-brightness-of-my-laptop-in-ubuntu](http://stackoverflow.com/questions/11523523/how-can-i-change-the-screen-brightness-of-my-laptop-in-ubuntu)

I don't understand what the above method does, my guess is I'm suppose to insert my monitors name into some parameter but not sure. So now I'm posting for help with my laptop specifically.

Link to laptop spec sheet [http://www.asus.com/ROG_ROG/G55VW/#specifications](http://www.asus.com/ROG_ROG/G55VW/#specifications)

Any help is appreciated :)

---

### Post by Toz on 2013-09-24
Which version of Ubuntu are you using?

Have you installed the proprietary nvidia drivers or are you using the opensource nouveau drivers. Entering this command in a terminal window should help identify it:
```
lspci -k | grep -A3 VGA
```

If you are using the proprietary nvidia drivers, you can try adding:
```
Option          "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of your /etc/X11/xorg.conf file.

If you are using the opensource nouveau drivers, you're probably going to need to set up [nvidiabl]("https://github.com/guillaumezin/nvidiabl").

---

### Post by miguel6 on 2013-09-25
> **Toz said:**
> Which version of Ubuntu are you using?

Have you installed the proprietary nvidia drivers or are you using the opensource nouveau drivers. Entering this command in a terminal window should help identify it:
```
lspci -k | grep -A3 VGA
```

If you are using the proprietary nvidia drivers, you can try adding:
```
Option          "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of your /etc/X11/xorg.conf file.

If you are using the opensource nouveau drivers, you're probably going to need to set up [nvidiabl]("https://github.com/guillaumezin/nvidiabl").

Thanks for the reply.

First off, the xorg.conf file didn't exist and after some searching I found out it never did exist as it is no longer needed apparently. If however I wish to create my own xorg.conf file I can do so and did threw this help of this thread 

[http://askubuntu.com/questions/25746/etc-x11-xorg-conf-doesnt-exist?lq=1](http://askubuntu.com/questions/25746/etc-x11-xorg-conf-doesnt-exist?lq=1)

after creating that I used VI in terminal to over write this file that was only access-able by root. This is exactly what I did:

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_005_zpsf552bf24.png~original[/IMG]

After this I saved and quit. Now trying to adjust brightness either via FN keys or even threw display settings that Ubuntu has but nothing happened :( I probably just pasted

```
Option          "RegistryDwords" "EnableBrightnessControl=1"
```

in the wrong place. Please correct me if I did. There were a lot of places with the word device and so I just put it there because it had the driver I was using...

Again i'm using a Asus G55VW

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_006_zps7ca01b17.png~original[/IMG]

---

### Post by Toz on 2013-09-25
Are you using the proprietry nvidia drivers of the opensource nouveau drivers? Try running this command in the terminal window:
```
lspci -k | grep -A3 VGA
```

---

### Post by miguel6 on 2013-09-25
> **Toz said:**
> Are you using the proprietry nvidia drivers of the opensource nouveau drivers? Try running this command in the terminal window:
```
lspci -k | grep -A3 VGA
```

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_007_zps880b9346.png~original[/IMG]

I have the proprietry nvidia drivers I installed from the nvidia website. In order to install it, it made me create

```
nvidia-installer-disable-nouveau.conf
```

which as the file says disables nouveau.

Not sure if it helps but I have FN keys that do work. All work except brightness really.

---

### Post by Toz on 2013-09-26
> **miguel6 said:**
> Thanks for the reply.

First off, the xorg.conf file didn't exist and after some searching I found out it never did exist as it is no longer needed apparently. If however I wish to create my own xorg.conf file I can do so and did threw this help of this thread 

[http://askubuntu.com/questions/25746/etc-x11-xorg-conf-doesnt-exist?lq=1](http://askubuntu.com/questions/25746/etc-x11-xorg-conf-doesnt-exist?lq=1)

after creating that I used VI in terminal to over write this file that was only access-able by root. This is exactly what I did:

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_005_zpsf552bf24.png~original[/IMG]

After this I saved and quit. Now trying to adjust brightness either via FN keys or even threw display settings that Ubuntu has but nothing happened :( I probably just pasted

```
Option          "RegistryDwords" "EnableBrightnessControl=1"
```

in the wrong place. Please correct me if I did. There were a lot of places with the word device and so I just put it there because it had the driver I was using...

Again i'm using a Asus G55VW

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_006_zps7ca01b17.png~original[/IMG]
Lets try again but this way. First, delete the xorg.conf file that you created. Secondly, create the file **/usr/share/X11/xord.conf.d/15-nvidia.conf** with the following content:
```
Section "Device"                                                                                                                                                                       
        Identifier     "Device0"                                                                                                                                                       
        Driver         "nvidia"                                                                                                                                                       
        VendorName     "NVIDIA Corporation"                                                                                                                                           
        Option         "RegistryDwords" "EnableBrightnessControl=1"                                                                                                                           
EndSection
```
...and log out and back in again. Check the function keys and also please post back your Xorg.0.log file like this:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

Also post back the contents of /usr/share/X11/xorg.conf/15-nvidia.conf.

---

### Post by miguel6 on 2013-09-26
Again thanks for the help, really appreciate it.

Here is the pastebin link...such a great feature! love it.

[http://paste.ubuntu.com/6160891/](http://paste.ubuntu.com/6160891/)

and this is the contents of /usr/share/X11/xorg.conf/15-nvidia.conf.

[IMG]http://i.imgur.com/ZU5AjGV.png[/IMG]

This is still not resolved :(

---

### Post by Toz on 2013-09-27
Looks like you might need to try [nvidiabl]("https://github.com/guillaumezin/nvidiabl") then. Open a terminal window and execute these commands:
```

wget https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.80_all.deb
sudo dpkg -i nvidiabl-dkms_0.80_all.deb
sudo modprobe nvidiabl
```
...post back the results of those commands.

Hopefully, everything will install normally, but the function keys may not work right off the bat. To test whether you can change the brightness:
1. Get your current brightness value:
```
cat /sys/class/backlight/nvidia_backlight/actual_brightness
```

2. Get your maximum allowed brightness value:
```
cat /sys/class/backlight/nvidia_backlight/max_brightness
```

3. Set a new brightness value:
```
echo XX | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...where XX is a value between 0 and the result of step #2.

If you can change your brightness manually this way, try your fn function keys. If they don't work, we can try mapping them.

---

### Post by miguel6 on 2013-09-27
> **Toz said:**
> Looks like you might need to try [nvidiabl]("https://github.com/guillaumezin/nvidiabl") then. Open a terminal window and execute these commands:
```

wget https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.80_all.deb
sudo dpkg -i nvidiabl-dkms_0.80_all.deb
sudo modprobe nvidiabl
```
...post back the results of those commands.

[http://pastie.org/private/xsss4a6qfekjwjx3xqvivg](http://pastie.org/private/xsss4a6qfekjwjx3xqvivg)

There's a link to a copy paste of what happened in the terminal. The install was successful.

OMG. 

```
echo XX | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

This works but FN keys still don't so I will have to map the keys as you mentioned. If you'd like you can post how to map the keys for the sake of this thread helping other people.

Also, I've been wondering how do you know Linux so well ? I see threads of people asking for help and there is always an answer how to do it. I hate being the one to ask ten thousand questions...so how do you know all these different methods and linux commands ? I guess I should study a linux API :redface:

---

### Post by Toz on 2013-09-27
Good news. 

First thing to do is to make the loading of the module automatic on every boot. As root, append **nvidiabl** to the list of modules to auto-start in /etc/modules.

Second, lets get a full report of your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

Thirdly, lets get the codes for your function keys. Open a terminal window and type in:
```
acpi_listen
```
...then press the function+brightness_up key combination once followed by function+brightness_down combination once. Post back the codes that are displayed in the terminal window. We will then create the necessary mappings specific for your computer.

> Also, I've been wondering how do you know Linux so well ? I see threads of people asking for help and there is always an answer how to do it. I hate being the one to ask ten thousand questions...so how do you know all these different methods and linux commands ? I guess I should study a linux API 
Basically, trial and error and lots of experience. I've been using Unix/Linux since about 1995 and have had a lot of opportunity to investigate the inner workings of this O/S. Don't worry about asking questions, I was the one asking them in 1995. Thats how you learn.

---

### Post by miguel6 on 2013-09-27
I found this link which I think is extremely useful for Asus G55VW. It has some info on screen brightness maybe if you want to look at it..

[http://www.linlap.com/asus_g55vw](http://www.linlap.com/asus_g55vw)

---

### Post by Toz on 2013-09-27
> **miguel6 said:**
> I found this link which I think is extremely useful for Asus G55VW. It has some info on screen brightness maybe if you want to look at it..

[http://www.linlap.com/asus_g55vw](http://www.linlap.com/asus_g55vw)

Yes, thats basically what we're doing here. "EnableBrightnessControl" didn't work for you, so we've moved to trying nvidiabl, which looks like it is working. Just need to map the function keys. Out of curiosity, does double-pressing the function key combos change the brightness?

---

### Post by miguel6 on 2013-09-27
> **Toz said:**
> Out of curiosity, does double-pressing the function key combos change the brightness?

I hold down FN and hit F5 (decrease brightness) multiple times it won't do anything, even making sure I just hit it twice.

Running acpi_listen displayed all the keys I pressed including when I did combos like ALT + random key and SHIFT and CTRL also F keys showed. The only combination that didn't work was when I held down FN + F key or FN + any key for that matter.

 Here's what it looks like;

[IMG]http://i.imgur.com/7GlrOPm.png[/IMG]

^[[15~ is F key for screen decrease
^[[17~ is F key for screen increase

The other inputs were combinations like SHIFT + key CTRL + key...

This person had the same problem [http://ubuntuforums.org/showthread.php?t=787734](http://ubuntuforums.org/showthread.php?t=787734)

My machine is recent so I doubt i'll need to update BIOS which is what the solution was for that thread.

Any other idea how to get FN key ?

I'm currently reading this Wiki

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by Toz on 2013-09-27
Hmmmm. Can you press the function+brightness keys again once then post back the results of these commands:
```
cat /var/log/syslog | grep -i acpi
```
...and:
```
dmesg | grep -i acpi
```

---

### Post by miguel6 on 2013-09-27
```
cat /var/log/syslog | grep -i acpi
```

[http://pastie.org/private/vvlrztz3c5itddhwciqadg](http://pastie.org/private/vvlrztz3c5itddhwciqadg)

```
dmesg | grep -i acpi
```


[http://pastie.org/private/aw4guhjxumya49qegmf9ta](http://pastie.org/private/aw4guhjxumya49qegmf9ta)

I think what you just asked was to press the brightness keys and paste those because they record all keys pressed if so they I'm pretty sure I did it right. I pressed FN + brightness then put that code into terminal and copied what it output.

---

### Post by Toz on 2013-09-27
> I think what you just asked was to press the brightness keys and paste those because they record all keys pressed if so they I'm pretty sure I did it right. I pressed FN + brightness then put that code into terminal and copied what it output.
Just to confirm:
1. Open a terminal window.
2. In the terminal window, run the command **acpi_listen** (press enter)
3. Press the Fn+Brightness Up key combination (is it Fn+F5?)
4. Press the Fn+Brightness Down key combination (is it Fn+F6?)
5. Look at the codes that show up in the terminal window. Paste them back here.

Can you also try going to the first tty (Ctrl+Alt+F1), logging into the text console, and running:
```
showkey
```
...then pressing Fn+Brightness up and Fn+Brightness down and post back if any codes are recognized there.

Can you also post back:
```
ls /etc/acpi/events
```

And one final thing:
```
modinfo asus_wmi
```

---

### Post by miguel6 on 2013-09-28
> **Toz said:**
> Just to confirm:
1. Open a terminal window.
2. In the terminal window, run the command **acpi_listen** (press enter)
3. Press the Fn+Brightness Up key combination (is it Fn+F5?)
4. Press the Fn+Brightness Down key combination (is it Fn+F6?)
5. Look at the codes that show up in the terminal window. Paste them back here.

**Yeah that's exactly what I did and no key is detected. Nothing shows up. Every single button works except for the FN key.**
> Can you also try going to the first tty (Ctrl+Alt+F1), logging into the text console, and running:
```
showkey
```
...then pressing Fn+Brightness up and Fn+Brightness down and post back if any codes are recognized there.

[B]I did this also and same thing when I use 
```
acpi_listen
```
No key is detected. All keys works except for the FN key. When I hold FN + any other key it won't do anything or even FN key on its own.[/B]
> Can you also post back:
```
ls /etc/acpi/events
```


[http://pastie.org/private/wn1mhxia8omcmmgnpkeia](http://pastie.org/private/wn1mhxia8omcmmgnpkeia)
> And one final thing:
```
modinfo asus_wmi
```

[http://pastie.org/private/kgymciqlo1ymoq43onxfew](http://pastie.org/private/kgymciqlo1ymoq43onxfew)

**So basically, I need to figure out why Ubuntu is not recognizing my FN key. Again, thanks for all the help.**

---

### Post by Toz on 2013-09-28
Can you post back the contents of /etc/acpi/events/asus-video? I don't seem to have that file on my computer.

Can you also try to unload asus_wmi?
```
sudo modprobe -r asus_wmi
```
...and see if that helps.

---

### Post by miguel6 on 2013-09-28
> **Toz said:**
> Can you post back the contents of /etc/acpi/events/asus-video? I don't seem to have that file on my computer.

Can you also try to unload asus_wmi?
```
sudo modprobe -r asus_wmi
```
...and see if that helps.

[IMG]http://i.imgur.com/xxTRFER.png[/IMG]

unloading asus_wmi didn't do anything. FN key is still not detected. :(

---

### Post by Toz on 2013-09-28
I don't know why you're function keys aren't being recognized. We could create a script that will allow you to change the brightness using a different key combination, say Ctrl+Up and Ctrl+Down. To do so, post back your new backlight information:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by miguel6 on 2013-09-29
I just tried some testing with different key combos. All FN + F key works! I can open a calc, adjust sound, shut off screen, change keyboard brightness basically ALL of them except brightness. They all show up in tty using showkey. I tested by pressing just the F key which would be like 60 then pressing it with the FN key which would be something like 113.

The only key that is not ever recognized as you already know is brightness. So the FN key does work just for some reason those keys don't lol....it's not a big deal if I can't have a shortcut to change brightness I just wanted to change it from 100% but I will try to create one.

[http://pastie.org/private/tlrxtmxujhuh00bqnf0g](http://pastie.org/private/tlrxtmxujhuh00bqnf0g)

---

### Post by Toz on 2013-09-29
> **miguel6 said:**
> I just tried some testing with different key combos. All FN + F key works! I can open a calc, adjust sound, shut off screen, change keyboard brightness basically ALL of them except brightness. They all show up in tty using showkey. I tested by pressing just the F key which would be like 60 then pressing it with the FN key which would be something like 113.

The only key that is not ever recognized as you already know is brightness. So the FN key does work just for some reason those keys don't lol....it's not a big deal if I can't have a shortcut to change brightness I just wanted to change it from 100% but I will try to create one.

[http://pastie.org/private/tlrxtmxujhuh00bqnf0g](http://pastie.org/private/tlrxtmxujhuh00bqnf0g)
Back in post #9, you installed nvidabl and were able to change the brightness. However, in this listing, the nvidia_backlight interface is not showing up. Can you try this (remove the asus wmi driver and start the nvidiabl module):
```
sudo modprobe -r  asus_wmi
sudo modprobe nvidiabl
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...then try the function brightness keys and:
```
acpi_listen
```
...again to see if you can get some codes to show up.

---

