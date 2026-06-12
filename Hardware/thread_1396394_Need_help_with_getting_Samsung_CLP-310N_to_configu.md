---
title: "Need help with getting Samsung CLP-310N to configure in Ubuntu 9.10"
date: 2010-02-02
forum: Hardware
---

### Post by Carlo1973 on 2010-02-02
Hi there. 

Having a hard time to get this printer to work in Ubuntu 9.10. It's a Samsung CLP-310N Network printer. It's hooked up to my network via ethernet cable so it's not directly connected to my computer (Printer is in the basement of the house - my computer is on the second floor). Printers IP address is not static but reserved on the router as 192.168.0.199.  I went through the instructions I found at [http://ubuntuforums.org/showthread.php?t=341621]("http://ubuntuforums.org/showthread.php?t=341621"). However I've ran into problems

1) Using CUP - Cups See's my network printer through auto-detection. It even reads the correct toner levels reported by the printer (although the cartridge #'s are all 0's.  - However it doesn't print properly. The printer shoots out a page stating:

> 
SPL-C Error - Please use the proper driver

POSITION: 0x0 (0)

SYSTEM: src/xl_image

LINE: 606

Version : SPL-C 5.35 11-20.2007


2) After Foomatic Install

 - Well foomatic doesn't see the printer at all. It just doesn't detect it over the network, even when choosing network printer option.


3) Using the Samsung Unified Drivers from the website (version 1.0)

- did not see the network printer at all
- broke components that were used in terminal mode
- got several errors with gedit (couldn't read any files)




I'm hesitant to install the version 3.0 drivers described in [http://ubuntuforums.org/showthread.php?t=341621]("http://ubuntuforums.org/showthread.php?t=341621") as the repositories state that they can break the same components that version 1.0 did. 

Is there another way to get this printer running without breaking anything?

Personally I would like to have CUPS running the show - as long as it can utilise the colour print modes.

---

