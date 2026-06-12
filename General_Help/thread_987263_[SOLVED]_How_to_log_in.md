---
title: "[SOLVED] How to log in?"
date: 2008-11-19
forum: General Help
---

### Post by itsmepaul57 on 2008-11-19
Hi greetings to you all....

I have just downloaded and installed UBUNTU on my laptop (external harddrive)   and when it started up the first thing it did was ask me for my username and password...

I had never been asked to register one so I do not know what to input...

is there a default username/password to get the prgram up and running??

I'm stumped!!
:confused:



Paul Edwards

---

### Post by Sub101 on 2008-11-19
When installing you should have been asked for a username and password? 

Were you not asked this at all?

---

### Post by itsmepaul57 on 2008-11-19
No - I didnt see one!!!  It just installed itself restarted my laptop - and presented me with a login details - which I dont know!!

---

### Post by aysiu on 2008-11-19
Something's wrong with your CD. The live CD shouldn't ask you for a username and password to log in.

This has happened to other people, but I believe it is a bug in corrupted CD images:
[https://answers.launchpad.net/ubuntu/+question/9193](https://answers.launchpad.net/ubuntu/+question/9193)
[https://answers.launchpad.net/ubuntu/+question/29297](https://answers.launchpad.net/ubuntu/+question/29297)
[https://answers.launchpad.net/ubuntu/+question/34967](https://answers.launchpad.net/ubuntu/+question/34967)

---

### Post by aysiu on 2008-11-19
> **itsmepaul57 said:**
> 
I have just downloaded and **installed** UBUNTU on my laptop (external harddrive)   and when it started up the first thing it did was ask me for my username and password...

I had never been asked to register one so I do not know what to input... Whoops. I missed that part. So you actually *installed* Ubuntu? Then you should have set a username and password.

If you've forgotten what you choose, you can reset your password by following these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by itsmepaul57 on 2008-11-19
As i said - DOWNLOADED it from website - no CD

Thanks Paul

---

### Post by itsmepaul57 on 2008-11-19
I dont remember seeing any option to creat log-in details.

Paul

---

### Post by aysiu on 2008-11-19
How did you install it without using a CD?

Did you load up a live session to a USB stick and boot from USB?

If you **install** Ubuntu, you should at one point see one of these screens (see attached screenshots).

---

### Post by itsmepaul57 on 2008-11-19
No just downloaded from website - never saw this screen

Paul

---

### Post by itsmepaul57 on 2008-11-19
> **aysiu said:**
> Whoops. I missed that part. So you actually *installed* Ubuntu? Then you should have set a username and password.

If you've forgotten what you choose, you can reset your password by following these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thank you. I tried this and it worked fine - up to a point - see, there are no usernames or passwords to re-set - zilch!!!

Now what???

Paul

---

### Post by aysiu on 2008-11-19
> **itsmepaul57 said:**
> No just downloaded from website - never saw this screen

Paul
Okay, you're going to give us some more details here. I still don't understand how you could have "installed" Ubuntu and not seen either of those screens.

Tell us **exactly** what you did, step by step. Do not leave out a single detail.

As examples: [quote=The appropriate amount of detail]I went to the Ubuntu website and clicked the download link and picked a download mirror for my country. Then I had this .iso file on my desktop, and I used Nero to burn it as a disk image to a blank CD. I rebooted my computer with the CD inside. I selected to Try Ubuntu without making changes to my computer. There was an orange bar that took a while to go across the screen. There were some loud sounds and I saw a desktop that was brown and grey. I clicked the *Install* icon on the desktop, and I went through a five- or six-screen installation wizard that asked me a bunch of questions. It took about twenty minutes to install Ubuntu, and then I was prompted to reboot the computer without the CD. I did it, and then I got to a log in screen asking for my username and password[/quote] [quote=Insufficient detail]I downloaded Ubuntu and installed it without a CD[/quote]

---

### Post by icanfly0307 on 2008-11-19
Hey,
         Did you actually INSTALL Ubuntu or did you just fire up your computer from the LiveCD? Again, it's impossible to install Ubuntu without setting up a user account. If you DID install Ubuntu on your computer, login to the Recovery Mode from the GRUB menu and when the blue screen pops up, select "Drop root shell". That will get you logged in as root and allow you to create an user account. Let us know what happens.

Good Luck!

---

### Post by KeyserSoze93 on 2008-11-19
If you installed with wubi (ie INSIDE WINDOWS) &#8212; as a friend of mine did &#8212; then it will probably have picked up your Windows username and password.

---

### Post by itsmepaul57 on 2008-11-19
It just installed itslef on my external hard disc - it didnt aske me to make ISo   it just went for it!!!

---

### Post by itsmepaul57 on 2008-11-19
Yes  the above is roughly true  - except that it didnt ask me to make an ISO . it just isntalled itself on my external hrd disc - then re-booted and asked me for my log-in details.

I also went and looked at the root - pressign esc to get there - but there was no sign of any other login details at all...

Paul

---

### Post by icanfly0307 on 2008-11-20
Nice! It looks like once you followed my previous instructions, you were able to drop to the root shell. Alrighty... After that, type: *useradd yourusername*

Then, type: *passwd yourpassword*

That's it! Reboot, go to the normal login screen and use your credentials that you just created. Good Luck!

---

### Post by itsmepaul57 on 2008-11-20
> **icanfly0307 said:**
> Nice! It looks like once you followed my previous instructions, you were able to drop to the root shell. Alrighty... After that, type: *useradd yourusername*

Then, type: *passwd yourpassword*

That's it! Reboot, go to the normal login screen and use your credentials that you just created. Good Luck!
yep, thanks very much to everyone - i have successfully logged in now, ta so much..

Now i have a new problem - cant connect to internet!!!!!

I have new BT internet homehub - works fine with Vista on my acer - but no show on the ubuntu.  By the way my wife has a little webbook with unbutu - connected straight away!!!!

Thanks Paul Edwards

---

### Post by aysiu on 2008-11-20
> **itsmepaul57 said:**
> yep, thanks very much to everyone - i have successfully logged in now, ta so much..

Now i have a new problem - cant connect to internet!!!!!

I have new BT internet homehub - works fine with Vista on my acer - but no show on the ubuntu.  By the way my wife has a little webbook with unbutu - connected straight away!!!!

Thanks Paul Edwards
Please start a new thread for that. Thanks!

---

### Post by duds2008 on 2008-12-30
append to grub rw init=/bin/bash use passwd command

---

