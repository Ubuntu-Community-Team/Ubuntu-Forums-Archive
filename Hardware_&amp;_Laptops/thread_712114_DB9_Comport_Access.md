---
title: "DB9 Comport Access"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by Patriot1776 on 2008-03-01
Hello, I'd like to be able to access the male DB9 jack on the back of my computer for custom device I'm rigging up.  How do I go about doing this?  Sorry if this seems newbish, but I am a newb at this.

---

### Post by Patriot1776 on 2008-03-01
Okay, it's probably located at /dev/ttys0.  I'm going to write a program and I need the program to be able to directly manipulate pins 7, 8, and 9, the RTS, CTS, and RI pins, on the DB9 jack if that's where it's located.  Is this hard to do directly from a program you've written yourself?

---

### Post by BullyCaSa on 2008-04-10
Take a look at this - it should get you started:

[http://www.easysw.com/%7Emike/serial/](http://www.easysw.com/%7Emike/serial/)

I am doing something similar on my Sun server.

Brian
[http://thandi.dyndns.org/arcade.php](http://thandi.dyndns.org/arcade.php)

---

