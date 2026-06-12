---
title: "Fingerprint Reader -- Gutsy -- Thinkpad T60"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Zetheroo on 2007-10-20
Hi there,
for some reason under Feisty my fingerprint reader was working wonderfully with Thinkfinger 0.3.

However since upgrading to Gutsy and reinstalling and setting thinkfinger up once more, it no longer works.

Installation of Thinkfinger 0.3 works.
Adding a user and inserting the 3 finger scans works.
In fact everything from this How-To works 100% ([https://wiki.ubuntu.com/ThinkFinger]("https://wiki.ubuntu.com/ThinkFinger"))

But when its time for the system to work, like upon login where you expect to scan your finger instead of enter a password, it does not work.

It is strange because it worked once, and then never worked again.
Please help!:(

---

### Post by Zetheroo on 2007-10-20
I'll have to keep posting in here to keep it on the first page -- I suppose.....

Please anyone have any thoughts on the issue?

---

### Post by alin.selea on 2007-10-21
One more step and you are done:
 
Edit /etc/modules and add the following line:
 uinput
Load the module manually for this session:
$ sudo modprobe uinput

It should work now.

---

### Post by jamesjtucker on 2007-10-24
This is not working for me on a t61p. It was working a while back (i have been running gutsy since tribe 5 came out) It seems that i have all the necessary deps. Any ideas?

jtucker@firefly:~$ lsmod | grep uinput
uinput                 10368  0 
j
jtucker@firefly:~$ sudo apt-cache search thinkfinger
[sudo] password for jtucker:
thinkfinger-tools - utilities for the STMicroelectronics fingerprint reader
libthinkfinger-dev - development files for libthinkfinger
libthinkfinger-doc - documentation for libthinkfinger
libpam-thinkfinger - PAM module for the STMicroelectronics fingerprint reader
libthinkfinger0 - library for the STMicroelectronics fingerprint reader
jtucker@firefly:~$ tf-tool

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

---

### Post by bantu on 2007-10-24
Follow the steps mentioned before. In addition, you will have to create a new directory: /usr/etc/pam_thinkfinger. 
For some obscure reason, that's where thinkfinger wants the user's authenitication files... (instead of /etc/pam_thinkfinger)... After creating this dir, add your user with "sudo tf-tool --add-user YOURUSERNAME".
Good luck, this worked for me on a Lenovo Thinkpad R60!

---

### Post by jamesjtucker on 2007-10-24
Which steps mentioned before, im pretty sure i have done all of them. 

i symlinked /etc/pam_thinkfinger to /usr/etc/pam_thinkfinger, and still no joy. I still do not see the "password or swipe finger" dialog when i log in.

---

### Post by bantu on 2007-11-02
Well, I basically followed the step described here (as far as I can remember):
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
In addition I had to create the afore mentioned directory, /usr/etc/pam_thinkfinger.
Then I loaded the uinput module and added swiped my fingers...

OK, let's see, step by step...
1)
download and compile according to [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
2)
sudo gedit /etc/modules 
and add the following line:
uinput
Load the module manually for this session:
$ sudo modprobe uinput
3)
test the fingerprint reader (still following the wiki entry)
4)
sudo mkdir /usr/etc/pam_thinkfinger
(that's what I did, no idea if symlinking will work)
5)
Follow the instruction under the heading "Use it everyday" in the wiki entry.
6)
reboot, and hopefully you will see the "swipe finger" in gdm...

Good luck!

---

### Post by zorkerz on 2007-11-05
[LEFT]I think i followed the same instructions on the thinkwiki site. I am having some odd behavior now with synaptic that i think is related. The first time it opens it only shows up in my gnome panel for a few seconds then disappears. Next time i try and open it the thinkfinger does not work for it.

i have used the scanner for sudo commands in terminal and when gnome asks for passwords through gui only synaptic has not worked.

Thinkwiki mentions something about gksu not working is this what is going on?

Does synaptic package manager open with gksu not sudo? How is this different?
[/LEFT]

---

### Post by hvac3901 on 2007-12-05
> **bantu said:**
> 
sudo mkdir /usr/etc/pam_thinkfinger
(that's what I did, no idea if symlinking will work)


for some reason I had to make these directories one at a time, is that what SYMLINKING does ???

---

### Post by esodin on 2007-12-05
> **bantu said:**
> Well, I basically followed the step described here (as far as I can remember):
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
In addition I had to create the afore mentioned directory, /usr/etc/pam_thinkfinger.
Then I loaded the uinput module and added swiped my fingers...

OK, let's see, step by step...
1)
download and compile according to [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
2)
sudo gedit /etc/modules 
and add the following line:
uinput
Load the module manually for this session:
$ sudo modprobe uinput
3)
test the fingerprint reader (still following the wiki entry)
4)
sudo mkdir /usr/etc/pam_thinkfinger
(that's what I did, no idea if symlinking will work)
5)
Follow the instruction under the heading "Use it everyday" in the wiki entry.
6)
reboot, and hopefully you will see the "swipe finger" in gdm...

Good luck!

I have followed the above instructions, but when I run "sudo tf-tool --add-user USERNAME" I get:
[I]
Initializing... done.
Could not acquire fingerprint (communication with fingerprint reader failed).[/I]

Any ideas? :confused:

---

### Post by hvac3901 on 2007-12-05
I wouldn't worry about it too much. its isn't as fully integrated, as it is in windows, it is little more than a novelty in Ubuntu. since it isn't fully integrated to be a function for all password entries.

Ok since i vented my frustration...:) you failed to mention your hardware, what are you working with. I have a link to somewhere that will make it work or tell you what doesn't

---

### Post by esodin on 2007-12-05
@havc3901
Thanks for the feedback. I am on a Sony Vaio SZ28GP (I am in Australia - the US and Europe [?] Vaio SZ numbers are different)


I managed to find some Vaio speciffic instructions [here]("http://okoye.wordpress.com/2007/10/24/configuring-ubuntu-gutsy-with-thinkfinger-fingerprint-reader-intel4965-card-and-intel-x3100-running-compiz-fusion-working/")

I now do get a request to "Enter password or swipe finger" at login. Trying to run "sudo tf-tool --acquire" iit does seem to recognize something, but I still get the same error:

```
jomar@je-linux-vaio:~$ sudo tf-tool --acquire
[sudo] password for jomar:
Password or swipe finger: 

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing... done.
Could not acquire fingerprint (communication with fingerprint reader failed).
jomar@je-linux-vaio:~$ 
jomar@je-linux-vaio:~$ 
```

Any thoughts?

---

### Post by ryanVickers on 2007-12-05
wo wo wo wo, hold on here, you have a fingerprint reader!!?!?! :P

---

### Post by hvac3901 on 2007-12-05
well the other gent raises a good point, are you using an external reader? or hard mounted?

second  of all the problems i had loading the function, I didn't get that error, nor did i find documentation on it or referring to it. You might assume its a hardware issue. your system manufacturer is different than mine, your fingerprint reader appears to be the same as mine. you will likely need manufacturers help documents to fix it.

---

### Post by esodin on 2007-12-06
Yes, I do have an internal FP reader.

```
jomar@je-linux-vaio:~$ lsusb
Bus 001 Device 008: ID 03f0:0217 Hewlett-Packard 
Bus 001 Device 007: ID 046d:c313 Logitech, Inc. 
Bus 001 Device 009: ID 045e:0084 Microsoft Corp. 
Bus 001 Device 003: ID 054c:0281 Sony Corp. 
Bus 001 Device 005: ID 05ca:1830 Ricoh Co., Ltd 
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```

It would be nice to take a look at the manufacturers docs, but Sony has never been very helpful with anything - particularly if they did not supply the software. :(

---

### Post by hvac3901 on 2007-12-07
vaiowiki.com check there. hope it helps.

---

