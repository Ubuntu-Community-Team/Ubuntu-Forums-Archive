---
title: "Won't install upgrade to 8.04"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by paul.macdonnell@gmail.com on 2009-09-21
I bought my Dell Inspiron Mini 10 about 3 months ago. When I plugged it in and booted it up it automatically tried to download and install updates to Ubunto 8.04. It downloaded updates but when it tries to install them I get the following message...

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline 

Ideally I'd like a solution to this that doesn't require a serious operation on the OS.. Any ideas..?

Paul

---

### Post by Partyboi2 on 2009-09-21
Hi, open a terminal (Applications>Accessories>Terminal) and type or paste
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libxcb-shape0.list
```
```
sudo dpkg --configure -a
```

---

### Post by paul.macdonnell@gmail.com on 2009-09-21
> **Partyboi2 said:**
> Hi, open a terminal (Applications>Accessories>Terminal) and type or paste
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libxcb-shape0.list
```
```
sudo dpkg --configure -a
```
Hi - I'm very, very new to Ubuntu...so forgive me if I make some elementary mistake. i did what you suggest - I take it I'm supposed to hit 'Return' between the two lines of code??

In any case when I do it nothing happens......I mean the code goes in I hit return and ...it just gives me another prompt...? I'll try it again.,,,

---

### Post by BraedenNaylor on 2009-09-21
> **paul.macdonnell@gmail.com said:**
> Hi - I'm very, very new to Ubuntu...so forgive me if I make some elementary mistake. i did what you suggest - I take it I'm supposed to hit 'Return' between the two lines of code??

In any case when I do it nothing happens......I mean the code goes in I hit return and ...it just gives me another prompt...? I'll try it again.,,,

Yes press return after each line. After you finish that run the updates again using update manager.

---

### Post by paul.macdonnell@gmail.com on 2009-09-21
Hi - This what happens...paul@paul:~$ echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libxcb-shape0.list [I press return and it prompts me with - ]
[sudo] password for paul: [I enter password here and press return]

paul@paul:~$ sudo dpkg --configure -a [I press return]
paul@paul:~$ [another prompt???]

I close the window and run the update...and eventually get - 

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' contains empty filename

- so. it doesn't work...??

---

### Post by Partyboi2 on 2009-09-22
Looks like it did not work, open a terminal again and move the list file with
```
sudo mv /var/lib/dpkg/info/libxcb-shape0.list /var/lib/dpkg/info/libxcb-shape0.lis.broke
```
then try reinstalling the 'libxcb-shape0' package with
```
sudo apt-get --reinstall install libxcb-shape0 
```
Then try updating again.

---

### Post by paul.macdonnell@gmail.com on 2009-09-22
Wonderful. It worked a treat. Many thanks for your help.

---

