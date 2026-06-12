---
title: "Combat Arms Installs"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by MasterPoulos89 on 2008-12-10
I have been trying to install Combat Arms for a while now and realized it was not ganna happen. Then i noticed that the wine page for Combat Arms showed some successes. It seems installing Internet Explorer(IEs4Linux) makes the Combat Arms installer display properly. And it does. I installed Combat Arms with no problem after installing IEs4Linux. When i run it, it gets the patch. Then when i run it again it displays the start up screen. When i press game start it continues to load the game. After it loads nothing happens. it just disappears. Has anyone else installed and ran this game properly. If so, Please help me out.

---

### Post by MasterPoulos89 on 2008-12-21
Can Anyone Help Please.......im so close.......just need some assistence.

---

### Post by Darkblood on 2008-12-22
What version of wine are you using? I'm using 1.0.1 and i can play.

I've installed playonlinux and from there i installed ie6. You could try the same thing, maybe it will work.

If you don't mind i'll use your thread to post a problem related with this game.
I can play, but i'm having some trouble, it's mostly with my mouse, and it isn't a hardware problem, i've tested with other mouse and the same thing happened.
It's hard to explain, it just feels like the mouse lost its accuracy. I don't know if this is a common problem or a specific problem of this game.
If someone could help, i would appreciate it.

---

### Post by MasterPoulos89 on 2008-12-29
I tried with 1.0.1, 1.1.8, and the latest 1.1.11, same results......I'll try to install ie6 with play on linux as u said instead of winetricks.

---

### Post by MasterPoulos89 on 2008-12-29
No luck......is anyone else having this problem and does anyone know why?

---

### Post by MasterPoulos89 on 2008-12-31
when i run it in terminal i get this error..........

Unhandled exception: page fault on read access to 0x01351000, invalid program stack in 32-bit code (0x1000bfc4).

what does that mean......does it have anything to do with 32-bit......im using 64-bit Ubuntu.......or does that not matter..........

Im also using an nvidia graphics card......if it helps.


Any more info needed from me that would help figure this out please ask.

---

### Post by MasterPoulos89 on 2009-01-02
Can anyone help me......why others can play but i get an error from terminal. This is Bull Sh it. I wanna play combat arms. Please someone help.

---

### Post by MasterPoulos89 on 2009-01-21
OK......i found out i have to run it with wine emulating windows ME or 95........it runs now but it freezes before i can start a game then i have to force quit......I guess combat arms isn't ready for wine.

---

### Post by Pelonchas on 2009-05-05
I was able to install CombatArms, instaling ie4linux (CA needs Gecko engine), and then Install CA.

The game run once only, ive tried the same configuration in wine but no luck. I've tried w98 to vista. w98 seems to work better but its the same problem. The game crash in the loading Nexon Screen, just before the login window.
If a run the game from terminal it does do nothing after the first window.
I need to run from the launcher on desktop created by the install process.

And also the games changes my screen res, to 1024x768 everytime and its quite frustating, i have a widescreen.

Wine Version: 1.1.20
Linux distro: Ubuntu 9.04 JJ

Whats the general configuration you have to made it run?

---

### Post by MasterPoulos89 on 2009-05-11
I have properly installed and played Combat arms by installing winetricks then the following in terminal:

[code]
winetricks ie6 comctl32 comctl32.ocx corefonts flash fontfix gdiplus gecko liberation mfc40 mfc42 msls31 pdh riched20 riched30 tahoma urlmon wininet native_mdac

Then just install and emulate engine.exe to run in ME or 98.

This method stoped working for me for some reason. Let me know if this method works for anyone else.

---

### Post by vonbrune on 2009-08-17
> **MasterPoulos89 said:**
> I have properly installed and played Combat arms by installing winetricks then the following in terminal:

[code]
winetricks ie6 comctl32 comctl32.ocx corefonts flash fontfix gdiplus gecko liberation mfc40 mfc42 msls31 pdh riched20 riched30 tahoma urlmon wininet native_mdac

Then just install and emulate engine.exe to run in ME or 98.

This method stoped working for me for some reason. Let me know if this method works for anyone else.

Wonderful! :D But as it turns out, the game crashes when running that anti-hack protection which doesn't even work. 
fixme:winmm:MMDRV_Exit Closing while ll-driver open
is the error :confused:

---

### Post by vonbrune on 2009-08-17
Ok got it to start by changing wine to run 98. Crashes at loading screen though:
err:seh:setup_exception_record stack overflow 944 bytes in thread 0026 eip 7bc3b334 esp 00240f80 stack 0x240000-0x241000-0x340000

---

### Post by vonbrune on 2009-08-17
Sorry to make 3 replies in 3min but I have a giant headache :S Anyway, by setting wine to ME it runs and you can see a zombie-dude moonwalking for 20 seconds and then he outsmarts the animation and moves out the screen just to see a wonderful black screen. >_>:lolflag:

---

### Post by safet14 on 2010-11-27
> **MasterPoulos89 said:**
> I have properly installed and played Combat arms by installing winetricks then the following in terminal:

[code]
winetricks ie6 comctl32 comctl32.ocx corefonts flash fontfix gdiplus gecko liberation mfc40 mfc42 msls31 pdh riched20 riched30 tahoma urlmon wininet native_mdac

Then just install and emulate engine.exe to run in ME or 98.

This method stoped working for me for some reason. Let me know if this method works for anyone else.
hey this thing aint work i try to get to installer i got 1.0.1 version of wine and it worked i get the installer of combat arms to work i press agree it fails then i install playonlinux and it installs 1.0.2 version of wine and uninstalls 1.0.1 plzzzz help me man cmon im counting on u plzzzzz help meee

---

### Post by safet14 on 2010-11-27
> **Darkblood said:**
> What version of wine are you using? I'm using 1.0.1 and i can play.

I've installed playonlinux and from there i installed ie6. You could try the same thing, maybe it will work.

If you don't mind i'll use your thread to post a problem related with this game.
I can play, but i'm having some trouble, it's mostly with my mouse, and it isn't a hardware problem, i've tested with other mouse and the same thing happened.
It's hard to explain, it just feels like the mouse lost its accuracy. I don't know if this is a common problem or a specific problem of this game.
If someone could help, i would appreciate it.
hey this thing aint work i try to get to installer i got 1.0.1 version  of wine and it worked i get the installer of combat arms to work i press  agree it fails then i install playonlinux and it installs 1.0.2 version  of wine and uninstalls 1.0.1 plzzzz help me man cmon im counting on u  plzzzzz help meee

---

