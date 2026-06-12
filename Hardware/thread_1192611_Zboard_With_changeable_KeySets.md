---
title: "Zboard With changeable KeySets?"
date: 2009-06-20
forum: Hardware
---

### Post by DarkenSX on 2009-06-20
Hi I Have a Zboard Gaming Keyboard With Changeable Keysets I Was Wondering if anyone Has gotten it to work successfully I Know That people have gotten the other model Zboards to work on linux using xmodmap and other things but some of the keys on my keyboard dont give keyscan codes. "example: (World of Warcraft wotlk keyset: Special WoW Keys "Right side of Keyboard" Dont Give codes when pressed)" I assume the reason for this is the same As windows. When The Woltk Game is not running in windows Zengine Disables the keys but in linux there is no zengine to enable them or even set them up So I dont have any idea what to do anyway. 
This is the keyboard im talking about: [http://www.steelseries.com/us/products/keyboards/zboard/information](http://www.steelseries.com/us/products/keyboards/zboard/information)

---

### Post by DarkenSX on 2009-06-22
Well I just Contacted Zboard company and this is what they told me:

[FONT=Arial][SIZE=1][COLOR=#000000][SIZE=2]Hi I was Wondering if it would be possible to have Some way to use my zboard on linux specifically Ubuntu there are alot of people who have zboards that have linux and the keyboards and cant use them and really want to i know it sounds like a daunting task im asking but a lot of people dont use windows.
[/SIZE] [SIZE=2][COLOR=#004477] [-Open- 06/20/2009 08:42:15 AM  - Request Submitted By Customer -] [/COLOR][/SIZE][SIZE=2]

Thank you for your interest in SteelSeries Professional Gaming Gear.

Sorry, but none of our products are supported by Linux.

Unfortunately we are not considering developing a proprietary Linux driver anytime soon.

The keyboard has a simple architecture and every key can be easily sniffed using a simple filter driver under Linux. So there is no real need to open up Windows driver source code (it is substantially different on Windows anyway) in order develop a Linux version. If the Linux driver gets developed as a community-driven open source project – we will be happy to support and promote it on our website.

Thanks,
SH

[/SIZE]       [SIZE=2][COLOR=#004477] [-Pending- 06/22/2009 07:48:49 AM - support - Request Updated By Customer Care Team Member -] [/COLOR][/SIZE][SIZE=2]




Maybe Someone Here can tell me how to "Sniff" the keys out. because 1. idk even what a filter driver is. and 2. idk where or how to do any of this.[/SIZE]    
[/COLOR][/SIZE][/FONT]

---

### Post by DarkenSX on 2009-06-23
Anyone? Does anyone know what a filter driver is or where i get it? Or How to "sniffed" the Keys out im really lost i know someone has to know what they are talking about.

---

### Post by klightspeed on 2009-09-06
The ZEngine software sends a command 
*(type OUT | CLASS | INTERFACE request 0x09 value 0x0200 index 1 data 05 01 00 00 00 00 00 00)*
to _disable_ the ZBoard's internal key re-mapping.  This enables _all_ of the keys on the keyboard.  The software is then responsible for re-mapping the keys.  *(This was found by using [SniffUSB](http://www.pcausa.com/Utilities/UsbSnoop/) under Windows, some trial and error under Linux, and some deductive reasoning.)*

The HID interface this command (and the Led and Query Keyset commands, and keyset change messages) are relayed on is claimed by HID by default, but is not claimed by a higher-level HID driver.  A program can use libusb (the keyset change events are not valid HID reports, and neither are the commands) to send commands and poll for keyset change events.

Unfortunately, four of the keys fall on "Unknown" codes inside the Linux HID driver - these are the search, web and info buttons on the top, and where the letter G on the "Gaming keyset" sits.

This means that either a modified USB keyboard driver would need to be made to utilize these keys, or a program that sits between libhid/libusb and uinput (unbinding the generic-usb driver also unbinds hidraw) converting HID keycodes to Linux keycodes, based on the current keyset.

---

### Post by nzadLithium on 2009-10-12
I've been working on a usermode driver using libusb. It took me a while to get it semi going then I kinda forgot about it :p

On my computer, my gaming keyset and standard keyset both work fine other than pad and bar lock buttons. The multimedia keys do not function at all.

I have got the pad lock and bar lock keys to register, but have to unload the kernel keyboard driver and load in my one which is a mess and i haven't written anything to interpret standard keys so keyboard stops working.
The usermode driver I have written detects all multimedia keys fine using the standard keyset, however as soon as adding the gaming keyset (the fps styled one that comes with it) the multimedia keys cease to report any key signals, I'm wondering about your signal you found klightspeed. I think i'll try sending it to my zboard and see if it reactivates multimedia keys with the gaming keyset setup.

I might take another look at what i can get out of usb sniffing on windows. I'm pretty new to drivers and usb so I didn't really understand what half the signals being sent in and out were :p But i'll take another look see if I can get it going better :D

I'm not making any promises here DarkenSX, as I have exams starting soon which I really need to do some work for :p But if you stick on your keyset then go to terminal and stick in 

sudo mount -t usbfs none /proc/bus/usb
sudo mount -t debugfs none_debugfs /proc/sys/debug
cd /proc/sys/debug/usbmon
now make sure your mouse is out of the way coz if its usb and high sensitive like mine it'll make a mess and you wont be tell between it and your keyboard easily :p
sudo cat 0u

Press all of your keys in some sort of order on your keyset and record the order you pressed the keys. Get the multimedia keys as well.

once your done ctrl+c to get out.
copy and paste that info here.

change keysets to the standard keyset
sudo cat 0u
press the multimedia keys in order, then bar lock and pad lock.
record the order and copy and paste the output here.

change keysets to the gaming keyset that the keyboard comes with.
sudo cat 0u
press the multimedia keys in order, then copy and paste here.

If you have any other keysets that don't work stick them in,
sudo cat 0u
record the order u press keys (only keys that don't work plz :p)
copy and paste the output here.

cat /proc/bus/usb/devices
copy and paste that here.

sudo lsusb -d 1038:0100 -v
copy and paste that here.

Those last two are really only for me to check everything is similar to mine.

Plz make sure you explain which results are from which keyset.

The way I have this usermode driver setup at the moment is it has a startup script that u stick whatever command u want run when a key is pressed and it runs it. I might be able to setup something that hooks your keyboard somehow and makes it send the key signals to programs but no guarantee's :p This is basically a temporary hack until I can collect enough info to make it work properly. Then i'll set to work on how to write a proper kernel driver :p I should prob contact whoever owns zboard now if i get that far see If I can get their approval for releasing. XP

As I said no promises, but if you can get that info for me I'll see what I can do.

---

### Post by nzadLithium on 2009-10-12
I am assuming:
"type OUT | CLASS | INTERFACE request 0x09 value 0x0200 index 1 data 05 01 00 00 00 00 00 00"
Is a control code? If so it does not work on my zboard, libusb reports LIBUSB_PIPE_ERROR which is supposed to mean the device doesn't support that command.

---

### Post by telemu on 2009-10-12
I have a similar problem.

Can anyone tell me where I can find drivers for my keyboard Zmerc from the same manufacturer as the Zboard?

I'm new to linux and I'd love to get my keyboard running smoothly.

Thanks for any help in advance

---

### Post by nzadLithium on 2009-10-12
telemu, as far as I've heard you don't need a seperate driver for the merc. You just need to remap the keys not working. 
Keyboard button configurations are available in this thread:
[http://ubuntuforums.org/showthread.php?t=385426](http://ubuntuforums.org/showthread.php?t=385426)
It says to check page 4 of that thread to find an application that will handle the setup of the merc for you.

It seems some versions of ubuntu were messing up the key repeat. I'm not sure if that still happens in new versions of ubuntu, if you find it does check that thread for more info.
and here for the guy that made it all works site:
[http://www.valdegames.com/pig/wordpress/2007/04/10/merc-zboard-driver-version-011/](http://www.valdegames.com/pig/wordpress/2007/04/10/merc-zboard-driver-version-011/)

---

### Post by nzadLithium on 2009-10-13
Zboard software freezes whenever I try to stick a logger on the control signals, it does the endpoints fine but they do the exact same thing as ubuntu once the zboard software freezes, gives u lots of null signals on gaming keyset :S

Since nothing seems to show up on the endpoints i'm assuming that all changes to the button configurations and notifying the computer which keysets are connected must be sent through control signals? If anyone else can try grabbing some logs of the control signals when they change from standard keyset to the gaming one that would be great.

On the steelseries website (which appear to be the new owners of the zboard hardware) they say on their page about a special edition mouse that they would happily assist any community driven efforts to create linux drivers, I think i'll email them and see if this extends to the zboard :D

---

