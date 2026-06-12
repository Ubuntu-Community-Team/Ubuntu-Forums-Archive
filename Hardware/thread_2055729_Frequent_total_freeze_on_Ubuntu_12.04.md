---
title: "Frequent total freeze on Ubuntu 12.04"
date: 2012-09-10
forum: Hardware
---

### Post by shane84 on 2012-09-10
My HP m6-1045dx laptop is barely a month old. I have Ubuntu 12.04 64 bit installed on it but I use the Awesome window manager instead of Unity. 

About a two weeks ago I experienced a total system freeze twice, that did not respond to the magic sysrq keys either and I was forced to use the shutdown button. Both freezes occured when I was using Firefox, Chromium, and Google Chrome simultaneously. 

Then it worked fine for two weeks until it froze three times yesterday and once today. Yesterday, I noticed that gimp was open each of the three times it froze, and once it froze while I was using the dolphin window manager, and once while opening a new tab among many others open in chromium. I uninstalled gimp and rebooted into recovery and ran fsck and other checks. But today it worked fine the entire day and then crashed again while opening a new tab in chromium while there were many others open. I think I remember this problem occurring ever since i installed google-chrome but not necessarily only when it is open, but to be on the safe side I have uninstalled google-chrome. 

Each time the freeze occurs, the laptop does not respond to ANYTHING: neither the mouse nor Ctr+Alt+F1 nor the magic sysrq keys, even though the sysrq keys are enabled (I am able to use alt+Sysrq+K when the laptop is working normally).

I just updated the kernel to 3.2.0-30.

The laptop temperature always seems to be between 47 to 55 degrees and rarely crosses that.  

I doubt any of this should be relevant, but just in case: also started using conky and recently shifted my /tmp to the RAM by mounting it as a tmpfs. 

Please tell me if there is any code I can paste here to make it easier to diagnose. 

Here is the part of the output of lspci -v that contains the graphics card information. 

```

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 18a4
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 3000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

Thank you!

---

### Post by 2F4U on 2012-09-10
The temperature seems to be fine, but did you also check the RAM? With such erradic freezes it is worth checking the RAM through a tool such as memtest.

---

### Post by shane84 on 2012-09-10
I tried a memtest from grub but it gave the error:
```

error: too small memory 
0x99100>0x91C00

```

Is this a problem with the way memtest is installed or is it mentioning an error in the RAM?
I hope this does not mean that the RAM is not working properly, because the laptop is new. I also run firefox entirely from the RAM (from /dev/shm) and mount my /tmp on it, but firefox always runs fine and neither have i faced trouble with videos. Is it still likely to be the RAM?

Thanks!

---

### Post by shane84 on 2012-09-10
Memtest worked from a bootable CD but it did not reveal any errors. Even watching youtube videos or streaming a movie does not freeze the OS so perhaps the RAM is fine. 

The laptop froze completely once again while opening a tab on chromium, which already had a number of tabs open. I will use firefox from now on, but I hope the problem is limited to chromium/ google-chrome! Has anyone faced anything similar?

---

### Post by averger on 2012-09-26
Hi, I also have this problem on my Dell Latitude E6530 with ubuntu 12.04. I tried to reinstall ubuntu but I still have the freeze problem for example when I open a new tab in Chrome. What kind of log could I check when I reboot the system ?

Thank you and have a nice day !

---

### Post by JJonesM4L on 2012-10-05
Can some one please help me, I am running Ubuntu 12.04 on a Toshiba Satellite laptop. It freeze completely on me when I am at home connected to my wireless network. The only thing I can do is hold the power button down till it reboots. When I am at school connected to the wireless network there it works just fine. Can some one please help me? I would really like to fix the problem.:confused::confused::confused::confused::confused::confused::confused:

---

### Post by Arlindor on 2013-01-29
Hi, I've got the same issue as you averger, on a Dell Latitude E6530 with a fresh install of Ubuntu 12.04 LTS. Also I'm using the gnome classic desktop, not Unity, can this be the cause of freezing ? It's a complete freeze, no response from keyboard and mouse.

@averger : Did you manage to fix the problem ?

Thank you !

---

### Post by NobleYorkshire on 2013-01-29
I was having the same problem essentially.  I had did several reinstalls of Ubuntu trying to get it to work but I realized that the lockups were coming when I downloaded and used Chromium.  I am not sure what the problem is with it but I get the complete freezes where I can't do anything.

---

### Post by Arlindor on 2013-02-01
I've downloaded all the Important Security Updates with the Update Manager, and it's been some days I don't have freezes anymore.

---

### Post by dmishh on 2013-02-12
I have same issue with Ubuntu 12.04 x64 on Intel Core i5. OS freezes completely only in Google Chrome. Trying to find the solution...

---

### Post by Sutarmekeg on 2013-03-27
Welcome to the club, I also have mystery freezes and months now of googling have produced nothing.
If your symptoms are like mine 

[https://bugs.launchpad.net/bugs/1154006](https://bugs.launchpad.net/bugs/1154006)

please mark this bug as affecting you too.

---

