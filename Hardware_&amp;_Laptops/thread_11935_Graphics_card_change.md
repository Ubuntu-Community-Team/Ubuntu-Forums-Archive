---
title: "Graphics card change"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by philip41 on 2005-01-20
Guys i am just about to change the graphics card in my linux box.
I am going from Nvidia to ATI. Is there anything i need to do, remove from Ubuntu before i do.

Thanks

---

### Post by poofyhairguy on 2005-01-20
[QUOTE=philip41]Guys i am just about to change the graphics card in my linux box.
I am going from Nvidia to ATI. Is there anything i need to do, remove from Ubuntu before i do.

Thanks[/QUOTE]

I would suggest with everything I have that you don't go from an Nvidia card to an ATI card!!!!!!

ATI's drivers in Linux SUCK ASS! You will never get the 3d to work well. Stick with Nvidia. A crap NVidia card is better than a nice ATI card in Linux. Heed my warning!

An Nvidia card works like a charm in Ubuntu. Look in the guide.

---

### Post by philip41 on 2005-01-20
[QUOTE=poofyhairguy]I would suggest with everything I have that you don't go from an Nvidia card to an ATI card!!!!!!

ATI's drivers in Linux SUCK ASS! You will never get the 3d to work well. Stick with Nvidia. A crap NVidia card is better than a nice ATI card in Linux. Heed my warning!

An Nvidia card works like a charm in Ubuntu. Look in the guide.[/QUOTE]

Yeh i have done lots of reading on the subject, and no what you are saying, But this machine is just for learning how to use linux (no gaming) so by the time i am competant enough to use Ubuntu as my main rig, the hardware will be half knackered and need changing anyway.

But you did not answer the original Q.

Cheers.

---

### Post by philip41 on 2005-01-20
Oh dear i seem to have cockedup somewhat. I have changed the cards over and now ubuntu will not boot.
It is still looking for the Nvidia card, i believe.

Message 

" i will disable this x server for now.
Restart GDM when it configured correctly.

If i click ok, i am taken to a command prompt ( Ubuntu login ) i login and am then left at .

phil@ubuntu: " $

Please help.

---

### Post by Rancoras on 2005-01-20
If you haven't hand edited your X config file, then after you login, issue this command:

```
sudo dpkg-reconfigure xserver-xfree86
``` 

Answer the questions and that should get your X running again.  You're right, it's still using the nvidia driver.

---

### Post by philip41 on 2005-01-20
[QUOTE=Rancoras]If you haven't hand edited your X config file, then after you login, issue this command:

```
sudo dpkg-reconfigure xserver-xfree86
``` 

Answer the questions and that should get your X running again.  You're right, it's still using the nvidia driver.[/QUOTE]

Ok i have just followed your above instructions, but no go.

This error was returned " /usr/sbin/dpkg-reconfigure: xserver-xfree86 is broken or not fully installed"

---

### Post by philip41 on 2005-01-20
Latest update, i have managed to get  X to restart, thats the good news.
The bad news is i do not think things are configured right, as i cannot change resolution without the screen becoming all garbled, so i have to wait for screen to reset itself.
Would there be some settings or files that i need to alter.

---

### Post by Rancoras on 2005-01-20
On that part, I have no idea.  I haven't used ATI in linux since my 8500 was new and I'll never do it again. ;)  Sorry I can't be of more help.

---

### Post by philip41 on 2005-01-21
[QUOTE=Rancoras]On that part, I have no idea.  I haven't used ATI in linux since my 8500 was new and I'll never do it again. ;)  Sorry I can't be of more help.[/QUOTE]


No sweat,  Guess I should have listened to poofyhairguy, infact i have, i have just got another Nvidia card.

---

