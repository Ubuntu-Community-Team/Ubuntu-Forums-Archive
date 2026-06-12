---
title: "ATI/ATI Hybrids"
date: 2012-05-04
forum: Hardware
---

### Post by aluiziofr on 2012-05-04
Ubuntu 12.04 64-Bits

In my laptop i have ATI AMD Radeon HD 6550M and AMD ATI Mobility Radeon HD 4200 but Catalyst 12-4, not switching between two ATI cards, why?

aluizio@HP-dv6-3270br:~$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series] (rev ff)

aluizio@HP-dv6-3270br:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.11631 Compatibility Profile Context

> xorg.conf

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by MonkeyPaw on 2012-05-04
Are you running the Catalyst drivers from support.AMD.com, or from Additional Drivers? I think you'll have better luck using the ones straight from AMD.

---

### Post by aluiziofr on 2012-05-04
From AMD with clean instalation Ubuntu 12.04

---

### Post by QIII on 2012-05-04
> **MonkeyPaw said:**
> I think you'll have better luck using the ones straight from AMD.

Why do you think that?  AMD and Ubuntu have had a nice little thing going on for several years.

Ubuntu 12.04 comes with Catalyst 12.4.

11.10 came with 11.10.

11.04 came with 11.4.

10.10 came with 10.10.

10.04 came with 10.4.

See a pattern?

AMD schedules a new ATI driver release to come out with Ubuntu before it is available to public consumption.  Phoronix complains about it every time.

The fglrx development stream for Ubuntu 12.04 is 8.960.  The one released to everyone else is 8.961.  The difference?  8.961 is the "post release."

---

### Post by MonkeyPaw on 2012-05-04
I had much better luck when using the AMD drivers when I was messing with 12.04 beta 2 on my Llano rig. The Additional Drivers failed to install, while AMD's worked perfectly. I suppose that's because they hadn't updated them yet?

As for the pattern, that's nothing new. For 12.4: 12 = year (2012), .4 (or .04) = Month (April). Ubuntu and AMD release names will always coincide unless either one decides to change their naming convention. That's why 12.3 Cats were launched in March, 12.2s in Feb, etc. Often the driver updates are minor, but it's the best way to know how old they are without lots of digging.

---

### Post by aluiziofr on 2012-05-05
Someone, help me?

---

### Post by QIII on 2012-05-05
Here's the way to do it in the terminal

```
sudo aticonfig --px-dgpu
``` activates the discrete graphics.

```
sudo aticonfig --px-igpu
``` activates the integrated graphics.

You have to restart X for each to take effect.

Please let me know if this works and I'll put it in my tool kit.

---

### Post by QIII on 2012-05-06
> **MonkeyPaw said:**
> I had much better luck when using the AMD drivers when I was messing with 12.04 beta 2 on my Llano rig. The Additional Drivers failed to install, while AMD's worked perfectly. I suppose that's because they hadn't updated them yet?

As for the pattern, that's nothing new. For 12.4: 12 = year (2012), .4 (or .04) = Month (April). Ubuntu and AMD release names will always coincide unless either one decides to change their naming convention. That's why 12.3 Cats were launched in March, 12.2s in Feb, etc. Often the driver updates are minor, but it's the best way to know how old they are without lots of digging.

Yes.

Point being that the 4th and 10th months are always provided to Ubuntu before they are released to the public.

---

### Post by aluiziofr on 2012-05-06
> **QIII said:**
> Here's the way to do it in the terminal

```
sudo aticonfig --px-dgpu
``` activates the discrete graphics.

```
sudo aticonfig --px-igpu
``` activates the integrated graphics.

You have to restart X for each to take effect.

Please let me know if this works and I'll put it in my tool kit.

 Even after use "sudo aticonfig --px -dgpu" anb restart X, the "fgrlxinfo" show me:

 aluizio@HP-dv6-3270br:~$ fglrxinfo display: :0.0 screen: 0 OpenGL vendor string: Advanced Micro Devices, Inc. OpenGL renderer string: ATI Mobility Radeon HD 4200 Series OpenGL version string: 3.3.11631 Compatibility Profile Context

---

### Post by DGINSD on 2012-06-26
Is your st up an ATI/ATI Hybrid or a ATI/Intel Hybrid 
your actually going t use ```
aticonfig --px-list-active-gpu
``` to see which GPU is running 

Mine is ATI/ATI Hybrid and is not switching when on battery as it supposed to either and I can find little to no info on why or how to change it.

Have you activated and set the powerexpress settings in catalyst control center?

---

### Post by DGINSD on 2012-06-26
Just a thought there's a script in /etc/ati called authatieventsd.sh there's various sections for a lot of linux display managers but not one for lightdm could this be why switching is not working correctly?

I don't know enough about the inner workings workings of the system and scripting but for someone that knew how should be relatively easy to use the "sudo aticonfig --px-dgpu" and "sudo aticonfig --px-igpu" and restart X upon ac adapter plug in or removal

---

### Post by DGINSD on 2012-06-28
Just found this [http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg]("http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg") Which basically states that the graphics card switching is working but hot switching in Linux is not (and therefor battery/ac auto switching) because x must be restarted.

Kind of frustrating after hours of searching to find it's just a no go.

---

### Post by lebaghaloo on 2013-05-06
when i try it this it what i get


No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.

---

### Post by lebaghaloo on 2013-05-06
this is what i keep getting

sean@sean-HP-ENVY-14-Notebook-PC:~$ sudo aticonfig --px-igpu
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.

---

### Post by QIII on 2013-05-06
What version of Ubuntu are you running and what models are your two GPUs?

---

### Post by lebaghaloo on 2013-05-06
12.04 LTS

sean@sean-HP-ENVY-14-Notebook-PC:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

---

### Post by QIII on 2013-05-06
Hello again!

That is not an ATI/ATI dual system, but an ATI/Intel hybrid.

Unfortunately, this sort of system is problematic in Linux, as OEMs have not provided good Linux support.

The first thing to do would be to read through [this thread](http://ubuntuforums.org/showthread.php?t=1930450) and see if anyone has given some guidance that might be helpful for your situation.

[This wiki entry](https://help.ubuntu.com/community/HybridGraphics) may be helpful.

I wish I had better news.

Best wishes.

---

### Post by lebaghaloo on 2013-05-06
the thread doesnt have mine listed, but im trying to work with the wiki entry. however, when i try to access my debug files it says no permission. how do i work around that?

---

