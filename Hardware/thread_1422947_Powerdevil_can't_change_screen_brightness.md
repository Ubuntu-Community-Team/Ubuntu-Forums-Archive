---
title: "Powerdevil can't change screen brightness"
date: 2010-03-06
forum: Hardware
---

### Post by sb73542 on 2010-03-06
Hi,

I have Kubuntu 9.10 on an Acer 4810T laptop. The FN+arrow keys work perfectly with OSD to change the screen brightness.  But Powerdevil can't change the brightness.  I move the brightness slider back and forth, but no change.  According to KDE, I do have all the capabilities of the power management system working correctly.  Any ideas?  

Thanks a lot!

---

### Post by jtweaker on 2010-03-10
> **sb73542 said:**
> Hi,

I have Kubuntu 9.10 on an Acer 4810T laptop. The FN+arrow keys work perfectly with OSD to change the screen brightness.  But Powerdevil can't change the brightness.  I move the brightness slider back and forth, but no change.  According to KDE, I do have all the capabilities of the power management system working correctly.  Any ideas?  

Thanks a lot!



Having the same problem with my Aspire 4736 but still no one has responded to my thread either. Some claim that if you have a dual booted machine (windows & ubuntu) boot into windows first change screen brightness there then reboot to ubuntu and that should have adjusted your screen brightness. Doesn't work for me. If i find anything else I'll post back.

---

### Post by sb73542 on 2010-03-10
Thanks for replying!

I should mention that I can adjust my screen brightness with Kubuntu using the Fn+arrow keys, and there's even a nice OSD.  Just that it doesn't work in PowerDevil, and my brightness doesn't automatically dim down when the power is disconnected.

---

### Post by jtweaker on 2010-03-11
Hi here I am again. looks like we're on our own here so let's just try to help each other out. :) Just to be clear, you're saying that when you use Fn+ keys slider works with OSD but no actual change on the screen brightness? If that's the case then we're on the same boat. Earlier I mentioned that changing screen brightness on windows (when you are on dual boot [windows&ubuntu]) doesn't do the trick for me when some have claim it does. Well, I was wrong. 

Just to cut it short, I did some test while on battery power which I didn't do earlier and turns out that when I change my screen brightness on windows, same happens with ubuntu. When i chose the power saving mode on windows, it dimmed the display. Then i rebooted to ubuntu and found out that the display was also dimmed.

That is my case. I have a dual boot with Windows7 and Ubuntu 9.10. Are you on dual booth too or just running on Kubuntu alone? If you are using Kubuntu alone, I still don't have any good solution for our problem on hand. I just shared my findings in hope that you may find it helpful even in just the littlest way.

---

### Post by Ayuthia on 2010-03-11
Do either of you have a brightness file:
```
ls /proc/acpi/video/VGA/LCD
```
If so, does it have any values in there:
```
cat /proc/acpi/video/VGA/LCD
```

You might even try checking to see the code values when you press the Fn+ key and see what displays:
```
xev
```
When you run that command, it will produce event values.  A little window will also appear.  To end the application, just close that window.

---

### Post by jtweaker on 2010-03-11
Yay! finally some help. I followed your instructions and here's what i got.

"cannot access /proc/acpi/video/VGA/LCD: No such file or directory"

I guess I don't have a brightness file..Also when i tried the code "xev" the only thing that changes when i press Fn+right/left is the value for serial. It just keeps increasing when i press either left or right.

sorry I'm a complete newbie here. Just installed Ubuntu a few days ago.

---

### Post by Ayuthia on 2010-03-11
> **jtweaker said:**
> Yay! finally some help. I followed your instructions and here's what i got.

"cannot access /proc/acpi/video/VGA/LCD: No such file or directory"

I guess I don't have a brightness file..Also when i tried the code "xev" the only thing that changes when i press Fn+right/left is the value for serial. It just keeps increasing when i press either left or right.

sorry I'm a complete newbie here. Just installed Ubuntu a few days ago.

Ok.  I don't have your computer so I am guessing for the location.  Can you check the following:
```
find /proc/acpi -name brightness
lsmod|grep acer
```
We are going to see if there are any brightness setting in acpi and also see if there is any special acer modules loaded.

---

### Post by jtweaker on 2010-03-11
> **Ayuthia said:**
> Ok.  I don't have your computer so I am guessing for the location.  Can you check the following:
```
find /proc/acpi -name brightness
lsmod|grep acer
```We are going to see if there are any brightness setting in acpi and also see if there is any special acer modules loaded.


I tried the code "find /proc/acpi -name brithness" and here's what i got 

//proc/acpi/video/OVGA/DD05/brightness
/proc/acpi/video/OVGA/DD04/brightness
/proc/acpi/video/OVGA/DD03/brightness
/proc/acpi/video/OVGA/DD02/brightness
/proc/acpi/video/OVGA/DD01/brightness

the second code didnt' produce anything..

---

### Post by Ayuthia on 2010-03-11
I was doing a quick search on this and found this [link]("http://bbs.archlinux.org/viewtopic.php?id=74829").  What they are doing is adding acpi_backlight=vendor to the boot options.  You might try that.

As for your results, my guess is that one of those five brightness files has the value for your backlight.  If the above does not work, can you post the results of:
```

cat /proc/acpi/video/OVGA/DD05/brightness
cat /proc/acpi/video/OVGA/DD04/brightness
cat /proc/acpi/video/OVGA/DD03/brightness
cat /proc/acpi/video/OVGA/DD02/brightness
cat /proc/acpi/video/OVGA/DD01/brightness

```
If we can find the one with the value, we might be able to create a workaround for controlling the backlight.

[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/490610") looks like the bug report in Launchpad for Ubuntu.

---

### Post by jtweaker on 2010-03-11
ok stupid question. how do I add "acpi_backlight=vendor" to the boot options or kernel parameter? I'm totally clueless on this one.As for the codes that you gave here are the results

```

cat /proc/acpi/video/OVGA/DD05/brightness
<not supported>

cat /proc/acpi/video/OVGA/DD04/brightness
<not supported>

cat /proc/acpi/video/OVGA/DD03/brightness
levels:  10 20 30 40 50 60 70 80 90 100
current: 100

cat /proc/acpi/video/OVGA/DD02/brightness
<not supported>

cat /proc/acpi/video/OVGA/DD01/brightness
<not supported>

```

---

### Post by Ayuthia on 2010-03-12
Ok.  We know that DD03 is the section where the brightness information is stored.  Based on the information there, there might be another file there that we can make adjustments to that can change the brightness.

As for updating the boot parameters, that needs to be done in the GRUB2 file.  I don't have GRUB2 installed so I am basing the information from this [post]("http://ubuntuforums.org/showthread.php?t=1195275").

From what I read, you will need to edit the grub file.  In Ubuntu:
```
gksu gedit /etc/default/grub
```
In Kubuntu:
```
kdesudo kate /etc/default/grub
```
Look for the line:
```
GRUB_CMDLINE_LINUX=""
```
and change it to:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
Then save the file and then update grub:
```
sudo update-grub
```

Once you reboot, that command should be used and hopefully the backlight will now be adjusted.

---

### Post by jtweaker on 2010-03-12
I followed your instructions and rebooted. I was really hoping it'll will work but it didn't. What happened was, the Fn+keys stopped functioning. Then I tried adding a brightness applet hoping I could adjust the brightness from there but there was a restriction icon on it now and produces a message "cannot get brightness applet" I then reedited the grub file and deleted the entry i made and it was back to how it was before. Thank you for all your effort in this. I hope this bug gets fixed in the upcoming releases.

---

### Post by rajayoganand on 2010-06-03
I have DELL New Inspiron R 4010 14". Installed Ubuntu 10.04 LTS. Working great except the brightness.

I have followed this post and the following is my files for brightness. Which is saying not supported. 


/proc/acpi/video/GFX0$ cat $(find ./  | grep brightness)
<not supported>
<not supported>
<not supported>
<not supported>
<not supported>
<not supported>
<not supported>
<not supported>


The only way which I found after a long search and fight with google is the FN+F4/F5 for increase/decrease brightness is working when I am in boot menu of GRUB. 

This is the only way which I have right now as a solution.

Any suggestions are welcome.

Thanks a lot.

---

### Post by faisalsani on 2010-11-15
> **jtweaker said:**
> I followed your instructions and rebooted. I was really hoping it'll will work but it didn't. What happened was, the Fn+keys stopped functioning. Then I tried adding a brightness applet hoping I could adjust the brightness from there but there was a restriction icon on it now and produces a message "cannot get brightness applet" I then reedited the grub file and deleted the entry i made and it was back to how it was before. Thank you for all your effort in this. I hope this bug gets fixed in the upcoming releases.
i have same problem, still not work in my acer 4736 :(

---

### Post by faisalsani on 2010-11-15
> **faisalsani said:**
> i have same problem, still not work in my acer 4736 :(

the problem solved on my laptop, check this out:
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948)

tq:)

---

### Post by owiknowi on 2010-12-02
Found a workaround on the web to reduce screen brightness manually (thanks to the original poster!)  Open a (root) terminal and type: sudo setpci -s 00:02.0 F4.B=xx (where xx is the required value).  btw. in a root terminal you don't need to type sudo.  This works with U10.04 on my NTUC0 where the Fn + Fx-keys don't work.

---

### Post by owiknowi on 2010-12-02
Alas: after rebooting the settings are lost. So they just work during a session.  Where can the brightness settings manually be adjusted and stored?

---

