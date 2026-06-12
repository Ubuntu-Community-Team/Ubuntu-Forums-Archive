---
title: "Hard drive light always on"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by clever on 2006-02-25
I'm using 5.10 and everything is working fine.  I just noticed that the hard drive light on the front of my computer case is constantly on.  

Someone on the #ubuntu IRC channel told me to check if the updatedb was running by executing "ps -A | grep updatedb".  It was not running, so that's not the reason.

Any ideas why this is happening?  Thanks...

---

### Post by rfruth on 2006-02-25
Does the light at least modulate, if so and everything is okay I wouldn't sweat it :rolleyes:

---

### Post by clever on 2006-02-26
Actually, no, it never blinks at all.  The light stays on constantly, whether there is any hard drive activity or not.

---

### Post by rfruth on 2006-02-26
Yikes the LED is on solid, this isn't normal, sounds like a hardware issue to me, hope you can hear it when the hard disk is working !  (just out of curiosity does the light come on the moment U apply power) :confused:

---

### Post by mjwood0 on 2006-02-26
Where did you get your computer?  I only ask since it almost sounds like your HD light isn't wired properly to the Motherboard.  If it comes on as soon as you apply power, I'd get the manual for your MB and verify it's connected properly.  

Good luck!

---

### Post by WildTangent on 2006-02-27
Ah yes, it sounds like it could be a wrongly wired cable. We once had an employee where I worked who would mix up the HDD and power LEDs all the time, and my boss would start freaking out when he saw the HDD light on constant, and the power coming on and off :)

-Wild

---

### Post by clever on 2006-02-27
The machine is a Dell SC420.  The hard drive light works fine when I boot into Windows, so I don't think there's any wiring issue.  It's only when I'm in Ubuntu that there's a problem.

The light is off/blinks normally at boot and until just after the Grub screen.  When the Ubuntu splash screen comes up during boot, the first item it lists is "Loading modules".  It's during that time that the hard drive light comes on and stays on.  It goes through the rest of the boot sequence fine, and I can log in and use the machine fine.  It's just that the light is always on.  I do hear hard drive activity when there's, well, any activity, but otherwise the drive is perfectly quiet.

Strange, eh?

---

### Post by mjwood0 on 2006-02-27
Hmm... Seeing that it works during boot and in Windows, sounds like a strange driver type problem.

Sorry I can't be more help.  I'm still a little new to this myself!

---

### Post by davidmoore83 on 2006-03-26
[QUOTE=clever]The machine is a Dell SC420.  The hard drive light works fine when I boot into Windows, so I don't think there's any wiring issue.  It's only when I'm in Ubuntu that there's a problem.

The light is off/blinks normally at boot and until just after the Grub screen.  When the Ubuntu splash screen comes up during boot, the first item it lists is "Loading modules".  It's during that time that the hard drive light comes on and stays on.  It goes through the rest of the boot sequence fine, and I can log in and use the machine fine.  It's just that the light is always on.  I do hear hard drive activity when there's, well, any activity, but otherwise the drive is perfectly quiet.

Strange, eh?[/QUOTE]

I have this exact same issue! I wish i could fix it!

---

### Post by clever on 2006-03-28
[QUOTE=davidmoore83]I have this exact same issue! I wish i could fix it![/QUOTE]

Well ok, so now there's two of us.  Should we file a bug report?  I am willing to help in whatever way would be useful to get this resolved.

---

### Post by frodon on 2006-03-28
Another idea, the "noatime" option allow to disable the ext3 atime default feature which made frequent hdd accesses to update the time parameter of files, more details here : [http://doc.gwos.org/index.php/TweakExt3#Remove_update_of_access_time_for_files](http://doc.gwos.org/index.php/TweakExt3#Remove_update_of_access_time_for_files)
Information on what noatime option is : [http://everythingsolaris.org/articles/ftat/frameset.html](http://everythingsolaris.org/articles/ftat/frameset.html)

I don't think it's your problem but it will reduce the filesystem activity.

---

### Post by davidmoore83 on 2006-03-28
[QUOTE=clever]Well ok, so now there's two of us.  Should we file a bug report?  I am willing to help in whatever way would be useful to get this resolved.[/QUOTE]

I found this issue is resolved in Dapper Flight 5. I think Breezy doesn't support my Raid/Disk controller

---

### Post by wsmoser2004 on 2006-03-30
I used to have this problem as well on my laptop (very bad for battery life).  I found a package that I believe is called **laptop-mode** (NOT **laptop-mode-tools**) which seems to reduce hard disk activity.  You should be able to just download the package (you might already have it, it installed with Breezy for me) and then issue ```
sudo laptop-mode start
``` from a terminal.  It works great for me, and I assume it would work fine on a desktop system as well.  The only problem is that you need to issue the above command every time you start the computer, but I think I created a script that runs at boot to execute the command.  

As far as I can tell, the only thing **laptop-mode** does is reduce the frequency of reads/writes to the disk.  It doesn't spin down the disk or anything fun like that.  Good luck.

---

### Post by clever on 2006-04-05
It doesn't feel to me like the hard drive is constantly being accessed, though I guess I'm not sure.  My assumption was just that the light was on, even when the drive wasn't being accessed.

Is there any hard drive monitoring software I can use to see whether the disk is really being accessed or not?

---

### Post by fozeyuk on 2007-10-22
my problem with the light staying on has only started since i upgraded to 7.10 another thing that it does is not shudown when i click shut down.

---

### Post by clever on 2007-10-22
> **fozeyuk said:**
> my problem with the light staying on has only started since i upgraded to 7.10 another thing that it does is not shudown when i click shut down.

I haven't had this problem for a long time.  When I started using Feisty, the problem was gone.  I haven't installed Gutsy yet, but I just fired up the Live CD and my hard drive light is working normally.

I'm not having any problems with the Shut Down command either.

---

