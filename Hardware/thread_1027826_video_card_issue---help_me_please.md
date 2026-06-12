---
title: "video card issue---help me please"
date: 2009-01-01
forum: Hardware
---

### Post by diver_ryanc on 2009-01-01
Hello everyone and thanks for reading this.  I am an ubuntu virgin and am having a problem with my video card.  I just wiped a HP Pavilion dv4310us clean and put ubuntu on it.  The previous operating system was XP but had some bad nasty virus rendering it unusable.  Everything has gone fine so far for the switch (i am actually using the machine right now) except i am having problems running a game i play on here.  Used to play it all the time on this laptop with xp and the laptop meets all of the system requirement for the game (EVE ONLINE) as well as ubuntu.

When i downloaded the EVE application it came with a eve online configuration application.  Within this application there is a system test check which my laptop passes everything except 3d acceleration test.  The test results say my graphics card does not appear to be setup correctly. Please check the documentation for your linux distribution and your graphics card drivers to ensure proper installation.  The graphics card in an Intel 915GM (512mb).  I know thats no rocket but it worked before xp locked up and i switched to ubuntu. 

If anyone can tell me what i need to do or load and/or how to do that i would be a very happy person.  The application for the game loads but the graphics are all scrambled and i cant read anything.  Please keep in mind that while i dont think im an idiot (opinions may vary) im going to need some very explicit intructions on ubuntu as i have approx 4 hours lifetime experience with linux.

Happy new year.

---

### Post by linux_tech on 2009-01-01
Start Synaptic, (System>Administration>Synaptic Package Manager)
Type i915 into the search box.
when you select it it will say
X.Org X server -- Intel i8xx, i9xx display driver
If it is already installed it will have a green box
If it is not installed, then check/mark for installation to install it.

---

### Post by linux_tech on 2009-01-01
Also check to make sure your system meets the Minimum System Requirements:

    * OS: 32 or 64 bit Ubuntu 7.04 or higher, Linspire 6 or higher, OpenSuSE 10.2 or higher
    * CPU: 1.1 GHz
    * Video: 64 MB NVIDIA GeForce FX class card or better, ATI graphics cards are not supported.
    * RAM: 512 MB
    * HD space: 6.0 GB or more 


Recommended system configuration for running EVE-Online:

    * OS: 32-Bit Ubuntu, OpenSuSE, Linspire
    * Video: NVIDIA GeForce 6XXX series card or better, ATI graphics cards are not supported.
    * CPU: 1.5 GHz or better
    * RAM: 1024 MB
    * HD space: 6.0 GB or more
    * Alsa supported soundcard

---

