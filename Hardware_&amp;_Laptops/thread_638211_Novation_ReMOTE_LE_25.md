---
title: "Novation ReMOTE LE 25"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by d22901 on 2007-12-11
Guys/Gals,

 Let me note I am a complete nOOb when it
 comes to anything that has to do with Linux, but I just get the feeling
 that my only chance at getting this problem resolved is going to come via
 someone who knows Linux fairly well.  If you have anything to offer
 here I would appreciate it.  Novation's tech support is just giving me the
 run around, so I am turning to other options.  Here is what I sent to
 them:

To the Focusrite/Novation team:

Let me first admit this is a bit of a desperation move here.  I own a
 ReMOTE LE 25 that was purchased last year around October, and has worked
 flawlessly up until about two weeks ago.  Fumbling around the Novation
 website I came across a new Operating System for the keyboard, version
 1.36.  Now it was recommended to use MIDI-OX to get the OS sysex file
 to the keyboard.  After getting the buffers correct to send the sysex
 to the keyboard, I got an Abort! message on the ReMOTE LE's display.  So
 I attempted to send the file again, but in the process, the display on
 the ReMOTE LE just went blank.  So at this point, whenever I power up
 the keyboard, it just hangs, which I would assume means that the
 firmware within is corrupted.  The display just stays blank, still with the
 blue backlight.  The top 16 of the 2x16 display have shaded boxes still,
 as if there should be something there, but there are no shaded boxes
 on the bottom 16.  Also, sometimes when I power it up the LEDs for
 the selectable buttons will come on and stay on, in no particular
 order; it changes each time when I turn it on.
 
 Honestly, now that I am out of warranty, I opened up the keyboard to
 see what internals were in charge.  I am no programmer, nor a computer
 expert for that matter, but I figured I would try to find out what could
 be done.  Now I am really intent on figuring this thing out as I have
 spent hours on end trying to learn what makes this thing tick.  Inside,
 the one interesting thing that I found was the Cypress AN2131SC EZUSB
 microcontroller.  From what I read, this chip can rewrite an EEPROM via
 I2C.  I would assume the EEPROM is an SST 29ee512, another chip I
 found and read up on.  There are two other major components, a Winbond
 microcontroller and an Atmel PLD, ATF16v8b.  Long story short, just about
 everything this unknowing mind has tried failed, once again I am no
 programmer.  I had figured out a way for this thing to be recognized as
 just the Cypress EZUSB 2131 by my OS, Windows XP Pro, but this just
 temporarily disabled the EEPROM on board, and I still cant figure out
 how to write to the EEPROM from Cypress' EZUSB Development Kit
 software.
 
 Now I must note as well, prior to attempting to download the new OS to
 the ReMOTE LE, I had already downloaded the updated drivers for the
 Novation, and now finding this site, I have downloaded the new beta
 drivers, which installed just fine and Windows is showing the device as
 completely functional.
 
 What I am asking is this:  Can this problem be rectified?  There must
 be a way to prompt the EEPROM for a new write, or something along those
 lines.  To be truthful with you, I would like to be able to do this on
 my own now that I have put an overwhelming amount of time into trying
 to understand how this works.  I dont care how technical the solution
 is, if you can give me an instruction set as to how to get this done you
 can best believe that I am going to follow through with it.  I have to
 believe this is something simple, surely something very simple for you
 guys.  The VID and PID show 1235 and 0004 respectively through Device
 Manager, which would indicate to me the EEPROM is still somewhat
 intact, since from what I understand the EEPROM is what defines the device
 through the Operating System on the host.
 
 Once again, I will stress that it would be nice to be able to figure
 this out with your help, and maybe I can understand even more as to how
 this device works.  I think I can safely say I will be stoked if you
 have a solution for me here.
 

 -----------------------------------------------------------------------------------------------------------------------

So that is where it stands.  I have a keyboard that when powered up
 just hangs immediately, none of the buttons work at all.  Is there any way
 to get the OS back on the keyboard or am I screwed?  All i have to go
 on here is the OS file in sysex format, .syx.  There is no
 documentation on any Novation hex or ihx files that I can find anyway. 
If you could point me in the right direction, that would be fabulous.  I took a look at a program fxload for linux which seems to be able to work with EZUSB devices, but I am assuming since the eeprom is at least partially intact then it is going to take precedence in identifying the device to Linux.  I have two lappys with WinXP and my desktop is Ubuntu, mainly just to fool with it because I have never used Linux before.  Keep in mind I am a noob so if you have any specific instructions just outlay them gently if you dont mind.

Thanks alot,

Derrick

---

### Post by d22901 on 2007-12-12
bump

---

### Post by hihihi on 2008-04-01
hi, did  u try to fix it under windows?
did your keyboard ever work under linux? / ubuntu?

---

### Post by d22901 on 2008-04-23
> **hihihi said:**
> hi, did  u try to fix it under windows?
did your keyboard ever work under linux? / ubuntu?

I had it connected before to ubuntu when the OS for the keyboard was still functional, but now that it is in a frozen state I cannot get any response when pressing keys on the keyboard.  After all this time I am still stuck on this one.  Somehow, I need to prompt this keyboard for an OS overwrite but I have no idea how to do this because it doesn't display anything to me at all on the LCD.  I figured I would have a better shot with Linux in communicating with this thing.  Any suggestions would be welcome.

Thanks,

D

---

