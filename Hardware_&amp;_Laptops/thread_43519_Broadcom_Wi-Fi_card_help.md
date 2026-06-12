---
title: "Broadcom Wi-Fi card help"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by Lrodom on 2005-06-22
I just put ubuntu on my laptop but I cant seem to get the w-fi card to work.  Ive tried working with ndiswrapper but I keep getting a "FATAL:error blah blah blah" message.  not sure what the problem is.  I tried following a guide online that used my same wi-fi card and drivers but I got the error message when I used the "modprobe ndiswrapper" command.  If anyone has any helpful info, I would greatly appreciate it.  Thanks in advance.   ](*,)

---

### Post by aamir on 2005-06-22
can you give me more info like which card you are using, and the exact error, I'd be happy to help you out.

---

### Post by Lrodom on 2005-06-22
thanks for the reply, im at work right now and my laptop is at the house.  Ill be home in about 5-6 hours and Ill post which error Im getting.  The card is made by Broadcom Corp.  I found some info online and a guide which walked me through the process to get his card working, but like I said, I received an error message.  Ill be sure to post up the message when I get home...  I may post it at lunch.  Look to see if you see a message from me in about 2 hours or so.  Thanks again.

---

### Post by Lrodom on 2005-06-22
ok so i didnt get to go home for lunch, so I should have that info up when I get home this afternoon.  thanks again

---

### Post by Lrodom on 2005-06-22
here is the error i get when i do modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by skyguy on 2005-06-23
I was getting this error trying to use the ndiswrapper-1.1 package with the -686 kernel. I solved it by installing the -386 kernel and booting off that. Alternatively, dig around for the instructions on how to compile ndiswrapper and compile it for the kernel you're using now.

---

### Post by Lrodom on 2005-06-23
[QUOTE=skyguy]I was getting this error trying to use the ndiswrapper-1.1 package with the -686 kernel. I solved it by installing the -386 kernel and booting off that. Alternatively, dig around for the instructions on how to compile ndiswrapper and compile it for the kernel you're using now.[/QUOTE]
 Yeah i think thats what I did, i was using ndiswrapper-1.2 with the 686 kernel.  still gave me the same error.  any suggestions?

---

### Post by aamir on 2005-06-23
you don't have ndiswrapper-source installed

apt-get this package then reboot see if the card works

---

### Post by phantom on 2005-06-23
I had the same issue here is what I did:

Scan your disks for any files called ndiswrapper.ko, they should be in /lib/modules and /usr/src, delete them all !!

go to the downloaded Ndiswrapper 1.2 dir and do "make clean" followed by "make" and "make install"

Install your drivers like this "ndiswrapper -i bcmwl5a.inf" and modprobe it, it should work.

---

### Post by acascianelli on 2005-06-24
[QUOTE=phantom]I had the same issue here is what I did:

Scan your disks for any files called ndiswrapper.ko, they should be in /lib/modules and /usr/src, delete them all !!

go to the downloaded Ndiswrapper 1.2 dir and do "make clean" followed by "make" and "make install"

Install your drivers like this "ndiswrapper -i bcmwl5a.inf" and modprobe it, it should work.[/QUOTE]

I'm also trying to get my Broadcom wireless working.  I had it working with the earlier array releases of Hoary but I can't seem to do it with the final release.

After I install the drivers I get the same operation not permitted error, but I noticed that when I do a "ndiswrapper -l" it shows the driver as being invalid.

---

### Post by byen on 2005-06-25
Well. i  have a  broadcom wlan chip and had similar problems until i found this walkthrough...see if it helps..good luck.
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

### Post by acascianelli on 2005-06-26
[QUOTE=byen]Well. i  have a  broadcom wlan chip and had similar problems until i found this walkthrough...see if it helps..good luck.
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)[/QUOTE]
 Sweet...

That worked flawlessly.  I think my problem was I had the .inf file but I didnt have the .sys file.

Thanks again.

---

### Post by byen on 2005-06-27
[QUOTE=acascianelli]Sweet...

That worked flawlessly.  I think my problem was I had the .inf file but I didnt have the .sys file.

Thanks again.[/QUOTE]
 lol. acascianelli.... would you believe it if i told you I wrote the message sitting at a place, less than a couple of miles away from sterling heights...funny!

---

### Post by Lrodom on 2005-06-29
[QUOTE=byen]Well. i  have a  broadcom wlan chip and had similar problems until i found this walkthrough...see if it helps..good luck.
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)[/QUOTE]

THANK YOU THANK YOU THANK YOU  for showing me this!  IT finally works  :smile:

---

### Post by acascianelli on 2005-06-29
[QUOTE=byen]lol. acascianelli.... would you believe it if i told you I wrote the message sitting at a place, less than a couple of miles away from sterling heights...funny![/QUOTE]

Haha, small world...

Somebody should host an Ubuntu meet or something :D

---

