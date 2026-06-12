---
title: "Unsolved question Windows like US International keyboard"
date: 2009-08-10
forum: Hardware
---

### Post by whatdoesitwant on 2009-08-10
Hi.
In 2007 Leftblank [asked]("http://ubuntuforums.org/showthread.php?t=476775") if US International keyboard with Windows-like accent behaviour is possible in Ubuntu. It is not. As far as i know this does not exist in Linux, although an attempt was made for OSX but not Leopard. What does exist is Linux' US International keyboard with Dead keys. The difference between the two is that in the case of linux dead keys can be modified by any following key except [space], whereas in the case of windows, the dead keys can only be modified by a *limited* but practical set of following keys. 

How does this behaviour work?
As I said, it uses selective dead key modifiers.
[LIST]
[*]Typing ***'*** followed by ***e*** translates into **é**.
Typing ***'*** followed by ***[space]*** followed by **e**** translates into **'e**.[/LIST]
[LIST]
[*]But typing ***'*** followed by ***t*** translates into **'t**.
And typing ***'*** followed by ***[space]*** followed by ***t*** translates into **'t** as well. 
[/LIST]
So ***e*** is a dead key modifier and ***t*** is not.

The Linux way is not workable when you deal with as many modified characters as we do in the Netherlands, especially when corresponding with Spanish, French and German speaking people as well, which, I've heard, is not uncommon.
An option would be to change to French keyboard, but that also changes the layout. 

So, as opposed to having to learn to type again, I wonder if it is possible to change the default behaviour of the US International keyboard layout with dead keys to the behaviour as I described above. In theory it is simply a matter of limiting the set of modifier keys to the practical set. But I don't understand Linux, nor am I a programmer. I can give a list of the modifier keys, though. 

For people like me (basicly all of the 22mln somewhat people living in the Netherlands or Flanders who are confronted with Linux) this would be a large improvement in usability, especially now that the Dutch government is beginning to push for OSS.

Ubuntu is the most usable flavour of Linux so it seems like the best point to start the implementation. How hard can it be? :-\"

---

### Post by sebagr on 2010-11-10
Hi,

Have you been able to 'fix' this?

All answers I find point me in the direction of creating a whole new keyboard layout, and I'm waaay too lazy to do it.

I'll appreciate if you could share your solution, if you have it!

Thanks!

---

### Post by Tamhvm on 2011-04-04
I know this thread is kinda old, but if someone stumbles upon this, I wanted to show my solution for this problem.

I created a series of scripts to solve the issue of having problems with the Linux's native US Intl keyboard layout, just as the OP wrote. I use it mainly because my mother language is Spanish, and I still use lots of English forums, texts, chats and so on (like this site). *Win US Intl for Linux* is its name. It tries to mimic the behavior of the Windows US - International key layout.

You can go to [http://t.tam.x10.mx/en/win-us-intl-4-linux/](http://t.tam.x10.mx/en/win-us-intl-4-linux/) to check it out.

---

