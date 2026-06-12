---
title: "Sony E series  brightness control not working in 12.10"
date: 2012-12-09
forum: Hardware
---

### Post by djpeck1 on 2012-12-09
I have a Sony E series laptop (64 bit) where keys Fn+F5 and Fn+F6 should control the screen brightness. On my machine these keys do control the brightness "slider", but they do not control the actual screen brightness. I am running Ubuntu 12.10. These keys did work to control screen brightness when running Ubuntu 12.04 LTS, but I updated to 12.10 to get EFI boot working correctly.

To date I have tried various kernel bootup options to get the keys working, but none have proved effective. I have tried;
acpi_backlight=video
acpi_backlight=vendor
acpi_osi=Linux
acpi_osi=Linux acpi_backlight=vendor

I had an earlier Sony laptop and to get the brightness controls working on that I had to use a custom gsd_backlight_helper module in gnome-settings-daemon. I've tried that fix for my new Sony, but that also fails to get the brightness controls working.

I'm sure it must be possible to fix this issue, but I'm not sure how to proceed. Can anyone help with this?

---

### Post by Toz on 2012-12-09
Hello and welcome to the forums.

Can you post back the results of the following commands (to identify your backlight interfaces):
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Can you also run in a terminal window:
```
acpi_listen
```
...press the brightness up and brightness down buttons and post back the codes that are returned.

Maybe we can create some acpi scripts to control the brightness for you.

---

### Post by djpeck1 on 2012-12-09
Hi Toz.
Thanks for getting back to me so quickly.
I have run the commands you asked and got the following results;

*for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done*

[B]/sys/class/backlight/acpi_video0
0
100[/B]

*acpi_listen*

Pressing brightness up gives;

[B]video LCD 00000086 00000000
video PEGP 00000081 00000000
video PEGP 00000081 00000000[/B]

Pressing brightness down gives;

[B]video LCD 00000087 00000000
video PEGP 00000081 00000000
video PEGP 00000081 00000000[/B]

Please let me know if you need me to run any more commands and thanks again for your assistance with this.

Dave.

---

### Post by Toz on 2012-12-09
Ok, lets make the following changes and see what happens.

Create the following files with the following content (you will need root privileges to do this, so for each file, run "gksu gedit <file>" where <file> is: )

**/etc/acpi/events/sony-brightness-up**
```


event=video LCD 00000086 00000000
action=/etc/acpi/brightup.sh
```

**/etc/acpi/events/sony-brightness-down**
```


event=video LCD 00000087 00000000
action=/etc/acpi/brightdown.sh
```

**/etc/acpi/brightdown.sh**
```


#!/bin/bash
curr=`cat /sys/class/backlight/acpi_video0/actual_brightness`
if [ $curr -gt 7 ]; then
   curr=$((curr-8));
   echo $curr  > /sys/class/backlight/acpi_video0/brightness;
fi
```

**/etc/acpi/brightup.sh**
```


#!/bin/bash
curr=`cat /sys/class/backlight/acpi_video0/actual_brightness`
if [ $curr -lt 93 ]; then
   curr=$((curr+8));
   echo $curr  > /sys/class/backlight/acpi_video0/brightness;
fi
```

Then, make all 4 of those scripts executable by running the following commands:
```


sudo chmod +x /etc/acpi/events/sony-brightness-up
sudo chmod +x /etc/acpi/events/sony-brightness-down
sudo chmod +x /etc/acpi/brightdown.sh
sudo chmod +x /etc/acpi/brightup.sh
```

And finally, restart acpid:
```

sudo service acpid restart
```

Check if the function keys work now.

---

### Post by djpeck1 on 2012-12-10
Hi Toz.
Thanks for your help with this.
I have created and double  checked the scripts you specified above (and rechecked that they are  executable), but unfortunately they do not allow me to change the screen  brightness. The brightness "slider" (top right of the screen) changes  when I press the function keys, but the actual screen brightness still  does not change. I have even tried rebooting the machine.
Have you any other suggestions that might help? I really appreciate your time with this.
Regards,  Dave.

---

### Post by Toz on 2012-12-10
Do these commands change the brightness?
```
echo 100 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

If not, can you post back:
```
cat /proc/cmdline
```

---

### Post by djpeck1 on 2012-12-10
Hi Toz.

The three commands you asked me to run did not alter the screen brightness.

I have run  *cat /proc/cmdline* and the output is;

**BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic.efi.signed root=UUID=0f0e5ff5-ec6b-4fdf-89da-2852db86b2cb ro quiet splash vt.handoff=7**

Regards,  Dave.

---

### Post by Toz on 2012-12-10
Can you add **acpi_backlight=vendor** to the kernel command line, then re-run these commands again and post back the results:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by djpeck1 on 2012-12-11
Okay. I've added the kernel command line option acpi_backlight=vendor and run;
cat /proc/cmdline

[B]BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic.efi.signed root=UUID=0f0e5ff5-ec6b-4fdf-89da-2852db86b2cb ro acpi_backlight=vendor quiet splash
[/B]
The I ran;

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done

[B]/sys/class/backlight/sony
63
7
[/B]
I hope this helps.

Regards,  Dave.

---

### Post by Toz on 2012-12-11
Okay then, do the following commands adjust brightness?
```
echo 0 | sudo tee /sys/class/backlight/sony/brightness
echo 4 | sudo tee /sys/class/backlight/sony/brightness
echo 7 | sudo tee /sys/class/backlight/sony/brightness
```

EDIT: What video card do you have?
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by djpeck1 on 2012-12-11
Hi. The 3 commands that you asked me to try did not adjust the brightness so I've run the commands to report on the video card. This is the output;

[B]01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7500M/7600M Series] [1002:6841] (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:90ac]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at c4000000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 5000 [size=256]
    Expansion ROM at c4040000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: radeon[/B]


I don't know if it's relevant but when I was running 12.04 LTS the brightness control worked just fine, but I was using the proprietary AMD drivers (fglrx). I can't test this theory in 12.10, because the  proprietary driver is not supported by the new version of X-server and consequently Unity does not run.

Regards,  Dave.

---

### Post by Toz on 2012-12-11
> **djpeck1 said:**
> I don't know if it's relevant but when I was running 12.04 LTS the brightness control worked just fine, but I was using the proprietary AMD drivers (fglrx). I can't test this theory in 12.10, because the  proprietary driver is not supported by the new version of X-server and consequently Unity does not run.

Yes, I'm thinking that this is why you're not getting brightness control in 12.10. I can't seem to manipulate the backlight interface manually. Can you post back the contents of your dmesg and Xorg log files via:
```
pastebinit /var/log/dmesg
pastebinit /var/log/Xorg.0.log
```
...and post back the links that are generated? I want to see if there is anything in there that might help.

Also, one more long shot, do the following commands affect brightness?
```
sudo setpci -s 01:00.0 F4.B=96
sudo setpci -s 01:00.0 F4.B=00
sudo setpci -s 01:00.0 F4.B=FF
xrandr --output default --brightness 0.5
xrandr --output default --brightness 1.0
```

---

### Post by djpeck1 on 2012-12-11
Hi.
The first pasteinit is **[http://paste.ubuntu.com/1425381/](http://paste.ubuntu.com/1425381/) ** (dmesg)
The scond is **[http://paste.ubuntu.com/1425387/](http://paste.ubuntu.com/1425387/)**  (Xorg)

The three setpci commands did not affect the brightness and the two xrandr commands gave the following messages;

[B]warning: output default not found; ignoring
xrandr: Need crtc to set gamma on.[/B]

but did not affect the brightness.

Please let me know if you find anything interesting in the log files.

Regards,  Dave.

---

### Post by Toz on 2012-12-11
From your dmesg log:
> sony_laptop: brightness ignored, must be controlled by ACPI video driver
...and yet ACPI video can't control brightness. Might be related to: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1005196]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1005196") but according to that bug report, a patch was applied to kernel 3.5 rc5 and you're already running that kernel.

I think you should create a bug report:
```
ubuntu-bug linux
```
...and have the devs look at it.

---

### Post by djpeck1 on 2012-12-11
Hi Toz.

Thanks for all your help with this. It is much appreciated.

I will do as you suggest and raise a bug report.

I have also noticed that ATI have recently released a proprietary driver for my graphics adapter that is not yet available in the Ubuntu repositories. I might download that and give it a try.

Regards,  Dave.

---

### Post by elchicosinhada on 2012-12-12
Same problem...

---

### Post by keibee on 2013-01-12
Does anyone have an update on this?  100% screen brightness by default is seriously influencing the autonomy on 12.10. Even after using powertop I get less than 3 hours...

---

### Post by chetancr9 on 2013-05-26
Hi Toz,

I too have the same problem.
Brightness control doesn't work with the function key on sony E series laptop on ubuntu 12.10.
I tried updating in grub but still it didn't work for me.

And here is the output of what u have asked. 

chetan@chetan-SVE15115ENB:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
15
chetan@chetan-SVE15115ENB:~$ acpi_listen
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b


Kindly help me to control the brightness.

really my eyes are burning with this full brightness

Thanks
Chetan C R

---

### Post by chetancr9 on 2013-05-26
Hello All,

I am running Ubuntu 12.10 on Sony E series Laptop

Brightness Control is not working (Fn F5/F6 ) is not working
The brightness remains same for all values (0-15)

I tried to update from the grub it didn't work for me.

Below is the output of commands acpi_listen with brightness + ans - function keys pressed. 

chetan@chetan-SVE15115ENB:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
15
chetan@chetan-SVE15115ENB:~$ acpi_listen
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sonyl/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 00000011
video PEGP 00000081 00000000
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011




Kindly help me to solve this problems

---

### Post by mörgæs on 2013-05-26
Threads merged.
Please don't post multiple threads on the same subject.

---

### Post by Toz on 2013-05-26
@chetancr9, does your Sony model come with an AMD video card?
```
sudo lspci -vnn | grep -A15 VGA
```
...If so, have you installed the proprietary drivers?

Does the following command change the brightness?
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

What kernel boot kernel parameters are you using?
```
cat /proc/cmdline
```
...have you tried the **acpi_backlight=vendor** parameter?

---

