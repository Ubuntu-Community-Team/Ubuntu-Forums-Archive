---
title: "problem with proprietary nvidia driver"
date: 2011-08-15
forum: Hardware
---

### Post by pko76 on 2011-08-15
when i use proprietary nvidia driver in ubuntu 10.04 i have problem with the startup logo of ubuntu .it is distorted what i can do with that.

---

### Post by DanneStrat on 2011-08-15
> **pko76 said:**
> when i use proprietary nvidia driver in ubuntu 10.04 i have problem with the startup logo of ubuntu .it is distorted what i can do with that.

Hi.

I will help you fix it.

We will set a higher resolution and higher color depth for the framebuffer to fix the problem. 

Follow these steps:

Reboot the computer.

At the grub boot screen (where you select which linux kernel to boot) press "c". You will be greeted with a command prompt. In this prompt type:

```
vbeinfo
```and press enter.

Now you will see all the vbe video modes your graphics card supports.

Write down the highest resolution you can find (for example 1280x1024x32).

Then press "esc" button to exit.

Get back into ubuntu and open terminal.

Now type:

```
gksudo gedit /etc/default/grub
```Find this line:

#GRUB_GFXMODE=640x480

Remove the "#" from the line and put the resolution you got from "vbeinfo" after the equals sign.

When you're done it should look something like this:

GRUB_GFXMODE=1280x1024x32

but with your own resolution of course.

Now we're almost finished, but there's one more thing. If you have ever switched to console mode, you may have noticed that you have low resolution there also, so we will fix that one too.

Right below the line you just modified you make a new line like this:
[FONT=monospace]
[/FONT]GRUB_GFXPAYLOAD_LINUX=

and then put your resolution after the equals sign the same way you did previously.

Now save the file (file >save) and exit.

Bring up terminal and do:

```
sudo update-grub
```Done!

Close terminal and reboot.

Now your splash screen and console should look a lot better.

Good luck!

/Daniel

---

### Post by pko76 on 2011-08-17
> **DanneStrat said:**
> Hi.

I will help you fix it.

We will set a higher resolution and higher color depth for the framebuffer to fix the problem. 

Follow these steps:

Reboot the computer.

At the grub boot screen (where you select which linux kernel to boot) press "c". You will be greeted with a command prompt. In this prompt type:

```
vbeinfo
```and press enter.

Now you will see all the vbe video modes your graphics card supports.

Write down the highest resolution you can find (for example 1280x1024x32).

Then press "esc" button to exit.

Get back into ubuntu and open terminal.

Now type:

```
gksudo gedit /etc/default/grub
```Find this line:

#GRUB_GFXMODE=640x480

Remove the "#" from the line and put the resolution you got from "vbeinfo" after the equals sign.

When you're done it should look something like this:

GRUB_GFXMODE=1280x1024x32

but with your own resolution of course.

Now we're almost finished, but there's one more thing. If you have ever switched to console mode, you may have noticed that you have low resolution there also, so we will fix that one too.

Right below the line you just modified you make a new line like this:
[FONT=monospace]
[/FONT]GRUB_GFXPAYLOAD_LINUX=

and then put your resolution after the equals sign the same way you did previously.

Now save the file (file >save) and exit.

Bring up terminal and do:

```
sudo update-grub
```Done!

Close terminal and reboot.

Now your splash screen and console should look a lot better.

Good luck!

/Daniel

unfortunately this solution didn't work. i replace the splash screen with other and now the splash screen is ok.

---

