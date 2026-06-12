---
title: "Keyboard problem"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by Pilsner on 2006-05-27
Hello all. I have checked around how to fix my pretty annoying problem with keyboard.

Let me describe it as this:

When I use keyboard whereever I use it, mozilla, console and everything in ubuntu I can write about 20 letters or something before it stops and doesnt print anything on screen.

It is not so annoying now but before it was very annoying if I pressed something it could repeat that letter with 20 more.

Like this. hellooooooooooooooooooooooooooooooo

I have turned of repeating in the system>preference>Keyboard

The repeating was stopped. That was little better.

But he problem that it stops.. 

Example: hello all my name is pilsner and I am a linux user. (When I write this I couldnt see "pilsner and i am a linux user".. I saw it after maybe 3-4 seconds.

What do I DO?

I have had this problem before.. I reinstalled it and then it worked good. But I dont want to install everything again. I think there must be a solution for this problem.

Can someone help me?

I am used to linux in console and installing programs.

I am not a newbie

/ Pilsner

---

### Post by Pilsner on 2006-05-27
anyone know how to solve this?

---

### Post by Pilsner on 2006-05-28
Arent there any solution for this? Come on...

---

### Post by meng on 2006-05-28
I can't be sure, but how much CPU utilization do you have - is the system becoming overloaded? Do you still have the problem if you log out of X?

---

### Post by Pilsner on 2006-05-28
You asked for resources and I took at screen-shot...

Log out of X? Well. Is it possible in ubuntu? I think If log out I will come to the window with user login and pass...

---

### Post by meng on 2006-05-28
Thanks for the screenshot. What do you see when you click on the second tab "Resurser"? That should give you a % of CPU utilization. Have a look with and without mozilla running.

Addendum: you can log out of X by ctrl+alt+f1, then
sudo /etc/init.d/gdm stop

allowing you to experiment with the keyboard with a lighter system load.

startx
should return you to gnome when you're done

---

### Post by Pilsner on 2006-05-28
Resurser...

With firefox ON in X (gnome)

---

### Post by meng on 2006-05-28
On second thoughts, maybe
/etc/init.d/gdm start
is a better way to start again.

---

### Post by meng on 2006-05-28
Well, it certainly doesn't look like your system is stressed. Even though I didn't initially believe that the keyboard itself was the problem, I guess it is possible. Have you got access to another keyboard you could try?

---

### Post by Pilsner on 2006-05-28
I tried to turn of Gnome display manager GDM in console and so. but it didnt help.
I mean when GDM was stopped. the problem with keyboard still was there... I write about 4 sentences and then it stops for 1-2 seconds.. 
Sorry I dont have another keyboard here right now.

I have had ubuntu installed before (have installed 3-4 times now) and 3rd time it worked excellent..

the keyboard name is Logitech Internet pro keyboard.
ps/2 connected.

---

### Post by meng on 2006-05-28
I have a similar but not identical keyboard. I'm very sorry I can't help. Good luck, hope someone else will be by shortly.

---

### Post by Pilsner on 2006-05-28
thanks for help. maybe someone else know...

---

### Post by Pilsner on 2006-05-29
The problem is gone for me now. Hahaha.. No idea how it was solved but i tried the "vanilla kernel guide" and compiled the kernel..
I had to fix the nvidia. but there was guide for that too. So now it works good for me.

But I dont think the solution is to compile the kernel. I am just happy that it solved for me... in weird way. :D

---

### Post by NicoDietrich on 2006-06-06
I'm experiencing the same problem here and it looks like this is definitely a kernel problem! (the problem doesn't appear using the current debian testing kernel).

I filed a bug: see [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48746](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48746)

---

