---
title: "reboots at GUI loading, maybe I/O problem - tried acpi=off already"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by nood1e on 2008-12-15
ok, i will list my set up first, then my problem, then what ive done so far to try and solve it. (i know it looks like a lot of reading but its not and i NEED HELP BADLY!!!!)

Set-Up:
Trying to install Ubuntu 8.10
HP Pavilion a1610n
Processor AMD Athlon64 X2 Processor 2.2GHz 4200+
RAM Speed: PC2-4200 (533MHz)3 GB DDR2 installed (2 1gb and 2 512mb)
Hard Drive Capacity: 320 GB (new HDD used solely for Ubuntu)
Drive Controllers: SATA-150
Lightscribe DVD RW multi drive
Swapped out the 300watt PSU for a 420watt PSU
.....
Video Chipset Brand: NVIDIA
Video Chipset: GeForce 6150LE (onboard)
Video Bus: PCI Express x16

My problem is this. i installed Ubuntu 8.10. it was like pullying teeth but i got it. i tried several things, but in the end i had to use acpi=off in the boot parameter at the end of the Kernel line combined with Safe Video Mode to get it to load to the GUI. Once there i was able to successfully install Ubuntu, but not with my USB mouse (teh acpi=off disabled that) but my ps/2 keyboard and mouse worked just fine. so at this point i was optimistic...shouldn't have been. 

so once it was installed and rebooted it loaded up all the way to the GUI loading part, then just restarted the computer. tried it a few more times and got the same result, except one time it just gave me a multi-colored array of squares, which the computer froze up on. after fussing with all that i added the acpi=off parameter again, which got the GUI to load up all the way to the desktop, but my ps/2 mouse and keyboard were both useless, and i got an error message "failure initializing HAL". 

so here i am. ive tried noapic, acpi=off, erasing the "quiet" parameter from the end of the kernel line (which loads the GUI but then i get glitchy graphics and my computer freezes before i reach the desktop). ive tried 8.04 and Ubuntu Studio as well. all of them fail to reach the GUI. the only thing i can imagine is that i have to use the Safe Video Mode to boot, but i dont know how to access Safe Video Mode via the command line or boot parameter. 

i might just try Fedora10 when i get home. maybe its the kernel. in my research ive found that others with my exact computer had no problem with earlier distros of Ubuntu (7.x) and such...so im concluding that its the new kernel. 

ANY HELP WOULD BE GREATLY APPRECIATED!!!!!!!
i installed this on my crappy busted and low spec laptop and absolutely LOVE it and want it on my much more powerful PC. please please share any info you think might patch me up. 

and if you feel like it you can email me with any ideas:
[email]noodle@bargertronic.com[/email]

---

### Post by nood1e on 2008-12-16
bump

---

### Post by dmizer on 2008-12-16
Did you install the 64bit or 32bit version?

Try removing the "quiet" and "splash" parameters from your boot line. That will allow you to see what message causes the reboot.

---

### Post by nood1e on 2008-12-16
tried that already. got OK's all the way down. 

i tried installing my nvidia 7100gs card to see if it was my video chipset, and i get it to boot with acpi=off but my ps/2 keyboard and mouse doesnt work.

---

### Post by dmizer on 2008-12-16
I think you have a bad install. In searching the forums, most people with your machine seem to be running just fine. Most complaints are about wireless rather than failure to install or failure to boot.

[http://ubuntuforums.org/showpost.php?p=4386442&postcount=4](http://ubuntuforums.org/showpost.php?p=4386442&postcount=4)
[http://ubuntuforums.org/showthread.php?t=928955](http://ubuntuforums.org/showthread.php?t=928955)

There's more, but they are older.

Bad/scratched CD maybe? Do a check on the install CD. If you installed 64bit, try the 32bit instead

---

### Post by nood1e on 2008-12-17
thanks for the reply.

ive tried this with ubuntu 8.10, ubuntu 8.04, ubuntu 7.10 x64, ubuntu 7.04 x32 & x64, kubuntu 8.10 and ive also tried ubuntu studio. none of the live images would load nor would the installs UNLESS i used acpi=off. but then i had no keyboard or mouse. USB or PS/2. 

I AM ABLE to use linux without the GUI though. takes all commands and everything, just no GUI. :(

the very first time i tried acpi=off on my very first install i was able to use my mouse and use my keyboard (PS/2 only) but after the install it wouldnt. and i got that "fail to initialize HAL" error. weird. 

just today i got Ubuntu to load up using acpi=off without the HAL error, but still no keyboard and mouse. 

crazy crazy crazy!!!


also, ive read the first link already and the second is irrelevant, but thank you for your efforts.

---

### Post by nood1e on 2008-12-17
well, my keyboard works fine with linux ive concluded. but NOT in the gui. with acpi=off my PS/2 and USB keyboards and mice wont work in the GUI, but my keyboard works in the terminal when i hit Alt-F3 at the GUI. weird. i dont get it!!!!!!!!!!!!!!!!!

---

### Post by dmizer on 2008-12-17
Try disabling legacy USB in the bios settings. Take a look at your other bios settings (particularly for power management) and see if any of those settings help matters.

Really, the two links I sent you were only to demonstrate that people do have Ubuntu running on your hardware. I'm seriously not sure why you're having such a difficult time.

edit:
You should also try adding:
```
pci=routeirq
```
as a boot option, that may help things.

---

### Post by nood1e on 2008-12-18
[SIZE="3"]actually, i got it installed and running with only [COLOR="Red"]acpi=off[/COLOR] as a peramiter. i dont know what the hell the problem was before, but all of a sudden it worked this time. maybe my disks were messed up. 

**[COLOR="Blue"]but now i cant get my ethernet controler to discover the network connection. tried all the obvious things like disabling it and unpluging the router...all that stuff. also tried a working wired connection that is working with my laptop. dont know. i have an NVIDIA motherboard, thus nforce chipset and nforce ethernet controller...and i hear they can be trouble.[/COLOR]**
[COLOR="Red"]
**[CENTER]---------how i fixed the install and failure to load GUI problem---------[/CENTER]**[/COLOR]

here is everything i did to get this working, just so people know if they run into the same problem:

and the problem with my drive not booting into the CD's seemed to be because i was using DVD's. if i use a CD is boots up no problem to the install disk.

-[COLOR="Red"]RE-DOWNLOADED[/COLOR] ubuntu 8.10 CD ISO image

-burned it to a CD (*instead of a DVD like i had been doing*)

-burned it using a newer burner, burning at 24x (*i know they say 4x, but this worked*)

-burnt it using Nero6 on windows xp laptop

-chose the [COLOR="Red"]install[/COLOR] option (*hitting [COLOR="Red"]F6[/COLOR] and choosing the [COLOR="Red"]acpi=off[/COLOR] peramiter before hitting enter to access the install*)

-doing a [COLOR="Red"]full drive[/COLOR] install

-when it reboots after the install hit [COLOR="Red"]ESC[/COLOR] at the GRUB before it loads

-type [COLOR="Red"]E[/COLOR] on the top most option, the general boot thing

-then go to the line that starts with KERNEL and hit [COLOR="Red"]E[/COLOR]

-type [COLOR="Red"]acpi=off[/COLOR] at the end, leaving a space between the last entry and [COLOR="Red"]acpi=off[/COLOR]

-hit [COLOR="Red"]enter[/COLOR] and then hit [COLOR="Red"]B[/COLOR] to boot

-once you are booted type this in the terminal (*to make the acpi=off change permanent, otherwise you will have to enter this at the boot every time*)
```
gksudo gedit /boot/grub/menu.lst
```
(if you get a blank screen in the editor then you entered the path wrong...happened to me. :P )


-find the line that says
```
# defoptions=quiet splash
```

-and make it look like this
```
# defoptions=quiet splash acpi=off
```

-now save it by hitting the [COLOR="Red"]save[/COLOR] button at the top and close it. 

-now type this into the terminal:
```
sudo update-grub
```

-restart, cross your fingers and let ubuntu start up as normal and you shoule be cool.[/SIZE]

---

### Post by nood1e on 2008-12-18
unfortunately this does mean that you can't use USB or any pci featuers...so it pretty much cripples the system of maximum usability. 

ive chosen not to put linux on my PC due to this problem. i even tried SUSE with the same problems. my hardware just isnt compatible. so very very unfortunate. i wish someone had a real fix for this...

---

### Post by dmizer on 2008-12-18
I still think that you could be successful by looking at bios settings.

Again, you are the only post I've seen which indicates you need acpi=off in order to boot. If you do not use acpi=off, do you boot into CLI only? What happens after you install the nvidia drivers (do you still need acpi=off)? Does "pci=routeirq" not work at all? What about turning off apic instead of acpi ("noapic"). What about bios updates? Usually acpi problems are a result of an old or poorly programmed bios.

Just trying to figure out what's going on here. Just because your machine does boot with the "acpi=off" option does not mean that this is your only solution.

---

### Post by nood1e on 2008-12-19
thank you for being so thorough, but ive tried most of that. 

what happens if i use nothing is this:
starts to boot, reaches GRUB, proceeds to the OS loading bar, once the bar gets to the last tiny bit it will either reboot the computer, freeze with a black screen, freeze with multiple colored squares or reach the first tan colored screen of the GUI and freeze with twitchy horizontle lines going across the screen.

with noapic i get the same result as if i did nothing.

pci=routeirq i havent tried yet, will later tonight. 

im about to try to install the nvidia drivers manually later tonight as well. not having networking is making this all a million times harder.

and i can't get BIOS updates from pheonix like most people since mine were exclusively released by HP (trust me, ive double, triple and QUADRUPAL checked into thsi), and HP hasnt released a new BIOS update since 2006 for my mobo, which i upgraded to the moment i purchased my computer a few years ago. and even if there were a beta one i wouldnt want to try it...too risky.

the only options i have in my bios that look like they would help is:
legacey support  on/off
plug and play OS  on/off
PS/2 mouse   detect/on/off
and there was one other but i cant remember what it was since it was some option to turn on/off for a support called...some string of numbers support...cant remember what the numbers were. i think it was to do witht he IDE support, which i need for my CD/DVD drive.

and ive read a TON of threads about people requiring this for boot and to run linux. i guess it doesnt bother some people, but i needs my USB devices. 

im currently runniung OPENsuse on that computer now. it installed and runs without me having to enter acpi=off in the boot line, but i still have no NETWORKING!!! i dont know if its a suse thing, that i have to configure it or not, but i am still without that. might be my nforce ethernet causing all these problems. 

from what ive read, older nvidia mobos DO NOT get along with linux. something about their chipsets just dont communicate well with linux. 

thanks for the response anyway. i will post the results of the routeirq command if i need to use it...since im in suse now i may not need to use it. although, when i first tried the GUI installer for suse the same damn thing happened. i had to install it with the "SAFE INSTALLER" but it booted up the first time no prob. havent tried restarting yet. 

i will update none the less. 

thanks for your input.

---

