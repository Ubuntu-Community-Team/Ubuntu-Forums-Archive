---
title: "radeon x1600 512mb agp....fglrx...=black screen cry for help!Can anyone help me with."
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by devilsrogue on 2008-02-19
Ok heres my problem 

I have a ati radeon vanilla(factory ATI)and everything works fine under windows.I wanted to install ubuntu because I am so dead sick of windows(PERIOD the way it looks,works,it gets so slow after a while and im just plain sick of it)

The problem is that when I try to enable the restricted module(driver) in ubuntu for my graphics card it asks me to reboot so I do and when it loads back up I get nothing but a black screen.I know a lot of others have had this problem but i couldnt figure out what to do.I want to be able to run the 3d desktop effects(beryl)as well.I tried installing the ati drivers fromt he site with the ati wiki too and still no luck

my system config
mobo=MSI K8n-Neo platinumn (socket 775 the older athlon 64 kind)This one uses Nvidia nforce 3 250gb chipset
2gb ram
agp ati radeon x1600 512mb card
80gb pata drive
dvdrw/cdrw sata drive

So if anyone could point me towards any how-tos or got anything theirselves lets me know:) thank you

---

### Post by AFCB on 2008-02-19
> **devilsrogue said:**
> Ok heres my problem 

I have a ati radeon vanilla(factory ATI)and everything works fine under windows.I wanted to install ubuntu because I am so dead sick of windows(PERIOD the way it looks,works,it gets so slow after a while and im just plain sick of it)

The problem is that when I try to enable the restricted module(driver) in ubuntu for my graphics card it asks me to reboot so I do and when it loads back up I get nothing but a black screen.I know a lot of others have had this problem but i couldnt figure out what to do.I want to be able to run the 3d desktop effects(beryl)as well.I tried installing the ati drivers fromt he site with the ati wiki too and still no luck

my system config
mobo=MSI K8n-Neo platinumn (socket 775 the older athlon 64 kind)This one uses Nvidia nforce 3 250gb chipset
2gb ram
agp ati radeon x1600 512mb card
80gb pata drive
dvdrw/cdrw sata drive

So if anyone could point me towards any how-tos or got anything theirselves lets me know:) thank you

have u waited very very time to see if he turn on???

see that

---

### Post by devilsrogue on 2008-02-19
Yeah I gave it like 10 mins but i figure there is something wrong because it locks up the whole system( i cant even use cntrl alt bckspc):lolflag:

---

### Post by AFCB on 2008-02-19
what your recomended resolution for your monitor???
the ubuntu logo apears during the loading??

---

### Post by devilsrogue on 2008-02-19
Yes the ubuntu logo appears and it loads then black screen(its not like the monitor goes out of range because it would say that)and it does this right before it would usually display the login screen

It can go up to 1600x1200 and up to 120hz so i know it cant be going out of range

---

### Post by AFCB on 2008-02-19
> **devilsrogue said:**
> Yes the ubuntu logo appears and it loads then black screen(its not like the monitor goes out of range because it would say that)and it does this right before it would usually display the login screen

It can go up to 1600x1200 and up to 120hz so i know it cant be going out of range


but what are the recommended resolution?

---

### Post by devilsrogue on 2008-02-19
It is 1600x1200@85 hz

---

### Post by AFCB on 2008-02-19
with the recovery mode hit:
[B]
sudo nano /etc/usplash.conf[/B]

and

**uname -r**

and tel me what appear

dont make any changes at the moment..

---

### Post by devilsrogue on 2008-02-19
I am on windows now lol.....I just did a complete reinstall.I will reinstall ubuntu real fast and get that for you

---

### Post by devilsrogue on 2008-02-19
It says 

1280
1024

I tried changing it and nothign so I changed it back

---

