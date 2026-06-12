---
title: "cannot shutdown / reboot laptop on 9.04"
date: 2009-04-23
forum: Hardware
---

### Post by Hendry on 2009-04-23
Just installed a fresh copy of 9.04. Everything is running fine, only thing is the shutdown or reboot of my laptop. It hangs in the end and I have to use my powerbutton to shutdown manually. Any ideas? My laptop is a HP Compaq NC6120.

---

### Post by sleepyenglish on 2009-04-23
Exact same issue here except im running a Dell XPS m1530

---

### Post by w3wsrmn on 2009-04-23
I too experience this issue.

If you press Ctrl+Alt+F7, does the last line say **Deconfiguring network interfaces** by chance?

---

### Post by sleepyenglish on 2009-04-23
When/where should i press Ctrl+Alt+F7?

---

### Post by w3wsrmn on 2009-04-23
When the laptop hangs during shutdown.

---

### Post by sleepyenglish on 2009-04-23
Nothing seems to happen.

---

### Post by EarthMind on 2009-04-23
Does it mention something about "acpi=force" at boot time? If so then you'll probably have to add this part to your boot file.

---

### Post by Hendry on 2009-04-24
> **EarthMind said:**
> Does it mention something about "acpi=force" at boot time? If so then you'll probably have to add this part to your boot file.

I did this, but no result. The last message is restarting system and then it hangs. Any other suggestions?

---

### Post by DelinquentSaint on 2009-04-24
Same problem on Dell XPS M1330.  Shutdown logs out and it just forgets to turn the power off?!  If left on for a while the screen gets lines across it.  I did not have this problem in 8.10 and it occurred immediately after upgrading to Jaunty. Btw... Ctrl-Alt-F7 did nothing.  I would appreciate any help.

---

### Post by kensonman on 2009-04-25
I got the same problem in Fujitsu S6510 laptop........

---

### Post by Blackpegaz on 2009-04-25
Hi, 

Did you have an fsck error when you restart your laptop ?

---

### Post by lisati on 2009-04-25
Occasional similar problem on a Toshiba m200 laptop running 64-bit 9.04: seems to do pretty much everything it should and then when it's at the stage when you'd expect the power to go off, there's a blinking cursor at the top left of a blank screen. I haven't noticed any error messages, and the system seems to respond to Ctrl+Alt+Del by restarting the system.

BTW, using EXT3 in preference to EXT4

---

### Post by liquerLOVER on 2009-04-25
my lappy spec:
aspire 4520
GeForce 7000m
AR5007EG

after fresh install, my laptop cant shutdown. hang during shutdown.nid 2 press power button to turn it off. i dont know whteher its a bug. im facing the same problem since ubuntu 8.10, so i change to linux mint 6. 

wireless out of the box but still, shutdown problem bringing me down

---

### Post by maGot on 2009-04-25
Same problem for me too. Dell Vostro 1500.

---

### Post by peppers on 2009-04-25
Same problem here, Toshiba Satellite A205-S4797.

---

### Post by turboxs on 2009-04-25
Same problem, HP-dv2617

---

### Post by peppers on 2009-04-25
Ctrl+Alt+Del shows me that KILLING ALL REMAINING PROCESSES have failed.

---

### Post by regisinferni on 2009-04-25
[https://bugs.launchpad.net/bugs/355054](https://bugs.launchpad.net/bugs/355054)

---

### Post by srikar on 2009-04-25
Even i have the same problem.
[http://ubuntuforums.org/showthread.php?t=1136387](http://ubuntuforums.org/showthread.php?t=1136387)

---

### Post by Dalgaim on 2009-04-25
Same problem here - MSI GX620, 9.04 64b.

I tried to dig up some informatin by shutting down in console or by pressing ctrl+alt+f7 during the shutdown splash, but I ended up with "system wil now reboot" or something similar. When I try to shut down with full graphics (nvidia ge force 9600m gt), i'm stuck at dark gray screen (which seems to be an equivalent to the final console output). In both cases, pressing ctrl-alt-delete reboots the computer.

But, surprisingly, suspending to disk works just fine. If I go for suspend to disk, everything is as it should be - the computer is working with hdd for a while and then the computer turns off without any problem. After turnig on, it wakes up exactly as it should. This could be temporary solution - instead of shutdown, suspend to disk.

But I'd rather find some solid solution for the problem, so if anyone knows, i'll be very happy :).

edit: when I added "acpi=off" and "reboot=b" (both without the quotes) options to boot options, i was able to reboot succesfully, but for shutdown it doesn't help at all and even disables the ctrl-alt-delete trick, not talking about acpi being turned off. I also tried using only one of both options and neither works.

---

### Post by Dallco on 2009-04-26
My Dell 1720 has the same problem on a fresh 9.04 64bit  install.................

ACPI=force acpi=off did not work..

---

### Post by hesapotman on 2009-04-26
I was having the same problem. If the laptop's wireless card was "on" at shutdown, it would hang and I'd get that blinking cursor in the top left corner. If the laptop's wireless card was "off" at shutdown, no problems at all.

So here's how I fixed it ...

Abstract: Add a short script to the init.d directory that uses "modprobe -r" to remove the wireless driver. Then add symbolic links to that script in both rc0.d and rc6.d directories.

Details:

1. Open a terminal and become super-user (yeah, this is a bad security practice, but I'm too lazy to type sudo before everything).
```
su
```

2. Navigate to the init.d directory.
```
cd /etc/init.d
```

3. Touch and edit your new wireless shutdown script. I use "vi," but feel free to use "gedit" if you like.
```
vi killwlan
```

4. Add line(s) that "modprobe -r" your wireless driver module(s). In MY case, I remove both "ipw3945" and "iwl3945" modules. In YOUR case, you'll need to find out the module names being used by your wireless device.
```
modprobe -r iwl3945
modprobe -r ipw3945
```

5. Save the script and exit the text editor.
```
[ESC] :wq [ENTER]
```

6. Navigate to the rc0.d directory.
```
cd /etc/rc0.d
```

7. Create a link to your killwlan script.
```
ln -sT /etc/init.d/killwlan S16killwlan
```

8. Navigate to the rc6.d directory.
```
cd /etc/rc6.d
```

9. Create a link to your killwlan script.
```
ln -sT /etc/init.d/killwlan S16killwlan
```

10. Now try to shutdown or restart.
```
init 6
```

This worked for me. If it works for you, great! If not, sorry for having wasted your time. Good luck!

---

### Post by Dalgaim on 2009-04-26
> **hesapotman said:**
> I was having the same problem. If the laptop's wireless card was "on" at shutdown, it would hang and I'd get that blinking cursor in the top left corner. If the laptop's wireless card was "off" at shutdown, no problems at all.

So here's how I fixed it ...

Abstract: Add a short script to the init.d directory that uses "modprobe -r" to remove the wireless driver. Then add symbolic links to that script in both rc0.d and rc6.d directories.

Details:

1. Open a terminal and become super-user (yeah, this is a bad security practice, but I'm too lazy to type sudo before everything).
```
su
```2. Navigate to the init.d directory.
```
cd /etc/init.d
```3. Touch and edit your new wireless shutdown script. I use "vi," but feel free to use "gedit" if you like.
```
vi killwlan
```4. Add line(s) that "modprobe -r" your wireless driver module(s). In MY case, I remove both "ipw3945" and "iwl3945" modules. In YOUR case, you'll need to find out the module names being used by your wireless device.
```
modprobe -r iwl3945
modprobe -r ipw3945
```5. Save the script and exit the text editor.
```
[ESC] :wq [ENTER]
```6. Navigate to the rc0.d directory.
```
cd /etc/rc0.d
```7. Create a link to your killwlan script.
```
ln -sT /etc/init.d/killwlan S16killwlan
```8. Navigate to the rc6.d directory.
```
cd /etc/rc6.d
```9. Create a link to your killwlan script.
```
ln -sT /etc/init.d/killwlan S16killwlan
```10. Now try to shutdown or restart.
```
init 6
```This worked for me. If it works for you, great! If not, sorry for having wasted your time. Good luck!


Good point! When I turn off wifi manually (pressing the button for wifi card), I can reboot/shutdown perfectly. I tried your solution, with "iwlagn" and "iwlcore" instead of your modules, but it doesn't work. Maybe I cose wrong modules. Is there a way how I could find out exactly which modules are connected with wifi card?
I tried "sudo lspci -v" and that gave me this:
```

...
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1301
    Flags: bus master, fast devsel, latency 0, IRQ 2296
    Memory at f9efe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 0
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number 12-6e-5d-ff-ff-ea-16-00
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
...

```Thanks for any advice.

**Edit**: when i run "sudo modprobe -r iwlagn" manually before I actually click on shutdown, everything (I mean shutdown/reboot) works fine, so i expect my problem to be the location and linking of the script. I'll play around for a while and if I find any results, I'll post them here.

---

### Post by Dalgaim on 2009-04-26
> **Dalgaim said:**
> Good point! When I turn off wifi manually (pressing the button for wifi card), I can reboot/shutdown perfectly. I tried your solution, with "iwlagn" and "iwlcore" instead of your modules, but it doesn't work.

**Edit**: when i run "sudo modprobe -r iwlagn" manually before I actually click on shutdown, everything (I mean shutdown/reboot) works fine, so i expect my problem to be the location and linking of the script. I'll play around for a while and if I find any results, I'll post them here.

I foud the cause of the problem - i forgot to change file permissions to enable executing.
```

cd /etc/init.d/
sudo chmod 755 killwlan

```

Everything else is as hesapotman posted, except the kernel modules, of course.

---

### Post by tsuanmi-dream on 2009-04-26
I'm having the same problem on my System 76 Pangolin (panp4n).  Will give this a try.

---

### Post by digirandi on 2009-04-26
its an error in the boot sector, try a bios update

---

### Post by lisati on 2009-04-26
> **w3wsrmn said:**
> I too experience this issue.

If you press Ctrl+Alt+F7, does the last line say **Deconfiguring network interfaces** by chance?

> **lisati said:**
> Occasional similar problem on a Toshiba m200 laptop running 64-bit 9.04: seems to do pretty much everything it should and then when it's at the stage when you'd expect the power to go off, there's a blinking cursor at the top left of a blank screen. I haven't noticed any error messages, and the system seems to respond to Ctrl+Alt+Del by restarting the system.

BTW, using EXT3 in preference to EXT4

Update on personal situation: have a fresh install of the 64-bit of Ubuntu studio (that's what I got the laptop for, to help with video stuff when I'm out and a bout)
Seems to be hung on the "deconfiguring netowrk interfaces", which kinda makes sense: the networking on the studio edition seems a little weird, I can use the wired connection if I restart networking manually through the terminal, but the network manager (manually installed) reckons eth0 isn't managed! 
Also have "killing all remining processes.... [fail]" and a few lines above, "Pidfile not found! Is jackd running?"



> **regisinferni said:**
> [https://bugs.launchpad.net/bugs/355054](https://bugs.launchpad.net/bugs/355054)

Thanks. 



EDIT: grumble grumble where did I put my 64-bit disks?

---

### Post by marios_geo on 2009-04-27
Same for me. HP pavlion 6680ev

---

### Post by l-x-l on 2009-04-27
> **hesapotman said:**
> 3. Touch and edit your new wireless shutdown script. I use "vi," but feel free to use "gedit" if you like.
```
vi killwlan
```


I don't see a file "killwlan" in the /etc/init.d/ directory. I'm on Jaunty.

---

### Post by Hortichris on 2009-04-27
I don't know if this is a red herring, however, in another thread there are complaints that laptops will not shut down or boot up when the computer is running on battery power.  When plugged in to mains power there is no problem.

---

### Post by jespdj on 2009-04-27
> **l-x-l said:**
> I don't see a file "killwlan" in the /etc/init.d/ directory. I'm on Jaunty.
You're supposed to create that file. It isn't there by default.

I have a similar problem on my XPS M1530. Most of the time it will not shutdown. In addition to not shutting down, I get a garbled graphics screen. I don't have my M1530 with me at the moment, I'll try the killwlan solution later.

---

### Post by l-x-l on 2009-04-28
I got a work around from this site & it works for me:

**[Workaround]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes")**

```
sudo gedit /etc/init.d/alsa-utils

Search for "stop)" and add immediately below: 
ifconfig eth0 down
ifconfig wlan0 down
```

---

### Post by jespdj on 2009-04-29
Ok l-x-l, but it is a bit ugly to put this in the file /etc/init.d/alsa-utils, because that file has to do with the ALSA sound system, while the problem does not have anything to do with sound, but with the wireless LAN drivers instead.

What [hesapotman posted](http://ubuntuforums.org/showpost.php?p=7149271&postcount=22) is cleaner and works also. Thanks, hesapotman.

I had to do:
```
modprobe -r iwlagn
```
for my XPS M1530, since iwlagn is the wireless driver that Jaunty uses on my laptop.

---

### Post by Dalgaim on 2009-04-30
I was also wondering - does anyone of you have any problem with hibernation? When I want my laptop to hibernate, somtimes it does, but sometimes it hangs at the point it should turn off I guess.  Heard somewhere that it could be related with nVidia GPU, but i don't know anything exactly.

---

### Post by l-x-l on 2009-04-30
> **jespdj said:**
> Ok l-x-l, but it is a bit ugly to put this in the file /etc/init.d/alsa-utils, because that file has to do with the ALSA sound system, while the problem does not have anything to do with sound, but with the wireless LAN drivers instead.

What [hesapotman posted](http://ubuntuforums.org/showpost.php?p=7149271&postcount=22) is cleaner and works also. Thanks, hesapotman.

I had to do:
```
modprobe -r iwlagn
```
for my XPS M1530, since iwlagn is the wireless driver that Jaunty uses on my laptop.


o.k. I'd like to try it but like I said, I'm a noob to Linux. So I'm extremely cautious about _creating_ scripts affecting my system, no matter how easy. I took a look at some of the other scripts in the /etc/init.d/ folder & they don't look particularly simple for a noob to understand.


Is it possible for you to show me your script (step 4 in hesapotman's post) since we have the same module? I'd appreciate it. Thanks.

---

### Post by Tralapo on 2009-05-01
I also have an Dell XPS M1530 laptop and i also have this problem.
jespdj, could you please post step by step what you've done? I'm a little bit of a noob and I would like to solve this annoying problem.

---

### Post by marcio_mi on 2009-05-02
Hi,
I also have the same problem with my sony vaio. I tried the suggestion by hesapotman but it didn't seem to work. When I turn off the computer the cursor stops in the left top corner. I tried to do <CTRL><ALT><F7> and here's what I get:

broadcast message from root@ubuntu

......


/etc/init.d/rc: 390: /etc/rc0.d/S16killwlan: Permission denied

* Asking all remaining processes to terminate...             [OK]
* Killing all remaining processes...                         [fail]
* Deconfiguring network interfaces...                        [OK]
* Unmounting temporary filesystems...                        [OK]
* Deactivating swap...                                       [OK]
* Unmounting local filesystem....                            [OK]
  mount: / is busy
* Will now halt



and then the computer stops there. It does not seem to be a problem with the wlan though. I had installed ubuntu 8.10 using the wubi installer, and I had no problems before upgrading to 9.04.

Can anybody help me here? thank you

---

### Post by mc.god on 2009-05-02
Hi,
i have the same problem after the upgrade to Ubuntu 9.04 on an Acer Extensa 5620 notebook, with an Intel iwl3945 wifi controller.

It solves if I tur off the wifi controller via hardware switch before rebooting or turning off the notebook, so I tried the way of "modprobe -r iwl3945" in a "killwlan" script, but it generates a bigger problem.

launching "modprobe -r iwl3945", via script or even manually in a root terminal, the system hangs, the mouse arrow disappear ed tthe "bloc num" led start blinking continously, and the then you have nothing to do but shut down the notebook by the power button.

So, I need to find out the exact command sequnce corresponding to turning off the wifi via it's hardware switch.

Hope it helps ^^

---

### Post by Tralapo on 2009-05-03
I tried the solution just like jespdj with iwlagn, and it works on my Dell XPS M1530! It does shut down now. The black screen with the little white stripe on the left corner still is there for a few seconds, but then I see a little message very quick (can't read what it says) and then the laptop turns of.

Thanks hesapotman and jespdj for the solution! Now Ubuntu 9.04 is perfect ;)

---

### Post by l-x-l on 2009-05-03
Update: I googled a few how-to's on basic scripting & tried hesapotman's method & it works. I'm now using that solution & instead of the one I provided earlier. Thanks to all for the help.

---

### Post by Guilden_NL on 2009-05-03
Nice job hesapotman!  And thanks for that file ownership reminder Dalgaim, I might have overlooked it as my brain is a bit fried from tracking down the fix to this bug.

Charles, I tacked on to bug report #302452 with my details too.  As I posted before, this was a bug back in 2004-2005 that appears to have crept into the kernel again. 

I updated the system changelog to reflect the workaround, so I can back them out and test any kernel fixes that are forthcoming.

---

### Post by zero7404 on 2009-05-03
between 8.10 and 9.04, 8.10 seems to be the only ubuntu flavor that has caused me no hickups...

yesterday evening i tried installing 9.04 for a THIRD time on my system. so now i have tried 2 fresh installs from disc and one smart upgrade via update manager. 

after the first install, i kept getting fsck checks during shutdown, with a whole bunch of action items that needed input. i decided to install with ext4.

after the second install, i found that i could not use nvidia's 177 driver because it was not listed, using 180 would not permit my screen to wake up after suspend, which i use most of the time....

after the third install, i tried using nvidia's 173 driver, which caused me all kinds of resolution issues and i could not switch back to 180....

thanks to programs like clonezilla, i got my 8.10 install back up and it's where i will stay for a while.

9.04 is very buggy, imo...

---

### Post by Tralapo on 2009-05-04
Oh, oh, oh, as I wrote in the post before this one, I tought the solution worked, but it doesn't!

Just like marcio_mi I get this:

> /etc/init.d/rc: 390: /etc/rc0.d/S16killwlan: Permission denied

* Asking all remaining processes to terminate... [OK]
* Killing all remaining processes... [fail]
* Deconfiguring network interfaces... [OK]
* Unmounting temporary filesystems... [OK]
* Deactivating swap... [OK]
* Unmounting local filesystem.... [OK]
mount: / is busy
* Will now halt


So I have to find another solution...

**Update**: I hadn't seen the chmod post from Dalgaim, so I did that now, and I will test that now.

---

### Post by chichicke on 2009-05-04
> **DelinquentSaint said:**
> Same problem on Dell XPS M1330.  Shutdown logs out and it just forgets to turn the power off?!  If left on for a while the screen gets lines across it.  I did not have this problem in 8.10 and it occurred immediately after upgrading to Jaunty. Btw... Ctrl-Alt-F7 did nothing.  I would appreciate any help.

got an m1330 as well ... mine is shutting down kinda well, but i am also getting these lines across the screen.

as i got further issues i opened another thread [http://ubuntuforums.org/showthread.php?t=1145448](http://ubuntuforums.org/showthread.php?t=1145448)
someone facing these problems as well ?

---

### Post by chichicke on 2009-05-05
I found out, that for me the shutdown works as long as i shut down via gui. as soon as i use "shutdown now" the laptop gets stuck at shut down.

the graphic errors doesnt occur as soon as i remove the properity driver, but then the hibernate doesnt work anymore. 

the wlan device doesnt solve anything for me at all.

---

### Post by mc.god on 2009-05-05
Hi,
as yo remember, the "killwlan" script didn't work well for me, as my system hangs up when I do modprobe -r iwl3945.
I'm usin wicd as network manager, and I noticed that simply unconnecting from the wifi network before shutdown, the system turn off correctly.
asd, simple and fast workaround ^^

bye

---

### Post by giovannisarto on 2009-05-06
I'm running jaunty 64bit on an HP 6710s and when I shut it down it hangs on a black screen with a white cursor blinking. I've noticed that if i push the button to turn off the wifi connection, the pc shuts down correctly. I have both installed acpi and apm. Has anyone an idea why this happens? With hardy and intrepid i've never had this issue.

Thanks!

---

### Post by kaotik2003 on 2009-05-07
I had the same prob till today, and I solved it by adding acpi=force to my menu.ls on /boot/grub

But I still have my pc hanged when I do a reboot order.

---

### Post by FokkerCharlie on 2009-05-08
Hi

I'm seeing the same problem, but modprobe -r iwl3945 results in a kernel panic.  How can I generate a list of loaded modules to check which one I should be targeting?  I thought that 3945 was the right one for me...

Cheers
Charlie

---

### Post by satipera on 2009-05-08
I too am having the laptop will not shut down problem with the blinking cursor. I am going to wait for a fortnight to see if there is an update fix, if there is not I am going back to a clonzilla image of intrepid I took just before upgrading. Jaunty seems to me to be buggy(not just shutdown) and slower than Intrepid.

---

### Post by vorgusa on 2009-05-16
> **l-x-l said:**
> I got a work around from this site & it works for me:

**[Workaround]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes")**

```
sudo gedit /etc/init.d/alsa-utils

Search for "stop)" and add immediately below: 
ifconfig eth0 down
ifconfig wlan0 down
```

Hey guys.  I have been experiencing the kernel panic when I used the killwlan script, but when I did the ifconfig wlan0 down commands like the quote above everything seems to work just fine.  I think the modprobe -r is more of a forced down that can cause problems.  I know some people might not like adding it to the alsa config, but a combined method might work, by replacing the modeprob -r with:

ifconfig eth0 down
ifconfig wlan0 down

---

### Post by rblasco on 2009-05-19
I had the same problem with my laptop, I could not shut-down/restart. Trying to optimize the battery life I installed the APMD package and then all works. Now, I can shut-down/restart without problems.

---

### Post by perfectska04 on 2009-05-24
> **hesapotman said:**
> This worked for me. If it works for you, great! If not, sorry for having wasted your time. Good luck!

Thank you SO much!
I've been having this issue on my laptop since I first upgraded to Jaunty, and none of the bugs related to it see any activity or future plans of releasing a fix.

Now I can shutdown/reboot properly without having to remember to switch the wireless kill button or face having to forcefully shut down the system.

---

### Post by liquerLOVER on 2009-05-25
what kind of shutdown problem you have? well, my problem is my machine goes blank and there is a blinking thing on the top of my monitor on the left. and it will stay there and your machine wouldn't shutdown until you press the power button. 

however, past few days, i realize by pressing spacebar or other button when the screen goes blank can turn off my machine. why does my lappy cant shutdown without pressing any other key? and how come other button can be a power button. but i don't mind with that little problem. im still on ubuntu 9.04

---

### Post by lesscode on 2009-05-26
Thanks to rblasco. After installing apmd package. It works for me.
 
Thanks a lot!

---

### Post by lesscode on 2009-05-26
I spoke too soon. It only worked if I did restart, but not shutting down.
Appreciate your help.

---

### Post by kemanamana on 2009-06-01
> **marcio_mi said:**
> 
* Asking all remaining processes to terminate...             [OK]
* Killing all remaining processes...                         [fail]
* Deconfiguring network interfaces...                        [OK]
* Unmounting temporary filesystems...                        [OK]
* Deactivating swap...                                       [OK]
* Unmounting local filesystem....                            [OK]
  mount: / is busy
* Will now halt


> **liquerLOVER said:**
> what kind of shutdown problem you have? well, my problem is my machine goes blank and there is a blinking thing on the top of my monitor on the left. and it will stay there and your machine wouldn't shutdown until you press the power button. 

however, past few days, i realize by pressing spacebar or other button when the screen goes blank can turn off my machine. why does my lappy cant shutdown without pressing any other key? and how come other button can be a power button. but i don't mind with that little problem. im still on ubuntu 9.04

I'm nOOb in the linux stuff I've just start using ubuntu 8.10 about three weeks ago and change it into 9.04 a week ago...

and I've had the same problem with marcio_mi and liquerLOVER... don't know how to fix it..

and other problem that i had was my laptop screen gets dim on boot probably the brightness level was about 20%... i had to manually set it again to 100 % after login... 

oh yeah one other problem is.. I can not set the resolution or other display utilities on display setting after i installed Nvidia driver... it had to set on nvidia x config ...

I notice that most of them who gets these problems are the people who had AMD based laptop bot using AMD64 and x86...

I don't have these kind of problem using intrepid

---

### Post by thom_ on 2009-06-02
> **EarthMind said:**
> Does it mention something about "acpi=force" at boot time? If so then you'll probably have to add this part to your boot file.

Hey.. I wanna try this one. But what I should do? I have no idea how to insert it. Many thanks. I have the same problem to in my PC

---

### Post by RichardG891 on 2009-06-02
> **thom_ said:**
> Hey.. I wanna try this one. But what I should do? I have no idea how to insert it. Many thanks. I have the same problem to in my PC

You need to insert it into the boot line.

open a terminal and type

gksu gedit /boot/grub/menu.lst

(that's an L not a number one)

That gives you access to the grub bootloader (Be VERY careful)

scroll down all the commented instructions and you'll get to the menu list. Edit the top (default) one by inserting your code anywhere on the first line:

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet **_acpi=force_** splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

save, close and reboot. If you've got an HP/compaq laptop (like mine) I had more success with "hpet=disable". If you have problems during reboot, select the (unedited) recovery option, boot as normal and remove the command.

---

### Post by hyapadi on 2009-06-03
I'm using Acer Aspire 4520 ( AMD Turion, Nvidia 7000m, Broadcom Wireless ) and Ubuntu 9.04 with nvidia 180.x and broadcom wireless driver.

Ocassionally, the shutdown process doesn't not shut off the laptop. The progress bar does move and finished. But in the end, the computer still running and show blank.

My temporary workaround was to press enter during that "blank" session. The computer will then shut off.

I did experience this in Ubuntu 8.10 and Ubuntu 9.04. I don't really remember how it was with the older release of Ubuntu since I wasn't really using it.

---

### Post by kemanamana on 2009-06-11
> **hyapadi said:**
> I'm using Acer Aspire 4520 ( AMD Turion, Nvidia 7000m, Broadcom Wireless ) and Ubuntu 9.04 with nvidia 180.x and broadcom wireless driver.

Ocassionally, the shutdown process doesn't not shut off the laptop. The progress bar does move and finished. But in the end, the computer still running and show blank.

My temporary workaround was to press enter during that "blank" session. The computer will then shut off.

I did experience this in Ubuntu 8.10 and Ubuntu 9.04. I don't really remember how it was with the older release of Ubuntu since I wasn't really using it.

[LEFT]I've had the same problem and same laptop as you are. after few workaround I eventually solve it with upgrading my kernel to [linux-image-2.6.30-8-generic]("http://packages.ubuntu.com/karmic/base/linux-image-2.6.30-8-generic")  and install other packages that related: linux-headers-2.6.30-8 and linux-headers-2.6.30-8-generic. from karmic download page...  finally it shuts down properly...

note : you might have to reinstall the NVIDIA driver...




[/LEFT]

---

### Post by ktechman on 2009-06-12
Make the option persistent between kernels with:

acpi=force in the "defoptions" line eg:

#defoptions=quiet acpi=force splash

---

### Post by Xanthm on 2009-06-15
> **RichardG891 said:**
> You need to insert it into the boot line.

open a terminal and type

gksu gedit /boot/grub/menu.lst

(that's an L not a number one)

That gives you access to the grub bootloader (Be VERY careful)

scroll down all the commented instructions and you'll get to the menu list. Edit the top (default) one by inserting your code anywhere on the first line:

## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet **_acpi=force_** splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

save, close and reboot. If you've got an HP/compaq laptop (like mine) I had more success with "hpet=disable". If you have problems during reboot, select the (unedited) recovery option, boot as normal and remove the command.

Thank you for this solution. Worked great. I wouldn't have had a clue on my own.

---

### Post by techstop on 2009-06-24
I've been following this thread as I had a Dell XPS M1210 that wouldn't shut down. I'm running 9.04 64-bit.

However, the problem seems to have gone with the latest kernel update to 2.6.28-13-generic. Has this fixed it for anyone else?

---

### Post by mattengstrom on 2009-07-29
Same problem here on a Lenovo W500.  Adding acpi=force to menu.lst in /boot/grub appears to have fixed the problem.  New install of 9.04 with all updates applied.

---

### Post by omarly on 2009-08-02
> **sleepyenglish said:**
> Exact same issue here except im running a Dell XPS m1530
Same here, but I think i got rid of it by booting in recovery-mode, took the option about xconfig, but i got it back? right now dual screen on my xps 1530. I have experienced it come and go.

---

### Post by yamamax on 2009-08-02
I went to the end of the threads hoping to find a solution to this problem. My experience so far my laptop will only boot and shut down properly when plugged in and for all programs to properly function needs ac. This defeats the purpose of a laptop. 

I have an HP pavillion dv6910 amd turion 64x2, nvidia graphics ((GeForce Go 7150M graphics), generously stocked with 3g ram. 

Any suggestions? I would like to run on battery power.

Thank You

---

### Post by UltraZone on 2009-08-02
> **hesapotman said:**
>  In MY case, I remove both "ipw3945" and "iwl3945" modules. In YOUR case, you'll need to find out the module names being used by your wireless device.


Ok, how can I tell the name of the drivers that my wireless is using.  My wireless worked out of the box, so I did not have to mess with it.  The code "modprobe -l" gives a very long list of stuff.:confused:

---

### Post by rexebin on 2009-08-08
> **RichardG891 said:**
> You need to insert it into the boot line.

open a terminal and type

gksu gedit /boot/grub/menu.lst

(that's an L not a number one)

That gives you access to the grub bootloader (Be VERY careful)

scroll down all the commented instructions and you'll get to the menu list. Edit the top (default) one by inserting your code anywhere on the first line:

## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet **_acpi=force_** splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

save, close and reboot. If you've got an HP/compaq laptop (like mine) I had more success with "hpet=disable". If you have problems during reboot, select the (unedited) recovery option, boot as normal and remove the command.

Worked for me. Thank you.

Before I try the above, I tried to turn off my wireless card before restart or shutdown, perfectly worked. I am sure it has to be the system failed to shutdown the wireless device. 

acpi=force does the job for me. However, could anyone tell me what's the side effect of it, to my understanding it has to be a reason why ubuntu does not come with this configuration to avoid such common problem.

---

### Post by happyisland on 2009-08-12
> **RichardG891 said:**
> You need to insert it into the boot line.

open a terminal and type

gksu gedit /boot/grub/menu.lst

(that's an L not a number one)

That gives you access to the grub bootloader (Be VERY careful)

scroll down all the commented instructions and you'll get to the menu list. Edit the top (default) one by inserting your code anywhere on the first line:

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet **_acpi=force_** splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3be998e1-d3ed-4dfb-869d-8b2010c5babf ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

save, close and reboot. If you've got an HP/compaq laptop (like mine) I had more success with "hpet=disable". If you have problems during reboot, select the (unedited) recovery option, boot as normal and remove the command.


FWIW, this solved my Vaio FW's failure to shutdown/reboot. Thanks!

---

### Post by archsin on 2009-08-13
i've solved shutdown problem on my asus f5gl (lcd screen turned to black after shutdown and then it started to change colours from black to white) but now i've got another...notebook turns always on immediately after shutdown like reboot...i can use command to shutdown in terminal but always the same..whats the problem?

---

### Post by 65daysofstatic on 2009-08-22
hi i just installed ubuntu 9.04 on my laptop(toshiba u405d-s2874) and I cant shutdown, when I try to shutdown the computer restarts,
is there a way to fix it?
thx

---

### Post by peeke75 on 2009-09-05
hi i just installed ubuntu 9.04 on my laptop(dell XPS M1330) and I cant shutdown,
I have tried all of the tips previously in this thread without any success. Judging from the thread there are still several people suffering from this. ANYTHING???

The screen goes blank and the fan keeps running. No input gives any responce. Really easy to get new ideas when the feedback is zero.

Help a novice to regain trust for Ubuntu.

---

### Post by gibbylinks on 2009-09-05
I had a dabble with Karmic Koala, which screwed my system. I've been forced to reinstall and I'm now running with kernel 2.6.28-15-generic. My system now shuts down fine. I do have the "noapic" option in my grub menu.lst (see below). My laptop hangs on boot without this.

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        bd76da27-918b-41d7-b415-9840b5985373
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bd76da27-918b-41d7-b415-9840b5985373 ro **[COLOR=Red]noapic[/COLOR]** quiet splash vga=792 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

Hope this helps someone.

(Running Jaunty on Toshiba Satellite A30 laptop) :P

---

### Post by fenario on 2009-09-06
I had the same problem on my desktop. I went to system>administration>authorizations
and granted permission to: all the WOL and powermanagement. That seemed to do it. Omn my laptop I have to shut down the network eth0 and then it will shutdown, otherwise blinking and hanging. 

My gosh I can't believe what a f...up and nightmare ubuntu had become; think I might go back to 8.04 LTS and refrain from updating and video driver installs. But I'm stubborn and rather find a solution.

---

### Post by Cris(c) on 2009-09-15
> **l-x-l said:**
> I got a work around from this site & it works for me:

**[Workaround]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes")**


I had the same problem on my Vaio VGN-C240e but I followed this workaround and now everything seems to be fine.

Thanks for the tip l-x-l!

---

### Post by jilson on 2011-06-18
I had also some problems with starting up and shutting down my toshiba notebook and ubuntu 10.04. acpi problem at startup and shutting down problem.. I had to press the power button to shut it down properly. Now I installed 11.04 and these two problems have gone completely.. So try the new Ubuntu..Thanks for the contributors...

---

### Post by NoonienSoong97 on 2011-07-08
I have no problem with shutting down the computer. The problem I have is with hibernation, suspension, and restart. All of those functions do work, but once the computer restarts I have either a blank screen, or a light green screen with multiple vertical white streaks.

I am using ubuntu 10.10 on a Toshiba Portege M200. Video card info is:

nooniensoong97@nooniensoong97-PORTEGE-M200:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)

At this time I am not using the NVIDIA accelerated graphics card driver version 173, or 96.

Is there any other info you need from me?

---

### Post by sobies on 2011-07-17
I have the same problem on HP compaq 8710p in ubuntu 11.04 (natty). System sometimes freezes during shutdown or reboot. 
My solution was to remove gnome-power-manager package. I have no information about battery status but I can reboot any time.

---

