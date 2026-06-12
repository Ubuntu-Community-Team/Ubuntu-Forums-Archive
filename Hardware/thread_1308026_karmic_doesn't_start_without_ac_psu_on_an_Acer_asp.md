---
title: "karmic doesn't start without ac psu on an Acer aspire 9301"
date: 2009-10-31
forum: Hardware
---

### Post by mvalero on 2009-10-31
A big hello to all the memebers of this excellent comunity, this is the second release of Ubuntu that I use, I'm so happy and impressed that I'm trying to show ubuntu to other people, as much as I can.

Anyway, straight to the point, I performed a fresh installation over v9.04 because it had problems with the graphics card (nvidia geforce go 6100) and the audio card, I think that I'm not the only one with problems with alsa drivers.
Karmic koala installed perfectly, nvidia driver installed ok, all the software installed without any problem, and I'm so happy, but...
Yesterday, I turned the computer on (no AC power source connected), guess what? booting process didn't past the logon image! That is, I introduced the password and logon window dissapeared but the image (the one that resembles a stage) didn't go away nor changed, the computer is not blocked (I can move the pointer and pressing numlock does turn on and off the numlock led), it just seems to be waiting for something.
Might it be trying to start some of the services related to the battery or the power supply? I really don't know, I just know that after waiting over half an hour to see if it continued to boot (might show some error, even), it stayed there. Conecting the the AC psu didn't help at this time, I had to conect the AC and reset the computer (powering off ad the on again).

I don't know if someone else has this problem, but it might not be related to the laptop.

My configuration is:
Acer Aspire 9301
Turion 64X2 @ 2.0GHz
4GB of ram
500GB HD
Nvidia GeForce Go 6100 (up to 256MB of shared ram)
DVD/CD Double layer Writer/Reader
Internal Audio card (don't remember wich one)
Nvidia Chipset
Wireless card B/G
Acer Orbicam webcam
Internal modem
Internal Ethernet card
Internal card reader

All the hardware is working properly! If I let the laptop start with ubuntu and AC power conected it continues to function properly even if i disconect the AC power (while is working), but it refused to continue working after the login screen if there's no AC power.

Thanks for your help! And if you're using 9.10 with a laptop or notebook, try to use ubuntu without ac power.

---

### Post by mvalero on 2009-11-02
So? Am I the only one that has troubles with its laptop to start Ubuntu v9.10 without AC power connected?
Can someone please confim? Any one who has a laptop/notebook/netbook and can use 9.10 powering only on battery.
I just want to know so I can make some other tests to see if some "service" is expecting something and that's why the computer just does not pass the login splash screen.

---

### Post by Jose Taza on 2009-11-22
Your Not alone! I have exactly the same problem with my Acer Aspire 9420. On 9.04 no problems of such kind but now on 9.10 this weird bug! I have checked the system logs to see if there was some kind of a clue but couldn't find anything.
So my search continues. I hope we are not the only one search for a solution...

---

### Post by mvalero on 2009-11-28
Ah! Thanks for your reply Jose, I felt alone here! (Somehow, I just don't know why) Anyway, I was mostly sure that this wasn't a problem only for me, and also I didn't have any problem with v9.04, I think it should be about a service related to the power suply module/battery monitoring/initializing, I don't know enough about linux, but I'm pretty sure that the system is expecting always to find the power supply attached, I don't know if it is just related to Acer laptops/notebooks, it seemed to me that this was not the case, so I came here to look for some help...

I might try to learn some inner working for linux...

Thanks for your information!

---

