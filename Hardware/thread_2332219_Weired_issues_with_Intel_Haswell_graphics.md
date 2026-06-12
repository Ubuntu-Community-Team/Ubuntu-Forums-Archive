---
title: "Weired issues with Intel Haswell graphics"
date: 2016-07-29
forum: Hardware
---

### Post by Henne91 on 2016-07-29
Hey there,

I have been having some issues with my desktop computer running Ubuntu 14.04 for a while and I am not sure what is causing this issue.
My computer is connected to a FullHD Medion display via VGA.

Whenever I boot the computer for the first time the maximum possible screen resolution is 1366x768 or 1024x768 (not sure right now, but it is always the same), which makes everything very difficult to read. If I then shutdown the computer (not reboot), wait for a second and boot again, the correct resolution of 1920x1080 is possible. A regular reboot does not help. When the issue occurs there seems to be no difference in the hardware detected, however xrandr does also not allow a higher resolution. If trying to add a new modeline the screen simply goes black. The only difference I could determine so far is the display showing as "Unknown monitor" when the issue appears and as "Messelektronik Dresden GmbH 23"" when the issue does not appear.

The broken resolution also affects the BIOS boot logo.

I disabled SecureBoot in the BIOS since I read somewhere this was causing issues, but it did not help.

Is this some kind of hardware issue? If so, what component should I replace and why does it only occur on first boot? My mainboard does not have a DVI or HDMI connector so I cannot use a different cable type to connect the monitor. Or maybe something is setting the graphics adapter to a different mode causing the issue?

I am not sure if this might have something to do with it but when I shutdown the computer I turn off the power via a switch on the power strip afterwards.

Please help me!

Henne

---

### Post by sudodus on 2016-07-29
It could be a hardware issue as well as a software issue. Maybe you can check things out via some troubleshooting.

What happens if you do not turn off the power on the power strip, or if you turn on the power strip maybe one minute before you turn on the computer? That may give the monitor a chance to get into the 'full working mode'.

Maybe the graphics chip is getting tired and needs time to get into the 'full working mode'. Would it work to shutdown the computer (not reboot) without going through a full boot into low resolution? For example after staying in the grub menu for 5 or 10 seconds?

Maybe the power supply unit is getting tired (or overloaded by feeding too much hardware) so that the voltage is dropping below the specified level. That could show up as various problems.

Is it possible to introduce or add some kind of delay in the BIOS (slow boot, opposite of fast boot)? Maybe only a few seconds would be enough to the the failing hardware catch up?

-o-

You wrote that the broken resolution also affects the BIOS boot logo. That indicates that the problem starts early, so I don't think it can be fixed by the software, but I am not sure. You can also check for possible software causes:

The easiest method would be to try other versions (14.04.x LTS, 16.04.1 LTS), and flavours (Kubuntu, Lubuntu, Ubuntu MATE, ... Xubuntu) of Ubuntu as well as other linux distros. Try them live without installing.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

Maybe you can check if there is a newer version of the BIOS.

You can try with a proprietary driver if there is a suitable one for your graphics chip.

---

### Post by nakanut on 2016-07-29
If your BIOS is old you should disable the 'VGA palette snoop' option if you have one.

---

### Post by Henne91 on 2016-07-29
Thanks for the fast replies!

So I think it has nothing to do with the power strip, since I noticed the issue also occurs if I reboot my system after having it booted with the FullHD resolution before. So to summon it up: The only way I get FullHD resolution is, to boot the system one time, completely shutdown and start the system again.

The power supply should not cause the problem because it is barely two years old, high quality and it also should be strong enough since I do not even have a graphics card installed in the system or any external devices (except for a wifi stick). However, I cannot be sure about it working 100% correct of course.

I am already booting in slow boot mode. The BIOS is up-to-date (latest version for my ASRock H81 Pro BTC from April 14th) and there is no option called 'VGA palette snoop'.

There is no proprietary driver for Intel integrated graphics.

I just upgraded to Ubuntu 16.04 today and the problem still persists. I will try a different flavor soon, but I do not have a lot of hope that it will work.

Nevertheless, thanks so far! Any ideas on what to test are still welcome or if you have any hints on what debugging output I could look at that would be great also!

Henne

---

### Post by Henne91 on 2016-07-30
Hey again,

I replaced the power supply with a brand new one, the issue still exists.

I also noticed the mainboard does have a HDMI port and tried connecting my monitor via HDMI. It works until the purple GRUB screen is shown, afterwards the screen is simply black. I also tried a different monitor, it is showing the same symptoms via HDMI.

Does this mean the IGPU within the CPU is defect? How could I confirm this?

Henne

---

### Post by sudodus on 2016-07-30
I would also suspect the GPU.

Have you tried another linux distro (not based on Ubuntu and debian), for example openSUSE, mageia or fedora? You can try them live without installing, if you get the correct installation iso files.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to suggest what to do. For example

- is it an option to try separate graphics card?

- are there known issues with your graphics chip?

---

### Post by Henne91 on 2016-07-30
I will try a different distro tonight.

My PC specs:
- Intel i3-4130 3.40 GHz
- RAM 4 GB
- Intel® HD graphics 4400
- Mainboard: ASRock H81 Pro BTC
- Wifi: It is a pretty old chip, it is recognized as ZyXEL Communications Corp. ZyAIR G-202 but I am pretty sure that this is wrong. It is working however.

I tried an old graphics card floating around via DVI. It seems to work fine, but I would have to clean it because I got it from a person who was smoking a lot so it is very dusty.

I found some people having issues with the Intel HD 4400 graphics, recommending to use "nomodeset". I tried that but it actually made the resolution even lower than before.

I just checked and I do have 1 year of limited warranty for the CPU left, so I might just try and send it back and see if that helps.

---

### Post by sudodus on 2016-07-30
That computer *should* have no problems to run Ubuntu.

I wish you good luck trying to replace the CPU with its graphics chip within the warranty :-)

---

### Post by sudodus on 2016-07-30
I have own experience of Intel® HD Graphics 4000 (in a Toshiba laptop) and Intel® HD Graphics 520 (in an Intel NUC), but nothing in between. I read on the internet, that some people have problems with linux and the Intel® HD Graphics 4400.

If ***[COLOR="#0000CD"]you[/COLOR]***, who read this now, have ***own experience of that Intel® HD Graphics 4400 chip***, please share it :-P

---

### Post by him610 on 2016-07-30
FWIW, one of my computers, a System76 Pangolin Performance 9, has an Intel Core i5-3210M Processor with integrated HD 4400 graphics. I have owned this computer for over 2-1/2 years. Never experienced any kind of graphics problem with it using either LTS 12.04 or 14.04. It has been the most stable laptop I have ever owned.

---

