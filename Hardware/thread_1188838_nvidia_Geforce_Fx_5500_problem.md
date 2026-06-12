---
title: "nvidia Geforce Fx 5500 problem"
date: 2009-06-16
forum: Hardware
---

### Post by raptor3D on 2009-06-16
Hello to everyone..:p

I recently installed ubuntu 8.10 (Intrepid Ibex) on my computer and i am having a hard time in setting my graphic card which is nVidia Geforce fx 5500 256Mb AGP.
After installation, i installed the driver and it ran successfully. But after ubuntu started running on this graphic card, it started hanging randomly anytime and also on pressing the 'shut down' button. And after two days, it is not even starting and sometimes gives the messege there is some problem with my graphical environment. I am a newbie to linux and know a little, but i could not configure out the problem. 

Any help??   ](*,)

---

### Post by raptor3D on 2009-06-16
Should I try Sayabon Linux...
I am not familiar with it but i can give a try if no option is left

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> Should I try Sayabon Linux...
I am not familiar with it but i can give a try if no option is left

whats the rest of your system specs? and what driver version?

---

### Post by raptor3D on 2009-06-16
My driver version is 173.14.18
It was downloaded when i was trying to activate desktop effects and it automatically did the work..

i have Intel 82845GV (Intel(R) Pentium (R) 4) motherboard with 1 Gigs of RAM and 160 Gigs of hard Disk.

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> My driver version is 173.14.18
It was downloaded when i was trying to activate desktop effects and it automatically did the work..

i have Intel 82845GV (Intel(R) Pentium (R) 4) motherboard with 1 Gigs of RAM and 160 Gigs of hard Disk.

your PC is pretty much exactly the same as my moms, except that has a 128MEGb GeForce 5700, which runs perfectly on the 173.14.18 driver on Intrepid.

how **EXACTLY** did you install the driver?

---

### Post by raptor3D on 2009-06-16
Well I tried to activate my desktop effects but it opened a window saying downloading driver...
I cancelled and opened my hardware list which showed two driver versions 90.something and 173.14 which was recommended. I clicked on activate and the previous window opened saying downloading driver. I waited or sometime and after installing the driver, it said me to reboot to activate the driver..

I rebooted and plugged from my onboard graphics to my 5500 driver and it worked.. 
But everytime is closed my computer, it hanged at the time of shutting down.

I don't understand what's the problem!

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> Well I tried to activate my desktop effects but it opened a window saying downloading driver...
I cancelled and opened my hardware list which showed two driver versions 90.something and 173.14 which was recommended. I clicked on activate and the previous window opened saying downloading driver. I waited or sometime and after installing the driver, it said me to reboot to activate the driver..

I rebooted and plugged from my onboard graphics to my 5500 driver and it worked.. 
But everytime is closed my computer, it hanged at the time of shutting down.

I don't understand what's the problem!

okkkkkkkkkk. I installed the driver manually, maybe that made a difference.

perhaps you should uninstall from Hardware Drivers, and install manually.

---

### Post by raptor3D on 2009-06-16
I tried this but the problem is still the same...

Any more great ideas??

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> I tried this but the problem is still the same...

Any more great ideas??

lol @ great ideas :P

ummmmm, well no not really. 

whats method did you use to manually install?

did you save the driver to your desktop and then;

CTRL+ALT+F1

then login;

then;

sudo /etc/init.d/gdm stop

cd Desktop

sudo sh ./N(press tab key)

and install via the options?

---

### Post by raptor3D on 2009-06-16
When i tried it earlier, it said that it will work in runlevel 3. But I was not able to do so. it did not solved the problem either...

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> When i tried it earlier, it said that it will work in runlevel 3. But I was not able to do so. it did not solved the problem either...

run level 3?

where you using Ubuntu when you tried to install that way?

---

### Post by raptor3D on 2009-06-16
Actually, I was.

I am a newbie...:D:D:D

But I'll try again

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> Actually, I was.

I am a newbie...:D:D:D

But I'll try again

okkkkkkkkk, do you need an exact guide, because what I put before wasn't complete.

---

### Post by raptor3D on 2009-06-16
Continue Please : Tell me from first step

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> Continue Please : Tell me from first step

first things first, have you removed the previous driver?

---

### Post by raptor3D on 2009-06-16
Yes i have

Next

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> Yes i have

Next

are you suing 32Bit, or 64Bit?

---

### Post by raptor3D on 2009-06-16
I am using 32-bit system

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> I am using 32-bit system

sweet, that keeps things simple. 

brb.

---

### Post by raptor3D on 2009-06-16
What to do next?

---

### Post by ayenack on 2009-06-16
This could be a problem with Firefox and the Nvidia drivers. I remember there was an issue. I think that it's still relevant. If the system hangs when using Firefox or browsing the web it may well be the problem.

---

### Post by raptor3D on 2009-06-16
I don't think firefox is the problem..

I am 100% sure it's a bloody driver problem

---

### Post by nolliecrooked on 2009-06-16
download this file to your **DESKTOP**

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.18/NVIDIA-Linux-x86-173.14.18-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.18/NVIDIA-Linux-x86-173.14.18-pkg1.run)

when it has finished downloading, right click it and goto properties. click the Permissions tab, and tick the "Execute: Allow executing file as program

now hit CTRL+ALT+f1, it will bring you to the command line. login with your username/password, and follow these instructions **EXACTLY**

type;

**sudo /etc/init.d/gdm stop**

and hit enter, it will prompt you for your password, type it and hit enter. 

next type;

**cd Desktop**

and then;

**sudo sh ./N(press the tab key here and it will bring up the rest of the file name for you)** 

and press enter.

follow the on screen instructions, it may ask you if it can remove the old driver, **LET IT**. and when you get to when it asks you if you would like it to update your xorg.conf (or X-Server Configuration, same thing), say **YES**. it should say that it was a successful install. at which point type;

**sudo reboot**

and you **SHOULD** reboot into a nicely installed driver.

Ill update this a little more when my insomnia isnt fighting my tiredness quite so hard xD

---

### Post by raptor3D on 2009-06-16
Thanks for help...

My OS crashed...

It sometimes boots otherwise not.
And in that sometime, if it boots then it hangs immediately afterentering username and password....

Think of something else..;);)

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> Thanks for help...

My OS crashed...

It sometimes boots otherwise not.
And in that sometime, if it boots then it hangs immediately afterentering username and password....

Think of something else..;);)

ugh sorry bro. it sounds like you have deeper issues. I dont think I can help ya anymore...

---

### Post by raptor3D on 2009-06-16
It's O.K.  but a hint for you

The program was saying that no precompiled kernel interface was found to match my kernel, the compiler build the kernel itself and after that you know what happened....
When i switched back to my onboard graphics, it said that no fatal screen was found.

But thanks anyway..

Could you suggest anything to restore my system back

---

### Post by raptor3D on 2009-06-16
I think I need to switch to Sayabon linux..

---

### Post by nolliecrooked on 2009-06-16
> **raptor3D said:**
> It's O.K.  but a hint for you

The program was saying that no precompiled kernel interface was found to match my kernel, the compiler build the kernel itself and after that you know what happened....
When i switched back to my onboard graphics, it said that no fatal screen was found.

But thanks anyway..

Could you suggest anything to restore my system back

that prompt about no pre-compiled kernel interface is normal, just choose no. it will compile one for you!

---

### Post by ayenack on 2009-06-16
Just for future reference. You should always make a backup of your xorg.conf before installing new graphics drivers.

To do this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

and then if you're booted down to the command line and need to restore the previous xorg.conf.

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

Not much help now though I'm afraid.

---

