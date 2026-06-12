---
title: "X server crash?"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by avatar3 on 2006-01-10
Hey, i just installed ubuntu on my laptop, and when it boots it just crashes and says that there was somekind of fatal error in X server ? 

What could be cousing that ? Ive been trying to find it out for days, and finally decided to post here. I hope you guys can help me.. 

-Avatar3

---

### Post by christhemonkey on 2006-01-10
I have this same problem.
Can you get into a terminal?

---

### Post by avatar3 on 2006-01-10
Yes i can. I hope i can get ubuntu running :(

---

### Post by christhemonkey on 2006-01-10
im in terminal and my xserver-xorg thing is configured correctly, but still no beautiful ubuntu splash screen :(
if you run sudo startx
does this bring up a nice cursor tht you can move around?

---

### Post by avatar3 on 2006-01-10
Yep, mine is configured right too. When i do the "startx" i wont get anything.. Except an error..

---

### Post by christhemonkey on 2006-01-10
Have you tryed killing the failed version of the Xserver?
by running;
sudo /etc/init.d/gdm stop
and then doing:
sudo startx

---

### Post by christhemonkey on 2006-01-10
When i ran 
sudo dpkg-reconfigure xserver-xorg
and changed the screen resolution and refresh rate to my monitors optimum settings (found tucked away in the screen manual!)
then did 
sudo startx
this got it all working and happy :)

---

### Post by avatar3 on 2006-01-11
lol, did all that. and still not working..

---

### Post by christhemonkey on 2006-01-11
hmmmm, what is the error message that it gives you?

---

### Post by avatar3 on 2006-01-11
Hey, i added you to my msn messenger, come online so we could "chat" more fastly :P

---

### Post by christhemonkey on 2006-01-11
sorry i aint helped yet :p

---

