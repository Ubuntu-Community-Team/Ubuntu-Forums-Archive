---
title: "[SOLVED] Laptop freezes, doesn't wake from sleep"
date: 2008-08-17
forum: Hardware
---

### Post by El Rogueo on 2008-08-17
I have a HP/Compaq Presario F500 running Kubuntu, fully updated, and I've started having odd problems with it. I've never used Kubuntu before, and only used KDE through things like Backtrack and Slax, so I'm rather unfamiliar with it.

The only modifications I've made to the computer since the clean install are to 

1) Rebuild my wifi drivers for injection use with Aircrack-ng, a process that was successful

2) Installed Dopewars :rolleyes:

3) Installed Pidgin

I loaded some of my music onto the computer via CD, and here's where problems come up. If I leave the computer on for a while, it'll go into some sort of suspension or sleep or otherwise low-power state, and the screen will turn off. The computer still appears to work, as far as playing music goes at least. I cannot wake the computer from this state. The screen brightens as though it has turned on, but then stays black. The power management is set to NEVER go into sleep or any similar type of suspension. The computer is plugged in.

I'm pretty much at a loss. :-?

In addition, sometimes the computer will bind up even performing normal tasks and just freeze, and I'll have to hold the power button down until the computer turns off, or until Kubu realizes I'm trying to kill it, at which point it will shut itself down cleanly.

I've seen a lot of forum posts for laptop issues with waking up, but never one that was actually solved.

Any ideas?

---

### Post by phidia on 2008-08-17
Can you get a CLI (commandline) by pressing Alt+Ctrl+F1? If you can then enter "dmesg" that might give you/us some helpful output. If you can't open CLI then when you reboot after this happens check your logfiles from System > Administration > System Log.

---

### Post by El Rogueo on 2008-08-17
> **phidia said:**
> Can you get a CLI (commandline) by pressing Alt+Ctrl+F1? If you can then enter "dmesg" that might give you/us some helpful output. If you can't open CLI then when you reboot after this happens check your logfiles from System > Administration > System Log.

could not navigate the menu to the location you describe; System contains no Administration tab, but does have KSystemLogs, which is what I chose instead.

having read the 1000 log lines, I'm not sure what to be looking for, or what to post.

How should I filter the results?

---

### Post by El Rogueo on 2008-08-17
Just froze again, checked logs on reboot

There's nothing that looks suspicious, a lot of wifi messing around that I was doing

The last line is:

```
<WARN> nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkMangerInfo.NoNetworks - org.freedesktop.NetworkMangerInfo.NoNetworks. 
```

this message shows up in a couple other places, along with

```
<WARN> nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
```

although I'm unsure if they're associated with the crash/inability to wake

I wandered into ifconfig, since that's the extent of my knowledge of networking and checked the wifi stuff (since an ethernet connection wouldn't need to check for networks), and my wireless card is listed kind of weird, even though I got the drivers:

```
wlan0           Link encap:Ethernet
```

that doesn't look right, but wifi looks to be working (there's no wireless near me right now) and I still don't know how that would tie to the crash

---

### Post by Farens on 2008-08-17
Hello, I have a compaq presario A940NR laptop & I am having the same issue.  Screensaver kicks in, runs for a bit then freezes.  System still active (shoutcast streaming) but can't get back the system to wake. If I can find an answer I'll post it here.

---

### Post by Hyper Tails on 2008-08-17
me same here ny laptop is a acer apsire 5175-4740

it wake up the first time (no problem) but when i wake it up again it freezes :(
help.

i run ubuntu sorry for posting in the kubuntu topic
please don't get mad at me...

---

### Post by El Rogueo on 2008-08-17
lol if we're all looking for the same thing it's not a problem to post in the "kubuntu" thread

I'm pretty sure the problem is related to laptops with any variety of ubuntu, as some of my fluxbuntu friends had this problem too, but don't recall how they fixed it.

@Farens, thanks for looking, I'm still digging around myself, but to no avail. The worst part is, I would even settle for just never going into sleep/turning off the monitor, but that's not even going to work

---

### Post by phidia on 2008-08-18
I'm not sure if it will help but there is the Ubuntu community [laptop testing page]("https://wiki.ubuntu.com/LaptopTestingTeam"), and take a look at the thread [here on suspend]("http://ubuntuforums.org/showthread.php?t=671334") in kubuntu.

---

### Post by El Rogueo on 2008-08-19
> **phidia said:**
> I'm not sure if it will help but there is the Ubuntu community [laptop testing page]("https://wiki.ubuntu.com/LaptopTestingTeam"), and take a look at the thread [here on suspend]("http://ubuntuforums.org/showthread.php?t=671334") in kubuntu.

I checked the suspend thread already, but it doesn't quite match my problem; I tell the computer not to suspend ever, and it still goes into some sort of powersave mode that I can't control after so much inactivity.

I got a partial fix by installing Kubuntu 32 bit instead of 64, but that just made the computer crash more frequently for no apparent reason, rather than crashing every time on wake up and only occasionally for no reason.

Will check out the laptop testing page though, thanks a lot, I should have thought of that!

---

### Post by phidia on 2008-08-19
El Rogueo, Most people have some resistence to going back but if you can overcome that you could try gutsy (7.10) and then go to intrepid (8.10) when it's released in October.

---

### Post by El Rogueo on 2008-08-19
> **phidia said:**
> Most people have some resistence to going back but if you can overcome that.

I just tried going back to Ubuntu and I couldn't get over the fact that it was GNOME and not KDE, so now I'm back to reinstalling Kubuntu (cleaner than removing gnome and adding kubuntu-desktop, for me)

Seeing as Intrepid is a month and a half away, I think I'm going to try to make Hardy work, since I have Vista installed as a backup on the other partition.

It's really weird, since neither problem seems to be consistent and changes frequency of occurrence on each installation.

---

### Post by Farens on 2008-08-20
Here's a little update.   I did an experiment, I left firefox running & walked away from the laptop.  After the system was suspended it would not wake.  I rebooted it & this time closed firefox & had no application running & walked away.  This time it would wake from it's sleep & was functional. I saved 2 logs, one of each scenerio & the main difference is the system never gets past:

Aug 20 16:45:11 - kernel: [ 1045.264874] ACPI: PCI interrupt for device 0000:02:01.0 disabled

The other scenerio shows it getting past the above line in the system log & then:

Aug 20 16:27:49 - kernel: [  309.102041] Syncing filesystems done.
Aug 20 16:27:49 - kernel: [  309.102068] PM: Preparing system for mem sleep
Aug 20 16:27:49 - kernel: [  309.102071] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug 20 16:27:49 - kernel: [  309.102668] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Aug 20 16:27:49 - kernel: [  309.198973] PM: Entering mem sleep
Aug 20 16:27:49 - kernel: [  309.198975] Suspending console(s)

I hope this might help someone out.

---

### Post by El Rogueo on 2008-08-20
I reinstalled, and haven't really extensively tested the new install, but I think the problem for me was that my swap file was too small, since I only have that one gigabyte of memory. Having increased it I haven't had the problem since (although like I said, I haven't used it a lot either)

---

### Post by jpeery on 2008-08-20
I'm on an HP Pavillion laptop, same problem, but when I set it to not suspend in the power settings all is fine.  Not quite a fix, but a decent work-around.  I would like to know what's up, didn't think about increasing swap.  Curious, how would that help?  I should clarify, in Power Mgmt, I have Actions: Put computer to sleep when inactive set at never, and the same on Display.  I do NOT have Dim display when idle selected.

---

### Post by El Rogueo on 2008-08-21
It's more of a personal thing than anything else, (I'm not even sure it'll fix the problem) but I noticed that when my computer runs in windows without swap, it freezes like all hell, and figured that the same thing could be happening in linux, especially since I set my page file to only 1GB.

tl;dr I really had nothing to lose by increasing it, and thought it might prevent operations from backing up, especially since I usually get the most freezing while running background apps like amarok or boinc

**UPDATE**

Increasing the swap space fixed the problem for the following reason; the laptop would go into a powersave mode that was specified by the hardware, not Ubuntu, and thus not controllable. When it did this it would try to cache the application data to swap, which was too small, and then crash to pieces. Sorry for everyone with suspend problems, looks like that wasn't it at all for me, and good luck.

---

