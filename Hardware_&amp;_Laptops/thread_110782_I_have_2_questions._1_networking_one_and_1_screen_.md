---
title: "I have 2 questions. 1 networking one and 1 screen problem."
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by Tom Beers on 2005-12-31
Hi, I am new to Ubuntu, and relativly new to Linux. I have an old Toshiba 4010CDS that was going to waste in a corner somewhere, so I put Ubuntu on it and I must say I am very impressed, but, I have 2 problems :confused: :

Oh and I also realise that these are probably very common problems, but I have been googling all day, and nagging a friend who seems to know a fair bit about linux, and yet nothing has come of it... So I am sorry but I have had to resort to posting here :).

1) I have an (unbranded) Wireless 801.11g CardBus network card (I also have full access to the WAG54G router and my dads Linksys WPC54G Wireless-G Notebook Adapter if needed), when I insert it into the correct slot, no lights come on or anything :S, going to System>Administration>Networking offers no help either, please help :(.

2) The laptop is capable of 800x600 yet only 640x480 is available in System>Preferences>Screen Resolution, after a great deal of googling I have read that /etc/X11/xorg.conf is the answer although I have yet to found out how/why :< :confused:, any ideas?

Thanks in advance :).

---

### Post by peanut butter on 2005-12-31
i can solve your networking problem.
because only a few companys make wireless drivers for linux you will need to use ndiswrapper (allows you to use windows drivers on linux) for this wireless card but you must have the windows driver for this card. you willalso want to install ndiswrapper-utils and ndisgtk from snaptic the go to system>administration>windows wireless drivers
and find your wireless card's inf driver file.
sadly i dontknow about your screen problem

---

### Post by Tom Beers on 2005-12-31
[QUOTE=peanut butter]i can solve your networking problem.
because only a few companys make wireless drivers for linux you will need to use ndiswrapper (allows you to use windows drivers on linux) for this wireless card but you must have the windows driver for this card. you willalso want to install ndiswrapper-utils and ndisgtk from snaptic the go to system>administration>windows wireless drivers
and find your wireless card's inf driver file.
sadly i dontknow about your screen problem[/QUOTE]
Thanks, I found ndiswrapper-utils, and then installed it, but I couldn't find ndisgtk and System>Administration>Windows Wireless Drivers isn't there either (that is after I installed ndiswrapper-utils of course) :(.

Edit: I am using 5.04 this wouldn't affect anything would it? :<

---

### Post by Tom Beers on 2005-12-31
:O I'm very sorry, I just realised I'm in the wrong section :/ :(, sorry.

Note: Sorry about the double-post; I'm using my PSP to write this which only allows so many characters >.>.

Edit: Discard the above; I have downloaded and installed 5.10 and I still have the same problem ;(, although the screen is fixed! XD.

---

