---
title: "CPU fan running too fast"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by 67GTA on 2007-02-24
I have recently switched from Windows to Ubuntu. I have installed all of my required drivers. I am not sure about my CPU fans. They seem to run faster with Ubuntu than with Windows. They really go crazy when a 3D screensaver runs, but not when I watch a video. Is this normal for Linux or do I need to configure something?

Intel Pentium 4 945GCZ board
ATI Radeon X1600

---

### Post by Richard Kut on 2007-02-27
Hello 67GTA! I had the same experience on my laptop when I switched from Windows to Ubuntu. It seems that the settings which trigger the fans are different between the two operating systems. 

I monitor my temperature, and try to keep it under 60 degrees Celsius as much as possible. Usually raising the laptop off the table by resting it on some books instead of right on the table works for me. This seems to allow for more air flow towards the fan openings on the bottom of the lappy. 

I read about a guy somewhere who actually stuck 1 inch rubber feet to the bottom of his lappy so that it always has good airflow! I won't be doing that, but I can see how that would help to keep the fans from coming on.

Getting back to the technical aspect: there may be some settings that you can tweak. I found some links that might be of interest, here:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72775]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72775")

and here:

[https://launchpad.net/ubuntu/+bug/22336]("https://launchpad.net/ubuntu/+bug/22336")

and what looks like a fix here:

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans")

Please note that I have not tried the above fix, and so I cannot vouch for it in any way. In other words, proceed with caution, your mileage may vary, etc, etc.

I hope that my ramblings helped in some way. Good luck!

---

### Post by raffytaffy on 2007-02-28
> **Richard Kut said:**
> Hello 67GTA! I had the same experience on my laptop when I switched from Windows to Ubuntu. It seems that the settings which trigger the fans are different between the two operating systems. 

I monitor my temperature, and try to keep it under 60 degrees Celsius as much as possible. Usually raising the laptop off the table by resting it on some books instead of right on the table works for me. This seems to allow for more air flow towards the fan openings on the bottom of the lappy. 

I read about a guy somewhere who actually stuck 1 inch rubber feet to the bottom of his lappy so that it always has good airflow! I won't be doing that, but I can see how that would help to keep the fans from coming on.

Getting back to the technical aspect: there may be some settings that you can tweak. I found some links that might be of interest, here:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72775]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72775")

and here:

[https://launchpad.net/ubuntu/+bug/22336]("https://launchpad.net/ubuntu/+bug/22336")

and what looks like a fix here:

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans")

Please note that I have not tried the above fix, and so I cannot vouch for it in any way. In other words, proceed with caution, your mileage may vary, etc, etc.

I hope that my ramblings helped in some way. Good luck!

funny i ran across this..i have succesfully mounted a 12volt car amp fan under my desk facing the bottom of my laptop and this has made a huge drop in temp! 20~ celcious less. i have placed a filter between the fan and the laptop to collect any posible dust..and have sealed this enviroment with one outlet with another filter. i may even take pictures and show u guys how i did this exactly

---

### Post by Richard Kut on 2007-03-01
That sounds really cool (pun intended)! I would love to see the pictures!

---

### Post by raffytaffy on 2007-03-02
> **Richard Kut said:**
> That sounds really cool (pun intended)! I would love to see the pictures!

[http://i48.photobucket.com/albums/f212/rafbak/0302071151.jpg](http://i48.photobucket.com/albums/f212/rafbak/0302071151.jpg)  -- bottom view

[http://i48.photobucket.com/albums/f212/rafbak/0302071152.jpg](http://i48.photobucket.com/albums/f212/rafbak/0302071152.jpg)  -- top view

---

### Post by hardyn on 2007-03-02
I saw that one machine was a vaio... is it P-M based?  are both of them P-M based?

if so, fall back to the i386 kernel, not generic... there is a bug with the SMP kernels and P-M sony / asus, and your machine will run hot becuase the processor is always pulling a 50% idle load.

something to check out anyway, if your P-M

---

### Post by raffytaffy on 2007-03-02
> **hardyn said:**
> I saw that one machine was a vaio... is it P-M based?  are both of them P-M based?

if so, fall back to the i386 kernel, not generic... there is a bug with the SMP kernels and P-M sony / asus, and your machine will run hot becuase the processor is always pulling a 50% idle load.

something to check out anyway, if your P-M

yes its pentium-M sony vaio. so youre saying i should install 

"linux-image-2.6.17-11-386" from synaptic package manager?

---

### Post by hardyn on 2007-03-02
the short of it, yes.

check your system monitor, if you cpu load bounces between 20%-60% and wont settle down to like 5%, you have the bug, and yes.  if no... then you will not benefit, and your machine is just running with loud fans.

depending on your video, some of the OSS drives are really efficient. and will over work the video... i notice NV to be really bad... you might do better with a CSS driver if you have anything more than integrated intel video.

good luck.

---

### Post by raffytaffy on 2007-03-02
> **hardyn said:**
> the short of it, yes.

check your system monitor, if you cpu load bounces between 20%-60% and wont settle down to like 5%, you have the bug, and yes.  if no... then you will not benefit, and your machine is just running with loud fans.

depending on your video, some of the OSS drives are really efficient. and will over work the video... i notice NV to be really bad... you might do better with a CSS driver if you have anything more than integrated intel video.

good luck.

i dont know how to thank you...everything you said has turned out true...i use conky to monitor my system..and sure enough it was at a constant 50-60% load... so i went ahead and installed the linux immage...rebooted tried to install nvidia...durrrrr silly me..forgot the headers...went ahead installed that...rebooted...now i notice conky says 10-15% avg load...wow...im sooo thankfull...you prolly saved my laptop a few months if not years. Now i see this update for linux-restricted-modules-generic....can this interfere anyhow since im runing -i386?

---

### Post by hardyn on 2007-03-02
you can actuly remove it... it will sit idle and not do anything, 
but it will still recieve updates though the synapic update manager... i left mine, its up to you.

... you still have a problem though... you have a big hole in your desk ;)

---

### Post by raffytaffy on 2007-03-03
> **hardyn said:**
> you can actuly remove it... it will sit idle and not do anything, 
but it will still recieve updates though the synapic update manager... i left mine, its up to you.

... you still have a problem though... you have a big hole in your desk ;)

Also if i want to compile my own kernel...what options would i have to make so that the end product wasnt SMP ? does the I/O scheduler have anything to do with the kernel beign smp? or would i just have to pick "386" from processor family instead of "pentium M" as i have before? found the proper options and now i have custom kernel 2.6.20.1 non-smp. and the temp is good and stable and cpu load is as it should be.

---

### Post by Prometheus.172214 on 2007-03-03
Big Chief no put hole in desk. Big chief run the i386 thingy from the Synaptics Package Manager thingy..........

**raffytaffy** : Your idea is pretty cool. It does improve cooling . . . . I would not dare it though, the desks in our office have stone tops and I for one have no intentions of trying this there :-)  


Question: I have a Hewlett Packard M2201 TU which is based on the P - M and this is my main workhorse, I don't see this problem on it, but I am considering a batch installation on four more units here and am wondering if I should start with the 386 version from start. If there is no overheating issue, does this change in version have any side effects ? If it is something within a week of the installation, I would not worry much, because I would use the first week to test. But if there is a delayed side effect of this change, I will be in trouble with 4 units out of use, till we patch the kernel.

---

### Post by raffytaffy on 2007-03-03
well to be honest i didnt get to use the "generic kernel" since as soon as i reboot after install i compiled my own -(which was SMP ) then i started noticing the overheating issue.  Today i recompiled my kernel without SMP and woilla.. it runs pefect. So basically u have to find out if the generic kernel is SMP or not. if it is..then yes def go for the 386 as mentioned above.

---

### Post by Prometheus.172214 on 2007-03-04
That sounds good to me. I did the batch install like I said. Everything looks good, except that one unit needs some tweaking, we tried a stunt with the wired connection. I think we might have to blacklist the device and reinstall it to solve the problem. Other than that, evrything works solid.

---

