---
title: "LightScribe problems"
date: 2013-03-29
forum: Hardware
---

### Post by vapor0 on 2013-03-29
I'm having a hell of a time trying to get LightScribe working on my Ubuntu box (which I wiped Windows off of and is my only pc with a LightScribe drive). 

I followed the instructions and installed the LightScribe basic software, and the application software, and did it with the force architecture, and the software runs. But it can't find my LightScribe drive. It says it can't connect to dbus.

So I tried compiling it, and got pretty far, until I got a cmake error complaining about an alarm loop function in the code. However, during this process I installed libdbus-dev, so I have no idea why it's not working.

Please help if you can, a magazine told me to send in a CD of my band's music and they'd review it. So I want it to look nice. 

Thanks. :guitar:

---

### Post by agillator on 2013-03-30
Does your computer recognize the lightscribe drive. Forget 'lightscribe' for a moment and simply put a data cd in the drive and see if it mounts, or if you can mount it. If not, then that problem has to be solved first. 
Once that is solved, try following the instructions at [https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe). The only software I have found that works is from LaCie (LaCie 4L) and those instructions are for installing it. I agree getting it to work can be a pain. When you do, write down what you did and save it so you know how to do it on your system next time. Once working it does a nice job of creating a monochrome label. I use it all the time.

---

### Post by vapor0 on 2013-03-30
I tested to see if it still read cd's, and it does. I followed those instructions, and have LaCie 4L working. But it doesn't detect the drive.

I solved the dbus problem simply by using sudo. Didn't fix the problem, tho.

---

### Post by agillator on 2013-03-30
This may not be news to you though I missed it earlier. I suspect your problem is that the software is 32 bit and your system is 64 bit. I did some googling and that seems to be a problem. See if this helps: [http://www.csamuel.org/2007/11/29/installing-lacie-4l-lightscribe-software-on-amd64-ubuntudebian-systems](http://www.csamuel.org/2007/11/29/installing-lacie-4l-lightscribe-software-on-amd64-ubuntudebian-systems). If not, googling for 'lacie 4l 64 bit' will give you several hits though they appear to all be in the same vein. Since I am not running the 64-bit version of Ubuntu I'm afraid I can't be of much more help.

---

### Post by adam12phoenix on 2013-12-31
Hello Everybody,

I'm having a similar problem getting lightscribe up and running. I recently switched to ubuntu 12.04 from XP and I'm loving the new OS. However, I just can't seem to get my beloved lightscribe up and going. I'm running a  rather ancient 32-bit system from the 2000's era, so the above compatability issues shouldn't be a problem. I've followed the advice in other threads but every time I visit the LaCie page and go to install the labeling utility (basic or the 4L) it want's to open in my movie player and not as an install package. Am I missing some key instruction here or is it simply a missing package that hasn't updated automatically for some reason?

Thanks in advance for the help guys. So far I've been able to solve my recent convert issues by digging through other posts, but I seem to have hit a brick wall here

Adam12

---

### Post by JDorfler on 2013-12-31
Go [here]("http://www.pawtec.com/lightscribe/") and download the System Software and the Simple Labeller.

For 64-bit

sudo dpkg --force-architecture -i /home/user/Download/lightscribe-latest.deb

sudo dpkg --force-architecture -i /home/user/Downloads/lightscribelatest.deb

Fix the missing liblightscribe.so.1 error

sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

sudo ldconfig

For 32-bit

sudo dpkg -i lightscribe-1.1810.2-linux-2.6-intel.deb

sudo dpkg -i lightscribeApplications-1.18.6.1-linux-2.6-intel.deb

Fix the missing liblightscribe.so.1 error

sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

sudo ldconfig

---

