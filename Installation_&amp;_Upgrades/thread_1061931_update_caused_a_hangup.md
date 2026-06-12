---
title: "update caused a hangup"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by avidsensei on 2009-02-06
so im in the middle of upgrading 8.04~.19 to the latest version when i lose internet connection and so im like well i will just install what i downloaded. so i continue and reboot but after the reboot the login screen comes up i log in all normal like. the desktop flashes i see my background image then it flashes ubuntu brown and just hangs there. i left it running for 30 min just to see if it would make it. nope, it just hangs right there. i tried using the automated recovery and when that did not work i tried using the backup version of ubuntu from grub but they both have the same problem. 

can anyone shed any light?

---

### Post by Partyboi2 on 2009-02-06
Boot into recovery and see if you can finish the upgrade.
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade
```

---

### Post by avidsensei on 2009-02-06
No, dice. My internet requires a browser window to be up for internet access when you close that window it logs you out of the internet. Could I download the packages through windows somehow? or bring up a browser in the terminal?

---

### Post by blade_ on 2009-02-07
Hi!

I had a similar problem. Update finished as much as it could before reboot. While I closed down some apps for the reboot, it froze. No matter what i tried it would not unfreeze, so I had to do it the hard way...Then, upon startup I get all nice reboot screens, but as soon as the log-in screen should pop up I have nothing. I can log in blindly (getting them nice drums and all), but seeing as I cannot use ubuntu blindfolded, that's no good. 

I can access the command line, no prob. So I have tried several tips: 
- sudo dpkg-reconfigure xserver-xorg, default answers only. NO
- Upgrade my graphics drivers. NO
- Your tip. NO.

I am at a complete loss here. Do you have any more ideas up your sleeve? I really need to use my beloved friend of a laptop...

Cheers

---

### Post by blade_ on 2009-06-29
Hi again. I re-installed my laptop, didn't dare to try update for quite some time. But the updates kept piling up and just now I tried it. Download of packages: OK, installation: fine. Reboot....Not so OK. I get the ubuntu start-up loading-bar and then black screen. Same as before. I can log on blindly. But that's just what I am from then, blind. I guess some graphics driver if mesing around with my laptop, but what can I do? This is getting really annoying. Please, help fellas...

Re-installing again...

Give me a shout

//blade_

---

### Post by blade_ on 2009-10-24
Just updating and ending my posting here. 

1. My graphics card: ATI Mobility Radeon X1350
2. The most recent update of Ubuntu 9.04 does not render my screen all black anymore. :KS

Cheers

---

### Post by motsteve on 2009-10-24
That's a heck of a lot of upgrading.  Any chance that you have a /home backup along with a snap shot of your installed packages?  You could try a clean install 9.04 and reinstate everything except for the apps you may have installed from tar balls.  That's what I did when I got Karmic'd (I did a upgrade dist instead of clean).

BTW, I love your avatar.  I have 12 cats inside and the neighborhood strays out.  That's what I get for marrying a Jap. :)

---

