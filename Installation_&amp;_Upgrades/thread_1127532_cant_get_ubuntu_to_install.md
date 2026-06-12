---
title: "cant get ubuntu to install"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by reece12345 on 2009-04-16
I just downloaded ubuntu from the website and i burnt it to a blank dvd. It says it says that it was burnt succesfully but when i boot from disk and try to install the screen will flash and suddenly go blank, forcing me to restart my laptop.
Can some1 please help i have no idea what to do.

---

### Post by Therion on 2009-04-16
Could be a number of things but first thing first:  When you browse the DVD you burned in Windows Explorer (I'm assuming you're running Windows), do you see one file on the DVD (ending with .iso) or you do you see several files and folders on the DVD?

---

### Post by reece12345 on 2009-04-16
when i open using windows explorer it opens up with lots of different files and different folders. When i also try to install green sqaures also flash on the screen

---

### Post by Therion on 2009-04-16
So do you get to a menu of choices [ that looks like this one](http://4.bp.blogspot.com/_jRRL0p_4W9I/SN0riB1AYbI/AAAAAAAACFs/F9SwEBpqwG0/s400/image42.png) before that happens?  

If you can, choose the option for "Try Ubuntu without making any changes to your computer" and see if you can run the LiveCD.

Also, since you're running Windows, go to Start/Run and in the textbox type in:  **dxdiag**
Click on the button for "Save results to a file".
Copy and paste the contents of the **dxdiag.txt** file that will be on your desktop into a new post in this thread.  This report will spec out your hardware so I can see what's under the hood of your PC.  Unless you know the hardware specs, then you can just rattle them off for me.

---

### Post by reece12345 on 2009-04-16
i can get to the menu of choices but when i choose any any of them the screen will flash with green boxes and then just go black. These are my specs

Operating System: Windows Vista™ Home Basic (6.0, Build 6001) Service Pack 1 (6001.vistasp1_gdr.090302-1506)
           Language: English (Regional Setting: English)
System Manufacturer: HIGRADED
       System Model: M7x0S                           
               BIOS: BIOS Revision: 1.00.08HI        
          Processor: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz (2 CPUs), ~1.6GHz
             Memory: 892MB RAM
          Page File: 907MB used, 1139MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6001.18000 32bit Unicode

---

### Post by Sargonos on 2009-04-16
i'm sorry to interrupt .... but i'm about to move from ubuntu to xubuntu

and i burned the disk from the internet, when i try to use the "try with out changes"

i get this

1 loading linux kernel
2 nice pretty blue screen, and then nothing else


i check the disk for errors, and had 1 reporting error.... do i need to re-download and burn again???

or could there maybe be another issue?

thought the problems could maybe be similar :S

---

### Post by Therion on 2009-04-16
> **reece12345 said:**
> i can get to the menu of choices but when i choose any any of them the screen will flash with green boxes and then just go black. These are my specs... 
Okay that's most of what I wanted to see... Do you know what video card or chipset you have?


[quote="Sargonos"]i'm sorry to interrupt .... but i'm about to move from ubuntu to xubuntu...[/quote]
You're going about it the wrong way.  You just need to install, and then use, the Xfce Desktop Environment from Synaptic.  

See post #2 in this thread for specific instructions:

[http://ubuntuforums.org/showthread.php?t=280768&highlight=xfce+gnome](http://ubuntuforums.org/showthread.php?t=280768&highlight=xfce+gnome)

---

### Post by reece12345 on 2009-04-16
this what else i could find

Card name: SiS Mirage 3 Graphics
     Manufacturer: Silicon Integrated Systems Corp.
        Chip type: SiS672 series
         DAC type: Internel
       Device Key: Enum\PCI\VEN_1039&DEV_6351&SUBSYS_08011558&REV_10
   Display Memory: 248 MB
 Dedicated Memory: 120 MB
    Shared Memory: 128 MB
     Current Mode: 1280 x 800 (32 bit) (60Hz)
          Monitor: Generic PnP Monitor
      Driver Name: SISGRUMD.dll,SiSClone.dll,SiSFunc.dll,SiSKrl.dll,SiSGlv.dll
   Driver Version: 7.14.0010.5110 (English)
      DDI Version: 9Ex
Driver Attributes: Final Retail
 Driver Date/Size: 3/12/2008 03:55:08, 3646464 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: 
Device Identifier: {D7B71ED9-2011-11CF-1E65-0B28B1C2CA35}
        Vendor ID: 0x1039
        Device ID: 0x6351
        SubSys ID: 0x08011558
      Revision ID: 0x0010
      Revision ID: 0x0010
       DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled

---

### Post by Therion on 2009-04-16
> **reece12345 said:**
> 
Card name: SiS Mirage 3 Graphics
     Manufacturer: Silicon Integrated Systems Corp.
        Chip type: SiS672 series
Most likely THAT is your problem.  SiS is not so good about releasing drivers.  Still, you should be able to get things up and running.  

What version of Ubuntu did you download and when you burned the disk did you burn it slooooowly?  

No faster than 16x for a CD and 4X for a DVD.  If you burned your install media any faster than that, then yes, re-burn the disks (slowly) and try installing again.

---

