---
title: "Ndiswrapper in Jaunty 9.04"
date: 2009-04-26
forum: Hardware
---

### Post by Landreville on 2009-04-26
I was using ndiswrapper with broadcom drivers for a few years, but it appears that it no longer works in the latest upgrade.

Previously all I had to do wa blacklist the bcm43xx module (which is documented everywhere).

Now there is an alternate driver "ssb" which cannot be blacklisted. Has anyone gotten ndiswrapper to work with wireless drivers? 

Mine is a broadcom BCM4318 onboard that uses a driver named bcmwl5.inf

I also have a Linksys WPC54G that uses a driver named lsbcmnds.inf

---

### Post by Landreville on 2009-04-26
After hours of searching its always right after i post the question that i solve it.

Here's what i did to get it working:
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b43

Running those commands will get the wifi working perfectly (after installing the driver with ndiswrapper). 

I am going to put these commands in /etc/rc.local so that they get run on startup. When putting them in /etc/rc.local I dont think you need to use sudo though.

---

### Post by littleman54321 on 2009-04-27
I also recently did a clean upgrade to 9.04 and am having issues with this damn wireless card. No idea if it makes a difference, but the laptop is an Inspiron 1300. I tried running these commands, but when I enter them I get 

```

mij@mij-laptop:~$sudo modprobe -r b43
WARNING: All config files need .conf: /etc/modprobe/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe/blacklist, it will be ignored in a future release.
```

I'm not sure if that makes a difference or not. The -r ndiswrapper says it as well...and so does the "sudo modprobe ndiswrapper" & "sudo modprobe b43"

And then for "ssb":

```

mij@mij-laptop:~$sudo modprobe -r ssb
WARNING: All config files need .conf: /etc/modprobe/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe/blacklist, it will be ignored in a future release.
FATAL: Module ssb is in use.
```

Any ideas how to fix this?

I have installed the ndiswrapper, as well as the .inf file (though it tells me "Unable to see if hardware is present." I hit "ok" and then i see "bcmwl5 hardware present: yes" :confused:

---

### Post by littleman54321 on 2009-04-27
Well, I got it working. I uninstalled the driver device from the Administration -> Windows Wireless Drivers and then clicked "Hardware Drivers". This found the "Broadcom B43 wireless driver" and said it was not activated. I clicked activate, and it did it's thing and started working. WOO!

EDIT: I rebooted, and the wireless isn't showing up now. Back to tinkering.

It seems that the driver became "unauthorized". There is a box that says "authorize for this session"...but that apparently won't be good for next session. And even after doing that, I can't connect to the wireless network. Hmmmmm.......

---

### Post by jsyl on 2009-04-27
Okay, I am in DESPERATE need of help. I have been going on for several days now searching and searching for what to do, and every time I try to install my wireless usb card, it doesn't work! I try every command that could possibly help it, but no! I have tried scanning through the terminal, and it tells me that wlan0 does not exist. I try blacklisting the other drivers and that does me no good at all. I tried modprobing and everything, starting at boot-time, but it just completely refuses to work! Can ANYONE help me? It would be SO MUCH appreciated, just tell me what to do.

I have a D-Link WUA-2340 wireless usb card, and it's been working with versions before 9.04, but it doesn't now!

Please help me.

---

### Post by littleman54321 on 2009-04-27
Well. I uninstalled ndiswrapper, and I can consistently make it work by going to Administration -> Hardware Devices, and clicking activate (on the Broadcom B43 wireless driver). After clicking "Activate", a window pops up and has an orange bar that scrolls back and forth, says "Downloading and installing", but stays at 0% the whole time. Then it goes away, and at the bottom of the main window, there's a little "refresh" looking arrow, and a message that says "This driver was just disabled, but is still in use.

I close it, and it connects to my wifi just fine. :confused:

EDIT: I uninstalled the b43-fwcutter, and still have the same results.

---

### Post by littleman54321 on 2009-04-28
Another update.

The Administration -> Hardware devices & clicking activate still works after a reboot, but is only at a speed of 1 Mb/s, which is unbearably frickin slow.

Anyone have any luck with this card in jaunty yet?


EDIT: Just for shits and giggles, I re-ran the sudo modprobe code he posted above, and the damn thing did connect, but is now only running at 6Mb/s, which is still unacceptably slow out of a wireless g capable card....And I haven't even tested if it will come back after a reboot. Here goes....

EDIT: Nope, wireless still down after a reboot. :(...but after going to system -> administration -> hardware devices, and clicking activate, i am now getting 36 Mb/s as a connection speed...much more practical.

Awww, crap. I spoke too soon. Back down to 1 Mb/s. BAH!

---

### Post by skullivan on 2009-04-28
Having the same problem getting my Linksys WPC54G ver. 3.1 (Broadcom B43 chipset) to work. I've tried for hours all the various fixes from the last 5 years or so and nothing works. ndiswrapper says it can't find the hardware but then it lists the broadcom driver as installed. The card is working and detected because it can scan for hotspots in the area, it just won't connect to any. 

Activating the Broadcom drivers under "Hardware Drivers" didn't do anything except make my wireless card disappear from the list of "wireless networks" where it was previously listed but greyed out (unselectable).

I just completely reinstalled 9.04 because I think all the screwing around I was doing was just making things worse and I figured it's better to start from a fresh install since I know nothing else worked anyway. 

I'm running 9.04 on an HP Pavilion zx5000.

EDIT: LOL, as per internet law, this problem magically resolved itself immediately after I posted this despite having tried for days to get it to work. I swear computers just want you to admit defeat, then they work things out on their own.

My steps from a fresh reinstall in case this helps anyone else:

Remove wireless card before installation. Don't insert until everything is finished.
Run Ubuntu updates
Activate the Broadcom drivers under System>Administration>Hardware Drivers (it wasn't showing up for me at first, you may need to reboot before it detects it)
After installing the drivers, reboot again.
Select the network icon in the system tray and select your network from the list
Enter the security key when prompted and you should be set

For me the key differences from my first install of Jaunty were removing the card before installation and activating the Broadcom drivers under "Hardware Drivers" after plugging in the card and running the updates. Previously I went right to the web searching for an answer as to why my wireless card wouldn't work and started applying all sorts of fixes. None of them worked and it clearly just made things worse. I never even had an option on my last install of Broadcom drivers under Hardware Devices, the only thing that showed up was for some SmartLink softmodem.

---

### Post by mbw290 on 2009-04-28
These commands work for me however I have to reeenter the commands with every reboot

---

### Post by jsyl on 2009-04-28
Does anyone have any ideas, like commands or anything at all that I could try to possibly get my wireless working? I tried the ones at the top that were first mentioned, and that didn't help. Ideas, anyone?

---

### Post by mjitkop on 2009-04-30
> **skullivan said:**
> 
My steps from a fresh reinstall in case this helps anyone else:

Remove wireless card before installation. Don't insert until everything is finished.
Run Ubuntu updates
Activate the Broadcom drivers under System>Administration>Hardware Drivers (it wasn't showing up for me at first, you may need to reboot before it detects it)
After installing the drivers, reboot again.
Select the network icon in the system tray and select your network from the list
Enter the security key when prompted and you should be set


Hi there. What do you mean by "Run Ubuntu updates" ? Doesn't it try to connect to the internet to check for updates?

I will have to try a fresh install again with my card out of the PC as you suggested. I noticed the same problem too with the b43 driver not listed at first.

Good suggestions. I will try tonight hopefully when I'm home.

---

### Post by littleman54321 on 2009-04-30
> **mjitkop said:**
> Hi there. What do you mean by "Run Ubuntu updates" ? Doesn't it try to connect to the internet to check for updates?

I will have to try a fresh install again with my card out of the PC as you suggested. I noticed the same problem too with the b43 driver not listed at first.

Good suggestions. I will try tonight hopefully when I'm home.

Well, ideally you would have an ethernet cord laying around... The downside to his instructions for some of us are that the wireless card is built into the lappy :(

---

### Post by adam_kimber on 2009-05-01
> **littleman54321 said:**
> Another update.

The Administration -> Hardware devices & clicking activate still works after a reboot, but is only at a speed of 1 Mb/s, which is unbearably frickin slow.

Anyone have any luck with this card in jaunty yet?

I get 1MB/s connection too! Yay! Someone else with my problem. :) Not found a solution. Am looking into using ndiswrapper instead of whatever the official hardware drivers thing uses.

---

### Post by littleman54321 on 2009-05-01
> **adam_kimber said:**
> I get 1MB/s connection too! Yay! Someone else with my problem. :) Not found a solution. Am looking into using ndiswrapper instead of whatever the official hardware drivers thing uses.

I tried using it before, but I couldn't get it to work. Granted, I'm not all pro Ubuntu, so....

---

### Post by NuWW on 2009-05-02
I've got a built in laptop card and the wireless worked fine even after a reboot with the broadcom driver. Usually I'd use Ndiswrapper and th bcmwl5.inf driver.

---

### Post by ouman63 on 2009-05-02
I've just recently updated to jaunty and ndiswrapper gives a message box that says "unable to see if hardware is present", even though it says hardware is present. I've used ndiswrapper in the past with gusty and intrepid with no problems. I've got a dell xps m1530 with wireless card 1505. Any ideas or suggestions would be great.

---

### Post by TheWendysGuy on 2009-05-03
> **Landreville said:**
> After hours of searching its always right after i post the question that i solve it.

Here's what i did to get it working:
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b43

Running those commands will get the wifi working perfectly (after installing the driver with ndiswrapper). 

I am going to put these commands in /etc/rc.local so that they get run on startup. When putting them in /etc/rc.local I dont think you need to use sudo though.

Worked for me! Thanks

---

