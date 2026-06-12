---
title: "ATI video card"
date: 2008-11-16
forum: Hardware
---

### Post by Slim1950 on 2008-11-16
I just installed Unbuntu 8.10, and my screeen scrolls in a very jerky fashion.

I have searched for awhile for the right advice. I am only getting more confused.

My ATI card is a Radeon 9200 series.

When I enter: grep -i driver /etc/X11/xorg.conf to find out what driver I am using, I get no response, not even a new prompt, only a cursor that blinks back at me.

When I enter: sudo lspci | grep -i vga
I get -
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

SO I do not know whether the right driver is installed.
Help please.

I just switched back from openSUSE.. I found that system way too complex for my liking, an was getting errors galore.

---

### Post by Skripka on 2008-11-16
When you run amdcccle -what does it tell you?  You should get the ATi Catalyst Control Center, if you have the ATi driver installed and active....The ATi driver is listed as "active" in Hardware Drivers, No?

---

### Post by Slim1950 on 2008-11-16
> **Skripka said:**
> When you run amdcccle -what does it tell you?  You should get the ATi Catalyst Control Center, if you have the ATi driver installed and active....The ATi driver is listed as "active" in Hardware Drivers, No?

No.
It tells me 
There was a problem initializing Catalyst Control Centre. It could be caused by the following.
No ATI Graphics driver is installed or the ATI driver is not functioning properly..
Please install the ATI driver appropriate for your ATI hardware or configure using aticonfig.

---

### Post by dynamethod on 2008-11-16
Make sure your using this driver: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

---

### Post by Slim1950 on 2008-11-16
> **dynamethod said:**
> Make sure your using this driver: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

Okay, I did that, and rebooted. It gave me an error on reboot, giving me the option of rebooting in lowgraphics mode (I have a memory of trying this about a year ago, and coming up with a blank screen.. ended up with a total reinsatall of the OS.)

Now, I still got the error that an ATI driver wasn't installed or configured properly.

I then ran aticonfig --initial and I got this response.
Uninitialised file found, configuring.
Segmentation fault
So I assume nothing happened.

---

### Post by jocko on 2008-11-17
> **Slim1950 said:**
> My ATI card is a [COLOR=Red]Radeon 9200[/COLOR] series.

When I enter: grep -i driver /etc/X11/xorg.conf to find out what driver I am using, I get no response, not even a new prompt, only a cursor that blinks back at me.

> **Skripka said:**
> When you run [COLOR=Red]amdcccle[/COLOR] -what does it tell you?  You should get the ATi Catalyst Control Center, if you have the ATi driver installed and active....The ATi driver is listed as "active" in Hardware Drivers, No?

amdcccle is only for the proprietary fglrx driver, which only supports cards from radeon 9500 and up. The open source driver (radeon) is the only driver that works with the 9200.



> **Slim1950 said:**
> I then ran aticonfig --initial and I got this response.
Uninitialised file found, configuring.
Segmentation fault
So I assume nothing happened.
Same here. aticonfig is also only for the proprietary driver.

You need to completely remove all packages with "fglrx" in their names and undo whatever changes you've made to xorg.conf.

To see which driver is used, check the output of:
 ```
lsmod | grep vesa || lsmod grep radeon
```If you see "radeon" there you use the correct driver, if you see "vesa" you are not.

Note that the installation of the fglrx driver may have replaced some important files which may make it difficult to get back to the state you had before you started messing. (in that case you will be stuck with the vesa driver, in which case you will probably be stuck at a low resolution and refresh rate and even slower scrolling...)

---

### Post by Slim1950 on 2008-11-17
> **jocko said:**
> amdcccle is only for the proprietary fglrx driver, which only supports cards from radeon 9500 and up. The open source driver (radeon) is the only driver that works with the 9200.




Same here. aticonfig is also only for the proprietary driver.

You need to completely remove all packages with "fglrx" in their names and undo whatever changes you've made to xorg.conf.

To see which driver is used, check the output of:
 ```
lsmod | grep vesa || lsmod grep radeon
```If you see "radeon" there you use the correct driver, if you see "vesa" you are not.

Note that the installation of the fglrx driver may have replaced some important files which may make it difficult to get back to the state you had before you started messing. (in that case you will be stuck with the vesa driver, in which case you will probably be stuck at a low resolution and refresh rate and even slower scrolling...)

Sorry for being a pain.
I have uninstalled all files containing fglrx.
I tried entering the line in terminal mode: lsmod | grep vesa etc..

But nothing happened.
I got no response.

How do I "undo whatever changes I have made to Xorg.conf? 
I didn't manually change anything in that file.

---

### Post by Slim1950 on 2008-11-17
Sorry for being a pain..

OK, I uninstalled all files with fglrx in them.
I tried running that code that would tell me what driver is being used, but I entered in terminal mode, and nothing hapens. No response.

---

### Post by Slim1950 on 2008-11-17
Maybe I should ask this question. What wold you recommend for a video card if I were to buy a new one? I am not a gamer, but I would like smooth action on my old machine here.

I have 512 Meg of ram, and a 1700 Ghz AMD Athlon machine.

---

### Post by jocko on 2008-11-17
> **Slim1950 said:**
> Sorry for being a pain..

OK, I uninstalled all files with fglrx in them.
I tried running that code that would tell me what driver is being used, but I entered in terminal mode, and nothing hapens. No response.

Why did you run it in terminal mode? As the driver is only used by xorg, you need to run that command while xorg is running, otherwise you will not get any output...


> **Slim1950 said:**
> Maybe I should ask this question. What wold you recommend for a video card if I were to buy a new one? I am not a gamer, but I would like smooth action on my old machine here.

I have 512 Meg of ram, and a 1700 Ghz AMD Athlon machine.

The open source driver (radeon) should work fine with your card. Maybe you need to tweak some setting in xorg.conf to make it run better... I don't know...
If I were to buy a new card now, I would go for nvidia (their proprietary drivers are better than ati's, but the open source driver is not good).
The support for ati cards is getting better from the open source side, but to me it seems like the proprietary drivers don't really improve in any significant way even if they are updated every month...
But before you buy any new card, make sure that you first have the correct driver (radeon) running, and try to tweak some settings in xorg.conf (I've seen something about EXA vs. XAA acceleration, and one is supposed to be better than the other, but you'll have to search for that yourself...)

---

### Post by Slim1950 on 2008-11-17
> **jocko said:**
> Why did you run it in terminal mode? As the driver is only used by xorg, you need to run that command while xorg is running, otherwise you will not get any output...



OK, go slow.. step by step.

What do I do with this code?

lsmod | grep vesa || lsmod grep radeon

I went to gnome-terminal, entered the above line exactly (I copied and pasted, and it returns nothing but a new prompt. (I am still very much a new user.

---

### Post by Slim1950 on 2008-11-17
Can someone please help with this dumb video problem? I feel like I ahve been going in circles for days now with this.

Surely it is not that uncommon a problem.

A 9200 series ATI video card

And my XORG.conf says:
ection "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Nothing that indicates the open source Radeon driver

---

### Post by jocko on 2008-11-18
> **Slim1950 said:**
> OK, go slow.. step by step.

What do I do with this code?

lsmod | grep vesa || lsmod grep radeon

I went to gnome-terminal, entered the above line exactly (I copied and pasted, and it returns nothing but a new prompt. (I am still very much a new user.

That's weird. Have a look in your /var/log/Xorg.0.log (while X is running).
See if you find any lines starting with something like this:
```

(II) RADEON(0): 
(II) ATI(0): 
(II) VESA(0): 
(II) FGLRX(0): 
```

Whichever you find is the driver that's in use.

> **Slim1950 said:**
> Can someone please help with this dumb video problem? I feel like I ahve been going in circles for days now with this.

Surely it is not that uncommon a problem.

A 9200 series ATI video card

And my XORG.conf says:
ection "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Nothing that indicates the open source Radeon driver

That's just the way it should be. Xorg autodetects what hardware you have and configures it without any need for xorg.conf. But you can still make it use xorg.conf by adding some options to it.

---

### Post by Slim1950 on 2008-11-18
That Xorg log file has TONS of lines beginning with Radeon. 
Shall I list the log here?
WOuld't that be indicative of the fact that I have tried installing Radeon drivers several times now?

---

### Post by zwaardmeester on 2008-11-18
Moreover, turning off Compiz by choosing 

-> System -> Preferences -> Appearance -> Visual Effects -> None

should improve your scrolling speed. I running without visual effects too on my old ati 9800 card. Let us know how it's going. Are you still getting errors at startup about Low Graphics mode ?

---

### Post by Stason on 2008-11-18
> **Slim1950 said:**
> I just installed Unbuntu 8.10, and my screeen scrolls in a very jerky fashion.

I have searched for awhile for the right advice. I am only getting more confused.

My ATI card is a Radeon 9200 series.

When I enter: grep -i driver /etc/X11/xorg.conf to find out what driver I am using, I get no response, not even a new prompt, only a cursor that blinks back at me.

When I enter: sudo lspci | grep -i vga
I get -
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

SO I do not know whether the right driver is installed.
Help please.

I just switched back from openSUSE.. I found that system way too complex for my liking, an was getting errors galore.

Save yourself - get Nvidia card. That is what I did after a month of pointless bashing with 9200 Radeon. I got 7300 GT very cheaply by the way.

---

### Post by Slim1950 on 2008-11-18
> **zwaardmeester said:**
> Moreover, turning off Compiz by choosing 

-> System -> Preferences -> Appearance -> Visual Effects -> None

should improve your scrolling speed. I running without visual effects too on my old ati 9800 card. Let us know how it's going. Are you still getting errors at startup about Low Graphics mode ?

I did that, and things have improved. I am not into gaming or any fancy 3D effects, so this will do for now.

Now on to the next problem. I need to get sound working. :)

---

### Post by Slim1950 on 2008-11-21
I ordered an Nvidia card. Will the right driver automatically be installed or am I going to have to spend a great deal of time learning how to find and install the driver?

---

