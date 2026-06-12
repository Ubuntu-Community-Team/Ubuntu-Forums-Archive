---
title: "Voice problem ."
date: 2008-07-28
forum: General Help
---

### Post by nbayiha on 2008-07-28
Hi ,
i have a problem with voice , i mean when i call someone i can hear him , but he can't hear me , so i tried to juggle between alsa or pulse audio or oss, but i get the same result . I tried a skype test call , and got the same thing. I looked around in the forum to see if someone has the same problem as mine , and i found some people who had problem with sound but with voice the had something different , and it's why i open this thread looking for your advice and Help.

Here is the result of different command 

```
 lspci | grep -i 'Audio'
```
 and i got this 
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

```
 cat /proc/asound/cards
```
here is the result
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 21

```

And by the way when i input alsamixer , 
My headphone are completely mute , i mean i can't even level them up , they are mark like non existing. So i guess maybe the problem is coming from there.
Anyway Thanks in advance.

---

### Post by nbayiha on 2008-07-28
Is there anyone who had the same problem , and know how to fix it ?

---

### Post by Dave Otter on 2008-07-28
Rt click volume icon  on tool bar

   Open volume control 

  Edit>>Preferences

   Tick mic capture

  Open Skype

  Go to options>>sound devices  >>set your card or default card     

   Make test call

   This  worked for me

---

### Post by nbayiha on 2008-07-28
```
Edit>>Preferences

Tick mic capture

```

I dont have any mic capture in my preferences. :?

Edit : I did fix it actually. Thank You .

---

### Post by miekje on 2008-07-28
hi 

how did you solv it i have the same problem

---

### Post by nbayiha on 2008-07-28
@miekje , 
actually  the only think i did was to disconect my Monitor (Iiyama) speaker, and to connect my headphone . Then everything work. 
So from now on, when i need to use skype i just have to disconnect my Monitor speaker and connect my headphone and everything is cool.

But i dont know if that will work for you. First give a try to what
@Dave wrote , i try to post here the output of your sound card .

---

