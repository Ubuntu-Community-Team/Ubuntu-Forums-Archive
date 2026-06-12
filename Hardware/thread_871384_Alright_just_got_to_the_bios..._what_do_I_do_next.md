---
title: "Alright just got to the bios... what do I do next?"
date: 2008-07-26
forum: Hardware
---

### Post by PsychedelicWonders on 2008-07-26
Is there anything special I have to change?

What exactly do I have to do next before I can try to install Ubuntu or windows?

---

### Post by PsychedelicWonders on 2008-07-26
i want my 1st boot device to be the cd-rom correct?

2nd boot device is HDD

and 3rd is now registered as floppy drive... but I have none... should I disable the 3rd boot device?

---

### Post by overdrank on 2008-07-26
> **PsychedelicWonders said:**
> i want my 1st boot device to be the cd-rom correct?

2nd boot device is HDD

and 3rd is now registered as floppy drive... but I have none... should I disable the 3rd boot device?

Yes set the cd as first boot device and the the hard drive. Install windows first then Ubuntu.

---

### Post by PsychedelicWonders on 2008-07-26
Is that the only thing I hav to change in bios?

What should I do next, put my windows cd in the drive and reboot?

Now I am going to be using a dell copy of windows xp that i have... will i know right away if it doesnt accept it... and if it doesnt... do I just take that cd out and put the Ubuntu in to install?

---

### Post by overdrank on 2008-07-26
> **PsychedelicWonders said:**
> Is that the only thing I hav to change in bios?

What should I do next, put my windows cd in the drive and reboot?

Now I am going to be using a dell copy of windows xp that i have... will i know right away if it doesnt accept it... and if it doesnt... do I just take that cd out and put the Ubuntu in to install?

Hi and if this is not a dell system the cd will not work. Then yes you can install Ubuntu.

---

### Post by PsychedelicWonders on 2008-07-26
alright I just ripped the Ubuntu... that windows cd wouldnt let me... so I will add on windows later when the budget allows.

For now... whats next though?

I want to play games ASAP... so I need wine correct?

What version and where is the place to obtain wine?

What other intial programs do I need added?

The only thing I'm worried about right now is surfing the net and playing games.

Should I start installing all of the software cds I have that came with my hardware?

mobo stuff, video card stuff, audio card stuff, wireless mouse & keyboard cd etc?

---

### Post by cariboo on 2008-07-26
You don't need any of your driver disks, as most of the drivers are buitlin to the kernel. The only time you might need a windows driver is if you have a wireless card, otherwise you are ok. To install wine go to Applications-->Add/Remove...  in the Show dropdown make sure **all available applications** is selected, then in search type: wine and hit enter mark wine to be installed and click apply. For game compatibility check here:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Jim

---

### Post by PsychedelicWonders on 2008-07-27
what is the "kernal"?

ok its telling me that Im not connected to the internet to get the most updated versions...

now when I tried to install my cable modem software... it gave me some kind of error mentioning I dont have any type of program to execute .exe's basically.

so what is need to be installed so that I can install the rest of my "windows" software like the cable modem software and my microsoft wireless keyboard and mouse combo software?

When I do the wine search I come up with the following...

Wine Windows Emulator
Winefish LaTeX Editor
Virus Scanner

What are these other 2?

Do I want to install them also, or just wine?

---

### Post by PsychedelicWonders on 2008-07-27
bump.. id like to make some headway on this tonight...

---

### Post by kspncr on 2008-07-27
> **PsychedelicWonders said:**
> what is the "kernal"?

ok its telling me that Im not connected to the internet to get the most updated versions...

now when I tried to install my cable modem software... it gave me some kind of error mentioning I dont have any type of program to ex
so what is need to be installed so that I can install the rest of my "windows" software like the cable modem software and my microsoft wireless keyboard and mouse combo software?

When I do the wine search I come up with the following...

Wine Windows Emulator
Winefish LaTeX Editor
Virus Scanner

What are these other 2?

Do I want to install them also, or just wine?

Just Wine is what you'll need (for games, no?) (btw does it really say Wine Windows *emulator*? I was under the impression that *w*ine *i*s *n*ot an *e*mulator)

You shouldn't need to install anything for your keyboard, mouse, or modem.

---

### Post by PsychedelicWonders on 2008-07-27
I have that computer turned off, but if thats what I typed earlier, then its true.

So just do wine windows emulator for now?

What do the other 2 programs do?

Since I have 7.04 I am going to have to download the newst ubuntu and the newest wine though wont i?

I am going to be using a microsoft wireless key board and mouse... so I have to install some software.

So basically any "normal" windows program that I would want to open or use, I have to do so through wine as a bridge if you will?

---

### Post by hugmenot on 2008-07-27
> **PsychedelicWonders said:**
> I have that computer turned off, but if thats what I typed earlier, then its true.

So just do wine windows emulator for now?

What do the other 2 programs do?

Since I have 7.04 I am going to have to download the newst ubuntu and the newest wine though wont i?

I am going to be using a microsoft wireless key board and mouse... so I have to install some software.

So basically any "normal" windows program that I would want to open or use, I have to do so through wine as a bridge if you will?

Hey, you should not need to install your Windows driver discs on Linux at all. Your keyboard and mouse will probably not work that way. What happens if you just plug them in and start Ubuntu?
You also almost certainly cannot use your modem with the Windows driver either. There should be special Linux drivers, chances are that they are already integrated in Ubuntu and you need to connect the modem with the right network configuration tool.
Wine is mostly used to get desktop applications to run on Linux; not drivers.

---

### Post by PsychedelicWonders on 2008-07-27
How do I figure out what the right network configuration tools are so I can get on the internet?

Where do I find if I have the linux drivers for my cabel modem?

I havent tried plugging the wireless stuff into that computer... I will try taht now.

So I should install the version of wine that 7.04 came with and then just download the update when I get the internet working on here?

---

### Post by PsychedelicWonders on 2008-07-27
alright I just tried the wireless keyboard and mouse on the Ubuntu machine and it works... but the software that comes with the kit allows you to assign hot keys on the keyboard and mouse... so I'm going to need this software on here to tweak it the way I want.

So I should still install the software right?

Also I tried to install wine and it told me that since I wasnt connected to the internet that it wont let me... so we gotta get this internet problem fixed first.

---

### Post by WRDN on 2008-07-27
> **PsychedelicWonders said:**
> alright I just tried the wireless keyboard and mouse on the Ubuntu machine and it works... but the software that comes with the kit allows you to assign hot keys on the keyboard and mouse... so I'm going to need this software on here to tweak it the way I want.

So I should still install the software right?

Also I tried to install wine and it told me that since I wasnt connected to the internet that it wont let me... so we gotta get this internet problem fixed first.

Click System > Administration > Network Tools.
Please confirm whether or not the modem appears in the "Network Device" combo box.

---

### Post by issih on 2008-07-27
You need to stop thinking like an xp user. The software supplied with your keyboard and mouse is of NO USE to you under ubuntu, forget about it, stop thinking about it, you will never need to install it in ubuntu, if you did I'd be quite surprised if it did anything at all.

If you are lucky, your hotkeys will already be supported, and you just need to set them up, go into System->Preferences->Keyboard shortcuts and try assigning those keys to an action. If that doesn't work there are various ways to try and get them supported, but the windows software is not going to help.

Concentrate on getting online, as once that is done, installing wine and anything else is going to be a billion times simpler (just use add/remove programs, in ubuntu the add actually means you can just click on a program in a list and it is installed)

Wine is getting better every day, but be aware it won't necessarily work with every windows program you throw at it, a lot of stuff works, and a lot of stuff doesn't, just a warning.

Concentrate on your cable modem, tell us what model it is, what type of connection it uses, all that kind of stuff.

Hope that helps

---

### Post by PsychedelicWonders on 2008-07-27
hey thanks, I just ended up needing to reboot the modem.  Been online all day downloading updates.

I appreciate the help and the call out on thinking like an xp user... sorry... its been 15 years of my life... shes all i know.

---

### Post by hugmenot on 2008-07-28
Your time must run slower than mine. Wasn&#8217;t XP released only seven years ago?

---

### Post by issih on 2008-07-28
Heh no need to apologise, nearly everyone does it at first :)

You just have to get used to it

---

### Post by hugmenot on 2008-07-28
> **issih said:**
> You just have to get used to it

Ya, and isn&#8217;t it cool that your stuff works without zipping through your stack of driver discs? Just plug and play?

---

### Post by PsychedelicWonders on 2008-07-28
> **hugmenot said:**
> Your time must run slower than mine. Wasn’t XP released only seven years ago?


of course it was... but do you know that windows has been around long before xp?

hugmenot - yeah its totally cool and still weird to understand. ha

---

