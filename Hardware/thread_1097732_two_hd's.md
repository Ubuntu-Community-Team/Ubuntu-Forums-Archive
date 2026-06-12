---
title: "two hd's"
date: 2009-03-16
forum: Hardware
---

### Post by tmail58 on 2009-03-16
My main hd is dieing, have installed a new hd and made it the master, made the old hd the slave (its listed as 4.5 GB Media in File Browser). 

I want to move some file from old hd to new hd, both have Ubuntu 8.04.

Problem is the old hd says I don't have permission to access it.

How do I fix this.

IF this is on a thread already, sorry for the double threading!

---

### Post by ponyexpress on 2009-03-16
one option, I don't know if it is the best, is

sudo chown -r <yourusername> /media/<hd>/*

this will change all the file ownership on hd to your user name. You have to replace yourusername and hd to valid values for your machine.

---

### Post by ponyexpress on 2009-03-16
> **ponyexpress said:**
> one option, I don't know if it is the best, is

sudo chown -r <yourusername> /media/<hd>/*

this will change all the file ownership on hd to your user name. You have to replace yourusername and hd to valid values for your machine.

Also, I don't know if it is clear that the <> will not be in the command you type, they're there to show values that need to be filled in.

---

### Post by tmail58 on 2009-03-16
this didn't work

sudo chown -r <yourusername> /media/<hd>/*

used this (read on a thread that the r had to be R

sudo chown -R <yourusername> /media/

Got me files moved!!!


THANKS!!!!!!!!!!!!!!!!!!!!!! :D

---

