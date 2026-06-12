---
title: "MSI WInd  and NO wifi in Ubuntu"
date: 2008-07-14
forum: Hardware
---

### Post by maprx on 2008-07-14
Well, unless you can compile the realtek drivers.  Ubuntu will not work in the MSI wind. I mean it looks great, but can't get wireless running.  Any chance some linux guru could make a deb file to automate the compiling process???

I don't want to change the wifi card as it may void the warranty

---

### Post by wiremoons on 2008-07-14
I have the same issue with my Advent 4211 that is a rebadged MSI Wind available in the UK from PCWorld stores.

The wifi card in question is a Realtek 8187se

I had tried the instructions posted on the MSI Wind forum here: [http://forums.msiwind.net/default-msiwind/have-the-wireless-drivers-but-t840.html](http://forums.msiwind.net/default-msiwind/have-the-wireless-drivers-but-t840.html)

The wifi card did work until I rebooted and then it didnt want to work anymore after that!  I did try repeating the process but no joy sadly. 

Some how it was working with the wifi turned off too - which was even stranger! There is a function key on the keyboard (Fn+F11) to enable/disable the wifi - this may have contributed to the problems I guess. The key worked to the point of the lights changing on the computer to indicate the enabled/disabled, but there were messages in the /var/log/messages stating the key press was not recognised.

Back on WindowsXP at the moment - but will give it another go if the problems can be solved, and the driver patched to work properly.

---

### Post by maprx on 2008-07-15
I even tried Mandriva live cd, it looked fine, but it would not recognize the realtek windows drivers thru ndiswrapper

---

### Post by Naralas on 2008-08-02
Google "MSI Wind Ubuntu"
GET: [http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron) (first result)

Goto "wireless"
Option 1: Replace Wirelses card (if ur intent on voiding ur warranty for no good reason at all) see: mental
Option 2: Typing (or copy-pasting) about 12 lines into bash while an ethernet cable is plugged in.

That's all it took for me. Done in 4 minutes.

---

### Post by simonuk on 2008-08-27
After ages trying various things I finally found this site:

[http://forums.msiwind.net/viewtopic.php?f=7&t=1976]("http://forums.msiwind.net/viewtopic.php?f=7&t=1976")

Had me wireless in minutes and I'm typing from my MSI wind wirelessly right now

---

### Post by mudguts on 2008-09-06
yup, i did the same thing... 
the wi-fi is a bit flaky though.  i had it flake on me a couple of things since I installed it yesterday.

I'm thinking about changing out the card.  I have an engenius 8602+s which is 802.11 a/g   and I've installed linux drivers on it with a PBX module that our company made.

I just hate to take it apart :(

site for cmd line prompts is here.

[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_2:_Compiling_Drivers_for_the_Supplied_Wireless_Card](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_2:_Compiling_Drivers_for_the_Supplied_Wireless_Card)

---

### Post by victor9098 on 2008-09-18
I have the Advent 4211 and just swapped out the wireless card to make things easy (upgraded ram while I was at it).

It is not an ideal solution but it works and I have not had a problem since. Most of my headaches come from how network manager and my usb modem get along but I understand the 0.7 release will hopefully solve all this.

Here is a link to my blog to show you what I did ([Click Here]("http://kd-signofthetimes.blogspot.com/2008/09/advent-ubuntu-perfect-partnership.html")). If you are not comfortable with it a local PC store should do the mod and I believe MSI can send you out a replacement warranty sticker!

---

