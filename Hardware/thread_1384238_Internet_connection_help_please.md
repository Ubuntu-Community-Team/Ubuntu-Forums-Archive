---
title: "Internet connection help please"
date: 2010-01-18
forum: Hardware
---

### Post by chris0108 on 2010-01-18
Just started using ubuntu 9.10, feed up with the microsoft rubbish, really good software just having one small problem, im running ubuntu on my laptop, its fully installed yet just off the disc, all works fine, when i go to connect to the internet (via a belkin pcmia card), click on the top connection bit and it shows 5 wirless connections, i click my own wireless connection and off it goes, it then asks for the password, i put this in and after awhile it asks for the password again? I thought i had put the wrong password in but another laptop running (sorry) windows uses the same password and find the connection just fine.
Is there something im doing wrong?
Oh yeah, used the hardware checker and it says the belkin card is working just fine.
Any help would be excellent, many thanks Chris

---

### Post by pi/roman on 2010-01-18
> **chris0108 said:**
> running ubuntu on my laptop, its fully installed yet just off the disc,

I'm confused by this. Are you saying that it is running from the hard drive or from cd/dvd?

---

### Post by chris0108 on 2010-01-18
Sorry, its running from a cd. I have yet to install it fully

---

### Post by pi/roman on 2010-01-18
I'm not sure if it will fix it, but I was having problems saving my connection information until I installed it to the hard drive.

---

### Post by chris0108 on 2010-01-18
I did wonder about that, thank you i will install it and have a go from there.

Can i ask, did you get rid of windows when you installed ubuntu?

---

### Post by pi/roman on 2010-01-18
I did not set up a dual boot myself but there is a guide for it here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by chris0108 on 2010-01-18
Iv done it as a single installation of just ubuntu but it still does the same.
I have just noticed something though, it shows a few wireless connections but they all have just one bar for signal strength, the reason i say this is on the other laptop it has full signal strength?

---

### Post by pi/roman on 2010-01-18
Mine seems to display a lower connection signal too.

When I first set it up with a network key it asks to allow the network manager access to the key, then I have to supply a seperate password to allow access.  So each time the computer boots up I supply the password to access the network key just once and network manager has access to the keys for the entire session.  But if it loses connection it should reconnect automatically without supplying the password again.

---

### Post by chris0108 on 2010-01-18
Think its just gone completely wrong, it doesnt save the password for the wireless connection (which i know is correct) it wont log into the connection and now it doesnt like booting up!

Can i have installed it wrong??

---

### Post by pi/roman on 2010-01-18
[FONT=Verdana]You could run a checksum on your installation cd or iso to make sure it is not corrupted.  Instructions are here:
[https://help.ubuntu.com/community/HowToMD5SUM#md5sum](https://help.ubuntu.com/community/HowToMD5SUM#md5sum)

To check your cd just go to your cd drive "cd /cdrom"
then check it by [/FONT][FONT=Verdana]"md5sum -c md5sum.txt | grep -vi 'OK$'"[/FONT]

---

### Post by chris0108 on 2010-01-18
think the installation is ok?
Think i may also have found the problem, but i need some help here.
I need to put some realtek 8185 drivers on it for the belkin card to work, but it tells me i need to use ndiswrapper, what is ndiswrapper and what do i need to download?

Im getting quite lost and confused with it all now :(

---

### Post by pi/roman on 2010-01-18
ndiswrapper is a utility which reads changes windows commands to linux commands so linux can use windows drivers.  I'm not sure how to use it because I never have so hopefully someone else can help you with it.

---

### Post by chris0108 on 2010-01-18
Thank you for that, you wouldnt know which version i need?

---

### Post by pi/roman on 2010-01-18
There is a guide for it here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

There are also some guides in the forum you can find though googling but I'm not sure which ones would be most suited for you.

---

### Post by chris0108 on 2010-01-19
Thank you for that, iv nearly got it sorted.
Iv installed everything and now the network light on the pci card comes on (huray!) but not for long :( think i know what iv done though, the forum has information about the driver i need for my card, iv downloaded the vista version and ubuntu doesnt seam to like it, so lets download the xp version and see what happens

---

