---
title: "Cannot install nvidia drivers"
date: 2008-08-15
forum: Hardware
---

### Post by MrNatewood on 2008-08-15
This is a very strange circular pattern.
It's so circular I'm not even sure where to begin.

Lets start with starting up the computer.
The first thing I see is an error message telling me that my graphics card was not detected properly and ubuntu is running in low-graphics mode.
I have a button that sass "configure" so I click on it.

It doesn't detect my monitor (terio 1280x1024 lcd) nor my graphics card(geforce fx 5600 ultra).
It chooses by default an 800x600 monitor and VESA driver.
So I click around, choose a generic 1280x1024 monitor(and set the resolution to that) and NVIDIA Geforce FX open-source driver(although I want the official nvidia ones, this is why all of this started. but I have no choice in this matter)

I click ok. Despite my choices I am loaded into an 800x600 desktop.
So I go to System -> Preferences -> Screen Resolution and I'm not given the choice of changing the resolution. just 800x600 and 640x480.
Confused, I go to Administration -> Hardware Drivers.
There I see my drivers are installed but not enabled. So, of course, I tick the enabling box.
Immediately after I click "close" I am prompted to restart my computer "In order to complete the update of your system".
Before I restart I check to see if I can change my resolution anyway, and I discover I can't.
Once I restart I'm back to exactly where I started at, the error message that nothing has been detected correctly and again I need to configure everything just so I can restart into the same error.

If it matters, this cycle started because I was using the Envy drivers but they didn't work with counter-strike over wine, so I removed them and tried to install the nvidia ones. I'm using ubuntu 8.04.

How can I break this cycle?

---

### Post by Uchiha_madara on 2008-08-15
> **MrNatewood said:**
> This is a very strange circular pattern.
It's so circular I'm not even sure where to begin.

Lets start with starting up the computer.
The first thing I see is an error message telling me that my graphics card was not detected properly and ubuntu is running in low-graphics mode.
I have a button that sass "configure" so I click on it.

It doesn't detect my monitor (terio 1280x1024 lcd) nor my graphics card(geforce fx 5600 ultra).
It chooses by default an 800x600 monitor and VESA driver.
So I click around, choose a generic 1280x1024 monitor(and set the resolution to that) and NVIDIA Geforce FX open-source driver(although I want the official nvidia ones, this is why all of this started. but I have no choice in this matter)

I click ok. Despite my choices I am loaded into an 800x600 desktop.
So I go to System -> Preferences -> Screen Resolution and I'm not given the choice of changing the resolution. just 800x600 and 640x480.
Confused, I go to Administration -> Hardware Drivers.
There I see my drivers are installed but not enabled. So, of course, I tick the enabling box.
Immediately after I click "close" I am prompted to restart my computer "In order to complete the update of your system".
Before I restart I check to see if I can change my resolution anyway, and I discover I can't.
Once I restart I'm back to exactly where I started at, the error message that nothing has been detected correctly and again I need to configure everything just so I can restart into the same error.

If it matters, this cycle started because I was using the Envy drivers but they didn't work with counter-strike over wine, so I removed them and tried to install the nvidia ones. I'm using ubuntu 8.04.

How can I break this cycle?

Listen are you sure that Nvidia is the Drivers of you're Pc/Laptop


Type :
> lspci -v


If it is Nvidia try that it must work with you

Listen Choose the System > Administration > restricted Drivers
then make check on all the drivers in the List


that is the way to configure Nvidia Drives

it's Strange because Ubuntu recognize it directly
except the VGA card

---

### Post by MrNatewood on 2008-08-15
Yes I am 100% sure. this has worked in previous versions of ubuntu and in windows.

Output of lspci -v:
```
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600 Ultra] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at fe5e0000 [disabled] [size=128K]
	Capabilities: <access denied>

```

---

### Post by MrNatewood on 2008-08-15
Solved.
This is what worked for me if someone has the same problem:
Downloading the driver installation from the nvidia website:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Clicking Ctrl+Alt+F1
logging in as root
/etc/init.d/gdm stop
cd to the directory the file was downloaded to
sh NVDIA*
clicking ok on everything.

---

