---
title: "Jaunty installation freezes"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by betete on 2009-04-24
Hello people, I have Ubuntu 8.04 installed on a Pentimu 4 HT 3.0Ghz and its running ok.

Today I tried to install Jaunty and I get a black screen just after the loading bar ends. I tried the test option and install option, and it's the same.

I have an Ati Radeon 9200 which gave me problems with past versions of Ubuntu, but I don't know if is this the case now.

I have also tried with safe graphics mode, but it's the same.

Can anyone help me.

---

### Post by betete on 2009-04-26
I can't find solution to my problem yet. I have tried checking the iso file for errors, but seems to be ok.

Have anyone had the same problem? Help please.

---

### Post by axel_2078 on 2009-04-26
When you're installing, try changing your boot parameters. Try the noacpi, noapic, and nolpic options and see if it will install correctly. That's what I had to do.

---

### Post by betete on 2009-04-27
Thank you for your reply. I have already tried all the parameters, and I get the same black screen. I have also removed the quiet and splash options to see what the system is doing, and I see no errors. Of course I can't see much because of the speed.

Any other idea?

---

### Post by betete on 2009-04-28
Please, can anyone tell me how could I know where the loading process stops in order to identify the problem. I know that removing the options quiet and splash I can see what is happening, but it goes to fast.

Another question: why did Hardy Heron run from Live CD and Jaunty Jackalope has a problem on the same hardware? I thought that every new release would add support, never go back.

My motherboard is a P4P800 SE. I have read about people having problems with this hardware, but as I said, I never had in the past.

---

### Post by hurdy on 2009-04-28
I also have the same problem. My graphics is an ATI Radeon HD3870 x2.

Any advice on how to fix this problem would be greatly appreciated.

Thank you,

Rob

---

### Post by betete on 2009-04-29
Hurdy, have you tried the alternate CD. I haven't because  I've read that I will have the same problem after rebooting.

I think that we should install Ubuntu using the alternate CD and then manually install the ATI driver. But I'm not sure how to do that.

Can anyone help me?

---

### Post by betete on 2009-04-30
Hi again, I tried the alternate CD. I could install Ubuntu, but after rebooting, I got a scrambled screen where the login screen should appear, and the mouse stopped working a few seconds after.

I then tried copying the xorg.conf from Ubuntu 8.04, which I have in another partition. That solved the problem with the scrambled screen. But the system still freezes a few seconds after the login screen appears.

How could I know what is causing the problem?

I think it may be the wifi card driver, because in recovery mode, when I try to ifup on that card, the system freezes. How could I remove the driver? In Ubuntu 8.04 I'm using ndiswrapper to load the windows driver, and it works fine. I would like to do the same. But it seems that Jaunty has installed the open source driver.

Please, help me!

---

### Post by betete on 2009-04-30
Finally I found the solution. Besides the scrambled screen, the real problem was my wifi PCI card. The driver of that card was the one causing the system to hang at startup. I'm gonna explain step by step how did I solve the problem in case someone is having troubles.

First, as I thought that the problem was my video card (ATI Radeon 9200), I tried to make it work just by modifying /etc/X11/xorg.conf. As I have Ubuntu 8.04 installed in another partition, I just copied that file in place of the one created by Jaunty. After that, I could see the logging screen but the system still hung.

I noticed that the system also hung when I tried to boot in recovery mode, and then choose the "root with network" option. I received a "wmaster0 unknown address 801" error.

To solve this problem, I "blacklisted" the rtl8180 module, in order to prevent the system from loading it. After that I rebooted and everything went ok. Of course I couldn't use my wifi card. But I installed ndiswrapper, I loaded the microsoft driver, as I had done in Ubuntu 8.04, I now my system is running perfectly well.

I hope someone finds this useful.

Thank you.

---

### Post by roger mexico on 2009-05-06
1.I tried to make it work just by modifying /etc/X11/xorg.conf. 

I noticed that the system also hung when I tried to boot in recovery mode, and then choose the "root with network" option. I received a "wmaster0 unknown address 801" error.

2. To solve this problem, I "blacklisted" the rtl8180 module


my system also freezes after the ubuntu screen.
i get the "wmaster0 801" message

how do you do these two things?  how do i fix this problem?
i am sorry, i feel stoopid. but i spent 10 hours downloading the new system, now it doesn't work
:(:(:(:(

thanks if you can help me

---

### Post by betete on 2009-05-23
Hi roger. Do you still receive de wmaster0 error after blacklisting the rtl8180 module? I'm not a linux hacker, but I think there is no way you could receive that error if the module is not being loaded. Check that you saved the blacklist file after modifying it. Are you sure that is rtl8180 the module that your wifi card is using? You should blacklist the module that your card uses.

---

### Post by welshboy on 2009-05-23
Hi there,

I've not used the forums here for a long while, I've been mostly coding in Windows (I know I know....) but that's due to my job.

As to your installation problem, Could you not upgrade from 8.04 to 9?  I had some interesting issues when I installed the new distro on my laptop, but that's for another thread.

Just a thought.

Welshboy

---

