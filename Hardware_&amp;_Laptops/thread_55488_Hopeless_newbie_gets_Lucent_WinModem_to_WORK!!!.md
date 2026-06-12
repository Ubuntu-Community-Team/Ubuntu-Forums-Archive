---
title: "Hopeless newbie gets Lucent WinModem to WORK!!!"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by blastus on 2005-08-09
I can't believe I actually got my modem to work!!! Woohoo! I'm browsing the web right now and and making this post in Ubuntu!

I know there's lots of people that have Lucent WinModems and can't get them to work on Ubuntu 5.04. I have a final exam coming up here in a few days but after that I'll put together a guide for dummies to getting a Lucent WinModem to work on Ubuntu 5.04. I need to write all this stuff down with explicit directions/steps/explanations and everything for myself so I can get my modem working again from a fresh Ubuntu installation. Then the Linux wizards can fill in better explanations where I lack knowledge or make the steps more efficient.

There's so much to learn. I'm using wvdial. How do I hang up the modem? How do I monitor the traffic on it?

---

### Post by heimo on 2005-08-09
[QUOTE=blastus]I can't believe I actually got my modem to work!!! Woohoo! I'm browsing the web right now and and making this post in Ubuntu!
[/QUOTE]

I know the feeling. :) Congrats! And thanks in advance for howto on this subject - many times people who had to struggle to get something to work write the best howtos, regardless of their level of general experience.

EDIT: When you have time to start the howto, be sure to check the existing documentation and [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) maybe you can edit/complete an existing guide.

---

### Post by blastus on 2005-08-09
I definitely will. I like having clear and complete guides. I want to make a step-by-step set of explicit instructions and for each step I would like to include....

1. The explicit instructions for that step
2. How you can validate that the step worked
3. An explanation of what that step does or why you need to do it in as simple terms as possible

 :-)  That #3 part is difficult for me because I don't understand most of the whys.

---

### Post by Gorgonzola on 2005-08-09
It'll be great once you complete the guide.

I remember trying linux for the first time a few years ago when I had dialup and gave up on it completely due to my inability to get my winmodem to work. It was very frustrating!

---

### Post by az on 2005-08-09
[QUOTE=blastus]I definitely will. I like having clear and complete guides. I want to make a step-by-step set of explicit instructions and for each step I would like to include....

1. The explicit instructions for that step
2. How you can validate that the step worked
3. An explanation of what that step does or why you need to do it in as simple terms as possible

 :-)  That #3 part is difficult for me because I don't understand most of the whys.[/QUOTE]



Please improve upon this:

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

---

### Post by Gezzer on 2005-08-09
[QUOTE=blastus]I can't believe I actually got my modem to work!!! Woohoo! I'm browsing the web right now and and making this post in Ubuntu!

I know there's lots of people that have Lucent WinModems and can't get them to work on Ubuntu 5.04. I have a final exam coming up here in a few days but after that I'll put together a guide for dummies to getting a Lucent WinModem to work on Ubuntu 5.04. I need to write all this stuff down with explicit directions/steps/explanations and everything for myself so I can get my modem working again from a fresh Ubuntu installation. Then the Linux wizards can fill in better explanations where I lack knowledge or make the steps more efficient.

There's so much to learn. I'm using wvdial. How do I hang up the modem? How do I monitor the traffic on it?[/QUOTE]

i tried and failed to get several WinModems to work PCI & USB
in the end i went and got an ethernet modem which worked first time

so all i can say is **Very Well Done** ...

---

### Post by blastus on 2005-08-13
[QUOTE=azz]Please improve upon this:

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)[/QUOTE]

OK I've got my exam done now and have started working on the tutorial I wish I had done a search on Wiki for Lucent WinModem when I started but I found this post 
[https://wiki.ubuntu.com/WinModemLucent?highlight=%28WinModem%29](https://wiki.ubuntu.com/WinModemLucent?highlight=%28WinModem%29) so some of my instructions will be the same and some will be different. But my tutorial will be for newbies. It isn't complete yet but it's divided into the following sections:

A. What You Need to Know
- this section lists the things that you should know before even reading the tutorial

B. Overview of the Process
- this section includes an overview of the process of setting up the modem

C. Understanding the Process
- this section includes aims to provide an understanding of the process involved in setting up the modem
- this section is about 1000 words but it covers some important basic concepts that newbies should know
- I think this section is critical because having an understanding of things you need to do as opposed to just type in this or that really helps

D. Setting up Your Modem
- this section includes a step-by-step list of instructions for setting up the modem

---

### Post by az on 2005-08-13
[QUOTE=blastus]OK I've got my exam done now and have started working on the tutorial I wish I had done a search on Wiki for Lucent WinModem when I started but I found this post 
[https://wiki.ubuntu.com/WinModemLucent?highlight=%28WinModem%29](https://wiki.ubuntu.com/WinModemLucent?highlight=%28WinModem%29) so some of my instructions will be the same and some will be different. But my tutorial will be for newbies. It isn't complete yet but it's divided into the following sections:

A. What You Need to Know
- this section lists the things that you should know before even reading the tutorial

B. Overview of the Process
- this section includes an overview of the process of setting up the modem

C. Understanding the Process
- this section includes aims to provide an understanding of the process involved in setting up the modem
- this section is about 1000 words but it covers some important basic concepts that newbies should know
- I think this section is critical because having an understanding of things you need to do as opposed to just type in this or that really helps

D. Setting up Your Modem
- this section includes a step-by-step list of instructions for setting up the modem[/QUOTE]


As I said, you should just improve this:
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

The other wiki page is for Warty and you had to compile the drivers from source.  This is not the case in Hoary.  Also, you should give Breezy a shot and see if your tutorial applies to Breezy.

---

### Post by blastus on 2005-08-14
[QUOTE=azz]As I said, you should just improve this:
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

The other wiki page is for Warty and you had to compile the drivers from source.  This is not the case in Hoary.  Also, you should give Breezy a shot and see if your tutorial applies to Breezy.[/QUOTE]

I don't know what udev or kppp is or any of the other things mentioned on that page. I didn't edit any rules files and didn't edit any grub files or anything like that. I downloaded and compiled the drivers to get the modem to work. All I know is that I figured out a certain combination of instructions and my modem works in Hoary! 

So maybe when I'm done this I'll PM it to you so we can work on this together. My knowledge is extremely limited here so I'm just going on what I know worked for me. The more information we can distribute about this the better I think especially for newbies. If we can simplify the instructions it would great. ;-)

I didn't know you could download Breezy? Anyway I'll finish the tutorial first. I also want to reinstall Hoary from scratch and try out my tutorial to see if it works (crosses fingers.)

---

### Post by blastus on 2005-08-16
[QUOTE=azz]As I said, you should just improve this:
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

The other wiki page is for Warty and you had to compile the drivers from source.  This is not the case in Hoary.  Also, you should give Breezy a shot and see if your tutorial applies to Breezy.[/QUOTE]

I finished my tutorial now and have appended it onto the Wiki posting at [https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent).  :arrow:

---

### Post by az on 2005-08-16
[QUOTE=blastus]I finished my tutorial now and have appended it onto the Wiki posting at [https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent).  :arrow:[/QUOTE]


Very nice information and nice wiki markup (formatting).  Just one question.  You know that Ubuntu already has the modules precompiled, don't you?  

Had you tried to use the precompiled modules and then moved on to a more recent version of the driver?  Or did you go straight away to compiling them yourself?

If it is the former, please edit the page and specify that the more detailed way is appropriate only if the easy way (using the precompiled modules) does not work.

Otherwise, well done!

Would you like to contribute more stuff to the Wiki, or be part of a task force to encourage more forum users to do so?

---

### Post by blastus on 2005-08-19
[QUOTE=azz]Very nice information and nice wiki markup (formatting).  Just one question.  You know that Ubuntu already has the modules precompiled, don't you?  

Had you tried to use the precompiled modules and then moved on to a more recent version of the driver?  Or did you go straight away to compiling them yourself?

If it is the former, please edit the page and specify that the more detailed way is appropriate only if the easy way (using the precompiled modules) does not work.

Otherwise, well done![/QUOTE]

I hadn't read that Ubuntu had the modules precompiled until I came across one of your posts. Ironically, I saw a post of yours prior to that regarding getting the "build-essential" package which enabled me to compile the modules. Keep in mind that at that I time I had no clue what apt or Synaptic were or anything and had no idea what I was doing even on a conceptual level! I haven't tried using the precompiled modules...I don't know how to do it yet so it is something I would have to figure out.

> Would you like to contribute more stuff to the Wiki, or be part of a task force to encourage more forum users to do so?

Definitely yes. :) There's a lot of stuff to learn but there are rewards for being able to configure and customize Linux to do what you want, when you want, and how you want.

---

### Post by kate on 2005-08-29
Thankyou so much. I'm gonna try it out tonight or tomorrow. I've converted my family to Linux, but I can't take over the entire harddrive unless I can promise internet connection.

---

### Post by Unix_Wizard on 2005-08-29
[QUOTE=blastus]I can't believe I actually got my modem to work!!! Woohoo! I'm browsing the web right now and and making this post in Ubuntu!

I know there's lots of people that have Lucent WinModems and can't get them to work on Ubuntu 5.04. I have a final exam coming up here in a few days but after that I'll put together a guide for dummies to getting a Lucent WinModem to work on Ubuntu 5.04. I need to write all this stuff down with explicit directions/steps/explanations and everything for myself so I can get my modem working again from a fresh Ubuntu installation. Then the Linux wizards can fill in better explanations where I lack knowledge or make the steps more efficient.

There's so much to learn. I'm using wvdial. How do I hang up the modem? How do I monitor the traffic on it?[/QUOTE]
 Well here is my less glorious temp solution. As I don't have lucent modem I did this:
1)Networked my laptop running XP
2)Set up internet sharing
3)Downloaded some needed apt-get stuff
All I did was set xp to share the connection. I didn't have to tell ubuntu to do anything. It just works.

---

### Post by blastus on 2005-09-01
[QUOTE=kate]Thankyou so much. I'm gonna try it out tonight or tomorrow. I've converted my family to Linux, but I can't take over the entire harddrive unless I can promise internet connection.[/QUOTE]

Thanks! As azz points out, the way I did it is not the easiest way to do it. Also, I find that I need to re-enter this command everytime I boot into Ubuntu...

sudo ln -s /dev/ttyLTM0 /dev/modem

...to recreate the link to /dev/modem otherwise wvdial will not work. It's strange, because the first time I got the modem to work I didn't have to do that--it was only after I reinstalled Ubuntu. I'll be reinstalling Ubuntu here again soon (I've repartitioned my hard drives again) and I'll see if I can get the modem to work the easier way with the precompiled modules instead.

---

### Post by az on 2005-09-01
[QUOTE=blastus]Thanks! As azz points out, the way I did it is not the easiest way to do it. Also, I find that I need to re-enter this command everytime I boot into Ubuntu...

sudo ln -s /dev/ttyLTM0 /dev/modem

...to recreate the link to /dev/modem otherwise wvdial will not work. It's strange, because the first time I got the modem to work I didn't have to do that--it was only after I reinstalled Ubuntu. I'll be reinstalling Ubuntu here again soon (I've repartitioned my hard drives again) and I'll see if I can get the modem to work the easier way with the precompiled modules instead.[/QUOTE]

You can make a udev rule so that the symlink get written on boot.  I do not know the comman, offhand.
start with :
man udev

---

