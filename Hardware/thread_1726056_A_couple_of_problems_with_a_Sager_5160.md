---
title: "A couple of problems with a Sager 5160"
date: 2011-04-10
forum: Hardware
---

### Post by christophski on 2011-04-10
I bought a Sager NP5160 from PC Torque as I was told that Sager laptops were the laptops that System76 used so I assumed it would work. Apparently I was wrong! I ordered it from America and had my Uncle ship it all the way to England (Still £400 cheaper than ordering a laptop of the same spec in this country).

First the Wireless does not work. I'm not really sure how to find out what network card I have either... However the Bluetooth does work and I'm pretty sure it's a combined Wi-Fi/Bluetooth card so I'm not sure what is going on there.

Secondly, The graphics are a state. It has Nvidia with Optimus which I've read is a nightmare but I just want to use compiz. Is there some way to just get the Nvidia card working? I don't care about switching graphics cards.

---

### Post by beew on 2011-04-10
> **christophski said:**
> 
Secondly, The graphics are a state. It has Nvidia with Optimus which I've read is a nightmare but I just want to use compiz. Is there some way to just get the Nvidia card working? I don't care about switching graphics cards.

No unless there is a BIOS switch to disable Optimus and choose the discrete graphic card. If all you want is Compiz your graphic demand is very low and there is no reason to pay extra for a Nvidia card (Compiz works perfectly in my  6-7 year old laptops with just old intel graphic cards though with Optimus even the Intel card may not support 3d acceleration)

With Optimus Nvidia basically stops supporting Linux on laptops. I believe most Linux laptop users are like you in that they don't really care for gpu switching, all they are asking is that Nvidia provides a way for them to use the card that they pay for and Nvidia supposedly supports by providing Linux driver (which wouldn't work if Optimus is enabled though the card is "supported"). This is not an unreasonable request.

If you have some time add your voice to the chorus.

[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

---

### Post by christophski on 2011-04-10
Yeah I know the graphics card is a bit overkill but there wasn't an option to not have it so I thought it wasn't a big deal, I was very wrong! Whenever I try and turn on compiz it asks me to install the restricted drivers which do not work. How do I tell if I am using the Intel card of the Nvidia card? 

I managed to fix the Wireless, turns out I have a Realtek 8176 and I followed this tutorial: [https://answers.launchpad.net/ubuntu/+question/132667](https://answers.launchpad.net/ubuntu/+question/132667)

---

### Post by beew on 2011-04-11
> **christophski said:**
> Yeah I know the graphics card is a bit overkill but there wasn't an option to not have it so I thought it wasn't a big deal, I was very wrong! Whenever I try and turn on compiz it asks me to install the restricted drivers which do not work. How do I tell if I am using the Intel card of the Nvidia card? 

I managed to fix the Wireless, turns out I have a Realtek 8176 and I followed this tutorial: [https://answers.launchpad.net/ubuntu/+question/132667](https://answers.launchpad.net/ubuntu/+question/132667)

You are on the Intel Card because there is no way to use the Nvidia card unless you have the BIO switch. But the Nvidia card is still draining resource and producing heat even though you can't use it. That's why Optimus is such a travesty for Linux.

The INTEL card alone would have been sufficient for Compiz (its driver is open sourced so it is included in the kernel), but with Optimus it has turned into a hybrid so perhaps you can't use it for 3d acceleration without installing driver for the Nvidia card, but the driver would not work in Optimus. Sorry to say this, but it means you are screwed.

Try to take your computer back for a refund or an exchange if that is still possible, and please write a letter to Nvidia  [http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278) 
This needs to be addressed. (and probably should write to the laptop manufacturer as well to ask for a BIOs switch)

P.S. If you can't return the desktop try this thread[ http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus") Seems to have a way to disable the Nvidia card and turn it to an expensive paper weight so it at least doesn't use up ssytem resources but I don't know whether you can use Compiz with the intel card that way.

---

### Post by christophski on 2011-04-11
Thanks for the reply, I managed to turn off the NVidia card usign that script and it has made the laptop a LOT quieter! Before I could hardly hear the DVD I was watching over the sound of the graphics card and DVD drive combined aha.

If I run compiz --replace in a terminal I get 
> Blacklisted PCI ID 8086:0116 detected

Is this likely something I can work around or something that will be fixed in the future?

edit: I have sent an issue to NVidia. Here's hoping they do the right thing...

---

### Post by christophski on 2011-05-02
The wireless issue is now fixed with 11.04 and compiz is now able to run in 11.04 also. 
However, I now have an intermittent crash for no apparent reason, I think it may have something to do with Glib as it spits out loads of errors into .xsession-errors but nothing in the system log.

---

### Post by ephman on 2011-05-17
try running the proprietary nvidia driver.  might help ya with your crashing.

be well,

ephman

---

