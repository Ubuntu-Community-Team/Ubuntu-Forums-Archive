---
title: "hp pavilion dv6 6119tx ubunut 11.04 problems with screen brightness and beats audio"
date: 2011-09-08
forum: Hardware
---

### Post by sharat_dev on 2011-09-08
I have a new HP Pavilion DV6 6119tx notebook. My configuration is as follows:

intel core i5 2410
4gb ram
1gb ati 6490m switchable graphics

I am running ubuntu 11.04. I am facing two issues.

1) I cannot change the screen brightness. when i press the function keys for brightness i can see the slider moving at the top right corner of the screen but there is no actual change in the screen brightness. i have tried googling but so far have not found a solution.

2) my notebook has HP Beats audio with 4 speakers ( 2 near the screen and 2 at the front). but in ubuntu the front 2 speakers are not working.

---

### Post by sharat_dev on 2011-09-08
initially i had problems with ubuntu booting into a black screen. after some googling i managed to solve it by blacklisting the radeon drivers. now vgaswitcheroo is working and i am able to turn the ati card off, but i can't change the screen brightness.

---

### Post by neerajds on 2011-09-30
same problem with me. I installed ubuntu 10.10 and not able to adjust brightness at all.

Any solutions?


-Neeraj

---

### Post by sharat_dev on 2011-10-01
This solved it for me - [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

just add the ppa to your software sources and update.

Regarding beats audio, if you choose connector as 'analog speakers' in output tab of sound preferences, you'll get output from all four speakers.

---

### Post by rameshb20 on 2011-10-30
hi, 
I am planning to buy the dv6 6119tx. have you had any issues with wireless connectivity (slow detection of WiFi /slow connection that keeps snapping etc. ) and have you used Skype on it? does Skype work well? would appreciate any inputs on this.
thanks
ramesh

---

### Post by sharat_dev on 2011-11-17
sorry i have not used skype/wifi in ubuntu. but overall i am really happy with this laptop. I would really recommend it.

---

