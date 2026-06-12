---
title: "nvidia geforce 9400 gt video goes black after grub loads - black at the grub menu"
date: 2010-03-13
forum: Hardware
---

### Post by siirial on 2010-03-13
I have been working on this for a couple days now trying anything I could find. I am attempting to install a geforce 9400 gt pci card into an older dell dimension 4500s. It has a p4 1.8ghz and 2gb of ram. I have the most recent linux mint main edition installed on my hard drive as well as a liveCD. Both are giving me the same exact issues.

I have gotten the BIOS to recognize and use the new card at boot. Once grub starts to load, the screen goes black. It is still working, i can move the cursors and make a selection (from memory of the menu when it last worked) and the computer continues to boot. I have tried disabling the new card and reverted back to using the integrated intel graphics (845e i believe) so I could go into recovery boot. I tried using EnvyNG to install the latest nvidia drivers and rebuild the xorg.conf. i even ran dpkg to update all my packages for good measure. Once I go back to using the new card again, same black screen.

I also get this from the live cd... except that once it first loads i get text saying that is it loading vmlinuz.img etc... then black.

I tried hitting alt-f1 and I get a cursor, but no prompt. I can type things, but they dont do anything. I am not a noob, but im still far from knowing the ins and outs of linux and am at a point to where I dont know where else to look for answers. Thanks in advance for any help.

Oh, I originally installed using the proprietary hardware drivers. I installed the card, booted, and selected the recommended nvidia driver from the hardware drivers. upon reboot, I got the mint splash screen on the old inegrated graphics, but it then goes to a login prompt and flashes constantly. I can only input if i can catch the prompt before it flashes blank. I can repeat this if I go through a regular boot with my bios using the integrated graphics as default video (i believe the new card is disabled when the bios does this).

---

### Post by lidex on 2010-03-14
If you're having issues at the grub screen, X hasn't even loaded yet so I don't think it's the drivers per se. Are you using grub legacy or grub2?

---

### Post by siirial on 2010-03-14
It is grub 2. But the issue is only when I am using the card. If i switch back to integrated, everything is fine. I know grub is running, just not displaying. I can hit enter to select which grub boot option i want (if i can remember the order) and it boots, but still no video. basically get the command line back end but no graphical part of the os. same thing if i boot off the livecd.

But the card works great if i try xp...

---

### Post by siirial on 2010-03-14
I would also like to add that i have tried a couple different ubuntu based linux livecd's and get the same exact result. I am going to try other distros and see if its ubuntu or linux related.

---

### Post by lidex on 2010-03-14
When, exactly, is it going black? Do you get the grub menu? 

Power down. Remove the video card. Connect monitor to onboard port. If you can boot with onboard graphics, do so. Disable all the drivers in "Hardware Drivers". Remove all the nvidia drivers you installed including from envy. Remove xorg.conf:
```
sudo mv /etc/X11/xorg.conf xorg.conf.old
```

Power down. Install video card and connect monitor to it. Boot into bios and disable onboard graphics. Reboot into grub. What happens?

---

### Post by siirial on 2010-03-15
It still goes black after grub loading. I can boot off of onboard graphics...

When it goes black, i get the cursor in the top left instead of the grub menu.

If you don't have any ideas off the top of your head, don't worry about it. I think i am going to send the card back to amazon and buy an atom 330 board and go with a new system. I'll just run this as a headless server or something. Just an old PC i had lying around and was wanting to get it to do something. Boxee looks to be too much for it.

---

