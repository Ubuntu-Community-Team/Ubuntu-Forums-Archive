---
title: "Hey! NOt sure where to put this post"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by x2breakoffate on 2007-07-26
i have ubuntu 7.09 feisty (and i'm lovin it lol)
i love everything about ubuntu, its freeness, its editbility even if thats not a word. i mean i've changed the boot screen the login screen my theme everything and it seems like its just... i mean its still ubuntu. on any other OS if i were to do that, especially windows, it would make it seem like its not the same computer anymore but ubuntu fits perfectly! and it doesnt use as much resouces.

Anyways...

We all know what the grub boot loader is correct? Well I was wondering, I'm only going to be using Ubuntu and if I use anything else then I'll be using virtualization. Is it safe to remove the grub bootloader and if it is how do I go about doing this without screwing up my system. I dont want to reinstall Ubuntu again lol.
If it cant be done, then thats fine but heres my other question.

I want to put windows in virtualization on ubuntu but dont want to pay for VMWare. Is there anything that I can use to do this. I want to put other Linux Distros and maybe Mac OS X but you know, I dont know of any free software to do this will. Someone help.

---

### Post by small_bigguy on 2007-08-04
Hey, i wanted to do this but apperently its pretty hard.

This is how i overcame it:

Open terminal and type
 sudo gedit /boot/grub/menu.lst

when the text editor opens search for a line that says
timeout =(number)
 i think the number is default 10 but just change it to 1
then on boot it will display grub for 1 second ten boot the 1st choice

(if linux isnt your 1st choice just move the sectionsaround within the menu.lst file and make it the 1st one)

This dosent get rid of grub but if you need to use it again for whatever reason then its still there. Also if you did want to ge rid of it completely i have heard that you can very easily screw up your ubuntu install.

Hope this helps :D

---

