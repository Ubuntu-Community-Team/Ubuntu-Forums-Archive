---
title: "I know this has been brought up already but..."
date: 2008-09-04
forum: General Help
---

### Post by ZALinuxDude on 2008-09-04
I needed to ask a question about the thread using a Nokia phone as a modem with "Ubuntu" thread: [http://ubuntuforums.org/showthread.php?t=378968&page=1](http://ubuntuforums.org/showthread.php?t=378968&page=1)

My question is when using Nokia PC suite on Windows XP I didn't need a userid or password what do i put in those relevant spaces if i don't have a userid or password, in order for the commands that were given in that archived thread to work i.e:

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = vf        [COLOR="Red"]<---- what do I put in here[/COLOR]
Password = vf        [COLOR="Red"]<---- what do I put in here[/COLOR]
Init3 = AT+CGDCONT=1,"IP","vfinternet.au";
Stupid Mode = 1


My service provider is Vodacom (South Africa)

Thanks in advance for the help

---

### Post by Kevbert on 2008-09-04
In the UK (Vodaphone) you can use either wap or web for both Username and password (depending on whether your on PAYG or monthly subscription).  You may even get away with leaving them blank!

---

### Post by ZALinuxDude on 2008-09-04
Sorry for the stupid question (what i know about Linux is beginner at best) the reason I asked is I was worried about syntax errors if i just left it blank I though perhaps i had to type in for the comands to be recognised as "no userID" and "no Password" needed, but i'll give it a try this weekend and see if there is any other help or advice available I'd sure like to hear that as well ...Just in case...

---

