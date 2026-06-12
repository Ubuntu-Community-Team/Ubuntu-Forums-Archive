---
title: "send some message to a custom service right before shutdown"
date: 2014-06-11
forum: Hardware
---

### Post by rompelstilchen on 2014-06-11
Hello,

i want to write a background service on ubuntu (the box is tied to an arduino and an LCD)

as an embedded system, everything is enclosed so i need to be sure the system is down before pulling the plug

but practicaly i am not sure how to achieve this

on system shutdown-> runlevel 0 -> script that sends a message to my service <---- this part i dont know how to do 
 
(then the service sends some data via usb to arduino and to LCD <---- this part i know how to do it)

any advice/explanation/help woudl be apreciated

i dev with netbeans/C++

thx

---

### Post by sudodus on 2014-06-11
I have not used it myself, but I think the following link will help you

[http://askubuntu.com/questions/51145/how-to-run-a-command-before-the-machine-automatically-shutdowns](http://askubuntu.com/questions/51145/how-to-run-a-command-before-the-machine-automatically-shutdowns)

---

