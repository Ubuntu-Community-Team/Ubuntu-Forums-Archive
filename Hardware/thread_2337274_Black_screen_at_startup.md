---
title: "Black screen at startup"
date: 2016-09-16
forum: Hardware
---

### Post by tonymp on 2016-09-16
First off, here's my computer's processor and video: AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G × 4 ; Gallium 0.4 on AMD CARRIZO (DRM 3.1.0, LLVM 3.8.0)

The computer model is an HP Pavilion 15

The Ubuntu version is 16.04 LTS

The problem: the computer starts up just fine but the screen is black; even though the screen is black I can hear the drum sound prompting me to log in. To recover from this issue I just press F10 then cursor down twice, press return, and then cursor once to the left, then hit enter to restart. Obviously this means that I have figured out that although the screen is black the operating system is successfully running the window and desktop environment! Anyway, when the computer restarts all is well with the screen and I have a fully functional system. Sometimes, though, I have to restart again because the screen starts to flicker. After a second restart, though, this problem goes away. All in all, I'm very happy with my OS and computer but I'd like to eliminate this problem. 

What I've tried: After looking things up in the forums I've tried: 1) using xdiagnose (this was when I didn't realize that actually xwindows was working properly it's just that the video wasn't working) 2) reading the boot log (in which no error messages appear) 3) reading various other logs where the OS records error messages but they are empty 4) upgrading the kernel (some forum posts in the past have suggested various kernel versions for this particular grpahics and CPU so I tried them all!) 5) reinstalling the OS.

What I suspect: It could be a video driver problem or a problem with the display. I'm leaning more in the direction of the video driver because although the screen is black it is a "lit up" black, in other words, the display is active. Also, when I power the computer on the screen is purple before it goes black. Without anything recorded in any logs I have no way of knowing for sure which one is the problem because I'm not an expert at these things. I mean, the most common problem I've read about is a failure to load the graphics driver correctly at start up, but in the forum posts I've read this causes the computer to freeze up or crash. In my case, I have no freezing or crashing and with the keyboard I can blindly navigate to safely restart the computer.

I think I've pretty much exhausted all the options and the limits of reading this forum. If no one can suggest a solution to this problem at the very least I'd love to hear how I can reproduce the problem so it is capable of being recorded to a log file so that in turn I can report this correctly as a bug and/or provide better details about the issue so someone can read it and say "this is your problem and this is how you fix it."

If you've got this far down into my post, thank you so much for reading the whole thing. It's a bit lengthy! 

Any suggestions are welcome and thank you in advance!

---

### Post by pacblo64 on 2016-09-20
Hello; this is my first post in this site; please, excuse my poor english, I write from Spain.
Friend **tonymp**,   I write this post replying you because recently I have had the same  problem you describe; my PC has the same SO and video card than yours  (Ubuntu 16.04 and Gallium 0.4 on AMD CARRIZO (DRM 3.1.0, LLVM 3.8.0). 
I  tried many ways reading in internet to get a solution but no one has  given me result. At the end, I have re-installed twice the SO, and then  in terminal I made a "apt-get update" and a "apt-get upgrade", and at  moment it seems that it has been solved, but I don't now for how long.

Saludos desde España.

---

### Post by tonymp on 2016-09-20
Hi! I also live in Spain. I've considered reinstalling the OS again but thought perhaps once was enough to see if that would solve the problem. I didn't think running the apt-get commands solved your problem and that it was probably reinstalling the OS that helped you. BUT I'm now running the apt-get upgrade command and a lot of things related to my processor, PAM, and other video-related software is being upgraded, so maybe that's the way to fix the issue! I never thought of doing that because I thought the automatic software updates would do that on its own. Apparently, it does not! We shall see if this has solved the problem on my end. I hope it solved yours! Thanks for the advice! Let's see what happens tomorrow when I switch the computer on for the first time. Y no te preocupes por tu intento a escribir en inglés. Si lo entiendo no hay fallos porque entenderse el uno al otro es lo que más importa en este contexto. (Soy nativo de inglés y hablo español como segundo idioma.)

---

### Post by tonymp on 2016-09-21
OK, it's the next morning. So, good morning! Running the apt-get-upgrade did not solve the problem. At this point I'm toying with the idea of reinstalling the OS to see if the second time is a charm. Thanks, though, Pablo, for your suggestion.

---

### Post by pacblo64 on 2016-09-21
Hi; unfortunetaly, second time I started my PC, troubles came back. So, its time to continuing looking for a solution. Maybe upgrading the kernel? I don't now.

---

### Post by tonymp on 2016-09-21
I upgraded to recommended kernels and the problem wasn't solved that way. Also, I updated to the most recent kernel and that didn't help either plus it isn't compatible with the Realtek wi-fi driver improvement. I think we might have to wait for a fix to happen in an update or maybe someone will see this thread and know what else we can try. At least we've got two heads thinking about this! Much better than one!

---

### Post by pacblo64 on 2016-09-25
Hi, friend! I'm yet here. What new kernel have you installed?

---

### Post by pacblo64 on 2016-09-25
It seems that the last stable version is 4.7 Isn't it? ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/))

---

### Post by tonymp on 2016-09-25
The latest is 4.8-rc6, I believe. [http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/native/v4.8-rc6/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/native/v4.8-rc6/) That's the one that I said isn't compatible with the wifi driver fix.

---

### Post by pacblo64 on 2016-09-25
Yes, but I've read in somewhere in the forums that "rc" versions of kernel are not stable at all.

Today I experienced the following: as others days, I booted my laptop and our known troubles came back; then (after working some minutes), I turned off the computer, and immediatelly I booted it again, and at that second boot, no troubles. Twice more (turn off and boot; turn off and boot), and NO TROUBLES APPEAR.

This has led me to ask: why first time problems appear and why then not appear?. Which differences exist between first boot and following boots? My answer: the temperature of processor and the temperature of video chipset. What do you think about this? Is it possible that cold temperature cause that problem?

---

### Post by tonymp on 2016-09-26
The same exact thing happens to me and I've thought about that, but if that's the case I think it's still a driver issue. I've been checking the AMD drivers and support page to see if they come up with a new driver for our processor (the graphics is integrated) and the latest version of Ubuntu. My best guess is that our driver is designed to work with an older version of Ubuntu and when 16.04 came out the developers didn't do much to change the native driver. If you haven't already done so, I suggest you use the proprietary driver for this processor instead of the one developed by Ubuntu. Both driver versions present the same problem we have in my experience, but the proprietary driver is better for power management (when you're running the laptop on battery power especially).

My understanding of the kernel versions is that mainline kernels are better than the ones listed as "stable" because they are patched frequently. Anyway, go right ahead and try different kernel versions you might get different results than me, who knows? I tried several different ones based on what other people have said in the forums here and on askubuntu and I was disappointed so I decided to stick with the one that comes with installation and upgrades from the usual Ubuntu package repository.

---

### Post by tonymp on 2016-09-26
Also, instead of turning the computer off, you can safely restart the computer (at least, I can) by following this keyboard sequence: fn-F10, down arrow twice, enter, left arrow once, enter If you keep switching the computer off you could corrupt the data on the HDD. The keyboard sequence are keyboard shortcuts. If your problem is the same as mine, the desktop is actually working, you just can't see it on the screen.

---

### Post by pacblo64 on 2016-09-29
> **tonymp said:**
> Also, instead of turning the computer off, you can safely restart the computer (at least, I can) by following this keyboard sequence: fn-F10, down arrow twice, enter, left arrow once, enter If you keep switching the computer off you could corrupt the data on the HDD. The keyboard sequence are keyboard shortcuts. If your problem is the same as mine, the desktop is actually working, you just can't see it on the screen.

In my laptop sequence: "fn-F10, down arrow twice, enter, left arrow once, enter" don't work, neither sequence "ctrl+alt+supr". I don't now why.

---

### Post by pacblo64 on 2016-09-29
By the way, today I've not had troubles in the start!
And you?

---

### Post by pacblo64 on 2016-10-02
Troubles come back; I'm thinking about the possibility of installing Ubuntu MATE (16.04 LTS) in order to try if troubles continue or disappear. What do you think about it?

---

### Post by tonymp on 2016-10-04
I think the only difference between Ubuntu and Ubuntu MATE is the desktop. In other words, the visual characteristics of the window system. Ubuntu uses Unity as the desktop style and Ubuntu MATE uses the MATE desktop style. Other than its appearance, I think everything else (drivers, etc.) are the same. If I'm wrong, someone can correct me (and please do!).

---

### Post by tonymp on 2016-10-04
Hi again, Pablo! Guess what? While using the proprietary driver today my computer stopped responding to restarting the safe way with fn-F10 and blindly cursoring to restart the computer. I've switched back to the driver distributed by canonical and now, although I get a black screen at startup, at least I can safely reboot again. Battery power isn't managed as well and I get more black screens at startup, but the "blind" method of navigating through the unseen GUI to reboot works again. So, I take back my recommendation about the proprietary driver. Don't bother with it. Eventually the keyboard shortcuts stop working with the black screen.

---

### Post by tonymp on 2016-10-12
I got the flickering screen problem to stop by installing the OIBAF graphics drivers. Unfortunately, I still get a black screen on startup every day but not as persistent as before (it had got to the point where I had to reboot five or six times, now maybe once or twice).

Here's how to install the alternative graphics drivers:

```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by tonymp on 2016-10-24
For anyone that is interested, I have finally, after a lot of searching, found a bug report on this issue. Here it is: 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amdgpu/+bug/1577074](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amdgpu/+bug/1577074)

Anyone with the same issue with the same computer should add themselves to affected people. Right now it is rated as "low priority" but the more people affected who say they are, the higher the priority rating! 

At this point, I would suggest rebooting the computer using ssh if the screen goes black. It's much easier than using keyboard shortcuts (it started getting hit or miss for me, ssh always works!). There is an app for the iPad called iTerminal that I've been using. There are plenty of apps for phones and tablets that will help you do the same thing. 

Upgrading to 16.10 does not help solve the problem, either. I bought the t-shirt on that one! We just have to wait for the bug to be fixed. The more people affected, the faster the fix will come!

---

### Post by pacblo64 on 2016-10-25
Saludos, **tonymp**.

Sigo con nuestro problema habitual. Gracias por los últimos comentarios que has hecho. Desafortunadamente no me han dado resultado; siguiendo tus instrucciones, instalé el paquete de "oibaf/graphics-drivers", pero no me ha funcionado.

I tried to solving the problem by installing ubuntu 16.10, but the problem keeps alive.

Puesto que tenía la necesidad de trabajar con mi laptop, he optado por introducir la opción "nomodeset" en el grub. So I introduced "nomodeset" after "quiet splash", and that way, at least, I can work, although the screen resolution is not good, only 800x800.

Saludos.

---

### Post by tonymp on 2016-10-28
Pero no he dicho que eso resuelve el problema. Lo que sí hace es ayudarme a tener pantalla normal sin irregularidades. He marcado esto como resuelto porque alguien sí ha podido generar un log que demuestra que esto es un bug. Por favor, si no lo has hecho todavía, que sigas el enlace en mi anterior post y marcar que eres un afectado por este problema. No va a haber solución hasta que se emita un controlador gráfico mejorado. Cuánta más gente afectada por el fallo en el controlador haya, cuánto más rápido lo solucionan.

---

### Post by pacblo64 on 2016-10-29
Certainly, I have also reported the problem to be in my laptop. 
([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amdgpu/+bug/1577074/comments/28](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-amdgpu/+bug/1577074/comments/28))

Have a good day, **tony**.

Saludos.

---

