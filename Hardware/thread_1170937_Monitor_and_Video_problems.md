---
title: "Monitor and Video problems"
date: 2009-05-26
forum: Hardware
---

### Post by lord4play on 2009-05-26
Hello everyone,
I'm sorry if I have posted in the wrong thread. I have a problem. Well ok I bunch of problems. But just a few in Ubuntu 9.04. I have installed Ubuntu 9.04 on my desktop as well as windows xp pro.
The problem I am having with Ubuntu is I can not install the Nvidia drivers if I want to use the computer normally. once I install the Nvidia drivers I can not use the computer normally. Yes I am a NOOB to Ubuntu I am sorry for that. So please be gentle with me.

This is a home built system I built it a while back it works Super in windows xp 

Here is a run down on the system 
AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
4GB ram
Dual EVGA 8500 GTs in SLI 
Mitsubishi Diamond Plus 200 monitor Model number NSH1117STTKW I have two of them but only one is hooked up at the moment
300 GB hard drive
250 GB hard drive 
DVD burner
DVD drive
Memory card reader
5 80mm case fans
2 120mm case fans
some dust and the kitchen sink

If you can help I thank you Since my new Laptop Just crashed it has Vista on it ( BAD Hard Drive)  I really hate vista 

Thank you for reading 
and thank you for any help you can provide
Jake

---

### Post by lord4play on 2009-05-27
From all the reading I have done it seems to be a problem with the monitor. Ubuntu does not recognize the monitor.

I have been searching for specs on the monitor but am unable to locate information on the monitor.


any help?   Please...Pretty please

Jake

---

### Post by Nevart on 2009-07-15
Hi, sorry for late reply!  Your problem is probably not the monitor, because that is a very common brand of monitor.  The reason nobody helped with your problem is that your description of the problem was not informative enough.

I hope that all new users will understand this important point... you need to say *much* more than just "it does not work normally".  You need to say how it *does* work, so for example do you just get a blank screen, or the colors don't look right, or it is upside down???  

We can't really give good advice unless we know what went wrong and what you were trying to do when the problem happened.

---

### Post by mister_p_1998 on 2009-07-15
If the problem is that the monitor is not displaying the correct resolution on boot, it sounds similar to a problem I had, Ubuntu detects the monitor as plug & play, which does detect all the correct resolutions. open a terminal & type:
gksu displayconfig-gtk

select your monitor type as something like: LCD panel 1280 X 1024
you might have to try a few before yo are happy but that may cure it. Also DO install the nvidia drivers preferably before doing the above.

Steve

---

### Post by krlosjcc on 2009-07-27
I did the above, but nothing showed as you said, I mean I couldn't select any resolution because nothing happened

---

### Post by zuerston on 2009-07-30
> **krlosjcc said:**
> I did the above, but nothing showed as you said, I mean I couldn't select any resolution because nothing happened

who are you?
:confused:

---

### Post by dagrump on 2009-07-30
If you install the nvidia drivers do you reboot into a CLI login? If this is the case, I might be able to help. I have 2 machines running SLI @ the moment.

*********
After the drivers are installed & it boots back up, go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.

Wow cut & paste worked, I didn't want type that all over!

Try that. It's how I was taught & it works on my rigs.

---

