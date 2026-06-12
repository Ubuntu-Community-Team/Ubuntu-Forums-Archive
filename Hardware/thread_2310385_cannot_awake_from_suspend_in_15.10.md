---
title: "cannot awake from suspend in 15.10"
date: 2016-01-18
forum: Hardware
---

### Post by pickarooney on 2016-01-18
I recently had to format and reinstall Xubuntu 15.10 and since then cannot reawaken the PC from suspend.
When I tap the power button now, instead of returning to the GUI I get a black screen with graphics errors. I have to restart the PC completely.

NVRM Xid graphics exception

I'm running the latest compatible driver (340.96) for my nVidia GeForce GT218 card. This is the suggested latest driver in the Additional Drivers tool.
I tried purging and installing the 355 and 358 drivers but in each case after reboot I was left with the nouveau drivers instead and with a very basic resolution.

Moreover, every time I restart the PC, fsck starts to run and wastes 10 minutes. I can cancel with ctrl-c but would prefer if it didn't do this. There's no need to run fsck on every boot!

If anyone knows a better driver version that will work with my card and allow waking from suspension and/or a way to prevent fsck running each boot, I'm all ears.

I realise it may be fsck-ing because I have to hard-reboot it, but without solving the first issue I can't really solve the second one for now

---

### Post by pickarooney on 2016-01-19
Thinking about changing to an ATI graphics card. Are these well supported nowadays on Ubuntu?
Asus Radeon HD 5450 -

---

### Post by pickarooney on 2016-01-21
The same happens with earlier versions of the nVidia drivers. Weird, as suspend used to work just fine before I reformatted and reinstalled 15.10.

I realised I have an on-board ATI card which I seem to have disabled in the BIOS, or else it's just being overridden by the PCI-E card.
In the BIOS settings there is a section on onboard graphics and the setting options are like GFX0-AGP etc.

Which option makes the on-board chip default or should I just pull out the nVidia while I test the on-board ATI?

---

### Post by pickarooney on 2016-02-17
So I pulled the PCI e card and booted with the on board radeon connected. First surprise - the turquoise xubuntu splashscreen displayed which I'd never seen happening. However I got stuck on a black screen with a mouse pointer indefinite. I booted to console and installed the fglx drivers and restarted. Sam thing. There was no way I could find to get X working. Switched back to nvidia and the splashscreen is gone, wake from hibernate is broken but at least X works. It's as though the screen resolution for the splashscreen doesn't fit the nviia and X doesn't fit the radeon.

So I've no clue how to get a gfx card working fully, be it nvidia or ati.

It's 2016. This kind of crap should be well in the past.

---

### Post by pickarooney on 2016-02-23
Is there any kernel parameters I should be putting in GRUB that might help with these issues?
As is stands boot alternates between a low-res splash screen then freezing and no splash screen and successful boot, but no wake from suspend.
I can't grasp why or how it does the splash screen sometimes and not others. This is a real pain, trying to do some basic stuff like starting, stopping and suspending a PC and not having to spend ten minutes messing about with config files every day.

Is there really nobody that can help?

---

### Post by pickarooney on 2016-02-24
I stupidly tried the advice at the bottom of this page: [http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen](http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen) 
And now I am completely unable to boot.

I need some solution for getting a basic grub etc. set up so I can use the computer again. Please!

---

### Post by pickarooney on 2016-04-26
Just tested this on 16.04 and amazingly I was able to suspend and restart at the first attempt. 
Luckily, as in this release it's no longer possible to either start X or a window manager on boot or skip the disk check which runs every single time.

---

