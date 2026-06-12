---
title: "Troubleshooting suspend and hibernate"
date: 2009-05-01
forum: Hardware
---

### Post by Mantrasong on 2009-05-01
I've seen dozens of threads posted on this forum about suspend and hibernate problems, many of them left orphaned and apparently unsolved. When I came looking for hints to solve my own problem (unable to either suspend or hibernate), all I've found is a confusing collection of threads mostly related to waking from a low-power state, rather than getting into it in the first place.

So what I'd like to know is if there is a general procedure for troubleshooting suspend/resume problems - logs to check, scripts/commands to run, what to do when you get a blinking cursor on a black screen, etc. I found [this thread]("http://ubuntuforums.org/showthread.php?t=505890"), but I'd like to start with steps less drastic than recompiling my kernel, and I suspect the information there is rather out of date anyway.

I can give more information on my personal problem, but for now I'd really just like general troubleshooting information, so others can use it too.

---

### Post by Mgiacchetti on 2009-05-08
Agreed, we should have a simple resolution process for this problem.  I am experiencing the same issues, and would like some information on at least where to start looking for the problem.

I was in #ubuntu on freenode, and they said it is motherboard specific.  So far, that's all I know.


Hmm.. on a whim i checked my kern.log and found that somehow i had disabled my Swap partition....

Now my system suspends and resumes fine.

I am just unsure if hibernation works.  It goes down, but on resume, it boots as normally, not resume from hibernation.

---

### Post by freonchill on 2009-05-08
ive asked the question in 2-3 of the "abandoned threads" (one of which i started) on what to do, dmesg, logs, etc

no one that knows what to do has the time/seems to care/etc to enlighten us.

---

### Post by Mantrasong on 2009-05-08
Ok, so due to the resounding silence on this issue, I've done my best to find and compile a general troubleshooting guide. I consider this a work in progress as I have the time to do the research to improve the list.

DISCLAIMER: I don't know any more about this issue than the average linux user (arguably less, actually), so I can't offer help beyond telling people where to look and (more or less) what to look for. If anyone has suggestions, additions, or would like to make this guide more helpful, *please* say so.

Because a lot of suspend/hibernate problems require a hard restart, I'm including this as general helpful information: 
Before doing a hard reboot, try the following combination:
hold down Alt+SysRq(Print Screen), and then type REISUB.
This combination should stop all programs, unmount all drives, and reboot the computer, more safely than just pressing the power button
If this doesn't work, then you can go ahead and hold down the power button.

Most of my information was gathered from these sites, so you may find it useful to read them, too.
[https://wiki.ubuntu.com/DebuggingACPI#Filing%20a%20Bug%20Report](https://wiki.ubuntu.com/DebuggingACPI#Filing%20a%20Bug%20Report)
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)
[http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890)

**[SIZE="4"]Suspend/Hibernate menu items not shown[/SIZE]**
If you don't have the suspend or hibernate menu items, you need to find out why they are disabled.

1. **Check to make sure that Gnome Power Manager is enabled**
Navigate to your login items (System -> Preferences -> Login Items), and scroll down to make sure that the Gnome Power Manager is checked.

2. **Make sure Gnome Power Manager is behaving**
Open up a terminal, and run the command 
```
gnome-power-manager restart
```
If suspend/hibernate appear now, then create a launcher for that command in your login items.

3. **Check if the HAL detectecd a sleep handler**
```
lshal | grep can_suspend
```

If this returns false, you need to check your BIOS settings and make sure suspend is enabled there.

4. **Check to see if the ability is there, but disabled**
If the previous check returned true, it's possible that the ability to suspend/hibernate has been disabled. You can check this by running
```
gconftool-2 -R /apps/gnome-power-manager | grep can
```
You should get something like
```

can_suspend = true
can_hibernate = true

```
If either of those are false type
```
gconf-editor
```
Navigate to apps/gnome-power-manager/general and change the appropriate values to true

5. **Determine why suspend/hibernate isn't offered**
If the one you're having problems with isn't shown at all, then follow the instructions in the [Debugging Gnome Power Manager]("https://wiki.ubuntu.com/DebuggingGNOMEPowerManager#Finding%20out%20why%20suspend%20or%20hibernate%20aren%27t%20offered") page to determine why not.


**[SIZE="4"]System freezes when suspending/hibernating[/SIZE]**
1. **Check Swap** 
Swap is essential for suspending and hibernating. If your swap isn't on and active, it appears to generate the "blinky cursor on screen when trying to suspend/hibernate," but it could manifest in other ways as well. 
You may also experience problems if your swap is smaller  than the amount of ram you have installed, or if you're using a swap file rather than a swap partition.
```

	cat /proc/swaps
	swapon -s
```
 
You should get something like this:
```

Filename				Type		Size	Used	Priority
/dev/sdb2                               partition	8393952	4716	-1
```


2. **Check your hardware** 
Search the [hardware incompatibility list]("http://ubuntuforums.org/showthread.php?t=361237") stickied at the top of this forum, and the forums to see if anyone has had problems with similar hardware and drivers. The biggest culprit appears to be graphics drivers, so check for proprietary drivers and search for them, first. If you have a laptop, try searching the make and model of the computer you're using.
People seem to frequently have success blacklisting graphics cards


Those are the easy fixes. Unfortunately, suspend and hibernate problems seem to be incredibly complex and difficult to debug, so next we move on to data collection.

3. **Check logging information** 
Ideally, you should do this right after rebooting from a failure, so the problems will be the last thing logged. 
Logs to check:
Kernel log (kern.log):
[INDENT]I believe you are looking for lines containing "PM:" to indicate sleep and wake calls
The line "Back to C!" indicates the point at which the kernel resumes[/INDENT]
Debug log (debug):
	[INDENT]Contains mostly the same information as the kernel log, but you may find something helpful there[/INDENT]

Code to run:
dmesg
[INDENT]Like in the kernel log, you're looking for the block of text starting with PM, or containing forcedeth[/INDENT]

**[SIZE="3"]If your problem occurs while suspending:[/SIZE]**
**Test ACPI scripts** 
Fire up your friendly neighborhood command prompt, and, depending on the function you're having problems with, run either pm-suspend, or pm-hibernate, and look for any errors scrolling by. 

**Test GNOME power manager**
Still in the command prompt, try these commands to bypass the GNOME power manager, and send commands directly to the HAL

Hibernate
 ```

dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate

```
Suspend
```

dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0 

```

[SIZE="3"]**If the problem occurs during resume:**[/SIZE]
There is, unfortunately, less helpful information here, though it might be beneficial to run the same suspend/hibernate commands. Otherwise, check the logs.

If it makes it all the way into standby/hibernate, restart the computer, and keep an eye on the disk indicator light to see if it blinks. If so, then it has  loaded the image, so the problem is further on than that.

At this point, if you haven't found a solution, you can try posting any logs that appear to have errors, and the output of the suspend/hibernate commands, if you saw errors there, on the forums, but you may end up needing to file a bug report. If you go that route, I suggest you read [this]("https://wiki.ubuntu.com/DebuggingACPI#Filing%20a%20Bug%20Report"), and [this]("https://wiki.ubuntu.com/DebuggingGNOMEPowerManager") before filing a bug report, to make both your life and those of the developers easier.

---

### Post by TiredBird on 2009-05-09
> **Mantrasong said:**
> ...a general troubleshooting guide.
Many thanks for your help. Considering the many unanswered pleas for help I've seen and made on this subject, your efforts will be appreciated.

However, (you had to know this was coming :P), my problem begins before your help does. When I click on the shut down button, (either in the menu or the one I've added to the icon panel, [Ubuntu 8.10 i386 and Ubuntu 9.04 amd64 - both on a custom desktop ASUS K8N with AMD64]), I don't usually get offered the option of suspending or hibernating - just "Shut Down" or "Restart".

> **Mantrasong said:**
> 
Most of my information was gathered from these sites, so you may find it useful to read them, too.
[https://wiki.ubuntu.com/DebuggingACPI#Filing%20a%20Bug%20Report](https://wiki.ubuntu.com/DebuggingACPI#Filing%20a%20Bug%20Report)
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)
[http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890)

Admittedly, I have not read any of the these, but I am about to.

> **Mantrasong said:**
> 
...run either pm-suspend, or pm-hibernate,...

I have run both of these from the command line and I am happy to say that the result is as it should be. However, I can't get the GUI to give me these choices. 

One final thing - when I do a normal shutdown, I can bring the system back to life by wiggling the mouse or tapping a key on the keyboard. However, when I am able to do a suspend or hibernate I can only restart by pressing the power button on the CPU box. 

I suspect that the foregoing is somehow related to my BIOS settings. I have an American Megatrends V02.54 BIOS. The ACPI Suspend Mode is set at 'S1' but 'S3' is also an option. I have ACPI 2.0 Support and ACPI APIC support enabled. PME Resume - Disabled; RI Resume - Disabled; RTC Resume - Disabled; Resume on PS/2 Mouse - Enabled; Resume on PS/2 Keyboard - Enabled; and Restore on AC Power Loss - Last State.

Any further suggestions you have to offer will be greatly appreciated and thanks again for your efforts thus far.

---

### Post by Mantrasong on 2009-05-09
> **TiredBird said:**
> However, (you had to know this was coming :P), my problem begins before your help does. When I click on the shut down button, (either in the menu or the one I've added to the icon panel, [Ubuntu 8.10 i386 and Ubuntu 9.04 amd64 - both on a custom desktop ASUS K8N with AMD64]), I don't usually get offered the option of suspending or hibernating - just "Shut Down" or "Restart".


Hopefully you've found this already, but if you haven't (and for others to come searching), this is the information you're looking for:
[Debugging GPM:Finding out why suspend or hibernate aren't offered]("https://wiki.ubuntu.com/DebuggingGNOMEPowerManager#Finding%20out%20why%20suspend%20or%20hibernate%20aren%27t%20offered")
[GPM FAQ: Why does GNOME Power Manager not let me suspend or hibernate]("http://live.gnome.org/GnomePowerManager/FAQ#head-5d4d7bb306ca154c956e3ef69dae036942f6cf40")

> 
One final thing - when I do a normal shutdown, I can bring the system back to life by wiggling the mouse or tapping a key on the keyboard. However, when I am able to do a suspend or hibernate I can only restart by pressing the power button on the CPU box. 

Just to make sure I'm clear, do you have to restart when doing a suspend or hibernate, or does the system fail to shut down after successfully suspending and resuming? What happens when you try to use the menu buttons to shutdown?

I'm reasonably certain that I saw this problem solved on the forums, but I can't seem to find the thread right now, but it might be worthwhile to look around to see if you can find it.

---

### Post by mariner09 on 2009-05-10
One of the biggest suspend/reume bugs is having UXA enabled in /etc/X11/xorg.conf for Intel video chipsets.

---

### Post by TiredBird on 2009-05-10
Thanks for all of your help. Progress is definitely being made but still no cigar.
> **Mantrasong said:**
> ...this is the information you're looking for...
I performed the tests as specified in the two links. Following are the results:

```

xxx@amd64:~$ gconftool-2 -R /apps/gnome-power-manager | grep can
  can_suspend = true
  can_hibernate = true
xxx@amd64:~$ dbus-send --session --print-reply --dest="org.freedesktop.PowerManagement" --type=method_call --reply-timeout=6000 /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.CanSuspend
method return sender=:1.44 -> dest=:1.48 reply_serial=2
   boolean true
xxx@amd64:~$ gconftool-2 -g /apps/gnome-power-manager/general/can_suspend
true
xxx@amd64:~$ polkit-auth | grep power-management.suspend
org.freedesktop.hal.power-management.suspend
xxx@amd64:~$ hal-device | grep power_management.can_suspend
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
xxx@amd64:~$ pm-is-supported --suspend || echo "Not supported"
xxx@amd64:~$ 

```

My interpretation of the foregoing is that hibernate and suspend should be working, and they do from the command line, but they don't appear in the gui menus, at least not usually. (They are there sometimes but I can't figure out what thats related to.)

> **Mantrasong said:**
> Just to make sure I'm clear, do you have to restart when doing a suspend or hibernate, or does the system fail to shut down after successfully suspending and resuming? What happens when you try to use the menu buttons to shutdown?

This problem was solved by information I found in another thread. Apparently, when I had done a full shutdown, the BIOS settings were starting it back up from mouse or keyboard activity. However, when I  did a suspend or hibernate the BIOS still believed the system to be on and did not reactivate it. In order to get it to work I had to change the values in /proc/apci/wakeup which I did with:
```

echo PS2K > /proc/apci/wakeup

```
I based that on information contained in another thread. (I'm trying to find it so you can have the info. I'll let you know as soon as I find it.)

However, further to your last question - my desktop, although still new, has been seriously tweaked. It doesn't look anything like the original install. I am using the 'Main Menu' applet to provide my menu and using the 'Shut Down' applet as my usual means of shutting down. The 'Shut Down' applet and the shutdown item on the 'Main Menu' applet both invoke the same module but I have yet to figure out what that is.

---

### Post by TiredBird on 2009-05-10
Here's the thread that provided the help for wake by mouse or keyboard.

[http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

---

### Post by TiredBird on 2009-05-10
> **mariner09 said:**
> One of the biggest suspend/reume bugs is having UXA enabled in /etc/X11/xorg.conf for Intel video chipsets.

I've checked the referenced file and it is empty.

---

### Post by Mantrasong on 2009-05-10
> **TiredBird said:**
> 
My interpretation of the foregoing is that hibernate and suspend should be working, and they do from the command line, but they don't appear in the gui menus, at least not usually. (They are there sometimes but I can't figure out what thats related to.)


Have you tried restarting the gnome power manager?
```

gnome-power-manager restart

```

---

### Post by TiredBird on 2009-05-10
> **Mantrasong said:**
> 
Have you tried restarting the gnome power manager?

We are definitely making progress - almost there but not quite. Thanks so much for your help.

I did as you recommended and the menu items appeared. However, when I shut down and restarted, they were gone again. I then did a little experimentation and learned that any invocation of the 'gnome-power-manager' for whatever reason, (I tried start, stop, restart, even some commands that I knew would not be valid), caused the menus to reappear. However, any shutdown causes them to revert to the menu with no hibernate and no suspend.

It looks as if any execution of 'gnome-power-manager' for whatever reason causes something to be reset that gives me the hibernate and suspend options. Unfortunately, whatever it is doing goes away with a reboot.

Any more ideas?

---

### Post by Mantrasong on 2009-05-10
> **TiredBird said:**
> 
It looks as if any execution of 'gnome-power-manager' for whatever reason causes something to be reset that gives me the hibernate and suspend options. Unfortunately, whatever it is doing goes away with a reboot.

Any more ideas?

It's a hack, but the solution they used in [this thread](http://ubuntuforums.org/showthread.php?t=1051664) is to add the command "gnome-power-manager restart" to run as a login item.

---

### Post by TiredBird on 2009-05-10
> **Mantrasong said:**
> 
...the solution...


I'm sure that would have worked but I think I found the problem.

After my last post I checked all the automatic startups. The power manager was not be being started. I don't know whether that was because I had inadvertantly shut it off or because this is a desktop and shouldn't need it.

In any event, I added it back to the automatic startups and by jove it seems to work now.

I can't tell you how much I appreciate all the help you've given me. If ever I can do anything to help you, please do not hesitate to ask.

---

### Post by TiredBird on 2009-05-10
My problems related to suspend and hibernate have been solved thanks to the posts in this thread and [http://ubuntuforums.org/showthread.php?t=814939]("http://ubuntuforums.org/showthread.php?t=814939").

---

### Post by Mantrasong on 2009-05-11
> **TiredBird said:**
> My problems related to suspend and hibernate have been solved thanks to the posts in this thread and [http://ubuntuforums.org/showthread.php?t=814939]("http://ubuntuforums.org/showthread.php?t=814939").

Congratulations :) I'll update the troubleshooting post/

---

### Post by Mike.lifeguard on 2009-05-12
> **mariner09 said:**
> One of the biggest suspend/reume bugs is having UXA enabled in /etc/X11/xorg.conf for Intel video chipsets.

Is there a bug filed for this? Is there a known workaround? What problems are known to be caused here? For myself, the only problem is that my system won't wake from hibernation. It seems to enter hibernation normally, but it boots from scratch instead of from a hibernated state. I don't know whether it actually does hibernate properly (it certainly seems to; it doesn't shut down in the normal manner).

---

### Post by v1nsai on 2010-03-17
Nothing I found on this thread was working for me, but I still think it's a great idea to keep hibernation troubleshooting (semi) organized.

My hibernation suddenly stopped working after doing fine for months.  I think I've gotten everything back to normal by nuking my swap, updating the UUID's in appropriate places and updating initramfs.  I'll explain:

1) Use gparted to unmount the swap, then format it as linux-swap again.

2)  The UUID has been changed since we formatted it, so now you need to update it in the right places.  First, do 
```
sudo blkid
```
and look for the partition labeled 'swap'.  Copy the UUID, then do 
```
sudo gedit /etc/fstab
```
and paste the UUID after the line that says something like "swap was on /dev/sda whatever".  All the other options don't need to be changed.

3)  Next do 
```
sudo gedit /etc/initramfs-tools/conf.d/resume
```
and paste the UUID to the new one there too.

4)  Now update the initramfs, this is used to resume.
```
sudo update-initramfs -u
```

5)  And finally, turn on the swap.  If the swap partition has been preventing you from hibernating in any way, this should fix it
```
sudo swapon -a
```

---

### Post by JamieKitson on 2010-10-14
For troubleshooting resuming there's a good walk through here:

[http://en.opensuse.org/SDB:Suspend_to_RAM#Troubleshooting](http://en.opensuse.org/SDB:Suspend_to_RAM#Troubleshooting)

Having said that it didn't solve my problems :(

---

### Post by v1nsai on 2010-10-14
I tried a fresh install of Ubuntu and was still having problems, after eliminating variable after variable inching toward a completely scrubbed system, I discovered that disabling my /home partition solved the problem.  I have no idea why.  If your still having issues and have multiple partitions attached to your filesystem, try editing them out in /etc/fstab and see if that helps.

Also, back up your data before you start "experimenting" as turning off your machine without a proper shutdown can cause issues, I lost my partition table already but thankfully was able to get it back without losing any data.

---

### Post by hubrat on 2011-01-11
After following all the suggestions in this thread without success, I came across this post
[http://georgia.ubuntuforums.org/showthread.php?t=1614891](http://georgia.ubuntuforums.org/showthread.php?t=1614891) which suggests the following for motherboards with USB3 which has worked for me.

> When the XHCI module is loaded for USB 3.0 operation the system cannot  suspend. Manually unloading XHCI will allow suspend to complete  normally. To avoid future suspend problems, the workaround is to add  SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module then the  system can suspend normally.

---

### Post by lobstar on 2011-02-12
For troubleshooting suspend problems I will recommend looking in the pm-suspend.log

By doing so i found my problem with a built in usb camera was blocking for suspend.

Read about bug and solution here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515109](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515109)

---

### Post by keithspg on 2011-05-05
Wow! It appears that this thread is needed even more today than when it was begun, IMO. It seems that much of the information pertains to Hardy or specifically to HAL which is no longer installed with the latest kernels. I look at the pm-suspend log and all looks well. The only issue is this (does not look fatal):

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

But it still goes along and says this:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Wed May  4 19:50:44 CDT 2011: performing suspend

So, it *appears* that it has suspended. When I power it back on, though, the fans come on, but it does not boot. It just sits there. This is a gigabyte MA78LM-S2 board with the V14 (latest) bios. I have has suspend working previously on another board and my laptop and want it to work on this desktop. This is a computer which gets occasional use and I would like it to be in a suspend state awaiting a user login. 

Any help? The only page which appears to be useful is that suse page, but I am a bit leery as it requires a new package to be installed in addition to the PM package set.

Keith

---

### Post by keithspg on 2011-05-06
Update: It appears to be a BIOS setting that is a problem. I set it to 'defaults' and suspend works beautifully. I will go back through one by one with all my BIOS edits and see which one is interfering.

---

