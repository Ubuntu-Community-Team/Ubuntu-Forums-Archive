---
title: "Mouse keeps freezing and to be honest i don't understand the other fixes, please help"
date: 2008-08-31
forum: Hardware
---

### Post by Jombib on 2008-08-31
Hi,
first time i have posted on here.
Just started using Ubuntu yesterday and i think its awesome, all except for the fact that for some reason my mouse keeps freezing up today.
It started happening after I tried to upgrade my RAM and graphics card. I got them from a big box of computer stuff I have and they didnt work, so i went back to my old set-up and all worked fine, except for my mouse keeps freezing.
Its just the mouse, keyboard still works, as I am typing this the mouse is frozen.
I can't understand why this is happening, but to make it worse i have found loads of explanations on how to fix it, but since i havent used ubuntu at all, or any other linux, i dont know where to type all these things into.
Can someone please help with a really simple step by step sort of thing.

Many Thanks in advance
Jombib

---

### Post by Tanker Bob on 2008-08-31
> **Jombib said:**
> Hi,
first time i have posted on here.
Just started using Ubuntu yesterday and i think its awesome, all except for the fact that for some reason my mouse keeps freezing up today.
It started happening after I tried to upgrade my RAM and graphics card. I got them from a big box of computer stuff I have and they didnt work, so i went back to my old set-up and all worked fine, except for my mouse keeps freezing.
Its just the mouse, keyboard still works, as I am typing this the mouse is frozen.
I can't understand why this is happening, but to make it worse i have found loads of explanations on how to fix it, but since i havent used ubuntu at all, or any other linux, i dont know where to type all these things into.
Can someone please help with a really simple step by step sort of thing.

Many Thanks in advance
Jombib
Hi, welcome to Linux and ubuntu. We need more information to help you. Is the mouse USB, P/S2 or serial? Is it hard wire, RF, or IR? What kind of computer or motherboard do you have? What other competing USB or serial devices do you have? What flavor of ubuntu are you using (ubuntu/kubuntu/xubuntu/edubuntu/etc.)?

In general, it's best to start with the simplest checks. You might want to check your BIOS setup to ensure it still correctly reflects your hardware profile. If you have a USB mouse, try changing the plug into which it is connected. If it's an RF or IR mouse, try changing the battery in the mouse. I have an RF mouse and changing the battery has cured every problem I encounter with it.

---

### Post by Jombib on 2008-09-01
hi,
i know i said i was new to linux, but would regard myself as somewhat of a computer expert (almost :D) i am microsoft certified (aaarrrggghhh Microsoft i know but i need it for my job). I have checked all my BIOS settings, and have now installed a new USB card. I have a USB optical mouse by the way that just plugs directly in. 
My system dual boots with XP aswell and the mouse seems to work fine there.
As far as what type of computer i have, it just one that i have thrown together using all sorts of different bits. I cant remember what the motherboard is, all i remember about it is it has a 400fsb if that helps, dont think it will though. I have a 2.8Ghz P4 i think, got 770mb ram, ddr sdram 2600 i think, got a really old gigabyte graphics card, netgear wireless card (802.11g) and 2 dvd writers.  
Thought i would tell you all i know about it incase any of these might be causing a conflict?
I had a PS/2 mouse plugged in before which worked, but that completely froze up, so i went and bought a USB so i dont think it is the USB ports, but i thought i would test that anyway since i had some lying around.

This whole system has been up and running for around 3 months on XP and has all been working fine, except for being slow :)

Sorry for the long post but i thought i would give as much info as poss.

please help because i really want to get my ubuntu back, was having so much fun using it compared to my old XP.

Thanks
jombib

Sorry forgot to say, think i am just using standard ubuntu? version 8.04 is what i donloaded from the ubuntu website. Sorry i really know nothing about all this, yet.

---

### Post by Tanker Bob on 2008-09-01
Thank you for that information. Please start the Terminal/Console and type:

```
lsusb
```
and cut/paste the output here. That should tell us if the mouse is recognized and loaded on startup.

Also, try unplugging the mouse, wait a few seconds, then plug it back in. In the Terminal/Console, type:

```
dmesg | grep usb
lsusb
```
and cut/paste the output here.

---

### Post by Jombib on 2008-09-02
Sorry i have taken so long to reply to you, it is going to have to wait until i can do that because somehow i have managed to completely break my machine. probably because i spend so much time messing about with it. i think it may be a problem with the motherboard. so i am going to build up a new computer when i find another half decent mother board amongst all my stuff and hopefully wont have the same problem.

---

### Post by Tanker Bob on 2008-09-02
No problem. Sorry to hear about the troubles with your box.

---

### Post by jazzcatgab on 2008-10-10
Tanker Bob,

Excuse me hopping in here, but I'm having the same issue as Jombib. MS optical mouse, USB but plugged in using the round serial adapter into the mouse port on the motherboard. Would I use the same commands in the terminal as below? I'm pasting my lsusb response:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000  

This wasn't a problem in Gutsy, how it freezes after a period of time and plugging and unplugging brings it back. If there isn't a solution, is there an easier workaround than reaching back and unplugging and plugging?


> **Tanker Bob said:**
> Thank you for that information. Please start the Terminal/Console and type:

```
lsusb
```
and cut/paste the output here. That should tell us if the mouse is recognized and loaded on startup.

Also, try unplugging the mouse, wait a few seconds, then plug it back in. In the Terminal/Console, type:

```
dmesg | grep usb
lsusb
```
and cut/paste the output here.

Thanks,

---

### Post by Tanker Bob on 2008-10-10
Hi jazzcatgab,

Sounds like you are plugging the mouse into the PS/2 plug using a USB-to-PS/2 adapter. In that case, the mouse will not show up in the USB list. It's hard to tell from your description what the problem might be. Does the mouse work OK when you first boot up? Would you post the "Input Device" section for your mouse from the /etc/X11/xorg.conf file?

---

### Post by jazzcatgab on 2008-10-10
Yep, that's exactly what I mean. I have modified xorg as you will see below:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

Also, it will work for hours and then complete freeze. It also sometimes jumps into the menu bar and starts clicking things (making new folders, etc. on the desktop).
Thanks for helping,

---

### Post by Tanker Bob on 2008-10-10
I don't see any obvious issues in xorg.conf. The PS/2 support in *buntu is pretty solid. Your description sounds a if something small like a crumb is getting stuck under one of your buttons. This may sound silly, but can you clean out that area of your mouse and see if that helps?

The reason I say that is that the only other thing that comes to mind is a software conflict with the driver. Is there any program that you consistently open or are in when this happens? Or some action or sequence of actions that you've executed? Some piece of hardware that you activate right before the failure?

---

### Post by jazzcatgab on 2008-10-10
If you saw my desk, you'd never believe there WASN'T a crumb or two stuck in the mouse buttons! But I think not. I've seen other complaints about this behavior, but no real solutions yet. I'll have to look at the conflicting programs aspect. Usually just Firefox and that shouldn't be a problem.

Until this is resolved, any ideas on a way to restart the mouse without actually unplugging and plugging? Being basically lazy, that would go a long way to ending my frustration with it. :-)

I appreciate your time and knowledge,

---

### Post by Tanker Bob on 2008-10-10
I did a Google search on your problem. I found quite a few reports of problems with optical mice on ubuntu over a number of versions. There were a number of suggestions, but nothing that seemed to work reliably. I don't have any further recommendations on that.

As for restarting the mouse, you can do that by restarting the xserver. Be sure to save all your work, then do a Ctrl-backspace. The xserver will restart and you'll be back at the login screen.

---

### Post by jazzcatgab on 2008-10-11
Great tip,Tanker Bob. I'll use that.

Oddly enough, I was online in Ubuntu for hours yesterday without the problem occurring. I'm going to keep a little text log of what programs I'm using, and have used in a particular session, to see if any trends crop up.

After you had made the imcompatible program suggestion yesterday, I was thinking that maybe Terminal Server was a good suspect, but I termed served into my Windows desktop at work later and it didn't freeze the mouse then or later. I was actually disappointed! Ha!

Anyway, thanks again for your patience and help,

---

### Post by Tanker Bob on 2008-10-11
You are most welcome. I hope that you are able to nail the issue down and work around it.

---

