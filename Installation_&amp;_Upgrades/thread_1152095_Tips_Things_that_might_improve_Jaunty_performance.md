---
title: "Tips: Things that might improve Jaunty performance"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by lovinglinux on 2009-05-07
I have been reading lots of threads about improved performance in Jaunty, but unfortunately my system was running slower just after a clean install. For example, I barely could watch a flash video on YouTube without practically freezing Firefox and the CPU usage was considerably higher than Hardy Heron.

After reading a lot of threads about different solutions for different problems, I did some tweaks that increased my system performance and improved Firefox benchmarks considerably. For additional Firefox tweaks visit [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)


> **[color=#CC0000]Remove pulseaudio and install esound:[/color]** this can improve performance considerably and solve issues of audio out-of-sync.

[How-To](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

**[color=#FF0000]Warning:[/color]** *when you remove pulseaudio or install esound, the package manager also removes the metapackage ubuntu-desktop. Don't worry, this file is used only for upgrades between Ubuntu releases. Just make sure you install it before upgrading. If you do clean installs between releases, then you don't need to worry about it.*


> **[color=#CC0000]Disable Remote Desktop:[/color] **it seems that there is a bug in the Remote Desktop server that makes it use 100% of the CPU, even not showing on *top*. Go to "System >> Preferences >> Startup applications", disable the Remote Desktop option and reboot.


> 
**[color=#CC0000]Remove Python 2.5 (Jaunty only):[/color]** this version of Python is definitely not playing well on Jaunty. If you have Python 2.6 installed you can remove the 2.5 version.

[color=#FF0000] **Warning: **[/color] *check first if there isn't any important package (gnome stuff)  dependent on Python 2.5, otherwise you might brake your system.This might also remove non-essential applications that strictly depend on the 2.5 version. For example I had ontv, mimms and guake that depends on it, but I can live without them (tilda is better than guake).*


> **[color=#CC0000]Xorg tweaks:[/color]** some modifications to the xorg.conf file might improve overall performance, including Firefox and Flash. Some of this might not apply to your graphics card. Intel graphic cards users check the [Jaunty Intel Graphics Performance Guide](http://ubuntuforums.org/showthread.php?t=1130582).

First make sure you have the proprietary graphics card driver installed. Go to "System >> Administration >> Hardware Drivers" and enable the corresponding driver.

To edit the xorg file run this:

```
gksudo gedit /etc/X11/xorg.conf
```

Then add the following lines ([original thread](http://ubuntuforums.org/showpost.php?p=7279783&postcount=18)):

```

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

These will enable direct rendering and compositing. I don't know exactly what they do, but I had a huge flash performance boost after this, Firefox is much more responsive and fast and the system is more responsive too. See discussion [here](http://ubuntuforums.org/showpost.php?p=7279783&postcount=18).

I also included the options below into the "Device" Section ([original thread](http://ubuntuforums.org/showthread.php?p=7121605)):

```
	Option	       "EXAOptimizeMigration" "true"
	Option	       "MigrationHeuristic" "greedy"
	VideoRam       [color=#CC0000]262144[/color]
```

The value in red will depend on your available memory. This setting is deprecated and might not work. See discussion [here](http://ubuntuforums.org/showthread.php?p=7121605).

[quote]
**[COLOR="Red"]Warning:[/COLOR]** In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert these option. 
[/quote]



> **[color=#CC0000]CPUFREQ tweak:[/color]** this helps to get more juice from your processor ([original thread](http://ubuntuforums.org/showpost.php?p=7394265&postcount=7)).

Run this command:

```
gksudo gedit /etc/init.d/ondemand
```

Then find **echo -n ondemand > $CPUFREQ** and replace it with **echo -n performance > $CPUFREQ**


> **[color=#CC0000]Performance tuning with ''swappiness'':[/color]** [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The swappiness parameter controls the tendency of the kernel to move processes out of physical memory and onto the swap disk. Because disks are much slower than RAM, this can lead to slower response times for system and applications if processes are too aggressively moved out of memory.

    * swappiness can have a value of between 0 and 100
    * swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible
    * swappiness=100 tells the kernel to aggressively swap processes out of physical memory and move them to swap cache
    * Ubuntu uses a default setting of swappiness=60

Reducing the default value of swappiness will probably improve overall performance for a typical Ubuntu desktop installation. A value of swappiness=10 is recommended, but feel free to experiment. Note: Ubuntu server installations have different performance requirements to desktop systems, and the default value of 60 is likely more suitable. 

How to change the swappiness value

```
      gksudo gedit /etc/sysctl.conf
```

Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:

```
      vm.swappiness=10
```

Save the file and reboot.



*UKeywords: 649167 2009 june tutorial optimization performance*

---

### Post by binary10 on 2009-05-07
Agreed about the ext3 to ext4 re-formatting - it's daunting deciding to make this change but it's brought my old samsung X25 (Intel(R) Pentium(R) M processor 1.86GHz stepping 08) with ATI (Mobility X600) back to life. Even seems quicker than my Lenovo.

---

### Post by lovinglinux on 2009-05-07
> **binary10 said:**
> Agreed about the ext3 to ext4 re-formatting - it's daunting deciding to make this change but it's brought my old samsung X25 (Intel(R) Pentium(R) M processor 1.86GHz stepping 08) with ATI (Mobility X600) back to life. Even seems quicker than my Lenovo.

I'm still trying to digest the speed of data transfer exchange. I'm asking myself if it was like this before. I just measured 15 seconds to copy a 800Mb file from one partition to another. :) I could be wrong, because I never bothered to measure it with ext3, but it seems much faster.

---

### Post by gnickers on 2009-05-07
My 1.5 gig sata hard drive is running MUCH slower since the upgrade from 8 to 9.04, doing a Save in open office takes seconds to load the dialog box, transmission dialogs grey out while waiting for the drive, brasero dialogs are slow to come up. I checked the system monitor and when idling 2 of the 4 cores are at 100% sometimes. The system is a dual xeon 3.2 ghz with 4 gig ram, nvidia 8800. Appz run fine until they have to read/write to the disk and then they have to wait. I have a second machine with the same specs but with SCSI drives and it has no problem - no change in speed and the older single cpu box with only a 160 gig sata runs fast on 8. 

Frustrating, but i am sure it will get fixed when the patches start arriving...I might try the python suggestion.

---

### Post by lovinglinux on 2009-05-08
> **gnickers said:**
> My 1.5 gig sata hard drive is running MUCH slower since the upgrade from 8 to 9.04, doing a Save in open office takes seconds to load the dialog box, transmission dialogs grey out while waiting for the drive, brasero dialogs are slow to come up. I checked the system monitor and when idling 2 of the 4 cores are at 100% sometimes. The system is a dual xeon 3.2 ghz with 4 gig ram, nvidia 8800. Appz run fine until they have to read/write to the disk and then they have to wait. I have a second machine with the same specs but with SCSI drives and it has no problem - no change in speed and the older single cpu box with only a 160 gig sata runs fast on 8. 

Frustrating, but i am sure it will get fixed when the patches start arriving...I might try the python suggestion.

Are you still using ext3 or did you formatted the drives with ext4?

---

### Post by lovinglinux on 2009-05-23
Another thing that helped was including this in /etc/X11/xorg.conf

```

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

These will enable direct rendering and compositing. I don't know exactly what they do, but I had a huge flash performance boost after this, Firefox is much more responsive and fast and the system is more responsive too.

---

### Post by slipperypig on 2009-06-03
I added the changes to xorg.conf on my Jaunty system and it made a HUGE difference for me. I also did this separately:

[http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/](http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/)

essentially changing
echo -n ondemand > $CPUFREQ
to
echo -n performance > $CPUREQ
in
/etc/init.d/ondemand

both of them seemed to improve my performance greatly. Reading more about it here and elsewhere it seems like there are other issues at play since some people didn't experience the difference I did, but i thought i should post that my results were awesome - i can listen to blip.fm again!

---

### Post by lovinglinux on 2009-06-03
> **slipperypig said:**
> I added the changes to xorg.conf on my Jaunty system and it made a HUGE difference for me. I also did this separately:

[http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/](http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/)

essentially changing
echo -n ondemand > $CPUFREQ
to
echo -n performance > $CPUREQ
in
/etc/init.d/ondemand

both of them seemed to improve my performance greatly. Reading more about it here and elsewhere it seems like there are other issues at play since some people didn't experience the difference I did, but i thought i should post that my results were awesome - i can listen to blip.fm again!

Thanks for the tip. I'm worried about doing the CPUREQ change because the CPU Frequency monitor in the panel doesn't work for me. It says my system is misconfigured or doesn't support CPU Frequency scaling. I will research about this a little bit more.

---

### Post by HunterThomson on 2009-06-06
There is no need to worry about having two partitions with different file-systems.

It is common place to do this. Some even sugjest to use the best file-system for each directory.

Like using reiserfs for /var. Reiserfs is vary fast with a bunch of small files. And, using XFS for your /home partition which is vary good for large files like your videos in your /home directory. And, using ext3 for your / partition because ext3 is rock sold and you need your / partition to be rock sold.

---

### Post by martinbaselier on 2009-07-08
Changing the ondemand script, to make ondemand become performance is a bit strange. I personally added the following line /etc/rc.local

echo -n ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

I'm using a laptop, so ondemand has my preference. 

You could change this to performance if you want your cpu always running top speed. If you have multiple cpu's you'll need lines for all the cpu's, at least I'd think so. Check /sys/devices/system/cpu to be sure.

---

### Post by lovinglinux on 2009-07-08
> **martinbaselier said:**
> Changing the ondemand script, to make ondemand become performance is a bit strange. I personally added the following line /etc/rc.local

echo -n ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

I'm using a laptop, so ondemand has my preference. 

You could change this to performance if you want your cpu always running top speed. If you have multiple cpu's you'll need lines for all the cpu's, at least I'd think so. Check /sys/devices/system/cpu to be sure.

Thank you.

---

### Post by photoscotty on 2009-09-07
I have two packages that come up when I try to remove Python 2.5 using synaptic (scribus and ubuntustudio-graphics), but I notice that both are also listed under Python 2.6.

Does this mean the programs would still run if I were to remove 2.5?

---

### Post by lovinglinux on 2009-09-08
> **photoscotty said:**
> I have two packages that come up when I try to remove Python 2.5 using synaptic (scribus and ubuntustudio-graphics), but I notice that both are also listed under Python 2.6.

Does this mean the programs would still run if I were to remove 2.5?

If Synaptic reports that they will be removed when removing python 2.5, then they depend on it and will be uninstalled if you remove pyhton 2.5. If they are not included in the list when you try to remove python 2.5, then it is safe to say that they will use python 2.6 instead.

Nevertheless, it has been some time since Jaunty was released and this problem might be already fixed on recent kernels. I haven't used python 2.5 since I wrote this tutorial, so I can't confirm that.

---

### Post by necron53 on 2009-09-08
Hey Lovinglinux,  Thanks for your post. I had some issues with performance specially when watching youtube videos. I disabled remote desktop and there was a huge improvement in performance. My laptop is performing tasks faster,
We newbies cannot thank you guys enough for making  our ubuntu journey a lot easier.:P

---

### Post by lovinglinux on 2009-09-08
> **necron53 said:**
> Hey Lovinglinux,  Thanks for your post. I had some issues with performance specially when watching youtube videos. I disabled remote desktop and there was a huge improvement in performance. My laptop is performing tasks faster,
We newbies cannot thank you guys enough for making  our ubuntu journey a lot easier.:P

You are welcome ;)

---

### Post by renkinjutsu on 2009-09-12
> **martinbaselier said:**
> Changing the ondemand script, to make ondemand become performance is a bit strange. I personally added the following line /etc/rc.local

echo -n ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

I'm using a laptop, so ondemand has my preference. 

You could change this to performance if you want your cpu always running top speed. If you have multiple cpu's you'll need lines for all the cpu's, at least I'd think so. Check /sys/devices/system/cpu to be sure.

does rc.local get executed before or after the init.d scripts? The scaling settings i put in there never stick... i have to execute it again in the terminal after logging in ```
sudo /etc/rc.local
```

---

### Post by nico_forgot on 2009-09-16
@hunterthomson: i completely agree that different filesystems on different partitions makes a huge difference. since jaunty supports ext4 so well i've made both my /boot and / partitions ext4. i have considered making my / partition extended with logicals for /var and /usr but never do. thoughts?

my /home is still in ext3. would you suggest xfs for a /home more than ext3? does xfs perform writeback?

it's super fast and totally stable. on the one hand there's the old if it ain't broke don't fix it but on the other this is linux :) it doesn't need to be broken to get a fix.

cheers - nico

---

