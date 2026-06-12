---
title: "Unable to install Restricted Drivers for Nvidia card."
date: 2010-08-06
forum: Hardware
---

### Post by bikalpapaudel on 2010-08-06
I just installed Ubuntu 10.04 32-bit on an external hard drive. While I was running Live CD mode, I was notified of the availability of restricted drivers for my card on the top left of the upper menu bar. Since it was Live CD mode, I did not care much about it. 

Now that I am running Ubuntu installed on my external, it does not show me any alerts on the availability of restricted drivers. I am, of course, connected to the Internet. 

One would then think of going to *System* > *Administration* > *Hardware Drivers*. I did. But clicking on Hardware Drivers icon gives me a small dialog box that says "**Downloading and updating package indexes**". And guess what? Upon completion of whatever it meant to do, it just closes. 

Here's a screenshot of the dialog box that comes up and abruptly closes, giving me nothing. 

[IMG]http://img375.imageshack.us/img375/714/screenshotdf.png[/IMG]



I DO NOT get the regular "Hardware Drivers" window that would alow me to select and install the requisite drivers. 

Every time I click on the Hardware Drivers option, it's the same story. The window that I expect never comes up. 

Tried purging the default open source driver of Ubuntu (Noeveau or something). Still does not work. 

I have Nvidia GeForce _FX 5200_ 128 MB driving an AOC Fovi F22 at _1920x1080 _via VGA D-Sub. And the GUI (windows and everything) runs pathetically slow, being just barely usable. 

Any help?

---

### Post by bikalpapaudel on 2010-08-07
Uh. I think I got it right, now. 

What I did was, I changed the server from where Ubuntu downloaded updates, thinking that the Nepalese servers might have some problem I used the option that allowed me to test for the best server, it pointed me to one from Singapore and subsequently updated the source list. 

Then, I selected "Hardware Drivers" and voila -- it said "Searching for available drivers" and then took me to the Window that allowed me to choose a Nvidia driver for my card!

Hope it does help somebody else with a similar problem.

---

