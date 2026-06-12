---
title: "Dell E1505/6400 Any issues/Heat?"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by mattyj on 2006-09-16
Hello,

I am looking to purchase a Dell E1505 and have read several issues about overheating, fans not going on/ACPI issues.  Now it seems that many people are using them just fine.

As far as configuration I am looking at:

Intel® Core™ 2 Duo processor T7200 (4MB Cache/2.00GHz/667MHz FSB) 
256MB NVIDIA® GeForce™Go 7300 
Intel PRO/Wireless 3945a/g

I wouldn't expect the processor upgrade to make much of a difference.

Questions:

1.  Have the overheating issues been resolved(BIOS/ACPI)?

[http://ubuntuforums.org/showthread.php?t=186003](http://ubuntuforums.org/showthread.php?t=186003)

2.  Does wireless work with the newest kernel?
3.  I assume nVidia-glx would get the graphics card working...

I greatly appreciate your help.

Thank You.

---

### Post by r0ydster on 2006-09-17
> 
I am looking to purchase a Dell E1505 and have read several issues about overheating, fans not going on/ACPI issues.  Now it seems that many people are using them just fine.

I have a Dell E1505, and I felt it did run a bit hot (50C at idle).  Once I installed the i8k modules I now run between 30c - 40c for pretty much everything.  Combine the i8k module with gkrellm and you can set thresholds to force the fans to turn on.


> 256MB NVIDIA® GeForce™Go 7300 
Worked for me out of the box - on the initial install, the   generic nvidia driver is installed - run apt-get install nvidia-glx like you say, to get it running right.

> Intel PRO/Wireless 3945a/g

This worked for me right out of the box as well. The Intel 3945 driver is now in the repositories.


Mike

---

### Post by mattyj on 2006-09-17
Thank You.

Could you tell me more about I8K and gkrelm or point toward a how/to?  I couldn't find one.

What is a reasonable temp to have fans go on/off?  
Are they set at default in I8K?  
I have used ubuntu on desktops for a while, but am unfamiliar with its use on laptops?

---

### Post by ysr on 2006-09-18
> **mattyj said:**
> Thank You.

Could you tell me more about I8K and gkrelm or point toward a how/to?  I couldn't find one.

What is a reasonable temp to have fans go on/off?  
Are they set at default in I8K?  
I have used ubuntu on desktops for a while, but am unfamiliar with its use on laptops?

Here is what you can do. A word of warning before you start - **by doing the below you will be taking control of the thermal behaviour of your laptop, so the manufacturer's warranty may not cover you - therefore do this at your own risk**. If you are still keen, read below.

```
sudo apt-get install i8kutils
sudo modprobe i8k force=1
sudo i8kmon --daemon --auto
```

This sequence loads the i8k module, gets i8kmon running in daemon mode with auto fan control using its own default presets for the temperature limits. You will however need to execute these commands each and every time you reboot your system (which for a laptop, is a lot many times). 

Therefore the two questions are...
[LIST]
[*]How to get the i8k kernel module loaded up automatically, and i8kmon started automatically at machine boot time.
[*]How to set up your own defaults for temperature
[/LIST]

_*To achieve the above objectives, you will have to edit system configuration files, so make sure you backup any file you edit, in case things go wrong and you have to revert back to the old system configuration.*_

To get the i8k module loaded at start up, you need to edit the files /etc/modules and /etc/modprobe.d/options. To the file /etc/modules add the line ```
i8k
``` at the very end. To the file /etc/modprobe.d/options add the line ```
options i8k force=1
``` This will load the modules at startup. The force=1 option may or may not be required, depending on whether your BIOS is recognized as supported by i8k, but having it in place will force it to load even if i8k thinks the BIOS is unsupported.

To startup i8kmon at startup you will need to write a small script and place it in /etc/init.d/ This thread has a good explaination of how to do this.

[http://www.ubuntuforums.org/showpost.php?p=1325507&postcount=128]("http://www.ubuntuforums.org/showpost.php?p=1325507&postcount=128")

Note: Do not forget to run the update-rc.d to link your script to the rcN.d directories where init looks for startup scripts. Also do not forget to make you script executable (common mistake that leads to hours of frustration).

To override the default temperature limits, you will need to create a configuration file (either /etc/i8kmon or ~/.i8kmon). The above post also contains an example of how to do that.

While you are at this, you might want to check out the manual pages for the following

```
man i8kmon
man i8kctl
man i8kfan
```

Also worthwhile exploring the two init related functions that you will be using
```
man update-rc.d
man start-stop-daemon
```

Once everything is done, do check that i8kmon is running in the background, but running ```
 ps aux | grep i8kmon 
``` The output should show a daemon process running.

Have fun with your new laptop, and happy linuxing...

---

### Post by mattyj on 2006-09-18
Thank You very much.

I am just an end user doing FEM without alot of linux experience so I am a little apprehensive to go this route.  I love ubuntu on a dual opteron machine I have at work.  It seems like this I8K is due to a BIOS that doesn't play well with ubuntu(you are just overriding it I think).  I think I can do the above but am a bit scared to take over all thermal control.  Do any other machines come with BIOS more suitable for this?  I was checking out the system76 machines.

---

### Post by ysr on 2006-09-19
> **mattyj said:**
> Thank You very much.

I am just an end user doing FEM without alot of linux experience so I am a little apprehensive to go this route.  I love ubuntu on a dual opteron machine I have at work.  It seems like this I8K is due to a BIOS that doesn't play well with ubuntu(you are just overriding it I think).  I think I can do the above but am a bit scared to take over all thermal control.  Do any other machines come with BIOS more suitable for this?  I was checking out the system76 machines.

Yes, by setting up your own temperature limits in /etc/i8kmon, you will be overriding the default BIOS thermal behaviour. That said, I am unsure if the ACPI already overrides the default BIOS behaviour without your knowledge, in which case I would prefer to have explicit control.

Another thing, I am not sure if it's only ubuntu that the bios does not play well with. I found that the laptop got quite hot even under windows (that it originally shipped with.)

---

### Post by r0ydster on 2006-09-20
Thanks YSR.  You stated it better than I could have done.

Mike

---

### Post by Daniel15 on 2006-09-22
ysr, on my laptop (a Dell Inspiron 6400) I didn't set i8kmon to run automatically at startup... Does this matter? GKrellm seems to be handling the fans properly (clicking on the fan while in 'Manual' mode does indeed change the fan speed).

Also, I tried running hdparm, but got this:
> 
daniel@daniel-laptop:~$ sudo hdparm -i /dev/sda
/dev/sda:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

Does anyone know what this means?

Oh yeah, and the wireless does indeed work out of the box, with WPA even :D

---

### Post by ysr on 2006-09-22
> **Daniel15 said:**
> ysr, on my laptop (a Dell Inspiron 6400) I didn't set i8kmon to run automatically at startup... Does this matter? GKrellm seems to be handling the fans properly (clicking on the fan while in 'Manual' mode does indeed change the fan speed).

Also, I tried running hdparm, but got this:

Does anyone know what this means?

Oh yeah, and the wireless does indeed work out of the box, with WPA even :D

Hi Daniel15, I believe you can use this package gkrellm-i8k instead of i8kmon to set automated fan controls. Is that what you are using? I have never used it myself, so cannot comment on the performance, etc. Also, does it work when you are not using X.

Personally, I prefer to avoid GUI based stuff as far as possible (having learnt most of my computing on a VT100 ;) ). The only GUI part of my i8kmon set up is a small applet in my panel using the sensors-applets package, and I keen an eye on it from time to time to make sure that the i8kmon is doing its job.

---

### Post by Daniel15 on 2006-09-22
> Hi Daniel15, I believe you can use this package gkrellm-i8k instead of i8kmon to set automated fan controls. Is that what you are using?
Yes, that's what I'm using at the moment :)

> Also, does it work when you are not using X.
Probably not, but I usually use X on the laptop. I have a server at home running Debian Linux which I use for all my text-based stuff :D

> having learnt most of my computing on a VT100
Haha, I've never used one of those... The first computer I ever used was an Amiga 2000 in 1996 (I was 6 years old)

---

### Post by manzuk on 2006-10-31
I also have a E1505. But the temperature when idle is 44C. Is it ok? Also, the CPUfrequency monitor shows when idle 800mhz (46%).
This is my first laptop and dont wanna burn it u know...
Any advice? Im running the gkrellm stuff. Should I use the daemon instead?
Thank u

---

### Post by garethc on 2006-10-31
I know that problems with ACPI on laptops such as the Inspiron 6400 were present under Dapper, but I think the important question now is have these problems been fixed in Edgy. In other words, will a default install of Edgy destroy certain laptops? For me, this is an extremely serious issue and should be receiving more publicity in the forums and elsewhere.

Maybe Ubuntu should pop up a warning during install that it may destroy certain laptops? ;-)

I have no idea whether my laptop is affected - I haven't noticed excess physical heat but the CPU may be running hotter. I'll have to get the lm-sensors package or something

Cheers,
Gareth

---

