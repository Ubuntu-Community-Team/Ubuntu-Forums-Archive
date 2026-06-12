---
title: "help me to fix hardware issue"
date: 2011-02-09
forum: Hardware
---

### Post by DR AMD on 2011-02-09
Hello friends,

I already installed UBUNTU 10.10 on a PC, but I am not sure if it installed correctlly....I followed the instructions and tried to install it 6 times.

In words, the problem is.....
The sound is not working although the monitor says it's ok.
I am not sure if the graphics runs perfectally.
Network is ok, but although i am using an ADSL 2 Mb/s ..updates and software is being downloaded with less than ( 14 kb/s)...(normally= 250 kb/s).

All what i know about my computer is that is is holding >> model : HP Compaq dc5100 SFF......I was runniung on it windows Xp/Vista/7 perfectly

PLEASE.PLEASE.PLEASE.PLEASE.PLEASE.PLEASE.PLEASE.PLEASE.

help me to fix this problem by any possible means as quick as it could be!!!!

If you need any other information tell me just how to get it>>>>

I am waiting your respond....

---

### Post by gordintoronto on 2011-02-09
The Compaq dc5100 SFF is actually a family of computers, so there are a variety of components which might be included. However, the two things you are having trouble with are standard across the line: AC97 audio, and Integrated Broadcom BCM5751 NetXtreme Gigabit Ethernet. I have no idea what might be slowing your downloads. Are you using Synaptic Package Manager for those?

Turning to the audio, your computer might have an internal speaker, and it has audio jacks front and back. Are you using external speakers or earphones? Have you tried plugging in to the front, and to the back? If you run System/Preferences/Sound and click on the "output" tab, there is a drop-down box labelled "connector." I suggest you start a song playing, then try different options in "Connector."

I don't understand what you mean by "the monitor says it's ok."

The back of the computer might have a sticker which says more about the computer. See this page:
[http://h18000.www1.hp.com/products/quickspecs/12145_na/12145_na.HTML](http://h18000.www1.hp.com/products/quickspecs/12145_na/12145_na.HTML)
for an explanation.

Also, you can run Accessories/Terminal and type in the command:
lspci
which will provide an accurate description of some of your hardware. If you want to see extreme detail, use these commands:
sudo lshw >myconfig.txt
gedit myconfig.txt
You will be asked for your password after the first command. It will not display as you type it, but it will be accepted.

The graphics adapter in the computer is not at all wonderful. If you can see your Desktop, it's working as well as it ever will.

---

### Post by DR AMD on 2011-02-10
Thanks very much

most problems have already solved>>>at least all hardware was fixed right>>

I enabled sound support by root... That solved sound problem..

all what i need to get is solving the low speed of the internet....i shall get some codes from its specific forum..

thanks again very much for your support..

---

