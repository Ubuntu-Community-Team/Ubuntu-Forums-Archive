---
title: "partioner"
date: 2009-07-07
forum: Hardware
---

### Post by Zasquatch on 2009-07-07
i am trying to install ubuntu on one partion of my computer the problem is there is no free space so i go in and earse one of the partions and it says something about the partion menu anyone wanna help me out?

---

### Post by pizza-is-good on 2009-07-07
OK, I can help, but I need more info. HDD size, all your current partitions, how much free space you have, and all info you can give me.

---

### Post by Revolutionary101 on 2009-07-08
I suggest using a software called Partition Commander 10.

It will let you resize your other partitions to free up space on your hard drive. I have used it and it works very well. But when editing your boot partition (Windows) which I suppose is the one you want to shrink, be careful I have done this a few times and I have completely lost some of my documents.

---

### Post by Zasquatch on 2009-07-08
*Okay not very computer savvy yet but here it goes i have a acer extensa 5620z the four partitions windows vista 9.8 GB/windows vista 220.6 GB/ ubuntu2.3 GB/ Swap 172.5.*
 
*I want to reload ubuntu becuase someone stole my computer and hacked it i dont have my user name or password.*
 
*As of right now i am looking at a screen that says prepare partitions *

---

### Post by pizza-is-good on 2009-07-08
> **Zasquatch said:**
> *Okay not very computer savvy yet but here it goes i have a acer extensa 5620z the four partitions windows vista 9.8 GB/windows vista 220.6 GB/ ubuntu2.3 GB/ Swap 172.5.*
 
*I want to reload ubuntu becuase someone stole my computer and hacked it i dont have my user name or password.*
 
Ok, so let me see if I got this right:
4 partitons:
a 9.8 GB for Vista
a 220.6 GB for Vista as well
2.3 GB for Ubuntu
172.5 GB for Swap
 
If that is right, then we really need to fix your partitions. Please confirm tho.
 
I suggest you go in with a live CD or usb of Ubuntu, and fix all the partitions through there.
 
I'll give you instructions on that when you confirm.
 
There will most likely be data loss, so be preapared and start backing up now.
 
Also, do you want to entirely remove the current Ubuntu? And what do you want to do with Vista?

---

### Post by pizza-is-good on 2009-07-08
> **Zasquatch said:**
> *As of right now i am looking at a screen that says prepare partitions *
 
What OS are you in now?

---

### Post by Zasquatch on 2009-07-08
Yes that is right and i want to remove the ubuntu i have on the system right now and reload ubuntu. i want to make vista smaller to and like i said sorry for the inconvience of this question but how do i back things up and where should i be at right now?
(As of right now i have a live cd in the computer but no more blank disc or flash drives will i still be able to back things up?
 
WAIT not ubuntu. ubuntu setup on no operating system but i can acsess windows vista if need be

---

### Post by pizza-is-good on 2009-07-08
> **Zasquatch said:**
> Yes that is right and i want to remove the ubuntu i have on the system right now and reload ubuntu. i want to make vista smaller to and like i said sorry for the inconvience of this question but how do i back things up and where should i be at right now?
(As of right now i have a live cd in the computer but no more blank disc or flash drives will i still be able to back things up?
 
Jaunty ubuntu.
 
OK, so you have the live CD. That's good.
 
If you have any data that you care about saving, copy it to another device. If you have none, and it is data really important to you, there are free online storages, this could be a good option [http://skydrive.live.com/](http://skydrive.live.com/)
 
The live CD is were you should be at.
 
I take it that you are unable to go into either Vista or Ubuntu.
 
You can mount your HDDs from the live CD, and back up from there.
 
also, execute this in the live CD ```
sudo apt-get install gparted
``` You will need to have internet connection for that.
It is the app for editing partitions. It might already come with it, but just in case.
 
I'm gonna check out for tonight. Sorry.
I'll continue helping tomorrow.

---

