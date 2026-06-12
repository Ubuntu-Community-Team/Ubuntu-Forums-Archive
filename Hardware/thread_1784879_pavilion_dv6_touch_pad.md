---
title: "pavilion dv6 touch pad"
date: 2011-06-17
forum: Hardware
---

### Post by FAMAS223 on 2011-06-17
Hey Ive just move my laptop (HP pavilion dv6) to Ubuntu 11.04 having never used anything other than windows having an issue with the touch pad in that the right mouse button won't work I think its a driver issue not sure tho. Cheers for any helo

---

### Post by sakishrist on 2011-06-17
Hi there,

First of all, which model is your dv6?

If you press Shift + F10, does that bring the right click menu? If it does, then it really has to be the drivers ...

---

### Post by FAMAS223 on 2011-06-17
Shift + F10 does bring up the right click menu so its a driver issue then

---

### Post by sakishrist on 2011-06-17
OK, open a terminal and try running "xev". This will open a small window. Now move your mouse inside the window (the terminal should go crazy as you move the mouse inside the window). Then keep the mouse still and do a left-click. Notice what the output on the terminal is. Now do a right click, the output should be similar.

Is it? ... Or does nothing appear at all?

---

### Post by FAMAS223 on 2011-06-17
yes when the left button is pushed you get a button press event serial 36 when the right is pressed you get a you also get a serial 36 button push event

---

### Post by mtantawy on 2011-06-17
you seem to have one of these HP touchpads that don't have separate buttons
i have the same issue with my HP mini 210, this should help
[SOLVED] HP Mini 210 touchpad right click not working

[http://ubuntuforums.org/showthread.php?t=1388164](http://ubuntuforums.org/showthread.php?t=1388164)

---

### Post by mtantawy on 2011-06-17
if this helped and your problem is solved, please mark this thread as SOLVED to help others know it is solved :)

---

### Post by FAMAS223 on 2011-06-17
when Running the code I get 
Bash: /ect/modprobe.d/psmouse.modprobe: No such file or directory

---

### Post by Pratchat on 2012-04-27
Not all of Sony and Hp touchpad will give you problem but if they do give you you can try the following sequence of commands on the terminal. You can bring the terminal in ubuntu by pressing ctrl+alt+t key together

 echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse


Copy paste the above code in terminal, write the password. and then check your right and left click. I am sure, it will work :)

 All the best.
Enjoy Ubuntu :)

---

### Post by andrewdavies007 on 2012-05-23
Hi,
This fixed the right click but now I cant scroll...
I would rather have right click so I'm going to leave it as is unless someone
can tell me how to fix both

thanks

---

### Post by albertosouza on 2012-07-21
Thanks Pratchat,

your code solved my touth pad right buttom problem

I have a Hp Pavilion DV6 3090

---

