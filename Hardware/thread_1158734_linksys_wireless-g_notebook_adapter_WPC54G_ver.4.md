---
title: "linksys wireless-g notebook adapter WPC54G ver.4"
date: 2009-05-14
forum: Hardware
---

### Post by RobFS1 on 2009-05-14
Can anyone help me install the drivers to a **linksys wireless-g notebook adapter WPC54G _ver.4_**?! Please, I'm not finding anything anywhere else, and I am trying to fix this computer for a friend of mine. Please!:) Running Ubuntu 8.04

---

### Post by steve01832 on 2009-05-14
Linksys cards use the Atheros drivers. Put the card in the slot and reboot the computer. You should get a pop out box showing restricted drivers in use. You can go to System>Administration>Hardware_Drivers to manually activate the Atheros driver.

Steve

---

### Post by RobFS1 on 2009-05-14
Not this one: when i put it in, nothing happens, but the power light is on on the card, so i know that it works... and my friend said it worked before he installed ubuntu. Are you _sure_ that my specific card uses the atheros driver? Because if it does, then can i manualy install it?

---

### Post by RobFS1 on 2009-05-16
Please, somebody answer. [-o<

---

### Post by chi2jjk on 2009-05-25
Did you ever get this working?  I have a WPC54G ver.4 also and have the same situation.

Any help is greatly appreciated as this is the last hurdle to make my home fully LINUX!!  Yes it is only one laptop and one desktop, but the point is no. more. windoze...

thank you from the bottom of my cup of Ubuntu...

---

### Post by RobFS1 on 2009-05-26
I still haven't got it working, and for that matter, haven't had good luck getting just about anything working using this forum.

---

### Post by rob2uk on 2009-05-26
The WPC54G v4 uses a Broadcom chipset.

Try using ndiswrapper to install the bcmwl5 XP drivers

---

### Post by snowpine on 2009-05-26
I have a Linksys wusb54g v. 4 as well.
It is supported out of the box with 8.10 and newer.
I have not used 8.04 in a long time, so I don't remember how I got it working (there is definitely a tutorial somewhere in these forums). I know it is possible though, so don't give up!

Good luck!

(edit) ps the terminal command lspci will tell you exactly which chipset you have. This is useful information when searching for a solution.

---

### Post by chi2jjk on 2009-05-26
Rob, thanks for chiming in.  I have the install CD for the WLAN card, which files should I be looking for?

---

### Post by rob2uk on 2009-05-26
Try looking for bcmwl5.inf

I can't help you with installing as I've never had to use ndiswrapper myself. I'm sure you can find the instructions though :)

Failing that, try ndisgtk ;)

---

### Post by chi2jjk on 2009-05-26
Thanks rob, I loaded the drivers you suggested, but still to not appear to 'see' the card.  There was no bcmwl5.*inf* on the CD, but there is a bcmwl5.*sys* file (hmm...)  Also, still no link light - only power.

Thanks again, we'll keep working on it.

---

### Post by a386673 on 2011-02-21
Hi, i have a linksys wireless wpc54g, and all i had to do was plug it un, and go 
System  > Administration > Additional Drivers.
The system recognized what it was, and downloaded the right driver automatically.
So, big thanks to whoever made it so easy!
Hope this helps :)

---

