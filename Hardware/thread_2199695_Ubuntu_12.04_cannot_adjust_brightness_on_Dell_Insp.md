---
title: "Ubuntu 12.04 cannot adjust brightness on Dell Inspiron 15R"
date: 2014-01-15
forum: Hardware
---

### Post by mike_kzc on 2014-01-15
Dell Inspiron 15r. The graphic card is Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Install Ubuntu 12.04 several days ago

If I use the function key Fn+F4/F5, it shows the brightness bar. But it can only go one leve down. Even if it is in highest brightness, the screen is very dark (my eye already feels unconfortable after typing these many words).

I googled and tryed the following suggestion, none of them works.

1.change /etc/default/grub: acpi_osi=Linux or acpi_backlight=vendor, 

Then I restarted my laptop: after the menu, it is stuck there.
Then I can only force to turn off the laptop, and restart to choose the  recover mode. Ubuntu will start. Brightness still cannot change.
I change the grub setting back. Now the laptop can start correctly.

2. install brighntess indicator app. ([http://www.omgubuntu.co.uk/2013/04/brightness-control-ubuntu](http://www.omgubuntu.co.uk/2013/04/brightness-control-ubuntu))
it shows that the brightness is 17. in the highest level.

3. Tried what is suggested in this post : [http://ubuntuforums.org/showthread.p...6#post12769346]("http://ubuntuforums.org/showthread.php?t=2170137&p=12769346#post12769346")


I used to have Ubuntu 11.10 on my old computer for two yrs or so. It works perfectly. Is it possible to go back to Ubuntu 11.10 from 12.04??

Please help, Thanks alot.

%*****************************************
Following the suggestion from [**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629")

This is the output for the code.

for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

**********************
 /sys/class/backlight/acpi_video0
99
99
99

 /sys/class/backlight/intel_backlight
574
4882
574
**********************************

---

### Post by oldfred on 2014-01-15
from this link. BIOS settings make a difference
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.

---

### Post by mike_kzc on 2014-01-15
> **oldfred said:**
> from this link. BIOS settings make a difference
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)4

Thanks a lot for the reply.

Please elaborate how to change the BIOS mode.

miek

---

### Post by oldfred on 2014-01-15
I do not have a Dell. You need to go into UEFI/BIOS and turn on Legacy mode, but leave UEFI on to keep booting with UEFI.

---

### Post by mike_kzc on 2014-01-15
btw, I am runing under Legacy Mode, showed by the following code:


[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode" 
Installed in Legacy mode

---

### Post by oldfred on 2014-01-15
Then you have Legacy mode on.

The link I posted above said the Dells work a lot better with 13.10 as that includes many updates (all of sputnik) to work better with Dell. You version may need Sputnik installed separately. But I do not know if that applies to all models or not. Know nothing about Sputnik otherwise.

---

### Post by mike_kzc on 2014-01-15
a little bit mor information.

The Fn+F4/F5 works fine under windows 7, it indeed can increase/decrease the brightness.

---

### Post by Toz on 2014-01-15
> 1.change /etc/default/grub: acpi_osi=Linux or acpi_backlight=vendor, 
Did you run "sudo update-grub" after the change? 

Can you try those parameters again and on reboot, post back:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
...as well as a copy of your dmesg log file via:
```
pastebinit /var/log/dmesg.log
```
...and post back the link that is generated? You may need to install the pastebinit app for it to work.

---

### Post by mike_kzc on 2014-01-15
> **Toz said:**
> Did you run "sudo update-grub" after the change? 

Can you try those parameters again and on reboot, post back:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
...as well as a copy of your dmesg log file via:
```
pastebinit /var/log/dmesg.log
```
...and post back the link that is generated? You may need to install the pastebinit app for it to work.

First of all, thank you so much for the relpy.

1. I did run "sudo update-grub" after change the grub  /etc/default/grub: acpi_osi=Linux or acpi_backlight=vendor, 

Again, I want to emphasize that, this does not work on my PC, it will crash my PC

2. The output from "cat /proc/cmdline" is:
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=40ce5124-c849-4a75-bfb9-94e149877f52 ro quiet splash vt.handoff=7

3. The output form "for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done" is:
*****************************
 /sys/class/backlight/acpi_video0
94
99
99

 /sys/class/backlight/intel_backlight
4882
4882
4882
******************************

This output is obviously different from what I got in the first post. Actually, what I did is: I am so frusted about the brightness problem in Ubuntu and so I get rid of Ubuntu, then install Fedora. Under Fedora, it seems the screen is much brighter. 

Since I am not familar with Fedora, I re-install Ubuntu 12.04 again (get rid of Fedora). 

Now, it seems that the screen is acturally much brighter. Actually, it is too much brighter, another extreme. I am trying to edit the actual_brightness under /sys/class/backlight/ wihtout success evenif under root

Probably, this is a solution.

4. The file dmesg.log does not exist.

Thanks agian. Hope to hear from you soon.

Mike

---

### Post by Toz on 2014-01-15
Sorry, the file is actually called /var/log/dmesg. Can you post back a link to it when you have used pastebinit to upload it?


Which of those backlight interfaces is the active interface? To find out, which of the following commands change the screen brightness:
```
echo  50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo  99 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...or:
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```


And finally, there is a way to temporarily test kernel parameters. This way, if the system fails to start, you just need to restart to get it back the way it was. Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions from the [Kernel Boot Parameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki page. Can you please test the following kernel parameters, one at a time:

- acpi_osi=
- acpi_backlight=vendor
- acpi_osi=Linux acpi_backlight=vendor 

Report back if either get the brightness working. If the screen freezes again during boot, try pressing the brightness key combinations (in case the screen brightness is set to 0 on boot). And if nothing, simply restart to get the system back to the way it was before the kernel parameters were used.

---

### Post by mike_kzc on 2014-01-15
> **Toz said:**
> Sorry, the file is actually called /var/log/dmesg. Can you post back a link to it when you have used pastebinit to upload it?


Which of those backlight interfaces is the active interface? To find out, which of the following commands change the screen brightness:
```
echo  50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo  99 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...or:
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```


And finally, there is a way to temporarily test kernel parameters. This way, if the system fails to start, you just need to restart to get it back the way it was. Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions from the [Kernel Boot Parameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki page. Can you please test the following kernel parameters, one at a time:

- acpi_osi=
- acpi_backlight=vendor
- acpi_osi=Linux acpi_backlight=vendor 

Report back if either get the brightness working. If the screen freezes again during boot, try pressing the brightness key combinations (in case the screen brightness is set to 0 on boot). And if nothing, simply restart to get the system back to the way it was before the kernel parameters were used.

Thanks again for yr time and patience, this is one of the great thing about Ubuntu community.

1. pastebinit /var/log/dmesg gives:[http://paste.ubuntu.com/6759559/](http://paste.ubuntu.com/6759559/)

2. The following code works 
*****************
echo 3600 | sudo tee /sys/class/backlight/intel_backlight/brightness
*****************
It become darker, hahahahahhaha, it works, it works, it works.

After using the above command, using " for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done ""

gives:
**********************************

 /sys/class/backlight/acpi_video0
99
99
99

 /sys/class/backlight/intel_backlight
3600
4882
3600
***************************************

3. Reading "Temporarily Add a Kernel Boot Parameter for Testing" Now. Trying to understand how to do the following, 
 testing "- acpi_osi=
- acpi_backlight=vendor
- acpi_osi=Linux acpi_backlight=vendor"

If possible, please elaborate regarding this point.


Thanks again.

Mike

---

### Post by mike_kzc on 2014-01-15
One more thing,

After reboot, I have re-do "echo 3600 | sudo tee /sys/class/backlight/intel_backlight/brightness". How to set this permanently?

Thanks.

---

### Post by Toz on 2014-01-15
> **mike_kzc said:**
> 
3. Reading "Temporarily Add a Kernel Boot Parameter for Testing" Now. Trying to understand how to do the following, 
 testing "- acpi_osi=
- acpi_backlight=vendor
- acpi_osi=Linux acpi_backlight=vendor"

If possible, please elaborate regarding this point.


Thanks again.

Mike
In a nutshell, hold down the shift key while the system boots to display the grub screen. When it displays it should be highlighting your current kernel (the top one). If not, use the arrow keys to highlight it then press the letter 'e'. Then use your arrow keys to move down and to the end of the line beginning with the word "linux" and at the end, enter a space then the keywords I identified. For the first test, add only **acpi_osi=**. Then press Ctrl+x to boot with that addition. Check for proper backlight control. 

Ten reboot and do the same for the other two options.



> After reboot, I have re-do "echo 3600 | sudo tee /sys/class/backlight/intel_backlight/brightness". How to set this permanently?
1. From a terminal window:
```
sudo -i gedit /etc/rc.local
```
2. Add:
```
echo 3600 > tee /sys/class/backlight/intel_backlight/brightness
```
..._above_ the line *exit 0*.
3. Save the file.


The reason why your backlight isn't working properly is because you have two backlight interfaces and the system is confused. The kernel parameters mentioned above may be able to eliminate one of the interfaces. In fact, if you enter the above command in /etc/rc.local, you may find that the **acpi_backlight=vendor** parameter may get it all working again for you (I believe that when you try that parameter, the computer is starting with the brightness level set at 0).

---

### Post by mike_kzc on 2014-01-16
Thank yo sooooooooooooo much Toz. I think the problem is solved.

1. Tried adding "echo 3600 > tee /sys/class/backlight/intel_backlight/brightness" to /etc/rc.local, it does not work, I have to copy this command to the terminal.

2. I tested all three kernerl parameters you mentioned

The Kernel line is this "Linux /boot/vmlinuz-3.8.0-35-generic root=UUID=40ce5124-c849-ca75-bfb9-94e19877f52 ro quiet splash $vt_handoff"


"- acpi_osi=", works perfectly on my PC (Dell insprion 15R), after I add this parameter when boot, not only the brightness is right, I can use Fn+F4/F5 to adjust the brightness.

The command " for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done"

gives:
*****************************
 /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
574
4882
4882
************************************************

"- acpi_backlight=vendor" does not work

"- acpi_osi=Linux acpi_backlight=vendor" Crashed the computer, I have to reboot


3. Since the parameter "acpi_osi=" works, I add this parameter to /etc/default/grub to make the this line like this "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=", reboot, it works, hahahaahhahahahhah


Thanks again, Toz.

If possible, please explain how you debug this issue, I will learn a great deal from that, actually, I have already learnt a great deal from yr post. Many thanks.

Mike

---

### Post by Toz on 2014-01-16
I'm curious about some of the settings now that you are using **acpi_osi=**. Can you post back the result of these commands:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
...then:
```
echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...then again:
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
> If possible, please explain how you debug this issue,
Mostly from a lot of reading, testing and experience. Here are some link that can get you started: 
- [https://wiki.archlinux.org/index.php/Backlight]("https://wiki.archlinux.org/index.php/Backlight")
- [https://wiki.ubuntu.com/Kernel/Debugging/Backlight]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")
- [https://wiki.ubuntu.com/DebuggingACPI]("https://wiki.ubuntu.com/DebuggingACPI")

---

### Post by mike_kzc on 2014-01-16
> **Toz said:**
> I'm curious about some of the settings now that you are using **acpi_osi=**. Can you post back the result of these commands:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
...then:
```
echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...then again:
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

Mostly from a lot of reading, testing and experience. Here are some link that can get you started: 
- [https://wiki.archlinux.org/index.php/Backlight](https://wiki.archlinux.org/index.php/Backlight)
- [https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)
- [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)


1.  cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic root=UUID=40ce5124-c849-4a75-bfb9-94e149877f52 ro quiet splash acpi_osi= vt.handoff=7
'
2.for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
4882
4882
4882

3. echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
[sudo] password for yyou: 
1000

4. for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
1000
4882
1000


I still feel a little bit unconfortable with the screen brightness. What I mean is: when the backligh is 4882, it is too bright. Then I use Fn+F4 to dim the brightness, it is still too bright. It is sort of like too much white color on the screen. Maybe, there is some optimal combination about the acpi_vedio and backlight.

Thanks a lot.

Mike

---

### Post by Toz on 2014-01-16
> I still feel a little bit unconfortable with the screen brightness. What I mean is: when the backligh is 4882, it is too bright. Then I use Fn+F4 to dim the brightness, it is still too bright. It is sort of like too much white color on the screen. Maybe, there is some optimal combination about the acpi_vedio and backlight.

Whats interesting is that you still have 2 backlight interfaces (acpi_video0 and intel_backlight). Ideally, you would only want one. The acpi_backlight=vendor kernel parameter should eliminate the acpi_video0 interface leaving you with just the one, but that doesn't seem to work for you. 



If you're willing, can we try to get the acpi_backlight=vendor kernel parameter working? If so...
1. Backup your existing /etc/rc.local file:
```
sudo cp /etc/rc.local /etc/rc.local.BAK
```
2. Edit /etc/rc.local to look like this:
```
#!/bin/sh -e
echo 0 > /sys/class/backlight/intel_backlight/brightness
exit 0
```
3. Save the file, reboot and temporarily try the kernel parameters **acpi_osi= acpi_backlight=vendor**



If that doesn't work, repeat the same steps but this time use this /etc/rc.local file:
```
#!/bin/sh -e
echo 4882 > /sys/class/backlight/intel_backlight/brightness
exit 0
```



Copy/paste the file contents to avoid typos. Try the function keys. Let me know how it goes.

---

### Post by mike_kzc on 2014-01-16
> **Toz said:**
> Whats interesting is that you still have 2 backlight interfaces (acpi_video0 and intel_backlight). Ideally, you would only want one. The acpi_backlight=vendor kernel parameter should eliminate the acpi_video0 interface leaving you with just the one, but that doesn't seem to work for you. 



If you're willing, can we try to get the acpi_backlight=vendor kernel parameter working? If so...
1. Backup your existing /etc/rc.local file:
```
sudo cp /etc/rc.local /etc/rc.local.BAK
```
2. Edit /etc/rc.local to look like this:
```
#!/bin/sh -e
echo 0 > /sys/class/backlight/intel_backlight/brightness
exit 0
```
3. Save the file, reboot and temporarily try the kernel parameters **acpi_osi= acpi_backlight=vendor**



If that doesn't work, repeat the same steps but this time use this /etc/rc.local file:
```
#!/bin/sh -e
echo 4882 > /sys/class/backlight/intel_backlight/brightness
exit 0
```



Copy/paste the file contents to avoid typos. Try the function keys. Let me know how it goes.

1. use the first suggestion, i.e., "echo 0 > /sys/class/backlight/intel_backlight/brightness" for rc.local and "**acpi_osi= acpi_backlight=vendor**"

total darkness, cannot see anyting

2. use the second suggestion, i.e., "echo 4882> /sys/class/backlight/intel_backlight/brightness" for rc.local and "**acpi_osi= acpi_backlight=vendor**"

Too bright, and the Fn+F4/F5 can only go one level down, but has no effect on the brightness at all.

So confused.

Thanks a lot Toz.

Mike

---

### Post by Toz on 2014-01-16
Okay, lets try another:

Set /etc/rc.local to be:
```
#!/bin/sh -e
echo 3600 > /sys/class/backlight/intel_backlight/brightness
exit 0
```
...and try the following kernel parameters: **acpi_osi=Linux acpi_backlight=vendor**

---

### Post by mike_kzc on 2014-01-16
will do so tomorrow moring. thanks.

mikje

---

### Post by Toz on 2014-01-16
I was just having a second look at your dmesg log file and noticed that you are using kernel 3.8 (missed that the first time through). Did you upgrade the kernel? With 3.8, I believe we have one more option available to us. Try these ones as well:

/etc/rc.local
```
 #!/bin/sh -e
exit 0
```
...and kernel boot parameter: **acpi_osi="!Windows 2012"**

AND

/etc/rc.local
```
 #!/bin/sh -e
exit 0
```
...and kernel boot parameter: **acpi_osi="!Windows 2012" acpi_backlight=vendor**

---

### Post by mike_kzc on 2014-01-17
> **Toz said:**
> Okay, lets try another:

Set /etc/rc.local to be:
```
#!/bin/sh -e
echo 3600 > /sys/class/backlight/intel_backlight/brightness
exit 0
```
...and try the following kernel parameters: **acpi_osi=Linux acpi_backlight=vendor**

Using this "**acpi_osi=Linux acpi_backlight=vendor**" freeze the screen for a while and then show some information on the screen like this 

"201.956490 end_request: I/o error, dev sda sector 1245879" and many lines like this

---

### Post by mike_kzc on 2014-01-17
> **Toz said:**
> I was just having a second look at your dmesg log file and noticed that you are using kernel 3.8 (missed that the first time through). Did you upgrade the kernel? With 3.8, I believe we have one more option available to us. Try these ones as well:

/etc/rc.local
```
 #!/bin/sh -e
exit 0
```
...and kernel boot parameter: **acpi_osi="!Windows 2012"**

AND

/etc/rc.local
```
 #!/bin/sh -e
exit 0
```
...and kernel boot parameter: **acpi_osi="!Windows 2012" acpi_backlight=vendor**

I don't think I upgrade the kernel. In fact, I don't know anyting about the Kernel. I just install the updates whenever Ubuntu tells me to do so. I do make ~500 updates, not sure whether these updates have anything to do with Kernel.

1. This parameter "**acpi_osi="!Windows 2012"**" and changing the rc.local gives the maximus brightness, just like "acpi_osi=" did. But using this combination will make the Fn+F5/F4 can only goes one level down, which has no effect on the brightness.

2. This parmaeter "**acpi_osi="!Windows 2012" acpi_backlight=vendor**" and rc.local freeze the screen forever, have to reboot.

Thanks a lot, really appreciate it.

For now, I am using the following solution:

1. add the "acpi_osi=" and make the rc.local like this:

#!/bin/sh -e
echo 3600 > /sys/class/backlight/intel_backlight/brightness
exit 0

It seems that this gives the best performance regarding the brightness.

Using the above solution, this code "for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done "
gives: 

 /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
3600
4882
4882


Again, thanks for the time and patience.

Mike

---

