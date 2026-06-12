---
title: "HOWTO:  Atheros AR5006EG on Toshiba P200-12W"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by mooha on 2007-12-24
How to make Atheros ar5006eg working on Toshiba P200-12W


goto system-administration-Restricted Drivers Manager

Disable Hal

Then you reboot the machine

install ndiswrapper from synaptic --- you can select the following packages:

ndisgtk
ndiswrapper-common
ndiswrapper-utils-1.9  

after installing ndiswrapper  get windows drivers files, I personaly went to [http://www.atheros.cz/](http://www.atheros.cz/)
and select the correct one (in my case was ar5006eg)

extract the file (in my case was xp32-5.3.0.56-whql.zip)

goto system-administration-Windows Wireless Drivers


click on Install New Driver

click on location then browse to where you extracted your windows file

Select the file with extension  .inf

click on Open then click on Install

you can close Windows Wireless Drivers after you see a confirmation that hardware is present.


then it's time for commandline:

we have to  blacklist ath_pci

so run

gksu gedit /etc/modprobe.d/blacklist

and add the following: 


blacklist ath_pci      at the end of file

then enter the following commands one by one:

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

then the last one:   gksudo gedit /etc/modules
and add:   ndiswrapper    at the end of file

please note: 

In my case after the last command I rebooted but nothing happened, so I turned off the PC the turn it on back again then I was able to see the Orange Light of my wireless, then after loging in every thing worked super fine.

Good luck

Salam Alikoum

---

### Post by keyo on 2007-12-25
Thanks for posting this.
I tried this on an asus with the same chipset (ASUS Z99He) and it worked fine.

I have one question though; why are we using the windows driver when there is a linux driver available? (on atheros.cz)

My dad just got a new laptop for christmas that came with vista basic, I'll be glad to get him on ubuntu. :) Thanks for the help.

---

### Post by mooha on 2007-12-26
I'm not sure, as long as it works .... cooooooooool

---

### Post by dogerelly on 2007-12-29
Can I say a huge THANKYOU.:):). I have been trying to get wifi working for ages, following instructions on lots of other links. This worked straight off and for a newbie was easily the most straightforward of all the posts.....
atheros 5007 EG (reported by ubuntu as 5006) on toshiba 200-15L.

just one last question--I rather stupidly downloaded the atheros driver to the desktop where I really don't want it. If I move it will I need to readd it on windows hardware driver manager  or is it going to give me more grief!!

---

### Post by Fritzwr on 2007-12-29
I am running a Toshiba Sattelite Pro A210 with an AMD Turion 64 and have loaded Gutsy Gibbon. I have gone through all of the steps in your tutorial and when I get to the sudo modpro ndiswrapper command, I get an error " FATAL: Module ndiswrapper not found."

Any suggestions would be greatly appreciated.

---

### Post by basketballer on 2008-01-05
I LOVE YOU MAN, IT WORKED PERFECTLY
a7la salam for the Arab people :guitar:

---

### Post by basketballer on 2008-01-09
After i have done this, every time i restart my computer
a black screen freezez. and then i have to push the button to switch it off then reboot.
coz Alt+Ctrl+Delete does't work!

---

