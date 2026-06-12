---
title: "System hangs on restore after sleeping"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by arnstein on 2006-07-12
Hi,

I have an HP-Compaq nx6110 laptop. I usually never halt my system, instead put it on sleep mode, and restore it when required. I have a few problems with this:

1. Very often, on restore either the system gets locked a second time (that is, a few seconds after unlocking), or the 'Quit' dialog is displayed, sometimes both.

2. Sometimes, I get the message, System was not able to suspend properly (on restore), when it appeared to have suspended alright. Is this an issue? And will it be damaging to my system?

3. Sometimes, the sytem doesn't restore at all. It merely crashes, the screen doesn't switch on. The power light lights up, and so does the indicator for wireless. I'm unable to switch off the wireless, go back to suspend, or halt my system (i.e. by playing with the keyboard altho my screen is off). Eventually I force power-off my system by pressing the Power button... This is a major problem for me as I have lost data because of it.

Btw, in case it maybe useful, I use Intel 2200bg wireless card, which is usually always on. (I read somewhere that this doesn't support suspending or something). My power controls are managed by gnome-power-manager and not by ACPI (I think). 

--AJN

---

### Post by arnstein on 2006-07-14
Hi again, 
I was hoping to get a reply on this. 
Btw, by suspending/sleeping I meant suspend to RAM.

Thanks,
Arnold

---

### Post by RafRaf on 2006-07-14
Hi, 

I have EXACTLY the same problems on my HP nc6000

---

### Post by RafRaf on 2006-07-16
can anyone help? Pleeese!](*,)

---

### Post by nekr0z on 2006-07-18
Not exactly the same thing here on my Fujitsu-Siemens AMILO M7400, but the same delivery: my system doesn't wake up at all. Well, it actually does wake up, but the video card does not, so I get black screen and need to reboot (by pressing the power button or even Enter if I have a console with pre-typed "sudo reboot" command).

What video card do you have?

---

### Post by arnstein on 2006-07-19
Actually, at least in my case its not a Video problem. This I know because the going-to-terminal-and-typing-reboot does not work. More obviously, the CAPS lock doesn't switch on the CAPS lock indicator. I can't switch off my wireless. I can't do anything. 

Can someone tell me, if I kill gnome-power-manager, and use ACPI for managing sleeping/restoring will I get better results. Will there be any issues? Is there any benefit (apart from the GUI, the gnome-power-manager GUI is too plain to be useful) of using either?

This problem seems to have increased in recent times. Today itself I've had to reboot twice. 

I'm gonna put lot of debug statements in my ACPI scripts for the timebeing to find out whats happening. I have a certain feeling that it happens when certain battery events take place before/during suspending.

--arnie

---

### Post by alvenegas on 2006-07-19
Hi, I have the same problem.  I recently upgraded the graphic drivers on my inspiron 8100 laptop with nvidia GeForce 2 Go.  With the default driver 
"nv" the suspend and hibernate buttons on Dapper work perfect.  When I put 
the "nvidia" driver it does not work.  This is gnome-power-management that I am referring.  When the suspend button is pressed, the computer goes to sleep and the screen goes off, however, when i try to wake from sleep, i guess the video card have problems trying to come back....it just gives me a black screen.  

Is it an uncompatibility between the gnome-power-management and video cards?

Any help will be greatly appreciated!

Alberto

---

### Post by LAI on 2006-07-21
This sounds like what's happening on my HP/Compaq Presario R3000. I set the power settings through System Settings->Laptops & Power->Laptop Battery->Button Actions to suspend when the lid is closed. Then I close the lid, and after a few seconds of disk activity the power light is blinking: so far so good. Then I open the lid back up and press the power button, and it looks like it's about to start up, but the screen never powers on, the HD light stays on and eventually the caps-lock light starts to flash.

Here's a quick rundown of my hardware and stuff:
Linux version 2.6.15-26-amd64-generic
Chip: Athlon64
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
driverloader v.2.34 (For the Broadcom wlan)

Edit: forgot to mention -- I'm running Dapper.

---

### Post by Rexbron! on 2006-07-21
I was having simaler problems to the ones that you guys are descibing. I was able to fix suspending to ram and to disk by upgrading to the latest (2.6.17) kernel (Note: I had to compile the kernel from source as the ones in the repositories are 2.6.15). There are some threads kicking around the forums that describe the process. My laptop is a Acer Aspire 3624.

---

### Post by psycosmyth on 2006-07-21
I feel like an oddball..I have a Dell inspiron and it too does exactly the same thing too. I upgraded to the latest kernel and instead of locking up entirely it gives a false boot screen and then returns to the session after I bang a few more keys.:-|

---

### Post by Rexbron! on 2006-07-27
> **psycosmyth said:**
> I feel like an oddball..I have a Dell inspiron and it too does exactly the same thing too. I upgraded to the latest kernel and instead of locking up entirely it gives a false boot screen and then returns to the session after I bang a few more keys.:-|

That should be normal for suspend to disk.

Bad news: Some package or update i installed has returned me to the black screen problem.:confused: I wish I knew what it is... Will update if I fix the problem.

---

### Post by berg82 on 2006-08-29
> **Rexbron! said:**
> That should be normal for suspend to disk.

Bad news: Some package or update i installed has returned me to the black screen problem.:confused: I wish I knew what it is... Will update if I fix the problem.

The same happend to me on my Dapper installation. I reinstalled it to fix the problem. It was the fastest way for me. 

I have an Amilo M7400 and I have noticed some problems with Suspend-to-ram when running KDE (kubuntu). After resume the Video Card doesn´t wake up. 
If I reboot my system and start Gnome instead, the suspend-to-ram works. 

/Andreas

---

