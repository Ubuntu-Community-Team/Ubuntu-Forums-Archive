---
title: "No Monitor"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by Duffman on 2006-06-02
When i use the live cd(amd64 desktop) to boot in not graphics safe mode it just goes to a black screen after loading and when i use graphics safe mode it brings up the X error message saying that there is no monitor... This was the same thing that happened with badger.

I have a MSI 1036 with a x700 and 17in monitor.

If you need anymore info tell me

---

### Post by Duffman on 2006-06-02
I went back in to Graphics safe mode and ran Sudo dpkg-reconfigre xserver-xorg now i dont know excatly what kind of monitor is on my laptop but i ran through the whole config did what i thought was right with the default resolution and everything and when i startx it gave me the error again

(EE)RADEON:No valid modes found
(**)RADEON:Radeon Freescreen
(EE)Screen(s) found but none have valid configurations

Fatal server error:
no screens found
fatal IO error 101


Now i know other people have gotten their monitors not detected and for the most part they could just install it to the HD and it would work. Im not sure i want to do that yet incase it still doesnt work. If someone could help me out on this on it would be greatly apprieciated.

---

### Post by Duffman on 2006-06-02
Bueller?

---

### Post by Duffman on 2006-06-03
ok so i installed it and still  nothing and i screwed up my windows. i need to get it working plz help

---

### Post by Duffman on 2006-06-06
Ok i went out and bought a new monitor so that i could plug it into my DVI port but i cant get it to become to used monitor. Is there anything i can do to activate it?

---

### Post by bob_the_d on 2006-06-15
Yeah, I'm having the same problem.  I'm trying to install Dapper AMD x64 on my ATi x800 GTO / Dell 2005FPW monitor.  Nobody's been able to tell me how to fix it, nor have I found any working solution on the forums.  Quite frustrating to encounter this kind of a roadblock even before it's installed.

---

### Post by Duffman on 2006-06-15
Ok what i did to fix this is start up in graphics safe mode.

```
sudo dpkg-reconfigure xserver-xorg
```

Then choose the vesa drivers instead of ATI and it should work.

---

### Post by bob_the_d on 2006-06-15
Yeah, I read about that too.  I've been trolling the forums and the archives for quite some time trying to figure out a solution to my situation.  When I start up in safe mode (the second option in the menu) it just goes through the loading thing and then after a while the screen goes blank, and the monitor light turns orange indicating that it's searching for a signal.

I'm new to the whole linux thing, and I heard Ubuntu is great with detecting hardware (little bit of irony here) so needless to say I'm a little vexed with the situation.

---

### Post by Duffman on 2006-06-15
When it loads up do you hear bells in the background? If you do that means that it loaded into ubuntu.

Press i believe its ctrl+shift+f1 to stop Xorg then it should bring you to a command line. 

Hopefully someone with more knowledge can help you because i dont know much either.

---

### Post by bob_the_d on 2006-06-15
Nope, no bells.  While I'm not positive, I've been working with computers for 20 years and my gut instincts tell me that the computer locks up with I do that.

But yeah, I'm in the same boat.  I've been working with Windows and Mac for the entire time, and this is my first stab at Linux.  Needless to say, it's a little confusing.  While I knew it would be challenging, I didn't think it would be so challenging that I couldn't even get the installation up.

---

### Post by bob_the_d on 2006-06-15
Great.  So I did the regular one and after it gives me an error message, it spits me back out onto the console.  I thought that was good, so I ran the command you gave me and it takes me through the configuration process.  However, after I pick the color depth in bits, it quits and gives me the following message:

xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20060615213515
ubuntu@ubuntu:~$

I was wondering if I'm on the right track at all, and if so, what do I do from here?

---

### Post by bob_the_d on 2006-06-17
I tried just launching X after doing that configuration, but what happens is that the screen goes blank and then the monitor status light blinks orange like it's trying to search for a signal.

---

### Post by bob_the_d on 2006-06-17
I also tried doing the steps outlined in another forum post:

[http://ubuntuforums.org/showthread.php?t=197324](http://ubuntuforums.org/showthread.php?t=197324)

Doesn't work either.

Does nobody have any ideas why this is happening?  Any ideas at all no matter how absurd you think it is.

---

### Post by bob_the_d on 2006-06-18
bump

---

