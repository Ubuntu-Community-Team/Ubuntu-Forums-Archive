---
title: "Wifi problem with Ubuntu 10.10"
date: 2010-11-19
forum: Hardware
---

### Post by EatTheFood on 2010-11-19
Hello everyone,

I'm new to Linux and I've just installed Ubuntu 10.10 on my laptop, an HP Pavilion zd8000. Everything was working fine until I tried to connect the computer to my Wifi connection (router). At first it said something like "Wireless Network (firmware missing)" when I clicked in the top-right icon for the networks. Then I followed some tutorials and downloaded packages but nothing worked, the only thing that has changed is that it doesn't say "Firmware misssing" anymore, and for some reason when I go into "Edit connections..." and then "Wireless" it doesn't find any Wifi connection. :confused:

The only information I have is that my Network Controller is a: 
Broadcom Corporation BCM4318 [AirForce One 54g] 802. llg Wireless LAN Controller (rev 02).

I got that information by typing this :
```
lspci | grep -i net
```in the terminal.

Does anybody know what the problem is or have some advice? :D

Cheers.

EatTheFood

---

### Post by coffeecat on 2010-11-19
You don't say what the tutorials told you to do, but the link below is the Ubuntu Community documentation page. If you installed the b43-fwcutter package to get the firmware, you need to activate the b43 driver by going to System > Adminstration > Additional drivers.

Here's the link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

If you do still need to install the b43-fwcutter package it first describes the steps to take if you can connect to the internet via a wired connection, and then under 'no internet' how to install this from the live CD.

Once you have the driver installed and activated all you need to do is to left-click on Network Manager and your available wireless networks will be listed. Click on yours and enter your passkey where prompted.

It's a shame you're having this introduction to Linux. As you've probably gathered by now, there are licensing issues with Broadcom which prevent the firmware and/or the proprietary driver being included in a default install. Many wireless chipsets work just fine out of the box. Things should get better with Broadcom next year as they recently eased up on their licensing.

Good luck!

---

### Post by EatTheFood on 2010-11-19
I've installed, uninstalled and reinstalled b43-fwcutter several times and nothing happened.
I'll try to install it again and be sure to activate it this time ;) (I think I forgot to do that last time). And try your method.

Thank you very much. I'll tell you if it worked or not.

Cheers.

EatTheFood

---

### Post by EatTheFood on 2010-11-19
Where is "Additional drivers" ? 8-[

'cause when I go to System>Administration there is no such thing called "Additional drivers" ...

---

### Post by coffeecat on 2010-11-19
> **EatTheFood said:**
> Where is "Additional drivers" ? 8-[

'cause when I go to System>Administration there is no such thing called "Additional drivers" ...

First in the list in System > Administration.

Let's be sure. You are running 10.10 (Maverick) and not 10.04 (Lucid)? You can tell by going to System > About Ubuntu. If you are running 10.04, then it's System > Administration > **Hardware** Drivers. Just to keep you on your toes. :wink:

Also - you are running Ubuntu/gnome, and not Kubuntu or Xubuntu?

---

### Post by EatTheFood on 2010-11-19
I am running "Ubuntu 10.10 (Maverick Meerkat" and es it is GNOME. 
An when I go into System>Administration the first thing I get is "Computer Janitor".

I'm really confused ... 

:(

(but again thank you for helping me...)

---

### Post by coffeecat on 2010-11-19
> **EatTheFood said:**
> An when I go into System>Administration the first thing I get is "Computer Janitor".

I'm really confused ... 

How odd. It must have got switched off in the menu somehow. Here's what to do. Hover the mouse over the main menu in the upper panel and right-click. Choose 'Edit Menus'. Scroll down to 'Administration' in the left pane and highlight it. You'll see all the Administration menu entries in the middle pane. Is 'Additional drivers' there? If so tick the box and it will appear in the menu. If not, post back and I'll tell you what to do to get it into the menu.

---

### Post by EatTheFood on 2010-11-19
> **coffeecat said:**
>  You'll see all the Administration menu entries in the middle pane. Is 'Additional drivers' there? If so tick the box and it will appear in the menu. If not, post back and I'll tell you what to do to get it into the menu.

So when I'm in the Menu "editor (don't really no what it's called)" there is nothing called "Additional drivers". Do you have a solution to get it ?

---

### Post by coffeecat on 2010-11-19
> **EatTheFood said:**
> So when I'm in the Menu "editor (don't really no what it's called)" there is nothing called "Additional drivers". Do you have a solution to get it ?

Yes, very strange that it's missing.

Open up the menu editor (it's called alacarte), and highlight the Administration line in the left pane. If you highlight the wrong line, the new menu entry will go in the wrong place.

Click on 'New Item'. In the small window that opens, you need to add the following text:

Type: make sure 'Application' is chosen from the drop down.
Name: Additional Drivers
Command: /usr/bin/jockey-gtk
Comment: Configure third-party and proprietary drivers

It's best if you copy and paste from this post because the command must be 100% correct. OK that, the little window will close. Close the main menu editor and you should be able to find Additional Drivers under Administration.

If by chance your new menu entry doesn't work, open a terminal (System > Applications) and run:

```
/usr/bin/jockey-gtk
```... and post any errors.

---

### Post by EatTheFood on 2010-11-19
Ok, the menu item I created appears but when I click on it an error comes up saying:
[I]
Failed to execute child process "/usr/bin/jockey-gtk" (No such file or directory)[/I]

So I tried in the terminal and what I get is : 

```
bash: /usr/bin/jockey-gtk: No such file or directory
```

Maybe I deleted it without knowing, or when I tried some of the tutorials I maybe changed something by writing commands in the terminal or isntalling packages... Any idea?

---

### Post by coffeecat on 2010-11-19
> **EatTheFood said:**
> Ok, the menu item I created appears but when I click on it an error comes up saying:
[I]
Failed to execute child process "/usr/bin/jockey-gtk" (No such file or directory)[/I]

So I tried in the terminal and what I get is : 

```
bash: /usr/bin/jockey-gtk: No such file or directory
```Maybe I deleted it without knowing, or when I tried some of the tutorials I maybe changed something by writing commands in the terminal or isntalling packages... Any idea?

You must have uninstalled jockey (which is the Additional drivers app). First - a word about Linux tutorials out there on the big wide internet. **Don't go there**. Seriously, not unless you've been recommended one by someone you trust or not until you have the experience to distinguish the dross from the gold. And, believe me, the dross far outweighs the gold. :( Two links for you:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

That's to get you started. And...

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Search for what you need. A lot is out-of-date but there's a lot of good stuff there.

Now to jockey. Go to Applications > Software Centre. Type 'jockey' in the search field and install 'Additional Drivers (jockey-gtk)' that will come up in the list. Of course, you will need an internet connection. Can you connect with a wired connection for now? Don't install jockey-kde - that's for Kubuntu.

Once you've installed that, Additional Drivers should work from the menu. You may get two menu entries.

Tell me: did one of the tutorials tell you to uninstall jockey?

---

### Post by EatTheFood on 2010-11-19
Yey, now I realize that I shouldn't have done all the tutorials that I  came up. I was so excited to finally get Linux that I juste wanted  everything to work. :sad:

But now I think I've learned not to start doing stuff without really knowing what it is. :wink:
And thanks for the links, I'll go check it out.

So "revenons à nos moutons" (french expression to say "Let's come back to the subjet" :biggrin:),

I've now installed jockey and it's working, but when I launch it there are no drivers, it says "*No proprietary drivers are in use on this system*".

How do I get to see my Wireless driver ?

> **coffeecat said:**
> 
Tell me: did one of the tutorials tell you to uninstall jockey?

I don't remember that any tutorial told me to uninstall it but some of them were saying to uninstall stuff via the terminal, so maybe I did that.

---

### Post by coffeecat on 2010-11-19
> **EatTheFood said:**
> I don't remember that any tutorial told me to uninstall it but some of them were saying to uninstall stuff via the terminal, so maybe I did that.

They may have told you to uninstall stuff that was needed and we could spend hours chasing moonbeams. I have a suggestion. You've only just installed Ubuntu. Why not do a fresh install and then follow the Broadcom wireless link I provided? That way you get a clean system to see if you can get wireless working the "official" way.

I know it's tedious but chalk it all down to a learning experience. I must have installed and re-installed various Linux versions several dozen times in my first few months. That was in 2005 and I couldn't get internet working at all for a month or more. :-s

I'll help you with the re-install if you need it, but if that link doesn't get the Broadcom wireless working I must tell you I have no direct experience of that particular wireless chipset. Nevertheless, I am confident it will work in a re-installed system.

---

### Post by EatTheFood on 2010-11-19
Ok, I'll do a brand new install and follow the link you gave me. ;)

But still thanks for helping me out. :D

If there are still problems after doing a brand new install I'll write them in this thread.

Cheers.

EatTheFood

---

### Post by coffeecat on 2010-11-19
Did you do a dual-boot install with Windows or just install Ubuntu to  the whole hard drive? If you're unsure of the steps to take with the installer, post back because some people have managed to get a triple-boot when reinstalling Ubuntu: Windows + two instances of the same version of Ubuntu.

---

### Post by EatTheFood on 2010-11-19
The fresh install of Ubuntu was successful, everything works! :D

The wifi is now operational, and I didn't have any installation problems (not event dual-boot problems).

Thank you very much for helping me out!
I think that without you I would have been serching for days!

Cheers.

EatTheFood.

---

### Post by coffeecat on 2010-11-19
Good news. I'm glad it's working.

A belated welcome to the forum and don't hesitate to start a support thread if you need.

Good luck! :)

---

