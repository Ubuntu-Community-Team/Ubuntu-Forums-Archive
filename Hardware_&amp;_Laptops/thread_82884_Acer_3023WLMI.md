---
title: "Acer 3023WLMI"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by innovatel on 2005-10-27
Hello to all!!! Sorry for my english, I don't know very well :oops: I'm a new "futhured" ubuntu user.

The next week i buy the Acer 3023WLMI and I want to install Linux. Yesterday night I read the procedure to install fedora cora 4 on this laptop but I don't won't it!

Someone know if possible to install ubuntu on my futhured laptop? I know is possible to install mepis and I hope in ubuntu.

Good night @ all :)

Andrea

---

### Post by John.Michael.Kane on 2005-10-27
Hello yes you can install ubuntu just fine on that machine. if you have any other issues or questions please post. 


Welcome to Gnu/linux/Ubuntu...

---

### Post by innovatel on 2005-10-27
Thank a lot :)

do yuo have some suggestion about the install? For exemple parameter to write @ installation boot ... configuration and setting ... 

ok, I ask a lot of question ... sorry but I'm very happy to buy a laptop :)

---

### Post by skirkpatrick on 2005-10-27
It will depend on whether Windows is pre-installed or not.  On my son's Acer Aspire 3002, Acer had a 2nd 30GB partition that I deleted and installed Breezy into.  You can do that during the Breezy installation.  Also you might want to check out the following threads concerning getting your batter status and wifi working:
[http://ubuntuforums.org/showthread.php?t=60484](http://ubuntuforums.org/showthread.php?t=60484)
[http://ubuntuforums.org/showthread.php?t=49045](http://ubuntuforums.org/showthread.php?t=49045)

---

### Post by innovatel on 2005-10-27
Thank a lot for the link ... i'm going to bed now ... i'll read it tomorrow 

:KS good night at all :KS

---

### Post by innovatel on 2005-11-05
Hello at all ... I've one problem now:

I had install ubuntu from cd rom and I wrote linux to start the installer proccess.

When the o/s is starting I don't saw the screen. what can I do?

I think to try another disto for example debian, gentoo but I think it's hard to setting :(

---

### Post by John.Michael.Kane on 2005-11-05
Try typing linux vga=792 beforeyou install ubuntu

---

### Post by innovatel on 2005-11-06
nothing to do ... i'm crying now :(

On another forum an user tell me to install fedora 4 because it's simple but i want a debian based. I try debian but not work the eth0.

I re-try with expert install ... I hope -.-

---

### Post by innovatel on 2005-11-06
Hello from my ubuntu-station

It's work perfectly .... thank a lot 

:KS good night @ all :KS


I undestand ... the solution:
on boot i pressed Return (default installation) and when I selected the screen resolution : 1280*800 ( or similar ... now I don't remember very well)

---

### Post by quai_k8 on 2005-11-06
Hi ... try this : ctrl + alt + F2 .. when your computer has finished loading ^^

" excuse my english too ^^ "

if a black screen with white commands appears it's great !!
because your computer want to use external screen !!
Do what I say to use computer screen :

Enter your login and pass !!!

now config the file xorg.conf by writing :

> sudo nano -w /etc/X11/xorg.conf

add this line in Section "Monitor"

> Option     "MonitorLayout"     "LVDS,AUTO"

My Section monitor ^^ :

> Section "Monitor"
    Identifier    "&#201;cran g&#233;n&#233;rique"
    Option        "DPMS"
    Option        "MonitorLayout"        "LVDS,AUTO"
EndSection

I had the same problem with my acer travelmate 8101 !!!
I hope it help you !!



.... too late ^^ !!!

---

### Post by innovatel on 2005-12-05
I have a very intresting problem.

The clock is too fast and the time is not correct.

For example:

Now is 00.00 after 10 real minutes my pc time is 00.30

Some one have an idea?

Thank a lot

(ubuntu is a very good distro :cool: )

:KS good night @ all :KS

---

### Post by GuyveR800 on 2005-12-07
Read the threads about the Acer 5024WLMi (5020 series), the solutions should be the same for the 3020 series.

---

### Post by hericus on 2005-12-07
Heh.
:KS Anyway, I'm going to get an Acer Travelmate 4002LCi, we'll just see how it goes with the installation :KS 
:eek:

---

