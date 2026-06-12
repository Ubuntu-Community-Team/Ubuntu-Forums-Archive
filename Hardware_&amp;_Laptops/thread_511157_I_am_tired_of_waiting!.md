---
title: "I am tired of waiting!"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by frayalejandro on 2007-07-27
I have been asking this q and nobody answers!

I have a small Windows 2000 Advanced Server network set up in my office. All stations have Windows XP, except mine. Everything is  fine in the files and internet sharing area, but I can no longer print with my Epson 5900L. When I select new printer, Network Printer, Windows Printer (SMB), Ubuntu detects the printer in the network, but when I send the print order, it says "stopped: job stopped" with the message "Ready: /usr/lib/cups/filter/foomatic-rip failed"

 Can someone tell me where I am going wrong please.:confused:

---

### Post by w4ett on 2007-07-27
You might try PM'ing the OP of this thread, who has seemingly fixed his problem (He has the same printer as you)

[http://ubuntuforums.org/showthread.php?t=48064&highlight=Epson+5900L](http://ubuntuforums.org/showthread.php?t=48064&highlight=Epson+5900L).

---

### Post by frayalejandro on 2007-07-27
Thanks.

But the link you gave me has no posts!

By the way, where do you know William of Ockam from?

---

### Post by w4ett on 2007-07-27
The OP (Original Poster) has marked the thread as "Solved"....why not PM (Private Message)  him or post on his original thread asking him how he "Fixed" is problem?   Just a thought.

Ockham's Razor

---

### Post by frayalejandro on 2007-07-27
I tried. But since he marked his message as "solved", his address is no longer available.

Thanks anyway.

---

### Post by fredj on 2007-07-28
I know William of Ockham because he was an important medieval philosopher but I don't know the 
answer to your problem. It's a real pain when people who solve a problem can't be bothered to share
the solution.

---

### Post by frayalejandro on 2007-07-28
Well. I just noticed I made a mistake: I installed the wrong driver for my printer. 

NOW: I downloaded the CORRECT driver (epsoneplijs 0.4.0), but when I try to install the epsonepl.ppd driver, it gives me this message: 
[COLOR="Blue"]Line longer than the maximum allowed (255 characters) at 206:'/home/alejandro/Desktop/epsoneplijs-0.4.0/cups/Epson-EPL-5900L-epl5900l.ppd' [/COLOR]

The "README" file sends me to run the gosthscript... I really dont know what to do with that.

Is it always so difficult to installa printer in Ubuntu? 

Yea, I know a bit of Ockham´s philosophy and his controversies with Pope John XXII. He´s most known ´cause the razor thing, but his moral and political thought is strange also. Weird franciscan brother. I like better Duns Scotus, he´s subtle.

---

### Post by p_quarles on 2007-07-28
It's often kinda difficult to get printers working, yeah.

I would try looking at the file that gave you the error:
```
gksudo gedit /home/alejandro/Desktop/epsoneplijs-0.4.0/cups/Epson-EPL-5900l.ppd
```
Scroll down to line 206, and post that line here.

---

### Post by frayalejandro on 2007-07-28
Thanks

But ill try this until monday!! I have to leave my office now. See you then...

---

### Post by frayalejandro on 2007-07-31
I am back.
I made the corrections to the line 206. The driver was installed perfectly, but i am still not able to print...
I dont know what else to do...Any idea? :|

---

