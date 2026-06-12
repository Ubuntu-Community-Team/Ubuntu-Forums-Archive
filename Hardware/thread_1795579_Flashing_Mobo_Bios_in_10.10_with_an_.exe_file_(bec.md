---
title: "Flashing Mobo Bios in 10.10 with an .exe file (because I sort of have to)"
date: 2011-07-02
forum: Hardware
---

### Post by nooodles on 2011-07-02
I'm stuck.... Back reading isn't covering what I'm after...
In short - any good advice on how to install a .exe BIOS update from a live 10.10 USB Thumb Drive?

Laptop (Toshiba Satellite A21 -> psafgc-ms608c ) seams to have a BIOS in trouble.

System Seldom boots.  When it fails....it does nothing visual on the monitor.  The monitor is on..but remains blank with no audio que's.

Repeated attempts MAY get a lucky hit and the system tries to boot.
When it does, the windows OS on the system gives a CMOS error in white text on black screen and stops.  Period.  Reboot required for anything else.

I did get into the BIOS - hit a 'reset to defaults'...the BIOS did not repsond that great. 
example: changing the boot order resulted in the 'blanking out' of options being pushed down.  Changing menu's and returning refreshed the screen and the options cold be read again.


Put ubuntu 10.10 live USB thumb drive in - and hit the power button for 2 days - and presto - Ubuntu is running - Data Backup done!

I downloaded a BIOS firmware - have it on the system. It's a .exe  
I opened it and see that there's a .vbs file that manages the actual .exe utilities... but now I don't know if there's really much more I can do.

Please note - the Optical drive is down (has been for months).

I'll be back in the morning to try to take this further.
Thank you much.

---

### Post by scu-ba-de-buntu on 2011-07-03
interesting. are you SURE its not a hardware problem? the sometimes boot part makes me think its hardware and not your firmware.

usually a BIOS patch is probably not a Win32 executable, but a high-bit dos one if that. The vbs comment is interesting though. I would find out what are the requirements for it, make SURE its integrity is sound, and not mess with anything but what it was written for. 

alternatively, if it is worth saving, bring it to your local repair guy/gal who should be able to make it like new for you whether its a hardware problem or not. (not some chain, as they tend to be less experienced with actual repair in my experience)

---

### Post by nooodles on 2011-07-03
Morning and thanks for the reply.

> interesting. are you SURE its not a hardware problem? the sometimes boot part makes me think its hardware and not your firmware.Well, I guess that's two options there.[INDENT]A ) It's the mobo and I try Flashing the BIOS for that magic hail mary try.
B ) It's the mobo (or even something else), and I don't try.  (Multimeter around the machine is outside my skill level/time constraint...)
[/INDENT]>  usually a BIOS patch is probably not a Win32 executable, but a high-bit  dos one if that. The vbs comment is interesting though. I would find out  what are the requirements for it, make SURE its integrity is sound, and  not mess with anything but what it was written for. I hear you.  The Toshiba's are.  (Also, the Toshiba website does not play with Linux;
[http://support.toshiba.ca/support/Download/ln_byModel.asp](http://support.toshiba.ca/support/Download/ln_byModel.asp).  )
The .exe file for this laptop (It's a laptop in case I didn't say) was direct from Toshiba's website.   Once opened it has 14 files:
```


[LIST]
[*]FindWFlash.exe - HKeyOff.exe  - m10a200.rom - mfc42.dll - msvcp60.dll -  msvcrt.dll - PHLASH.INI - Phlash9x.vxd - PhlashLc.dll - PhlashNT.sys - PowerStatus.exe - Waiting.exe - Wflash.vbs - WinPhlash.exe
[/LIST]

```> 
alternatively, if it is worth saving, bring it to your local repair guy/gal who should be able toammm....nooo... Sorry, but no. I'll resolve it without a shop.  My skills be good, just not ubuntu flashing the bios good.  Tho I am hoping to change that :guitar:

I can't see it being the CPU...Ram... Power supply...or the Chipset.   
The hard drive is a month old, and running Bit Defender from Ubuntu came up clean...for what that's worth..
Don't know enough to rule out a fat capacitor or those type of issues (which obviously I will not be able to correct with a flash) that could cause these symptom.

So I'm looking square at the BIOS.
But I don't think I can run the flash from Ubuntu.  At least, not very easily...
Searching here I've found a few threads on the topic, but they all diverged into different directions before actually trying to flash.

I can try a Dosdisk...but with no optical drive, and a system that possibly take days between every successful boot...reinstalling windows would ruff.

---

### Post by MartyBuntu on 2011-07-03
> **nooodles said:**
> 

Well, I guess that's two options there.[INDENT]A ) It's the mobo and I try Flashing the BIOS for that magic hail mary try.



FWIW, this doesn't sound like a problem that can be fixed with a BIOS update. It's most likely a hardware failure.

Flashing the BIOS on already shaky hardware is a *bad* idea...

---

### Post by nooodles on 2011-07-03
> **MartyBuntu said:**
> FWIW, this doesn't sound like a problem that can be fixed with a BIOS update. It's most likely a hardware failure.

Flashing the BIOS on already shaky hardware is a *bad* idea...


Try and against all odd's it works!  AWESOME!
Try and fail however is the same as not trying and failing, but without learning anything.


So if anyone has some direction?
I've thought of WINE, but my trusted buddy failed repeatedly with a Dell system that was 'ubuntu supported' (seams an updated library broke Dell's flash utility...which they never updated...because their Dell...
[rant]-->> YOU HEAR THAT MIKE!  This is part of why your company has dropped to 3'rd and fighting not to go to 4'th - because you don't take care of the customer [/rant]

---

### Post by scu-ba-de-buntu on 2011-07-03
> **nooodles said:**
> Try and against all odd's it works!  AWESOME!
Try and fail however is the same as not trying and failing, but without learning anything.

Its not quite the same, as if your BIOS update doesn't update correctly, you have what is called a brick. Now, sure it is POSSIBLE to unbrick a system, but it requires either a solid working knowledge of the system, the datasheet for the chip (bios memory) and reflashing it with a programmer, and maybe some crazy JTAG skillz.

Make sure its not the caps. athey like to go out of style. there may be a bulge on them or some crap on their top. this is only for the big ones. the small package, surface mount ones are harder to tell.

It really doesn't sound like it is a BIOS software issue. Maybe the chip has physical junk on it, but not software. If it works sometimes, the data is (i would guess) there.

> **nooodles said:**
> 
So if anyone has some direction?
I've thought of WINE, but my trusted buddy failed repeatedly with a Dell system that was 'ubuntu supported' (seams an updated library broke Dell's flash utility...which they never updated...because their Dell...
[rant]-->> YOU HEAR THAT MIKE!  This is part of why your company has dropped to 3'rd and fighting not to go to 4'th - because you don't take care of the customer [/rant]


I thought WINE, but I doubt it will convert lowlevel requestes such as what that program will do. WINE is amazing, but it is really best at GUI call conversions. Wine is not an full emulator, it converts calls.

Likewise, even if you could run it in dos, I would also stay away from DosBox, or emulation without direct hardware access as it will just virtualize the hardware you are trying to talk to.

PS. Who is mike?

EDIT:
also, i am thinking that your VB file and MFC stuff may only act as an GUI interface for calling the actual updater

---

### Post by nooodles on 2011-07-03
Thanks for the reply...

First off - Who is Mike = Michael Dell.
Some of the things Dell did (after Mike left as CEO - to be fair), made it Reeealllll easy for me when I worked at HP to push ahead of them... Such as bla bla and bla bla bla...etc..etc.. and so on...:popcorn:


I hear about bricking the system.
I guess what I'm thinking is - the system isn't working now...so if it's bricked...no big loss..  I'm not big on having capacitors replaced on a board.  I feel that if one goes...then there are others heading that way too....  

I agree about emulators (yes, WINE is not an emulator...).  
Guess really if I want to flash firmware, I should keep a windows OS around....at least until the desktop monopoly is broken... 

Thanks for the help...I have a plan B so...guess I'll head that way.

---

### Post by scu-ba-de-buntu on 2011-07-06
alright, well post here what your results were so others can benefit especially if it was just a BIOS error. Good Luck!! :)

---

### Post by CMOS4081 on 2011-07-06
Just by reading that the flash utility is a .exe means you have to make a bootable DOS usb drive.

Get the DOS-on-USB from: [http://www.jamesonline.ca/support/dos-on-usb-support]("http://www.jamesonline.ca/support/dos-on-usb-support")

Make a plain dos bootable USB drive, copy the flash util files and pray your hardware is not shot.

---

### Post by nooodles on 2011-07-07
Will do on the update question.

And thanks  for the dos on usb stick link.

This project has been pushed down a couple steps in the priority list.... but not forgotten...!

---

