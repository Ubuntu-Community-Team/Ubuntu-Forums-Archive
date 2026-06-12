---
title: "Toshiba Tecra M4 - $sudo toshset -bluetooth on - Simply Doesn't work."
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by escragg on 2007-11-13
Hey Guys,

Switched over to Gutsy after being a life-time windows user last week.  For the most part I'm thrilled, but there are is one inop which is driving me crazy-

I've spent most of the afternoon trying to get my bluetooth working.  After googling, I found plenty of references to toshset, but when I run it, I get the following:

root@escragg-laptop:/home/escragg# toshset -bluetooth on
wireless switch is off
bluetooth: wireless switch is off

root@escragg-laptop:/home/escragg# toshset -q
 machine id: 0xfcff    BIOS version: 1.50    SCI version: 2.82
 toshset version: 1.72                  Toshiba Model: Portege M100/M300 Tecra M2/A2/A3/M4
 HCI/SCI access mode: kernel            battery save mode: full power         
 power source: external                 LCD backlight: on                     
 fan: low                               select bay: CDROM                     
 USB legacy mode: enabled               USB FDD emulation mode: enabled       
 LAN controller: enabled                Video out: internal: LCD              
 flat panel:  1400_1050, 18 bit TFT     lcd brightness: super-bright          
 lcd intensity: 7/7                     CPU speed: fast                       
 CPU sleep mode: off                    Display stretch: off                  
 battery percent: 100%                  cooling method: performance           
 power-up alarm: disabled              SciFeature::query: received an unexpected response for feature Standby time: 1
                                       
 boot method: hard disk->CDROM->floppy  wireless support: present             
 wireless switch: unavailable           bluetooth: wireless switch is off
    
 owner string: [ max length: 513]
root@escragg-laptop:/home/escragg# 

I.E, it appears that toshset -bluetooth on|off simply has no effect what so ever, and hcitool dev still shows no hardware address.

Any ideas? I'm kinda at a loss here.

-Scott

---

### Post by escragg on 2007-11-13
Somewhat related but not nearly as annoying-

There is also a system beep which triggers whenever I try to use the cursor to move beyond the bounds of a text buffer (pressing backspace at a shell prompt, for example).

I tried using toshset to disable it:

root@escragg-laptop:/home/escragg# toshset -b off
SciFeature:action: error setting system beep
        SciSet returned: FAILURE

root@escragg-laptop:/home/escragg# 

Any ideas?

---

### Post by escragg on 2007-11-13
Ok, Ok... I get a dunce-cap for this one... 

Three hours googling online, and the answer to my problem was... *drumroll please*

The little "wifi" switch at the front of my computer was in the "off" position.

durr.....

---

### Post by harce on 2008-04-23
any luck with the system beep? I'm struggling with the same thing (the system settings way of turning it off wont work)

---

