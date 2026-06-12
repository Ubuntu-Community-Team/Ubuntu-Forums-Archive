---
title: "[SOLVED] Problem Connecting with modem"
date: 2008-11-26
forum: General Help
---

### Post by voodooxombie on 2008-11-26
I read the ubuntu documentation page for 8.10 desktop. The link is below: 
[https://help.ubuntu.com/8.10/internet/C/modem-connect.html](https://help.ubuntu.com/8.10/internet/C/modem-connect.html)
It's say to press System &#8594; Administration &#8594; Network

But I couldn't find any Network option in the menu. I don't know where to look for. Hope to get help soon. 

Thank you.

---

### Post by voodooxombie on 2008-12-01
Hello, No one there to help....Help to me connect through modem. I don't know even which modem do i have and how to download package for the modem and get it running.

I read ubuntu documentation and it says to download some package called scanmodem and then go to System &#8594; Administration &#8594; Network.
But couldn't find any Network menu. I read some other post too which says Network Configuration under System->Preference menu is same as Network but couldn't configure anything out of it for my modem.

Hope to get some answer this time.
Thank you.

---

### Post by editrix on 2008-12-01
I don't use Gnome or 8.10, but you've been more than patient awaiting a reply and you deserve some acknowledgment.

I'm just guessing, but perhaps when you installed (or when you boot up) Ubuntu doesn't recognize any networking hardware, so the option doesn't show up? 

However, most computers come with an ethernet card nowadays, and that should have been detected.

Also, as I understand it, there's no dialup program that comes with the install CD, except maybe wvdial.

Check out the older dialup howto: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

And Linmodems.org [http://www.linmodems.org/](http://www.linmodems.org/)

I've got a post here: [http://ubuntuforums.org/showthread.php?p=6228819#post6228819](http://ubuntuforums.org/showthread.php?p=6228819#post6228819)
with the contents of the relevant programs--but remember this is 8.04, and something may have changed. (I doubt it, though. The dialup technology hasn't changed.)

---

### Post by Bibek on 2008-12-01
First of all,
That guide works for external modem. 
If you have an internal modem you have to install its driver. on top of that, if you have a winmodem, then its trouble. 
Follow this guide to identify which modem you have.
[https://help.ubuntu.com/8.10/internet/C/modem-identify.html](https://help.ubuntu.com/8.10/internet/C/modem-identify.html)
You will get the instruction on where to look for the driver for your modem in the folder created by scanmodem.

---

### Post by voodooxombie on 2008-12-01
I already used the scanmodem but didn't knew it will give me instruction about driver loaction.  I will check that. What 
Thank you Bibek.

[http://www.linmodems.org/...This](http://www.linmodems.org/...This) is a great link. It explain thing clearly. I need to go home to try this. 
Thank you editrix

---

