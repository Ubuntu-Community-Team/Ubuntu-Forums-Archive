---
title: "anyone used the emachines m6810 model?"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by sal on 2006-02-25
im buying an emachines m6810 laptop and was wondering if anyone here has used it with ubuntu/kubuntu? if so what was your experiance?

here is what im wondering:

which versin would be best to load on it, Ubuntu or Kubuntu (which would work better) 

which architecture x86 or AMD64 worked the best on it

would it be a better idea to run the current Dapper on it (if so which version x86 or AMD64)

how well is the 802.11g handled on it by ubuntu/kubuntu

how well is the power managment on it (such as suspend/hibernate)
how well is the battery life on it (how long can it last)

and any other things you might now about the model and its use with Ubuntu/Kubuntu

Thanks for all the info in advanced

---

### Post by salocinbake on 2006-03-27
My humble experience on Ubuntu, and my M6810:

Ubuntu 5.10 works flawlessy. Ndiswrapper is easy to install with the bcmwl5.inf driver.

I prefer Kubuntu, but I have a lot of networks issues. eth and wlo. I am no expert, so I reverted back to Ubuntu.

I try the latest 64 bit from Kubuntu (flight 5), very buggy for this laptop. Still network problems.

I tried amd 64 of ubuntu 6 months ago, but found that there was a lot of drivers or applications not up-to-date for the 64bits world. One game I wanted was not available, so I switch back to Ubuntu.

Salo

---

### Post by Joshefson on 2006-04-14
I am using Ubuntu 5.10 on an emachine M6811 which should be very similar to the M6810.  

I have used SusE 10.0, Fedora Core 4, Fedora Core 5, and the 64-bit version for all 4 distro's. 

64-bit is still way too buggy with all distro's and I had alot of driver issues.
32-bit is the way to go for now.

All function keys work with a fresh install as well as volume, media player, and internet buttons.

as salocinbake said Ndiswrapper installed the bvmwl5.inf driver flawlessly.

I have not checked the Hibernation etc... since my ATI driver install today but ATI claims that it should work.

The only problem I had was getting the ATI driver installed but today I finally found a working guide and can now play COD Guild Wars and UT2004 flawlessly.
Here is the link for ATI Driver install on Breezy and Dapper: [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") 

I hope this helps

---

### Post by salocinbake on 2006-04-21
I finally got the Ati card to work with ubuntu 5.10, you can use the xorg.cong file in the link below. It's a mobility Radeon 9600. 

Next it's to get the modem working...


[Here]("http://www.ubuntuforums.org/showthread.php?p=935431#post935431")

---

### Post by salocinbake on 2006-06-04
I upgraded my M6810 from Ubuntu 5.10 to Dapper,

My issues; I had my ati driver installed [with this method]("http://www.ubuntuforums.org/showthread.php?t=75378&page=36"), but crashed the X window on start up. So did a fresh install.

Installed afterward the ati driver with no problem [with the method above]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide").

Wireless, I could not make it work with ndiswrapper, but [this method]("http://www.ubuntuforums.org/showthread.php?t=185174") works actually better than my windows or ndiswrapper. 

I used bcmwl5.ini driver.

Great distro.

---

### Post by salocinbake on 2007-03-22
Update on my Emachine M6810, I still use Ubuntu, but now I upgraded to 6.10. 

Very easy now, wireless works [with this method]("http://www.ubuntuforums.org/showthread.php?t=185174"), sound as well. Graphics are good also with the original install.

Small note for the wireless, sometimes the blue wireless light will not light up, and no connection as well. I reboot to Xp, the when I return to Ubuntu, it works. There is probably a simpler way, but it's my fix

I can't seem to see other wireless network, but input the SSID and password, then reboot.


Salo

---

### Post by salocinbake on 2007-04-07
Update Feisty:

I started using Ubuntu Feisty (7.04) in March 2007, So far pretty impress. I used the 32 bit version.  (i386)

Wireless:  I don't recall if I needed to do anything to get the wireless working. I upgraded from Edgy, so Fwcutter for the wireless is probably still active. The new network manager is working, I can finally use my laptop on the road, without pulling my hair to get connected in Wifi spots.

Graphic card (Mobility 9600) : I was able to get beryl working, this is soo great!  I use this ["how to"]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon").

"Specials" key works, sound, internet, e-mail, etc.

This would apply also to M6805 M6807 M6809 M6811 , since they share the same motherboard.

Hope this helps,  ;-)

Salo

---

