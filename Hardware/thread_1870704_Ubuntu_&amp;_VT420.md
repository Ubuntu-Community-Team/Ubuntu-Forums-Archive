---
title: "Ubuntu &amp; VT420"
date: 2011-10-27
forum: Hardware
---

### Post by evilg on 2011-10-27
Hello,
 
I have just aquired a VT420 which is great for when im messing around with cisco kit etc but I would much rather use it as a permanant additon to my desktop to manage my little ubuntu server which unfortunately only has a usb connection.
 
Failing that it would at least be quite nice to use as a monitor for when im messing around with linux VM's on my laptop which at least has a serial connection.
 
The VT420 has a serial port on the back with a rj45 adapter which im making the massive assumption I can just plug one of my cisco cables into and that in turn into my laptops serial port and then configure VM player to pass the serial port to the ubuntu VM.
 
Then I am once again making the massive presumption that all I have left to do is configure the linux VM to pass the screen output to the serial port in question.
 
How wrong am I? and can anyone please point me in the right direction?
 
Any help greatly appreciated.
 
Kind regards
 
ps, if its not already apparent im a complete linux n00b so you will have to spell everything out for me, thanks for your time.
 
G

---

### Post by wolfen69 on 2011-10-27
Install *vttest*. "This package provides a program designed to test the functionality of
a VT100 terminal (or emulator). It also supports analysis of VT220,
VT420, and xterm.

The program is menu-driven and contains full on-line operating
instructions. It tests both display (escape sequence) and keyboard
handling."

---

### Post by evilg on 2011-10-27
Thanks for answering Wolfen,
 
Right, frank addmission here, I dont actually currently have a keyboard for my VT420 but im thinking I should at least be able to get some output over there.
 
That app you kindly supplied certainly looks the ticket but none of the tests appear to output to my VT screen, do I need to be setting up any getty configuration or specify some settings for the serial port before I expect any output?
 
essentially do I need a keyboard or a better understanding of the workings of this terminal business? ;)
 
Cheers
 
G

---

