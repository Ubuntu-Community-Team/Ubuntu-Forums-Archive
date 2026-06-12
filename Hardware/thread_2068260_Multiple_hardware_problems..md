---
title: "Multiple hardware problems."
date: 2012-10-08
forum: Hardware
---

### Post by douggiephresh on 2012-10-08
Ok, pretend you are explaining this to an infant. 

#1- System settings > Displays is reading as one big laptop screen.
I have 2 screens, both different sizes. I cannot, for the life of me, get "Displays" to read that I have two screens. Whenever I seem to change something in nvidia-settings, either one screen or the other stops working or goes white. Also, my main monitor, HP 2511x, does not look up to par. The resolution is set to 1920x1080 like it should, but it doesnt look crisp and when I watch a movie or scroll the internet there are lines on the screen. I think it needs a driver.

#2- I think I got the nvidia driver to work for my GTX570. If I did, it was just by typing random commands into the terminal because I have no idea what I was typing, I was just trying random bits and pieces of what I was reading online. Is there a way I can overclock my hardware (CPU, GPU) in the OS or will I have to do it through the BIOS?

3#- Will I need any other drivers or anything like it for my new setup? Alot of this is kinda confusing, I might have jumped into the deep end a little early, but then again, it doesnt seem like there is a shallow end. Any and all help is appreciated. Remember, start from square one and assume I dont know anything, lol. Thanks.

BTW, Ubunutu 12.04 64-bit

---

### Post by Bashing-om on 2012-10-08
Hello again douggiephresh; Welcome to the forum.

How bout we simplify things and get only one monitor functional, later get the other operating ?

For now lets see what display and driver you have loaded..terminal commands:
```
sudo lshw -C display
lspci | grep VGA

```Will tell a bunch. Then compare for compatibility .
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by douggiephresh on 2012-10-08
doug@doug-desktop:~$ sudo lshw -C display
[sudo] password for doug: 
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: GF110 [GeForce GTX 570 HD]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:57 memory:fb400000-fb7fffff memory:c0000000-cfffffff ioport:f000(size=64)
doug@doug-desktop:~$ 
doug@doug-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570 HD] (rev a1)
doug@doug-desktop:~$ ^C
doug@doug-desktop:~$

---

### Post by Bashing-om on 2012-10-08
The i915: I am aware of some problems with some resolutions. Thinking on the xorg.conf edits for both drivers. Lemme see what I can come up with.

Is your machine a laptop or desktop ?

[INDENT]scratchin <==BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-10-08
At this point not looking good for the i915 driver//all solutions seem to turn off kernel mode setting ..for now I am not sure how doing this effects the Nvidia GTX 570.

This is going to be a learning process for sure! <==BDQ

---

### Post by douggiephresh on 2012-10-08
What do you mean 915? Im running a desktop

---

### Post by douggiephresh on 2012-10-08
I really wanna give linux a shot, i know that it should be a better way to use a computer than windows, but why is it so complicated just to get your monitor to work?

---

### Post by ahallubuntu on 2012-10-08
To be clear: you have a desktop with both integrated video (the Intel controller) AND a separate video card - the NVidia - right?

Your two monitors are plugged into the NVidia only and not into the main motherboard monitor (VGA) connector?

There may be a setting in your BIOS Setup to disable the on-board video entirely; it may still be active even if you are not using it.  That could make it less confusing for Ubuntu.

Also - have you tried with just one monitor?  What happens?

Are the two monitors identical?  If not, have you tried swapping them?

---

### Post by Bashing-om on 2012-10-08
complicated: not really, just takes some adjustment in thinking process.(anything and everything is configurable) Please bear in mind that the cd you used to install with works on 90 percent of the systems (many many many different configurations,-out of the box-. It just is not possible to meet every contingency with the one installation medium. The great thing is that ubuntu can be made to run on such a great variety of hardware. And all for free with no strings attached and the options to do with it whatever/however you wish.

At the present time we will get your system to play nice with your monitors. I just have a small hitch IRT Nvidia compatibility listing for your GTX 570 HD//
and I am tired and am going to sleep on it ...I will see this thread in my AM.

---

### Post by douggiephresh on 2012-10-09
thanks for all the help, i really appreciate it! Another couple things, when i try to run MyUnity it says im stuck in 2d mode. and when i view displays in system settings it shows i have 1 big laptop monitor.

---

### Post by douggiephresh on 2012-10-09
yes, the two monitors are plugged into the video card. monitors are not identical.

---

### Post by Bashing-om on 2012-10-09
Couldn't sleep yet...soo
1. Nvidia GTX 570 has not made it to the compatibility catalog, However, several have got the card working in their system. If they can we can!

The trick is going to be to get it up on one monitor first, and then dualize it. Looks promising and will prove to be interesting  seeing this through.

It is great that Nvidia supports ubuntu to such a LARGE extent.

Anyway, in the AM will be better prepared and will  see how your system performs. Will take it up there.

[INDENT]looking to try <==BDQ

[/INDENT]

---

### Post by douggiephresh on 2012-10-09
thank you so much for your enthusiasm! I somehow ended up with 2 monitors not working so I just did a fresh install. All I did was update it. Ill leave the clean slate so we can work on it tomorrow. thanks again!

---

### Post by douggiephresh on 2012-10-09
It wont let me erase information from my USB stick or format it.

---

### Post by Bashing-om on 2012-10-09
Hey no problem.
 In all my many years, this is my chosen operating system, I do what I can to share and promote.
Situation at hand:
 Assume you have limited experience with ubuntu.
We have a clean slate to work with, that is a good.
Now to procedure to get you up.

Only connect one monitor.
Boot up the install, when the bios screen clears depress any key->boot options menu;[INDENT]f6 key selects the "nomodeset" boot option,
f10 continues the boot into ubuntu.
[/INDENT]Full explanation this link (and many others)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
You are now booted up with limited abilities; Now to load the graphics driver;[INDENT] the launcher is on the left of the screen, click on "system settings" ->under hardware is "Additional Drivers", Click on Additional drivers and select the latest driver available (may have as many as 4 choices),
install the driver (wizardly manner). Reboot !
Advise me at that time what results.

[/INDENT]If now all looks good will proceed to dualize your system.

off topic: Winter here is coming on and I have things to do, Got to go out of town to get materials, will be tonight before I can get back on this. Will catch up with you then.
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by douggiephresh on 2012-10-09
Wait, so I do another install? Or what? Im pressing any keys after the bios and its not bringing up any special menu. it just goes to the ubuntu log in like usual

---

### Post by douggiephresh on 2012-10-09
I dont want to cave and go back to windows but, god, its so much easier.

---

### Post by Bashing-om on 2012-10-09
sorry I took your post #13 to be the "fresh install". See no reason at all to do another.

You are trying to install 12.04.1 no ? and are you installing from cd ?

I gonna reboot my system and closely observe,,,back in a bit.

Driver troubles: Let me tell you I have had a lot more hassle with windows (long time in the past) both graphics and wireless than I have ever experienced with linux. Not even microsoft is able to support every piece of hardware out there, And they can be difficult sometime to relate to ---I hate the term proprietary information, but this work-a-round should work!-- What can I say ...Sometimes I want to know.

[INDENT]ubuntu -no secrets- 
[/INDENT]

---

### Post by douggiephresh on 2012-10-09
thanks for all your help bashing, but Ive switched to linux Mint13 cinnamon. My monitors worked out of the gate and i like it alot more. im currently working on getting my openvpn configured.

---

### Post by Bashing-om on 2012-10-09
Apologies I did miss-direct you---instruction were for booting from the cd:

Install procedure:
Bios screen clears, depress the shift key -> grub menu:
Down arrow key (any key actually) to halt the countdown:
arrow key back up to the current boot kernel,,,could use the "recovery mode" but just as soon not.
"e" key for edit, arrow down to a line similar to this:[INDENT]linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff

and arrow across;
[/INDENT]add "nomodeset" parameter -with out the quotes- just before "quiet splash":
CTL-x to continue to boot into ubuntu.

This is germane  only for this one boot.

once booted ..do the "Addition Drivers" procedure.

  Rebooted -Now what are we looking like ?[INDENT][INDENT][INDENT]BDQ

[/INDENT][/INDENT][/INDENT]

---

