---
title: "some problem with Dell inspirion 640m"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by ryon on 2007-01-17
ubuntu is a first linux i'm trial. i download and burn to cd then i boot by that cd they have a problem.i take a photo that
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007512.jpg[/IMG]
then
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007513.jpg[/IMG]
then
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007514.jpg[/IMG]
and
[IMG]http://i107.photobucket.com/albums/m290/ryon_handsome/16012007515.jpg[/IMG]

How can i fix that.i'm never use linux before.
my laptop is Dell inspiron 640m
sorry because my english is limited

thanks a lot

---

### Post by MadmanTM on 2007-01-17
it would help if we had more details :(

is the boot function of your pc, for the cdrom so you could boot.

---

### Post by ryon on 2007-01-18
my laptop use ubuntu 6.10
14.1" Wide Screen XGA TFT Display
in [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell) 
this website say i must to install package 915resolution for fix X but i don't know what is this.
Can you help me find that and tell me how to install that.
thank you very much

---

### Post by orengolan on 2007-03-12
hi, I have the same problem, any news about fixing it?

---

### Post by catoctin on 2007-03-15
Here's how I installed Ubuntu 6.10 on my Dell Inspiron 640m.

Problem: Can't install 6.10 using Live CD, because of graphics problem.
Solution: Install 6.10 in text mode by using alternate installation CD.

Step 1
Dowload alternate CD located here: [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
 --> choose: **Other installation options** including 64 bit CD images, server installation CDs and alternative installation methods for OEM computers and computers with less than 192MB RAM.

Step2
Install 6.10 in text mode, using the alternate installation CD.

Step 2
After installation, restart the system, when GRUB loads, use the ESC key to boot into "recovery mode"
Note: there will be several options, choosing the recovery mode allows you to get into Ubuntu through the command line interface (text mode).

Step 3
Log into Ubuntu (text mode).

Step 4
Install 915resolution, by typing in:
sudo apt-get install 915resolution


Once 915resolution is installed and you restart your system, everything should be working.

I hope this helps. I'm new to Linux; if I left anything out, please correct me.

---

### Post by orengolan on 2007-03-16
thanks for the great tips.

i solved it in a different way:
I connected an external monitor and than I could see GUI of ubuntu,
than i installed the 915solution and the problem was fixed!

thanks again.

now i have issue with my wireless connection (I can connect throw LAN) - 
[B]When I run lshw I see that my wireless is disabled.
[/B]I try clicking on fn+ f2 but it doesn't do anything.
any ideas?
I've heard that in the bios you can activate the functions key, is it true?
how can i do it?
i

---

### Post by orengolan on 2007-03-16
...and here is my post about this problm:
[http://www.ubuntuforums.org/showthread.php?t=386292](http://www.ubuntuforums.org/showthread.php?t=386292)

---

