---
title: "bluetooth"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by calmpey09 on 2009-05-07
[COLOR=Purple]***[SIZE=3]hello. how can you disable the bluetooth during boot up? i cant go to my desktop. it always stop on "Starting Bluetooth". what will i do with this problem? help plz!!!!!.....[/SIZE]***[/COLOR] :(

---

### Post by HyRax on 2009-05-07
You can remove Bluetooth from startup with the following commands:

```

$ sudo mv /etc/init.d/bluetooth /etc/init.d/bluetooth_old
$ sudo update-rc.d bluetooth remove

```

This renames the Bluetooth startup script to something else and then removes the Bluetooth service from startup so it doesn't try to launch the Bluetooth startup script in the first place.

---

### Post by DerinDevlet on 2009-05-07
more detailed information?

---

### Post by calmpey09 on 2009-05-07
***[SIZE=3][COLOR=Purple]other information? i have tried this code but it doesn't help[/COLOR][/SIZE]***
 ```

$sudo apt-get install sysv-rc-conf

```***[SIZE=3][COLOR=Purple]and here's another one[/COLOR][/SIZE]***
```

$sudo sysv-rc-conf

```[B][I][SIZE=3][COLOR=Purple]im using ubuntu 9.04 now... and im going crazy with this bluetooth... 
another thing I DON'T HAVE ANY BLUETOOTH DEVICE INSTALLED ON MY LAPTOP[/COLOR][/SIZE][/I][/B]

---

### Post by HyRax on 2009-05-07
Don't install SysV - it's being replaced with UpStart in Ubuntu.

Just remove the init script as I've already described.

And if you don't have a Bluetooth adapter and it's throwing your system off, then report a bug about it in Ubuntu's Launchpad. Bugs can't be fixed if Canonical don't know about them.

---

### Post by calmpey09 on 2009-05-07
***[SIZE=3][COLOR=Purple]where will i encode that commands? i tried it but it says  no such command or something....[/COLOR][/SIZE]***

---

### Post by HyRax on 2009-05-07
Encode?

You need to type these commands in a terminal. Open a terminal by going to Applications->Accessories->Terminal. Type the commands at the "$" prompt.

NOTE: The $ character in what I wrote earlier specifies that you type in everything AFTER it as the command. Do not type in the "$" sign itself.

---

### Post by calmpey09 on 2009-05-07
[SIZE=3][COLOR=Purple]***i cant go to terminal.. when i boot up my laptop, it logs or stop in "STARTING BLUETOOTH"***[/COLOR][/SIZE]

---

### Post by HyRax on 2009-05-07
Boot up the "Recovery mode" option then - that will drop you to a root terminal instead of booting up to the GUI.

You can make your changes there and then type in:

```

$ sudo reboot

```

...to reboot the PC to let it start normally.

---

### Post by calmpey09 on 2009-05-07
***[SIZE=3][COLOR=Purple]it logged when i go to recovery mode? is it usually long until it reach to the root terminal?[/COLOR][/SIZE]***

---

### Post by HyRax on 2009-05-07
No, it usually comes up pretty quickly because it's an absolute minimal system - no networking, no GUI, etc.

---

### Post by calmpey09 on 2009-05-07
[SIZE=3]***[COLOR=Purple]but for me it didnt reach the root terminal... it logged already. and i cant type anything on my keyboard.... can i edit the command in the kernel? and what would be the command?[/COLOR]***[/SIZE]

---

### Post by HyRax on 2009-05-07
You obviously got Ubuntu installed successfully in the first place which means the LiveCD didn't have any issues with your phantom Bluetooth adapter.

Boot up the LiveCD, access your hard-drive's root partition, get into the /etc/init.d directory and rename "bluetooth" to "bluetooth_old" or something (which will cause the Bluetooth init script to not execute because it won't be found under its expected name and hence not start).

Reboot and see what happens.

Failing all that, there's a chance that perhaps the initial install failed. I could also suggest reinstalling the OS from scratch as personally I've never heard of a lack of a Bluetooth Adapter causing the Bluetooth service to fail.

---

### Post by calmpey09 on 2009-05-07
***[SIZE=3][COLOR=Purple]are there any way on how to solve this kind of problem?[/COLOR][/SIZE]***

---

### Post by chipppy on 2009-05-07
Personally I used boot-up manager to cleanup my boot process a little to start with.  Thi allowed me to stop a heap of bootup process that i didn't need.

I help reduce my boot time for my Mythbuntu installation.

cheers
chipppy

---

### Post by HyRax on 2009-05-07
> **chipppy said:**
> Personally I used boot-up manager to cleanup my boot process a little to start with.  Thi allowed me to stop a heap of bootup process that i didn't need.

I help reduce my boot time for my Mythbuntu installation.

cheers
chipppy

Yeah, but his issue is that he can't even boot up in the first place!

---

### Post by calmpey09 on 2009-05-07
***[SIZE=2][COLOR=Purple]yups.. he's correct.. i can't boot up.. i have dual boot.. i'm using xp now.. i just install ubuntu 9.04 just this afternoon together with my friends... when we install it, its fine.. when we shut it down it appears on the screen "SYSTEM HALTED". so we just turn it off.. long key press on the power button.. and when i got home and i want to boot it up again, their, it appear already the "STARTING BLUETOOTH".. so that's my problem. i can't boot up the ubuntu because of the bluetooth!!!![/COLOR][/SIZE]***.. ***[SIZE=2][COLOR=Purple]my xp is ok!!! [/COLOR][/SIZE]***:(

---

### Post by HyRax on 2009-05-07
Another thing you can try is going into your BIOS and reset everything to factory defaults, reboot and see if Ubuntu still hangs at the Bluetooth init.

But like I said, boot up the Live CD again, get into your Ubuntu install's /etc/init.d directory and rename the "bluetooth" init script in that directory to something else so it cannot be executed.

---

### Post by calmpey09 on 2009-05-07
***[SIZE=3][COLOR=Purple]ok i'll try it.... if it wont work i'll consult again........... is that ok?!!!![/COLOR][/SIZE]***

---

### Post by HyRax on 2009-05-07
Well, by the time you come back, I'll have gone to bed - it's midnight where I am right now!

---

### Post by Galifron on 2009-05-09
Have you tried unplugging everything from your USB ports (Don't forget your modem/router!)? I have Ubuntu 8.10 on a USB flash drive and couldn't get past the Bluetooth problem. 

I didn't think it would work as Ubuntu is on a USB drive; but unplugged the modem and USB keyboard anyway.

Success! (and fast too!)

---

### Post by Nachowarrior on 2009-05-31
i have a post on this feed describing how to do it step by step, using info from this thread as well... it's all there. [http://ubuntuforums.org/showthread.php?p=7378802#post7378802](http://ubuntuforums.org/showthread.php?p=7378802#post7378802)

---

