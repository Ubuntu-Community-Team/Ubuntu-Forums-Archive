---
title: "Problem power down"
date: 2009-12-10
forum: Hardware
---

### Post by pappy on 2009-12-10
Hello
I have this problem with a laptop. When i shut it down it goes to a black screen where it writes this
[1969.215549] Power Down
and stops there without powering down.
The battery is removed from the laptop.
Anyone had that problem and if yes did it fixed?
BTW i have the some problem in 9.04 and 9.10
Thank you

---

### Post by pappy on 2009-12-16
Hello 
Can someone help with this problem? Now when i shut down the laptop 
it goes to a black screen and stays there indefinite. I have to press the power button to shutdown the pc.
Anyone had this problem or has any idea of why the laptop has this behavior?
Thx

---

### Post by hristostoev on 2009-12-16
I have the same problem. Even worse, my laptop shuts down unexpectedly. It shuts when I am using the browsers or other programs. I don't know how to fix it because I am new to Linux, I keep trying it since 8.10 , but I always have the same problem. My fan is just going crazy and the computer gets hot and it shuts down, but sometimes it shuts down when is not hot. There is a message on the screen when I boot in to Linux saying that ACPI is not connected and some timer is not connected. I also have issue with the battery not showing on the panel. 
My computer is Toshiba A210 with ATI radeon X1200 and Turion x 64. 
I am running Linux Mint Gloria and I think it switched back to Ubuntu, because I installed ubuntu studio.
I appreciate your help. Thanks

---

### Post by arvevans on 2009-12-17
"Pappy" seems to have a problem relating to computer power management, while "hristostoev" seems to have something similar, but the symptoms are a bit different.  

OK.  For Pappy...this URL [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") will tell you what the problem is associated with.  You should try searching this discussion group for "ACPI" and will probably find several references to the same, or similar, problems and solutions.  There are some boot-time commands that can force older BIOS/ACPI to work with Linux, and some fixes for newer ones.

For "histrostoev",...Similar problem, but different indications.  Still ACPI related, but in your case it sounds like your PC uses BIOS software to control the fan.  Without fan control your PC heats up and shuts down.  The boot message complaining about ACPI is telling you that it cannot talk to the power management routines, which are part of your BIOS firmware.  You too should do a search on this discussion group for "ACPI" and also one for "fan control" to locate previous discussions and problem resolution for this situation.

The battery monitor not being available on a laptop is also indicative of Linux not talking with the hardware's power management routines.

Arv
_._

---

