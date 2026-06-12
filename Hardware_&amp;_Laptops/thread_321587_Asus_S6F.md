---
title: "Asus S6F"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by FrankVdb on 2006-12-19
I ordered a nice Asus S6F laptop, which I will be using for professional purposes.

I'll be I'll be installing Ubuntu 6.06 on it. My question is: what kernel do I need for the Core Duo LV2300 processor the S6F carries?

The graphics card is an Intel 945GM. Is there anything I should particularly consider? 

Thanks in advance.

---

### Post by whoismilan on 2006-12-19
It will run on the default Ubuntu kernel, and for 6.06 there is also a seperate 686 SMP kernel (available in the repositories).

For the graphics card you will probably need to install and configure 915resolution in order to get the wide-screen resolution that laptop looks best in.

[QUOTE="Hermelinen, https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelmate3012WTMi"]
The resolution on this baby is 1280x800 which is not recognised by driver since it can't get the information from the BIOS. Instead you get the default 1024x768 which looks weird. This is easily solved by enabling your universe repositories and installing 915resolution. Now you need to edit the file /etc/default/915resolution. Find a free mode by issuing the command 915resolution -l. Then set "MODE" to the free mode you found, "XRESO" to 1280, "YRESO" to 800 and "BIT" to 32. That's it![/QUOTE]
NOTES:
- This is written for another laptop, but if you change 1280x800 to 1366x768 (which is the native resolution of the S6F), it applies for the S6F also
- By "free mode", he means an existing mode which you don't need.

Also see this for laptops with similar hardware as yours: [https://wiki.ubuntu.com/LaptopTestingTeam/Asus](https://wiki.ubuntu.com/LaptopTestingTeam/Asus)

---

### Post by FrankVdb on 2006-12-20
Thank you very much, that is very useful!

I've saved all your info, as soon as I have my laptop (delivery delayed until end of next week...), I'll let you now if the install worked out.

Kind regards from Belgium,
Frank

---

### Post by davmac on 2007-04-30
Frank,

How did it all work out? I've been happily running 6.10 on my S6F for a while now. I upgraded to 7.04 at the weekend and some things have stopped working, but generally all OK. The only thing I haven't been able to get working is the card reader.

Dave Mac

---

