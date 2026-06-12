---
title: "Very veird problem pls help."
date: 2012-08-13
forum: Hardware
---

### Post by applesFTW on 2012-08-13
Hey ppl,
I have so much weird problem, and I actually don`t understand how it could appear. It all started, when i booted ubuntu with my laptop unplugged  ( I have battery). For some unknown reasons, the login screen was other graphical style and message in uper right corner appeared saying something like "Power manager not installed correctly, please connect admin" (Cant quota it because ubuntu isn`t in english). It did not let me log in. I googled it, looked through forums, though without any luck. So I returned to MS Vista, as I was too much lazy and didn`t see any hope in there. Then after few months I tried to fix the problem again. I was messing with recovery mode, when my younger brother unpluged my pc. And it all went back to normal! I cant understand how and why it fixed the problem, but it worked.. until i rebooted my pc. It started dropping that error again. Once again I googled the problem and found on some forum:

sudo apt-get purge gnome-power-manager
sudo apt-get install gnome-power-manager

And with this I think I screwd things up. Thing is I can connect to internet through router only, because my network card is broken by lightning (that means no direct wire internet connection). And because of this I cant install power manager, as it cant find update server. So my questions are:

1. How to install package through other partition (MS Vista if precise)?

2. ::maybe not related:: How to increase used memory?

The second question is because i read somewhere that if memory is full it can cause problems. And thing is I don`t know why, on ubuntu I always had only < 500mb memory (though disk where I installed it has 250gb).

Hopefully looking for answers,

Arvydas.

---

### Post by irv on 2012-08-13
First of all you are trying to ask all these question and it becomes overwhelming. Let's start small.
It looks like you have hardware problems with your network card. So let me ask a question. Can you get on the Internet at all? With Vista or Ubuntu?

Next. Boot with the live DVD or USB and run gparted and take a screen shot of your Hard drive and post it here. This will give us a picture of how much room you have on your hard drive and how it is partitioned. 
How long have you been using Ubuntu? If you just installed it you may what to start over again. First post the information I asked for and we can start from there.

---

### Post by applesFTW on 2012-08-13
> **irv said:**
> First of all you are trying to ask all these question and it becomes overwhelming. Let's start small.
It looks like you have hardware problems with your network card. So let me ask a question. Can you get on the Internet at all? With Vista or Ubuntu?

Next. Boot with the live DVD or USB and run gparted and take a screen shot of your Hard drive and post it here. This will give us a picture of how much room you have on your hard drive and how it is partitioned. 
How long have you been using Ubuntu? If you just installed it you may what to start over again. First post the information I asked for and we can start from there.


Yes I can connect to internet, but only with wireless connection both on vista and ubuntu.

I dont actually know what live DVD or USB, and I actually forgot how I installed ubuntu. I think somehow with wubi, dont remember.

I have been using ubuntu maybe for 6 months. Thing is I`m on vacation, where internet is kinda expensive, so reinstalling is not an option to me.

---

### Post by irv on 2012-08-13
> **applesFTW said:**
> Yes I can connect to internet, but only with wireless connection both on vista and ubuntu.

I dont actually know what live DVD or USB, and I actually forgot how I installed ubuntu. I think somehow with wubi, dont remember.

I have been using ubuntu maybe for 6 months. Thing is I`m on vacation, where internet is kinda expensive, so reinstalling is not an option to me.

OK, this helps. If you have the wubi installed this answers some questions. Wubi runs inside windows and it is a image file that is limited to it's size. So if you are running out of room and you want to move to the next step in running Ubuntu. You can remove Ubuntu by going to your control panel in windows and uninstall it like any other application. 

Now to install it on part of your hard drive to run a dual boot system with windows you need to follow these instructions. 
First download the iso file from Here: [http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop") You need to know if you are going to use the 32 or 64 bit version.
Next you need to make a DVD or USB installer. You will need software in windows to do this. (I don't know what you have so you need to figure this out yourself.)
After creating a Live DVD or USB you want to Try Ubuntu before you install it. Follow these instructions: [http://www.ubuntu.com/download/help/try-ubuntu-before-you-install]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install") If you check the side bar on this webpage you will see a link to how to create a DVD or USB in windows.
If everything is working when you are running the Live OS off DVD or USB and you want to install it follow these instructions.
[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")
Hope this helps. 
May I add, if you are not sure about doing this, find someone who has done this before and have them help you. But to be honest with you I find it very easy to do and have done it many times.

After running the Live OS off the media run gparted and post a screen shot so I can see if you have enough room on your hard drive to do the install.

---

### Post by QsoftStudios on 2012-08-13
Seems like you have some hardware issues you sure that the network card was the only thing fried by lightning?

---

