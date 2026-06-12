---
title: "XPS M1710 - Geforce 7950 go GTX - fan failure"
date: 2010-11-21
forum: Hardware
---

### Post by jophos on 2010-11-21
Ever since I purchased my XPS M1710 I have experienced overheating issues.  Both the fans have had failed bearings at one time or another in the past and this had led to the VRAM getting damaged.  Thankfully these failures were covered by my extended warranty.  Later I was not so lucky...

First I noticed that the CPU was fixed at its lowest clock speed, 1GHz, regardless of the setting in the CPU Frequency Scaling Monitor.  I determined that the CPU clock had been locked down because the computer had detected that it had overheated and it was trying to avoid melting itself.  It became pretty clear when I opened a 3D application that the GPU was not being cooled, as there was no sign of the temperature slowing down as the temperature reached 100°C.  Later I found out that the fan had completely stopped even though the software was reporting that it was moving at maximum RPM.

I contacted Dell, expecting that they would just replace the fan, but after insulting my intelligence and risking destroying the memory of my GPU by running the boot-up diagnostic tests (at least it was confirmed by the tests that the VRAM wasn't damaged this time) they finally quoted me the cost of repair:

**[COLOR=#1f497d]Replace MBD[/COLOR][COLOR=#1f497d]+graphics card[/COLOR][COLOR=#1f497d]:[/COLOR]**
  
  **[COLOR=#1f497d]Next Business Part only fix it yourselves :[/COLOR]**
  
  Net:........627.07 £
VAT(17.5%):.109.74 £
SUM:........736.81 £
  **[COLOR=#1f497d]Next Business day Engineer Onsite  :[/COLOR]**
  
  Net:........687.07 £
VAT(17.5%):.120.24 £
SUM:........807.31 £
  
  **[COLOR=#1f497d]Replace graphics card only[/COLOR]**
  **[COLOR=#1f497d]Next Business Part only fix it yourselves :[/COLOR]**
  
  Net:........353.26 £
VAT(17.5%):..61.82 £
SUM:........415.08 £
  **[COLOR=#1f497d]Next Business day Engineer Onsite  :[/COLOR]**
  Net:........413.26 £
VAT(17.5%):..72.32 £
SUM:........485.58 £

This is ridiculous for a laptop which is over 4 years old considering that the GPU in my newly built desktop (1GB GByte GTX460 OC PCI-E) cost only £163.87 inc VAT.

Having decided to give Dell the 'two-fingered salute' I proceeded to attempt to rotate the fan through the duct with a paperclip, in the vain hope that the motor wasn't burnt out.  The fan had some trouble revolving, but I wasn't sure if this was due to the positioning of the magnets.  After some fiddling I got the fan to turn completely, at which point it immediately started to spin up.

I hope that this account may help those who are experiencing similar problems from wasting a silly amount of money lining Dell's coffers.

---

### Post by cascade9 on 2010-11-22
Looks like Dell has priced repairs so high that its not worth getting the work done....you could get a new laptop with similar/better specs for not much more than that.

You could try replacing the fan yourself. 

> **jophos said:**
> Having decided to give Dell the 'two-fingered salute' I proceeded to attempt to rotate the fan through the duct with a paperclip, in the vain hope that the motor wasn't burnt out.  The fan had some trouble revolving, but I wasn't sure if this was due to the positioning of the magnets.  After some fiddling I got the fan to turn completely, at which point it immediately started to spin up.

FYI, the resistance to spinning the fan would be from totally siezed bearings, nothing to do with magnets.

---

### Post by jophos on 2010-11-22
Just to clarify that the fan worked fine after I manually revolved it with the paperclip - I guess that a bit of hair or dust prevented the fans from turning.

I am aware that the arrangement of magnets in some motors makes them resistant to manual rotation, which was what I was referring to. I could tell that there was no damage to the bearings because there was no grinding feeling while turning the fan and when the fans starting spinning there was no sound from the bearings.   I know what it sounds like when the bearings are broken because they have done so before (like bolts in a blender).

---

### Post by cascade9 on 2010-11-23
When you unseize bearings, thats what happens, they spin fine. Sometimes anyway. Well, till next time you try to start them, then sometimes they will have reseized. :( 

Different bearing 'feel' different when they unseize. No sound from the bearings after unseizing isnt that common, but I've had it happen.

---

### Post by jophos on 2010-11-23
I haven't restarted it yet, but I was a little concerned anyway that the fix may not be permanent.  At worst the fans will be seized up next time, but at least I now know for sure that only the fan is damaged.  If the fan is a standard size then I will try to replace it.

---

