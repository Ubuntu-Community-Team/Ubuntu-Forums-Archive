---
title: "external monitor help"
date: 2008-12-18
forum: Hardware
---

### Post by Spitz13 on 2008-12-18
i have an hp pavilion dv9008nr, 
Processor:1.6 GHz AMD Turion™ 64 X2 Dual-Core
Ram: 1gb DDR2
Video: NVIDIA GeForce Go 6150 (UMA)

the thing is, the screen is broken, and has a very scattered image that is almost impossible to make out, so i have it plugged into an external monitor. when i run the live version of ubuntu 8.10, and i press cntrl+alt+f7, i get the ubuntu desktop on my laptob screen (i can hardly make it out, but it looks like the ubuntu desktop) and on my external monitor i get a bunch of weird bright colors, i tried pressing fn+f4 but it only switches from my external monitor being on and it then being of, it never sends the desktop to the external monitor, and i cannot function with the external monitor being on the laptob's screen as it is REALLY messed up, how would i go about sending the desktop to the external monitor? 

thanks

---

### Post by Spitz13 on 2008-12-18
bump
i really want my ubuntu to work :( :( :(

---

### Post by overdrank on 2008-12-18
> **Spitz13 said:**
> bump
i really want my ubuntu to work :( :( :(

Hi and please do not bump your thread so quickly.
I have never tried what you are attempting but I will try and assist you. I understand you are trying to use the live cd?
The external monitor shows nothing during the boot or anything?

---

### Post by Spitz13 on 2008-12-18
> **overdrank said:**
> Hi and please do not bump your thread so quickly.
I have never tried what you are attempting but I will try and assist you. I understand you are trying to use the live cd?
The external monitor shows nothing during the boot or anything?

sorry about the bump, the external monitor works throughout the boot(show's the manufacturers logo, the ubuntu loading screen, ect. and it shows command lines (sorry i'm a noob) when i press cntrl+altf1,f2,f3,f4,f5,f6, but when in f7 i get the flashing colors, but on the laptob's screen is ubuntu's desktop..

---

### Post by overdrank on 2008-12-18
> **Spitz13 said:**
> sorry about the bump, the external monitor works throughout the boot(show's the manufacturers logo, the ubuntu loading screen, ect. and it shows command lines (sorry i'm a noob) when i press cntrl+altf1,f2,f3,f4,f5,f6, but when in f7 i get the flashing colors, but on the laptob's screen is ubuntu's desktop..

Ok ctrl, alt, F1 thru F6 will bring you to the virtual terminal and combo with F7 brings you back to the desktop. You may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option, hopefully this will correct the graphics issue. Then you should be given the option to boot normally.
I do not know for sure if the nv driver will use the external monitor.

---

### Post by Spitz13 on 2008-12-18
> **overdrank said:**
> Ok ctrl, alt, F1 thru F6 will bring you to the virtual terminal and combo with F7 brings you back to the desktop. You may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option, hopefully this will correct the graphics issue. Then you should be given the option to boot normally.
I do not know for sure if the nv driver will use the external monitor.

I booted into recovery mode, but how do i use the xfix option? is it a command?

---

### Post by overdrank on 2008-12-18
> **Spitz13 said:**
> I booted into recovery mode, but how do i use the xfix option? is it a command?

When you boot into recovery mode you should be given four options, boot normally is the first and xfix in the last.

---

### Post by Spitz13 on 2008-12-19
> **overdrank said:**
> When you boot into recovery mode you should be given four options, boot normally is the first and xfix in the last.

when i run recovery mode i get a bunch of lines loading, saying that things are loading and such (i can't remember exactly) and then i just get the ubuntu@ubuntu $: to imput commands..

:confused::confused:

---

### Post by overdrank on 2008-12-19
> **Spitz13 said:**
> when i run recovery mode i get a bunch of lines loading, saying that things are loading and such (i can't remember exactly) and then i just get the ubuntu@ubuntu $: to imput commands..

:confused::confused:

Ok what version of ubuntu are you using?
I thought 
> when i run the live version of ubuntu 8.10

---

### Post by Spitz13 on 2008-12-19
> **overdrank said:**
> Ok what version of ubuntu are you using?
I thought

i have 5.10 installed, i can't run recovery mode on the live version of ubuntu, i think..and when i try to install 8.10 i get weird colors before it even installs..

---

### Post by overdrank on 2008-12-19
> **Spitz13 said:**
> i have 5.10 installed, i can't run recovery mode on the live version of ubuntu, i think..and when i try to install 8.10 i get weird colors before it even installs..

Ok 5.10 I have no experience with as it is older than I started with 6.06.
You may try the command ```
sudo dpkg-reconfigure xserver-xorg
``` to configure you graphics on 5.10.
You may choose to try Hardy 8.04 live cd or the alternate with the text install.

---

### Post by Spitz13 on 2008-12-19
> **overdrank said:**
> Ok 5.10 I have no experience with as it is older than I started with 6.06.
You may try the command ```
sudo dpkg-reconfigure xserver-xorg
``` to configure you graphics on 5.10.
You may choose to try Hardy 8.04 live cd or the alternate with the text install.

yeah, i've tried reconfiguring the x server a couple of times, but in the end it always says its malconfigured and disables itself.. i think the solution to the problem would be a way to get ubuntu to totally ignore my laptob screen and have my external monitor as its only display, but i have no idea how i would do that..

---

### Post by terribletrouble on 2008-12-19
A little of my experience:

- Difference between live cd and install.
- Issues with resolution while starting an install, or running....

I could not get ubuntu to install on my system, the screen never showed any data at all. so here is what I did:

1. While grub is loading, hit esc.
2. Highlight the first entry, hit e for edit.
3. Move to the end of the line, remove everything (backspace) until you get to the ro.
4. Then get out of that, and boot.
(you may need to mess with vga=xxx settings in grub...)

Then when I booted, all was textual, but when the GUI finally came up, it was perfect on 2 monitors.

Maybe worth a try.

---

### Post by Spitz13 on 2008-12-19
> **terribletrouble said:**
> A little of my experience:

- Difference between live cd and install.
- Issues with resolution while starting an install, or running....

I could not get ubuntu to install on my system, the screen never showed any data at all. so here is what I did:

1. While grub is loading, hit esc.
2. Highlight the first entry, hit e for edit.
3. Move to the end of the line, remove everything (backspace) until you get to the ro.
4. Then get out of that, and boot.
(you may need to mess with vga=xxx settings in grub...)

Then when I booted, all was textual, but when the GUI finally came up, it was perfect on 2 monitors.

Maybe worth a try.

this sounds like its what i need, but i have a couple of questions before i try this, what line do i remove everything from? i think there's four lines.. and i didn't understand the vga=xxx part.. but this sounds like its what i need, thanks in advance

---

### Post by terribletrouble on 2008-12-19
Once you have started the edit process within grub, you can hot F1 for help I think, and that is where I found it.

I think a good setting is vga=771

Here is a link that references it better, even though it is for gutsy.

[http://ubuntuforums.org/showthread.php?t=454392]("http://ubuntuforums.org/showthread.php?t=454392")

---

### Post by Spitz13 on 2008-12-19
> **terribletrouble said:**
> Once you have started the edit process within grub, you can hot F1 for help I think, and that is where I found it.

I think a good setting is vga=771

Here is a link that references it better, even though it is for gutsy.

[http://ubuntuforums.org/showthread.php?t=454392]("http://ubuntuforums.org/showthread.php?t=454392")

OH MY GOD THANK YOU!
this did it, thank you, soo much. now i'm going to get rid of 5.10 and bring in 8.10, but one question, how would i fix this on an install? because i get the same problem while trying to install ubuntu 8.10, if not i could try this on mandriva 09 to see if it fixes the issue, once again, thank you soo much

---

### Post by terribletrouble on 2008-12-19
That is exactly where I had my troubles...

I was installing Mythbuntu in my lounge to a 4-" lcd, that defaults to 1920x1080. No way Ubuntu would work with this.

On the install process, I hit esc, changed the option to remove splash, quiet and added the vga= setting. I then completed the install.

On first boot, I made the same changes as above.

Once running, go into /boot/grub, and edit menu.list. Find the section, and make the changes, then run sudo update-grub. When you reboot, all will be taken care of.

---

