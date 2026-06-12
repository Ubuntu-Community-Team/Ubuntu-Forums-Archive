---
title: "Belkin USB to serial adapter"
date: 2008-07-30
forum: General Help
---

### Post by SmarterThanMyPhone on 2008-07-30
I have a Belkin F5u109 serial to usb adapter that I use to console into my cisco routers, I'm trying to figure out how to make my ubuntu 8.04 see that I have that plugged in so I can access my routers.

---

### Post by SmarterThanMyPhone on 2008-07-30
I'm trying to find another device that advertises linux support, if I find one I'll post with details.

---

### Post by fwre01 on 2008-07-30
I think my usb-to-serial adapter is a different make (prolific i think), but it normally appears as /dev/ttyUSB0, i use minicom as the terminal program, it seems pretty good

i think you can check if its recognized by doing an "lsusb"

---

### Post by ModelM on 2008-07-30
If this is like most of these devices, when you plug it in it should appear as:

/dev/ttyACM0

is that device not present?

---

### Post by SmarterThanMyPhone on 2008-07-31
ok I got the device recognized and installed cutecom via synaptic, my connection fails with the message;

```

tcsetattr() 2 failed
tcsetattr() 3 failed
tcsetattr() 1 failed
tcsetattr() 4 failed
tcsetattr() 2 failed

```

---

### Post by ModelM on 2008-07-31
Ya got me. I've never seen this. I suppose the first thing I'd try is experimenting with different baud rates.

---

### Post by SmarterThanMyPhone on 2008-07-31
yea thats what I thought too, I've tried 3 so far with the same result. cool app though, I like the little gui.

---

### Post by kbf on 2008-08-03
```

tcsetattr() 2 failed
tcsetattr() 3 failed
tcsetattr() 1 failed
tcsetattr() 4 failed
tcsetattr() 2 failed

```[/QUOTE]

Got the same with an Prolific Technology, Inc. PL2303 Serial Port

---

### Post by fwre01 on 2008-08-03
have u tried using a different application?

---

### Post by SmarterThanMyPhone on 2008-08-04
no, I did try to install winagents hyperconf via wine, but it wouldnt install. what other applications could I try? I did a search for linux ios editor, and cute/minicom are the only ones ive seen so far.

---

### Post by fwre01 on 2008-08-04
I would advise minicom out of the two, i have used minicom for a while on lots of different cisco boxes, i think theres another one call gtkterm, but i havent used that so cant comment on it.

do a sudo apt-get install minicom
then once its installed run "minicom -s" and set the device settings, save it.
then just run it using the command minicom

---

### Post by Beltic on 2008-08-04
> **SmarterThanMyPhone said:**
> I have a Belkin F5u109 serial to usb adapter that I use to console into my cisco routers, I'm trying to figure out how to make my ubuntu 8.04 see that I have that plugged in so I can access my routers.

I was able to use mine by using /dev/ttyUSB0 with putty - works great.

---

### Post by fwre01 on 2008-08-05
...or putty, i forgot they had a linux client! putty is brilliant in windows, i can only hope its as good in linux.

Beltic, how have u found serial support in putty on linux? i found on windows it used to sometimes cut me off with a strange error (which i cant remember off the top of my head)

---

### Post by cbulleri on 2008-09-25
Hi, 

Im trying to install a F5u409 in my Ubuntu run 8.04. 

this is what i see when I list all the USB devices under the dev folder. 

usbdev1.1_ep00  usbdev2.1_ep81  usbdev2.2_ep81  usbdev3.1_ep81
usbdev1.1_ep81  usbdev2.2_ep00  usbdev2.2_ep82  usbdev4.1_ep00
usbdev2.1_ep00  usbdev2.2_ep02  usbdev3.1_ep00  usbdev4.1_ep81

I don't see the usb0 device as mention before. 

Maybe I'm missing something in order to allow Ubuntu to detect the device first properlly. 

offcourse Im a Ubuntu newbe and I appreciate all the help I can get. 

I'm trying to use putty as well. 

Thanks

Carlos

---

### Post by fwre01 on 2008-09-25
Can you paste the output from ```
 lsusb 
```

---

### Post by SmarterThanMyPhone on 2008-09-25
I dont rememner exactly what I did to make my usb adapter work, it never worked 100%, there were random errors and it was really slow so I just use a machine with a serial port now. I'll revisit the usb adapter and post the solution I used maybe it will work better for you.

---

### Post by deadpistoria on 2008-12-23
I have a different use for the cable, trying to connect to my bct15 using free scan under wine.

my lsusb:
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 050d:0109 Belkin Components F5U109/F5U409 PDA Adapter
Bus 001 Device 001: ID 0000:0000  

no problem, but i cant get freescan to recognize a comport under wine so it can connect to the scanner.

thoughts?

---

