---
title: "Sound Card Support"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by Croatian on 2005-10-28
I have an IBM 380XD
i have installed Ubuntu 5.04 on it and it runs amazing, i am a new user to Linux and i am enjoying the ride, i ran "sudo apt-get install xmms" and it intalled it for me
now when i try to play an mp3 on it it says please make sure ur sound card is configured

how do u configure a sound card

when i go to sound controle it says " No volume control elements and/or devices found."

i have used this laptop with win 2000 and i listend to sound on it via CD. mp3 or internet radio
i don't know why it wont work wit linux

i found sound card drivers but i can't find anything for linux on ibm website

can someone help me here

thank you so much

---

### Post by tehwa on 2005-10-28
Hello,

Verify the device is installed correctly by running the following command in a terminal window:```
aplay -l
```You should see some info on your soundcard.

If this command shows that your card is installed, there could be any number of things preventing sound from playing. Take a look at these wiki pages for possible solutions:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[https://wiki.ubuntu.com/Sound_Problems_Hoary](https://wiki.ubuntu.com/Sound_Problems_Hoary)

---

### Post by Croatian on 2005-10-29
[QUOTE=tehwa]Hello,

Verify the device is installed correctly by running the following command in a terminal window:```
aplay -l
```You should see some info on your soundcard.

If this command shows that your card is installed, there could be any number of things preventing sound from playing. Take a look at these wiki pages for possible solutions:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[https://wiki.ubuntu.com/Sound_Problems_Hoary](https://wiki.ubuntu.com/Sound_Problems_Hoary)[/QUOTE]


----------------------

I tryed the:
```
aplay -l
```
and i got
code]aplay -l
aplay: devices_list:200: no soundcards found...[/code]

then i ran
```
lspci -v and lspnp -v
```
and i got
```
0e CSC0000 Crystal PnP audo system CODEC
io disabled
io disabled
io disabled
irq disabled
dma disabled
dma disabled

0f CSC0010 Crystal PnP audio system control registers
io disabled
```

i have Crystal Audio Vearsion 2.60 CS4237B

what do i do

---

### Post by tehwa on 2005-10-29
> i have Crystal Audio Vearsion 2.60 CS4237B

Have a read of this thread.

[http://ubuntuforums.org/showthread.php?t=10192](http://ubuntuforums.org/showthread.php?t=10192)

Sorry chief, I don't have an answer for you.

---

