---
title: "Suspend refuses to work on 8.04"
date: 2008-08-06
forum: General Help
---

### Post by milasch on 2008-08-06
I tried the out of the box suspend. The computer basically exits X, then for 1-2 seconds it does some HD activity, then halts completely with the cursor blinking. 

Nothing happens further to that and I can't interact of any manner with the computer other than with the reset button.

I found a little about uswsusp, installed it, set up the uswsusp.conf to look like this:
```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
#resume device = UUID=087b0a7e-5eb0-4801-a164-0638b7e6852b
resume device = /dev/sda3
splash = y
compress = y
early writeout = y
image size = 971371151
RSA key file = /etc/uswsusp.key
shutdown method = platform
compute checksum = y
suspend loglevel = 0
max loglevel = 0

```

where /dev/sda3 is my swap drive, and it freezes after exiting X and displaying the "Taking snapshot" message on s2disk or s2both.

checking /var/log/kern.log or /var/log/messages doesn't help much:

```

Aug  6 23:34:30 milasch-desktop kernel: [  200.938383] ACPI: PCI Interrupt for device 0000:00:14.0 disabled

```

My processor is a Q6600 and mobo is a ASUS P5N-D (based on nforce 750i).

I hoped that installing nforce drivers would help, but nvidia doesn't supply chipset drivers for this platform I guess, living me with no choice but use the native ones. Anyway, I wouldn't know if this is a driver related issue.

As you can probably notice, I'm no linux genius, so forgive my newbieness.

Thanks for any help

---

### Post by cmnorton on 2008-08-07
This is an interesting question, because I can hibernate with Kubuntu 8.04, but cannot bring the system (Thinkpad T61p) out of a suspend other than to force power off and reboot.

I've posted this question: [https://answers.launchpad.net/ubuntu/+question/41538](https://answers.launchpad.net/ubuntu/+question/41538)

Edit:
-----------------------------------------
You could also look at the output from man pm-hibernate, man pm-suspend, and man pm-is-supported. This stuff is configured in /etc/pm.

---

### Post by Uchiha_madara on 2008-08-09
tell me how is the capabilities of your pc/Laptop

sometimes Suspending and hibernating can't work because

both need space and high ram

Good Luck

---

### Post by fragos on 2008-08-09
Make sure your swap space is larger than your memory size. Suspend and Hibernate work perfectly on my Dell 1420n laptop.

---

### Post by milasch on 2008-08-12
> **fragos said:**
> Make sure your swap space is larger than your memory size. Suspend and Hibernate work perfectly on my Dell 1420n laptop.

I guess this is exactly the issue... I have installed more memory after I created the swap partition. I'll try resizing it to a larger an let you guys know.

---

### Post by milasch on 2008-08-12
> **Uchiha_madara said:**
> tell me how is the capabilities of your pc/Laptop

sometimes Suspending and hibernating can't work because

both need space and high ram

Good Luck

My system is a Intel Quad Core Q6600, 3GB RAM and 500GB Hard drive...

The only issue where I think the problem lives is that the memory now its larger than the SWAP partition. As I replied to fragos, I'm trying to resize the partition to at least 1GB more than the memory (it's currently 2GB now), and play a little with this. 

Thanks!

---

### Post by lukjad on 2008-08-12
Suspend never really worked for me in either Ubuntu or Windows. I recommend against suspending because I have seen too many problems that are caused directly by hibernation. Recently I was helping a neighbour who have Windows Vista and could no longer print. The reason was because she had been hibernating for months on end and a document was stuck in the print cue and couldn't be deleted without a reboot or shutdown. 

[/rant against hibernating a computer]

---

### Post by milasch on 2008-08-13
Well, I basically need to suspend because I work a lot remotely with my home desktop, and sometimes when I wake up, I forgot to turn the computer on... Suspending would be the best answer because then I can wake it up through the internet when that happens... Not to count on the amount of electricity I can save suspending my computer remotely when I know I won't use it for a certain amount of time, and when needed again, I would wake it up on lan. But of course i'm looking for a reliable way of doing that because it sucks to need the computer and it's off or it froze by some reason and needs a hard reset.

---

### Post by fragos on 2008-08-13
Wake from LAN may be a BIOS parameter.

---

### Post by milasch on 2008-08-13
It is, but in order to test it and stuff, I need to get the suspend working properly.

---

### Post by fragos on 2008-08-13
I don't know if this makes a difference to you but resuming from suspend requires password entry and I'm not sure what the start of the startup process when it's requested. I'm also not sure that all desktops are designed for suspend, hibernate might be a better choice.

---

### Post by milasch on 2008-08-14
> **fragos said:**
> I don't know if this makes a difference to you but resuming from suspend requires password entry and I'm not sure what the start of the startup process when it's requested. I'm also not sure that all desktops are designed for suspend, hibernate might be a better choice.

I figure hibernate is a better choice, although it shuts the computer down and doesn't allow by that means wake up on lan, or wake up something. I know that on Vista, suspend is working fine, even though I had it tested a couple of times only.

About the password, I wasn't aware of that, but probably there's something that can be done in the resume scripts.

About swap, I just figured how to set up a swap file instead of resizing the partition (for those who ever need: [click here]("https://help.ubuntu.com/community/SwapFaq"))... As soon as I have time I'll test if suspend/hibernation is working fine, and post the results here.

---

### Post by Mgiacchetti on 2008-08-14
File a bug report, its a bug.  I had the same problem.  also, when you do get it 'fixed'  your usb will go out when you resume from suspend/hibernate. (another bug)

---

### Post by milasch on 2008-08-14
OK, I've created a swap file, modified the /etc/fstab to point the swap to that swap file I created, all looked right.

Since I have 3GB RAM, I created 2x my RAM as per the recommendation in (even though i know 6GB is more than I'll ever need) [this tutorial]("https://help.ubuntu.com/community/SwapFaq").

Rebooted, everything was fine. Finally I tried to use the pm-suspend through the GNOME Quit button. Same stuff... Computer got ready to power off, hard drives stopped spinning, the keyboard NUM/CAPS/SCROLL locks lights blinked, and the computer froze, not going to the suspend state. To use the computer again I rebooted it. Ubuntu started booting then froze... Argh!!!

I could only manage to boot using the "recovery mode". Than I started rolling the changes back, and I finally got to state 0, having a /dev/sda3 swap partition with 2GB space. Ubuntu now boots almost normally, except for the fact that instead of showing that splash screen until I get to gnome, it, at some point before starting hard drive activity, closes the splash screen and starts being verbose, showing whatever is being done on the boot.

Not to forget that, when I had the 6GB swapfile, i couldn't manage to use uswsusp s2both nor s2disk by any means. It simply would say that there was no swap file... I tried setting uswsusp.conf to /mnt/6GB.swap where my file was located, and also using the UUID returned by the mkswap command. I tried playing with these both values in the /etc/fstab with no success...

I tried looking for the system logs: messages, kern.log, etc, and couldn't find anything that would indicate where the problem was living.

Think it is a hopeless case, isn't it? Should I wait for some kernel update?

```

uname -r
2.6.24-19-generic

```

---

### Post by milasch on 2008-08-14
> **Mgiacchetti said:**
> File a bug report, its a bug.  I had the same problem.  also, when you do get it 'fixed'  your usb will go out when you resume from suspend/hibernate. (another bug)

if you remember, can you share how you got it 'fixed'?

---

### Post by milasch on 2008-08-19
> **milasch said:**
> if you remember, can you share how you got it 'fixed'?

I guess that's either a: "I don't remember" or a: "will not share" or even a: "I didn't read your last post".

:lolflag:

Ok, ok... not funny

---

