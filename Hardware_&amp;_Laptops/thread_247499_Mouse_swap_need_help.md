---
title: "Mouse swap: need help"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by Buzzygirl on 2006-08-30
I apologize in advance for asking about what's probably a very simple procedure, but since I'm an Ubuntu noob and still fairly weak with the command line, perhaps one of you experts would deign to point me to an answer? 

So I've got this crappy old three-button PS/2 mouse of the Logictech brand connected to my computer and I don't like it. I have a newer three-button Micro Innovations optical mouse (also PS/2) that I would prefer to use. I'm running Dapper on a 700 MHz Pentium III.

Tried swaping out the old one for the new one... the new one didn't work (I didn't expect it to) so I figured I'd have to change some settings to get my computer to recognize the new mouse. How do I do that? I've already searched for an answer in the Ubuntu Wiki, the Ubuntu Guide and Googled for an answer and so far, I've only found instructions on how to set up multi-button, Bluetooth or side-button mice, none of which pertains to my situation.

Again, I'm a bit weak on my command-line skills, but I can copy and paste with the best of 'em, so if someone could point me to a detailed tutorial on how to configure an optical PS/2 mouse, I would very much appreciate it.

Jackie
(hoping that by asking questions here, I will someday no longer be a rank amateur)

---

### Post by zxee on 2006-08-31
Hmmm both mice are ps/2 and yet it doesn't recognize the one you want to use?
Have you tried to change it _while_ the computer is off and then start?
If you did that and it didn't work you may need to go through the xserver configuration setup.
Open a terminal and enter this: > sudo dpkg-reconfigure xserver-xorg That program will ask you questions about your video, monitor, keyboard and mouse. Just hit enter for things you don't know/don't want to change. When you get to the mouse you'll get to select what's most appropiate for the mouse your using. Hope that helps.

---

### Post by Buzzygirl on 2006-08-31
> **zxee said:**
> Hmmm both mice are ps/2 and yet it doesn't recognize the one you want to use?
Have you tried to change it _while_ the computer is off and then start?
If you did that and it didn't work you may need to go through the xserver configuration setup. {...}
 
Yes, that was the first thing I tried (changing mouse while 'puter was off) and it still didn't want to deal with the newer mouse.

I will try what you suggest with regard to setup. If I continue to have trouble, I may pick up a USB mouse and see how that works.

Thanks for your reply.

---

