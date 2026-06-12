---
title: "Save settings on startup?"
date: 2009-01-10
forum: Hardware
---

### Post by Naughty 240 on 2009-01-10
I have ubuntu 8.04 installed on an IBM Thinkpad (Model Number 1830 RM5) and the battery life is a little shorter than the XP that used to be on it (about 20 minutes). I can get about 2 hours use out of it (Msn, music, wireless) until it gets to about %5-%10 charge, at which point i recharge. I have downloaded Powertop and apply the things it suggests, but after a reboot it goes back to the default settings, also i have discovered my video card (M7 mobility radeon 7500 32mb) isnt supported by 8.04 so cannot activate powerplay. I have stumbled upon rovclock, and just like powerplay when i reboot it goes back to defaults. I currently have changed the cpufreg governors to run at slowest speed on battery power, and ondemand on AC, and have disabled unused ports in BIOS and all together that has increased battery life by 40minutes. I believe if i can keep the clocks of the video card down then i can match, or surpass the battery life i used to get in XP.
I am quite new at Ubuntu so im no Guru lol.

BTW great forum you have here, it has answered many of my questions ive had during my initial setup.
Thanks.

Ryan

---

### Post by tuxxy on 2009-01-10
It will be a difficult task to have it match the battery life that XP will achieve, Windows is still more efficient at power management which is resulting in your shorter battery life.  I dont think 20 mins is too bad though having seen much worse figures in the past.

---

### Post by Naughty 240 on 2009-01-10
Yeh i know, i guess im one of the lucky ones as ive seen some people only being able to get 1 hour from their batteries. I still believe if i am able to make the rovclock settings startup i will be able to save quite a bit of power, as in windows i think it gave me an extra 30minutes of time, compared to the card running at full tilt. 
I dont mind if it was only 1 and a half hours if i have everything applied, but i know i can further improve it, but i need to know how to make powertop and rovclock start automatically.

---

### Post by iggykoopa on 2009-01-11
you could try my power management gui here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . It doesn't have an option for rovclock but I could add it in if you want. If not you could write a shell script with the rovclock command then make it executable and add it to preferences-> sessions . Also it's recommended to keep the cpu governor on ondemand for all modes because it will allow processes to complete sooner and your cpu to go back to a deeper sleep state sooner saving more power.

---

