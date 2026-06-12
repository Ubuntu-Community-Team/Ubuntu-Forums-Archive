---
title: "automate command for wireless"
date: 2011-10-11
forum: Hardware
---

### Post by rawrmonster on 2011-10-11
i have a alfa wifi usb wireless card and it uses the rtl8187 driver from the kernel and works well after the command "sudo iwconfig wlan0 rate 5.5M fixed" is typed in otherwise it will be a really spotty connection and drop signal  all the time. This may just sound lazy i get tired of having to type that command in every time i plug in the card i want to be able to make it when the card is plugged in to the laptop i want the OS to execute the command i just don't know exactly  how to go about this i am not asking you to make the program for me i just want some web site to read up on it because i cant find anything on-line. maybe i am just asking Google the wrong question well thank you for hearing me out and have a wonderful day

---

### Post by wolfen69 on 2011-10-11
I can't actually fix your problem, but can make things easier. When you open the terminal, (before typing anything) hit the up arrow, (you may have to do it more than once, and can go back with the down arrow) and you will see the command you need because the terminal will remember it. Good luck.

---

### Post by spiky001 on 2011-10-11
Or make a script, then create a launcher on desktop to run script

---

### Post by rawrmonster on 2011-10-11
i have a bash script made but still i know its possible to do i really want to find a way with no user interaction

---

### Post by spiky001 on 2011-10-11
How about having the script run at startup? add the script to startup applications

---

### Post by rawrmonster on 2011-10-11
because the device is a usb device that is not pluged in all the time so having it run on startup doesn't do anything for me unless the device is plugged in at boot. I think it will have to tie in to udev to work I am not scared to get my hands dirty. and i dont mind programming i just dont know how to go about this. i want the proper way to this this "not saying what your saying is wrong" but i want it to execute anytime the device is plugged in thank you for your reply.

"i hope you don't take that the wrong way im not trying to say that your wrong or is bad just looking for what needs my needs exactly"

---

### Post by spiky001 on 2011-10-11
No offence, When it,s plugged in would the watch command help pick it up then return when it is to execute the command? I,m far from any good at scripts but i have used watch command, There are others good with scripts Thebigusgreekus for 1, maybe pm him

---

