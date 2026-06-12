---
title: "[SOLVED] Toshiba Laptop Woes"
date: 2008-08-18
forum: Hardware
---

### Post by ktechman on 2008-08-18
Cheers everyone,

            I just purchased a Toshiba A305-S6864 and there are a couple of problems that I have experienced with it under Ubuntu.  First the wireless card does not function even though it "sees" my router it will not connect with it.  The chipset is the new Atheros AR9281 using the ath9k driver.  I have a feeling that this issue will be solved by the Atheros team in short order but if anyone has a solution I would appreciate the help.  Second the function keys for the "Sound" under the "escape" key and F6 and F7 work for the brightness "up" and "down", the rest F1=lock, F2=PowerPlan F3=Sleep(causes kernel attack), F4=Hibernate, F5=Output(Laptop screen or VGA), F6 & F7=Brightness(both work)F8=Wireless, F9=TouchPad, SpaceBar=Zoom do not function.  If there is a solution to this problem please point me in the right direction.

            Thank you, Ktechman

---

### Post by go_beep_yourself on 2008-08-18
This guy got that laptop to work. Try searching the forums next time.

[http://ubuntuforums.org/showthread.php?t=834640&highlight=A305-S68641](http://ubuntuforums.org/showthread.php?t=834640&highlight=A305-S68641)

---

### Post by ktechman on 2008-08-18
I have been all over the forums and beyond and I wouldn't post without having looked at this forum and others first.  The post from the above has no details whatsoever and his last visit to the forum was in early July.  He did not mention if the function keys even work.  Do you have any ideas?  Cheers Ktechman:)  The above laptop A305 is a model 6843 with an Intel wireless card not a model S6864 with the new Atheros AR9281 Wireless card I have done my homework.  Thank you for your input "Beep_yourself"

---

### Post by ktechman on 2008-08-18
Bump

---

### Post by aron23 on 2008-08-19
I have the same problem

I first tried building a kernel to support ath9k in kubuntu but was in way over my head.  Next I tried the deb here - [http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097) again with kubuntu had no luck - the kernel fromt he deb would not even boot

Last night I almost succeeded with the deb from the link above using ubuntu rather than kubuntu - this time I could see wireless networks but I've yet to get it to connect, a couple of times I was able to get wicd to display connection bars but it was not able to actually access the internet.

Some of the gotchas I've been able to get around include:

the lockup during install which required me to turn off the LAN in bios (works fine after install so you can turn it back on and boot)

network manager does not recognize the wireless card which required me to install wicd

I would love to have a functional install of ubuntu on my laptop but seems we must wait for ath9k development to mature...

---

### Post by CheeseEatingBulldog on 2008-08-19
I have a Toshiba Satellite as stated in my sig and can say that the wireless card did not work out of the box and in the end I just installed ndiswrapper, which works fine, there is even an automated ndiswrapper up these days [https://launchpad.net/auto-ndiswrapprer]("https://launchpad.net/auto-ndiswrapprer"). The function keys are a bit of a pain, and to be honest I have installed ubuntu on multiple laptops but have never gotten any of them to sleep/hibernate without having them go into meltdown. Still waiting for fixes on that.

---

### Post by aron23 on 2008-08-19
The A305-S6864 has a new 802.11 N card which I was only able to access at all with ath9k, ndiswrapper did not work at all and ath9k is the active development effort from the chipset maker and the folks at madwifi - regardless my wireless won't work...

---

### Post by ktechman on 2008-08-19
I am going to perform a complete reinstall to see if it makes any difference.  I think that I tried every driver that was even remotely associated with this laptop so I could have a conflict somewhere.  Thank you everyone for your input and if anyone has anything new please post it here.   Ktechman

---

### Post by ktechman on 2008-08-19
Here is what I've found that after a fresh install of Hardy, and the installation of the compat-wireless package that the driver installs and identifies my hardware and even communicates with my router but the wireless card on the motherboard does not receive any communication from the router.  I came to this conclusion after looking at my routers system log.  Hopefully there is someone monitoring this and other forums that will add this missing element and repair this problem.

---

### Post by TrevorPace on 2008-08-25
If you are still having this problem I recently had a similar problem. First off search the Ubuntu help for a page on the internet and find out how to disable IPv6. Second make sure that you have left all the connections in Network Configuration to Roaming and that there are no checks beside the any of them.

Also make sure that the switch on the front of your computer for wireless is set to on...that gave me a few headaches.

---

### Post by ktechman on 2008-08-26
TrevorPace Do you have the same laptop?????  Ktechman

---

### Post by TrevorPace on 2008-08-26
No, I've got an A-300. But it is very similar. It might have the same kind of wireless card though.

---

### Post by ktechman on 2008-08-26
The chipset on my laptop is an Atheros AR9281 and is only supposed to work under the ath9k driver which is not complete yet. How about your chipset, which one do you have? and which driver are you using?

---

### Post by Frettbottx on 2008-08-26
hey guys, im using toshiba L40 laptop, mi dualbooting vista and linux. my wifi card is rtl8187 and i solved my wifi problems here : [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)


hope this helps! :)

---

### Post by ktechman on 2008-08-26
I believe that is one of the Realtek chipsets not the atheros, atheros is under development thank you for your reply.  Ktechman

---

### Post by ktechman on 2008-09-15
Anyone with the Toshiba A305-S6864 laptop which has AR9281 wireless chipset this post [http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3) worked for me, even after a hard restart.  Many thanks to "Volanin" for the help.         Ktechman

---

### Post by latchekeyed on 2008-11-05
> **TrevorPace said:**
> 

Also make sure that the switch on the front of your computer for wireless is set to on...that gave me a few headaches.

Thank you, that was much appreciated.

---

