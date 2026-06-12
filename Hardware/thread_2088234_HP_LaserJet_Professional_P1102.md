---
title: "HP LaserJet Professional P1102"
date: 2012-11-25
forum: Hardware
---

### Post by Mubat on 2012-11-25
I want to install HP LJ Professional P1102 on Ubuntu 12.04 LTS. I selected from pinter driver but it does not work. 
There is error message 

     Idle - /usr/lib/cups/filter/hpcups failed HP LJ P1102

Please help

PS. It is shared printer on Windows 7

---

### Post by Bucky Ball on 2012-11-25
You need to install HPLip. You can find it in Software Centre/Synaptics.

When you say it is a shared printer on Windows, the printer is physically connected to the Windows machine and you are able to see the Windows machine with your Ubuntu machine? If so I'm wondering if you need to use a Samba printer share to do that.

UPDATE: I had a look at the printer and is wireless. Why not just do it like that? You need to find out the printer IP address (press some button on the front five times or something???), then go to Printing>Add Printer>Network Printer ... wait for a bit and it should find it. Do all that *after* installing HPLip. ;)

---

### Post by daslinkard on 2012-11-25
> **Mubat said:**
> I want to install HP LJ Professional P1102 on Ubuntu 12.04 LTS. I selected from pinter driver but it does not work. 
There is error message 

     Idle - /usr/lib/cups/filter/hpcups failed HP LJ P1102

Please help

PS. It is shared printer on Windows 7

Are you using this on a Network via either wired or wireless?

---

### Post by Bucky Ball on 2012-11-25
> **daslinkard said:**
> Are you using this on a Network via either wired or wireless?

That's it. But it does have cable ethernet. If you have a wireless router, just set it up. Doesn't matter if the Win machine is cabled to the router, as it's on the same network it will access it no problem. We have three wireless machines and a hardwired desktop all using the same wireless printer. ;)

I edited post #2 to give you some tips setting up wirelessly.

---

### Post by daslinkard on 2012-11-25
You should be able to go to your Windows 7 machine and pull the IP address for the printer.  **You should be able to obtain this from your Hardware directory containing all available printers.  At that point you would do the following:

1. Add printer
2. Select Network printer
3. Select Find Network printer
4. Where it asks for Host enter in the IP address you obtained from your Windows 7 machine.
5. At this point it will point you through your port for printing and should be able to follow the steps to finish the set up.

---

### Post by Mubat on 2012-11-26
I use this printer on Network via wired and find the network printer. Also it says "This printer share is enable" 
I installed HPlip and during setup did not find HP device

---

### Post by Bucky Ball on 2012-11-26
So the printer is plugged into a router??? If the printer is on the network there is no need for a 'share'; each machine can use it independently. No need to daisy chain machines or enable shares ... that means you need machines to be on when you want to use the computer. You just want to be able to use the printer directly from your machine without relying on another being on, or at least that is the simplest scenario ... that is what network printers are about else you may as well have a regular USB printer attached to one machine and use Samba shares ...

---

### Post by daslinkard on 2012-11-26
> **Mubat said:**
> I use this printer on Network via wired and find the network printer. Also it says "This printer share is enable" 
I installed HPlip and during setup did not find HP device

What I would recommend doing would be getting the IP address for the printer from your windows machine and then following the steps I had listed out above....how you can do that (get printer IP address) is as follows:
> 
1. Press the Windows "Start" button  and choose Control Panel.
2. Select Hardware & Sound,  and then choose Devices and Printers
3. Right click on the printer that you want to know the IP address of and select properties
4. Click on the Ports tab and the first number listed should be your IP address for the printer. Hopefully this helps you.
[LEFT][COLOR=#000000]
[/COLOR][/LEFT]

---

