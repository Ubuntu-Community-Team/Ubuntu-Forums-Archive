---
title: "wireless connecton"
date: 2011-08-09
forum: Hardware
---

### Post by montana68 on 2011-08-09
Hello All
I am using a lenovo B560 to get on line. I'm not able to get on line.
I'm running Ubuntu 10.04  kernel 2.6.32-21 generic.
There is a red exclamation point on top of the wireless symbol.
I know that the wireless works because I'm using win 7 to get on line. I'm not able to use a ether net connection to get on line. So I would have to use win to download all drivers to install on ubuntu. I would need instructions on how to install any thing that would need to be installed. Like I said I'm a real newbie, so all instructions would have to for a person that doesn't understand anything.
Thank you in advance for your help.
Montana

---

### Post by Metaxa on 2011-08-10
A few things to check, Do you get a symbol on your status bar that looks like a green network card that when you mouse over it gives the name " Additional drivers "? If the answer to the following is no do the following:

Go to accesories-->Terminal

Once it opens up type the following command into it. It will ask for your password to execute the command.

> sudo lshw -class network

After doing this it will list what type of card your machine is using. Once you have that information you would need to post it to this thread and you can be advised what to do from their.


Most of the time the driver is already in your system just not allowed to be used, sometimes the card you are using is just incompatible and you would need an external adapter.

Regards,

Metaxa

---

### Post by chili555 on 2011-08-10
You can get a shorter line to post with:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

You can be notified by email of responses to your thread by using Thread Tools at the top and select subscribe to thread and instant email notification.

---

### Post by montana68 on 2011-08-11
Here are results for the command
montana@ubuntu:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
montana@ubuntu:~$

---

### Post by montana68 on 2011-08-11
Sorry I forgot to tell you that this machine is a laptop.

---

### Post by montana68 on 2011-08-11
I did some research before about this and found a thread that said that the machine was using an Acer wireless driver. That driver was what was causing the problem but I couldn't figure out how to do what they said. They were using 11.04 and had this problem.
Sorry for not mentioning it before.

---

### Post by chili555 on 2011-08-11
> I'm not able to use a ether net connection to get on line.That's a shame; this would be a two minute job with an ethernet connection. Are you sure you can't get one for a few minutes? If so, open Applications > Synaptic and go to Settings > Repositories. Activate Restricted. Press Reload. Then search for and install bcmwl-kernel-source. Detach the ethernet cable, reboot and enjoy your new wireless.

If you can't do so, get a USB key and a cool drink or two and go here: [http://packages.ubuntu.com/natty/bcmwl-kernel-source](http://packages.ubuntu.com/natty/bcmwl-kernel-source)

Get the package as appropriate for your machine; that is either 32-bit (i386) or 64-bit (amd64). Get all the dependencies listed: dkms, libc6-dev, linux-headers-generic, linux-libc-dev. They might have dependencies of their own! Download them all to your desktop. Open a terminal and do:```
cd Desktop
sudo dpkg -i *.deb
```After a few hours of struggle, call a buddy and ask to use his/her ethernet connection and be done.

---

### Post by montana68 on 2011-08-12
Tomorrow I might be able to connect to an ether net connection.
 When I connect with the ether net cable, it will connect automatically to the internet I guess. When I connect I'll do what you said but could you tell me how to install the program. I'm a real newbie and don't know much.
Thank you.

---

### Post by chili555 on 2011-08-12
All you have do do is what I suggested before:> open Applications > Synaptic and go to Settings > Repositories. Activate Restricted. Press Reload. Then search for and install bcmwl-kernel-source. Detach the ethernet cable, reboot and enjoy your new wireless.Synaptic will do all the hard work and install the correct driver and a few dependencies and you'll be all set.

---

### Post by montana68 on 2011-08-12
Okay I will do that. I am at my friends house now as soon as I get off here I will do what you said. Sorry for the question about installing the program but like I said I'm a real newbie.
Thank you very much.
montana68

---

### Post by montana68 on 2011-08-13
I did what you told me but at one point they asked me if I wanted to upgrade and of course I said yes. After all was done I couldn't get it to work. So I went over to hardware drivers and opened that. After opening it it started to search for drivers it came up with one for Broadcom an STA  it listed the one that I had. I let it download it and then installed it. Now it works fine so far. I'm writing this on line with ubuntu.
Thank you a million times for had you not told me to go on line with ether net connection I wouldn't be using ubuntu for on line.
Once more thank you a million.
If I have any questions in the future I'll come back here.

---

### Post by montana68 on 2011-08-13
How do I mark this closed or solved?

---

### Post by trungvkvk on 2011-08-13
can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanks

---

### Post by montana68 on 2011-08-13
[B]Sure as far as I know anyone can join in. I don't have a problem with that.
I tried to update it but get
montana@ubuntu:~$ sudo apt-get update firefox
[sudo] password for montana: 
E: The update command takes no arguments
montana@ubuntu:~$ 
Can you please tell how to either install a new version or how to update it. I checked synaptic package manager all I saw was an older version.montana@ubuntu:~$ sudo apt-get install firefox 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
montana@ubuntu:~$ 
I get this message when I try to install it but when I check Fire Fox it says that the version is 3.6.18. I'm presuming there is some kind of a problem.
Can someone please help me with this?
Thank you.
[/B]

---

### Post by chili555 on 2011-08-13
The version of Firefox that's available is dependent on your Ubuntu version. The official Ubuntu repositories won't offer to install Firefox 5.0 if you have an older kernel version that is in some way not completely compatible with 5.0. Now, you could certainly download it and install it manually, probably with some warnings, and it would probably work...mostly.

Of course, that begs the question; if you are a newest, latest bleeding edge user, why do you have an older Ubuntu version installed? 

For comparison, I have a fully updated Natty 11.04 install and:```
chili@LAPTOP60:~$ firefox --version
[COLOR="Red"]Mozilla Firefox 5.0[/COLOR]
chili@LAPTOP60:~$ uname -r
[COLOR="Red"]2.6.38-10-generic[/COLOR]
```The proper way to update a package is:```
sudo apt-get update
```This will check the Ubuntu repositories and compare available versions to what's installed on your system. Then you can do either of two things:```
sudo apt-get upgrade
```That will upgrade everything for which there is a later version. You can specify just one package to upgrade with:```
sudo apt-get install <some_package>
```However, why not upgrade everything available?

---

### Post by chili555 on 2011-08-13
> **trungvkvk said:**
> can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanksWould you like to learn how to get your wireless or ethernet going? Or what?

---

### Post by montana68 on 2011-08-13
I did get the wireless working I'm sending over my wireless with Ubuntu and at that time I also updated everything. I'm using 10.04 it is a LTS I believe it's called. I believe that it's supported till April 2013 for updates. The kernel was updated to 33 I believe.
Thank you for all your help with the wireless connection. It's working great now it's better than windows. When I tried to connect on windows it just told me that I couldn't connect and there was a problem. I think the problem was that it didn't ask me for the password and I could see how to put it in.
Thank you for your help it was and is appreciated.

---

### Post by chili555 on 2011-08-13
I'm glad it's working! Would you please use thread tools at the top and Mark Solved?

---

