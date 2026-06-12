---
title: "Canon LBP-6200"
date: 2012-04-13
forum: Hardware
---

### Post by tora201 on 2012-04-13
Just got this printer. Any ideas on how to get it going in 12.04 64 bit? Have followed the numerous guides around but the thing just won't print. 

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

If anybody has actually managed to get it going, please do let me know. The thing is, I have tried so many things that I reckon my system/CUPS is probably completely broken now. 

Oh, and I did actually manage to make the thing print a test page! Just once. After that, not a damned thing no matter how much I re-installed/deleted/removed changed settings. 

I know - should probably have experimented with a live CD first....

---

### Post by tora201 on 2012-04-13
Somehow got it printing (for the time being?) Still trying to figure out how. 

All I know is that the device URI should be: ccp:/var/ccpd/fifo0
(I manually changed it in the print properties, from: 
ccp://localhost:59787

Will do some more testing on another machine when I have a moment.

Apart from the guide above, other things I did that may have made a difference:

1) Make sure usblp is not blacklisted.
2) Changed paper size to A4 as default 
3) Step 6-9 of this post seems to be important: [http://ubuntuforums.org/showthread.php?t=1315665](http://ubuntuforums.org/showthread.php?t=1315665)
4) Good luck! Believe me, you'll need it.

Finally, if somebody really does know the EXACT steps to get these printers going, please do post. Seems to be rather hit & miss.

---

### Post by tora201 on 2012-04-23
Got fed up with it and installed 12.04 32 bit. Immediately more of a success following instructions from the Wiki. It works (kind of) The problem is it prints just one job. After that, nothing; nada; naught....

Thoughts? Somebody must have some idea?

Cheers.

---

### Post by Sivella on 2012-04-25
Hello tora201

I have a Canon LBP5000, using the same drivers than your LBP6200.
I have installed 12.04-32bits in order to help you  ;)

Here is the way I have succeed to run my LBP5000:

Using the drivers provided by Canon, version 2.40.
1) Install **cndrvcups-common_2.40-1_i386.deb**.  Take care dependence: libglade2-0 is needed.

2) Install **cndrvcups-capt_2.40-1_i386.deb**

3) Restart cups:
> sudo service cups stop
sudo service cups start4) Create the following directories/file:
> sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon5) Register the printer:
> sudo /usr/sbin/lpadmin -p LBP6200 -m CNCUPSLBP6200CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E6) Register the printer with ccpd daemon:
> sudo /usr/sbin/ccpdadmin -p LBP6200 -o /dev/usb/lp07) Start ccpd daemon (no need to modify):
> sudo /etc/init.d/ccpd startTest install:
> captstatusui -P LBP6200will open the Statusmonitor window. If the message "Ready to print" is displayed --> all is OK.

Following this procedure my LBP5000 prints like a charm a huge of papers ...

Don't forget to PURGE (not only remove) previous Canon drivers install before trying this.

Good luck.
Hope my message well understandable, english is not my native language.

---

### Post by tora201 on 2012-04-25
Sivella, thank you! I'll try it as per your instructions and let you know. I really appreciate your help. 

By the way your English is perfect!

---

### Post by tora201 on 2012-04-26
Hey there Sivella,

It works (kind of) but I'm having a similar same problem I had before (when trying various things). It prints but after one job I get this error in captstatus monitor:

"Load [Letter] paper, and then press the Paper key of the printer.
See the instruction manual for more information on how to load paper.
To do 1-sided printing with the currently loaded paper, click [Resume Job]."

If I click "resume" it prints the same job again and again. Or, if I push the "paper key (its flashing now) then, it prints the same job.

The only way I can print anything else is to close the captstatus monitor, and then reopen it. Then I can print, but just one job again - then I get the same error.

Finally, I changed the default paper to A4 in the printing preference, but that made no difference.

P.S the CCPD script times out as well, if I leave it idle for more than a few minutes. It works again if I re-run it in a terminal, but of course, the above error re-occurs as well. Aaagghhh..... any proposed solutions?

---

### Post by Sivella on 2012-04-27
Hello,

Very strange, it is the first time I heard such problem and I never had such things with my LBP5000.

Does your printer able to print on the other side ?
If yes, try to disable it in the preferences

Are you using A4 our letter "real paper" ?

An other thing strange is the CCPD daemon times out "alone"...
If you start it manually with :
> sudo /etc/init.d/ccpd start                      there is no reason it stops.
Hope it is not a bug in the Canon drivers.

Is there a "new" LBP62000-2 (self detected) ?

I still look for.

---

### Post by tora201 on 2012-04-28
I really to appreciate it. If you find out anything, please do let me know.

---

### Post by Sivella on 2012-04-30
Hello,

Just an idea.
Your printer LBP6200 is also supported by the version 2.3.
Look at:
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

there is a link to download this version.

Why not trying this version instead of the 2.4 ???

---

### Post by tora201 on 2012-04-30
That's actually a good idea! Will try it and let you know the result. Thanks.

---

### Post by tora201 on 2012-05-14
Didn't work.... And 6200 has only been "supported" since 2.40. Sigh. Anyway, thanks for your help.....

---

### Post by Sivella on 2012-05-16
Bad luck  :(
I run out  any other idea .
I have looked about LBP6200 on other "non-english" Ubuntu forum, but nothing similar.
Most of the others Canon LBP printers using CAPT Drivers work well using the procedure in my post#4
Sorry.

---

