---
title: "Epson c120 inkjet printer - local - works on ubuntu 8.04 - confirmed"
date: 2008-05-17
forum: Hardware
---

### Post by cgarre on 2008-05-17
I just connected my C120 epson inkjet color and ubuntu 8.04 works ! almost out of the box and i printed the test page - it looks beautiful !!!

Here is what i did .. dont know if thats required 
1. I went to synapic package manager (System->Administration->Synaptic Package Manager)
2. I searched for epson and i got a few packages.
3. There are two which are installed by ubuntu out of box (i guess) , make sure they are checked, otherwise check them (cupsddk-drivers and foomatic-db-engine) 
4. Now select these (inkblot, mtink and optionally escputil).
5. Apply, then it will install some more like libinklevel4 etc on its own. 

Once installed .. 
1. Power up your epson inkjet.
2. Plug in your printer to laptop via USB port.
3. Wait 2-3 seconds, you will find a system tray option saying a printer is connected and it will take about 5 seconds more to recognize the brand etc and it will give a message saying that Epson_C120_Stylus printer is installed and ready for use. There is an options button in the message.
4. Optionally you can click the "Options" button, and select print self test button and then click print test page. thats it ... 

So you are ready to go ... Your ubuntu is now ready to print ... 

It was very very easy and i didnt have to bother for looking around for drivers anywhere seems it was already ready out of box !!! wooo hooo ....

---

### Post by djmoore on 2008-07-10
> **cgarre said:**
> I just connected my C120 epson inkjet color and ubuntu 8.04 works ! 

Excellent! I'm new to Linux/Ubuntu, and have never installed a printer before. Everything worked fine with your instructions. (I'm running 8.04 on a generic desktop box with an ABIT NF8 motherboard, if anyone cares. Printer currently connected via a USB 2.0 expansion hub.)

Note: The user manual on the Epson CD ships as a Windows executable. HTML manuals are available on the Epson Support website. I admit I found the manual mostly useless, and I was unable to download it so I could look at it off line.

Fine little printer for the price. (I figure on going through about two cartridge changes, then throwing the printer away and buying its upgraded replacement.)

Now getting ready to install an external backup drive....

---

