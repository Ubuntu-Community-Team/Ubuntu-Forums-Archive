---
title: "Ubuntu 11.10 Touchpad mouse sensitivity issue"
date: 2011-10-07
forum: Hardware
---

### Post by stevpm on 2011-10-07
I recently upgraded to ubuntu 11.10, [ its a second time am doing this]. I only got one problem, i have problems with clicks..let it be right or left..or even by using the touchpad. My laptop is October 2010 Samsung RF510, Intel i5, 4GB RAM.

I tried to adjust the touchpad settings to the maxmum sensitivity and acceleration but i see no difference.. always running on the latest updates.. :confused:  

am waiting :popcorn:

---

### Post by ffvieira on 2011-10-14
> **stevpm said:**
> I recently upgraded to ubuntu 11.10, [ its a second time am doing this]. I only got one problem, i have problems with clicks..let it be right or left..or even by using the touchpad. My laptop is October 2010 Samsung RF510, Intel i5, 4GB RAM.

I tried to adjust the touchpad settings to the maxmum sensitivity and acceleration but i see no difference.. always running on the latest updates.. :confused:  

am waiting :popcorn:

I am having the same problens... Can someone help me? My laptop is Samsung SF510!

---

### Post by pracedru on 2011-10-15
Hi 

I am using Samsung RC530.
The buttons work fine but the touchpad needs to be pressed hard or with large surface of the finger. Otherwise there isn't any response. Seems like pressure sensitivity is to low. How can i change this?

---

### Post by ffvieira on 2011-10-15
> **pracedru said:**
> Hi 

I am using Samsung RC530.
The buttons work fine but the touchpad needs to be pressed hard or with large surface of the finger. Otherwise there isn't any response. Seems like pressure sensitivity is to low. How can i change this?

Hi, I tried changing the sensitivity to maximum and it still doesn't work...

---

### Post by a8j8i8t8 on 2011-10-17
Same with me :(
I have Samsung RV509.
Is it only with Samsung models?
Following solution worked for me, try and let me know.
> sudo su
> echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
> reboot
--
Cheers,
Ajit

---

### Post by Rinshan on 2011-10-24
I have a Samsung rc530 too and I experienced the same sensitivity problem.
Running
> sudo su
> echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
fixed the sensitivity problem but now the touch-pad is recognised as PS/2 Generic Mouse instead of ETPS/2 Elantech Touchpad (which means no edge scrolling and similar) :confused: .

---

### Post by stevpm on 2011-10-29
stephen@stephen-RF510-RF410-RF710:~$  sudo su
[sudo] password for stephen: 
root@stephen-RF510-RF410-RF710:/home/stephen# echo options psmouse proto=exps
options psmouse proto=exps
root@stephen-RF510-RF410-RF710:/home/stephen# /etc/modprobe.d/psmouse.modprobe
bash: /etc/modprobe.d/psmouse.modprobe: No such file or directory
root@stephen-RF510-RF410-RF710:/home/stephen# echo options psmouse proto=exps
options psmouse proto=exps
root@stephen-RF510-RF410-RF710:/home/stephen# /etc/modprobe.d/psmouse.modprobe
bash: /etc/modprobe.d/psmouse.modprobe: No such file or directory
root@stephen-RF510-RF410-RF710:/home/stephen#

---

### Post by stevpm on 2011-10-29
> **stevpm said:**
> stephen@stephen-rf510-rf410-rf710:~$  sudo su
[sudo] password for stephen: 
Root@stephen-rf510-rf410-rf710:/home/stephen# echo options psmouse proto=exps
options psmouse proto=exps
root@stephen-rf510-rf410-rf710:/home/stephen# /etc/modprobe.d/psmouse.modprobe
bash: /etc/modprobe.d/psmouse.modprobe: No such file or directory
root@stephen-rf510-rf410-rf710:/home/stephen# echo options psmouse proto=exps
options psmouse proto=exps
root@stephen-rf510-rf410-rf710:/home/stephen# /etc/modprobe.d/psmouse.modprobe
bash: /etc/modprobe.d/psmouse.modprobe: No such file or directory
root@stephen-rf510-rf410-rf710:/home/stephen#

i cant seem to be winning!!!

---

### Post by Rinshan on 2011-10-30
> **stevpm said:**
> i cant seem to be winning!!!

Run
```
sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```as a single command, then reboot.

---

### Post by insession on 2011-11-29
anybody know how to un-do this command? I want to change settings on my touchpad but it's fooling my computer into thinking it's a mouse, so it doesn't even detect a touchpad


EDIT: Here's how:

```
sudo rm /etc/modprobe.d/psmouse.modprobe
```

---

### Post by alfhakon on 2011-12-23
I tried it and it worked. Unfortunately I can't find a way of having the goods of both ends..

Anybody know how we get the "correct" sensitivity, and the ability to enable two-finger scrolling?

---

### Post by mephissto on 2012-01-23
I have the same problem on my RC530 and your solution solved my problem, but I really miss the scrolling :/

I subscribe to this thread, let's hope someone find a full functionnal solution :)

---

### Post by smittix on 2012-02-19
Hey,

I have recently purchased a Samsung RF511 and I have the exact same issue.

I have to press really hard to move the cursor.

---

