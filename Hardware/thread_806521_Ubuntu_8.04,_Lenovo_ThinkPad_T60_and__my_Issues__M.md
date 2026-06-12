---
title: "Ubuntu 8.04, Lenovo ThinkPad T60 and  my Issues:  Modem, USB, FingerPrint"
date: 2008-05-25
forum: Hardware
---

### Post by m.h.shams on 2008-05-25
hi friends,

i have a ThinkPad T60 fresh ubuntu installed.

please help me to config followings: 

1 - Dial up Modem : i don't know how to do it

2 - Blue Tooth : there is no device detected in bluetooth applet.

3 - Finger Print Detect : i don't know how to do it

4 - Desktop Effect can't be enabled.

thanks

---

### Post by Steve413z on 2008-05-25
if the bluetooth LED isn't on under the screen, you need to activate the bluetooth device by pressing "Fn + F5" (possibly multiple times, the same button controls the WiFi, and bluetooth)

---

### Post by hotweiss on 2008-05-25
> **m.h.shams said:**
> hi friends,

i have a ThinkPad T60 fresh ubuntu installed.

please help me to config followings: 

1 - Dial up Modem : i don't know how to do it

2 - Blue Tooth : there is no device detected in bluetooth applet.

3 - Finger Print Detect : i don't know how to do it

4 - Desktop Effect can't be enabled.

thanks

Try these instructions for the finger print reader:

A) First we&#8217;ll need to add the driver source to our software repository by typing the following in Terminal to open the sources list:
> sudo nano /etc/apt/sources.list

B) Now scroll to the end of the file and paste the following line there:
> deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Update the source list by typing the following in Terminal:
> sudo aptitude update

E) Install the fingerprint reader driver by typing the following in Terminal:
> sudo aptitude install fprint-demo libpam-fprint libfprint

F) Enroll your fingerprint by typing the following in Terminal:
> sudo fprint_demo

G) Click on Enroll and swipe your finger.

H) Now we will have to tell Ubuntu when to use your fingerprint by editing the fingerprint reader driver&#8217;s configuration file by typing the following in Terminal:
> sudo nano /etc/pam.d/common-auth

I) Paste the following in the file at the end:
> auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure

J) Hit Ctrl-O to save and then Ctrl-X to exit.

H) Reboot, and you will be now scanning your finger instead of typing your password each time.

---

### Post by m.h.shams on 2008-05-26
- bluetooth device was off default. i turned it on and its work fine.

  sorry about my stupid mistake. ;)


know just dial up modem is the big problem. i read somewhere that T60 modem is Conexant. is it true ???

any success story about Conexant on Ubuntu 8.04 64Bit ?


thanks all.

---

