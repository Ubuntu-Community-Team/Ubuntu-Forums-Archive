---
title: "Ubuntu 9.10 and SPSS 16"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Badcrumble on 2009-11-01
SPSS 16 working well under 9.04 upgraded to 9.10 all working well except SPSS 16 which I absolutely need! Tried reinstalling won't do so...fails:(
Please help...

---

### Post by Pasd on 2009-11-02
In the same boat... Just tried to boot up SPSS 16 and.... Nothing....

Please please help. I need this program or I am otherwise going to have to try and re-install 9.04 to get SPSS up and running.

---

### Post by Pasd on 2009-11-02
After a few hours of googling, I found and fixed the issue. Something to do with a 9.10 using a new libstdc++ version 6, whereas SPSS needs ver 5 (as a computer non-genius, I have no idea what this is, but no matter).

I am on a 64bit Computer and I figured out what I needed to do. If you are on a 32 bit system, I don't know what the differences are.  

What I did was follow the instructions on this page: 

[http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html](http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html)  

Voila! SPSS up and running again.

---

### Post by szymooon on 2009-11-06
I have the same problem with spss 16 after upgrading to 9.10 and i've followed the above mentioned instructions but it did not help.
still getting the same message about the lack of libstdc++.so.5 :(((
i'd be grateful for any ideas

---

### Post by Badcrumble on 2009-11-08
Oh dear...tried above but no luck. Above fix is for running  libstdc++.so.5 32 bit on a 64bit machine. Need to run  libstdc++.so.5 on a 32bit machine so spss 16 will run under karmic koala 9.10. Can anyone help further?

---

### Post by ikar6 on 2009-11-23
Problem solved for Ubuntu 9.10 32 bit as well! Just download the aforementioned package (libstdc++5_3.3.6-17ubuntu1_i386.deb) and run it with your package manager. SPSS worked right away!;)

---

