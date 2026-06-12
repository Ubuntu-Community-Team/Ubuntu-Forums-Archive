---
title: "Virgin Ubuntu User &gt; ATI x1900 Drivers"
date: 2010-04-02
forum: Hardware
---

### Post by AP0ll0UK on 2010-04-02
Hi Everyone

As the subject suggests I've just installed Ubuntu on my main PC [as outlined here - [http://ubuntuforums.org/showthread.php?p=9064304#post9064304]](http://ubuntuforums.org/showthread.php?p=9064304#post9064304]).

My system is using an ATI x1900 and I think there is an issue with the current driver, video playback is ok for both standard divx and HD movies but during fast moving scenes there seem to be a few lines appearing for a split second.

I don't 'think' it is codec related, I enabled MediaBuntu to get the codecs down and working, and the issue also appears visible in flash playback on YouTube.

I've tried to pull down the Linux x86 driver from the ATI site but when I try to install it I get the following message "could not open the file /home/dave/Downloads/ati...taller-9-3-x86.x86_64.run - gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again"

The two character coding options I have are:-

 - Current Loacle (UTF-8
 - Western (ISO-8859-15)

During the Ubuntu install I selected that I was in the Uk and I shouldn't be using any non-standard character sets. But I am coming from the Microsoft world so maybe this error is referring to something else, not.

Can anyone offer any advice please?

---

### Post by AP0ll0UK on 2010-04-03
I've also tried the recommended x1900 driver from within the package manager and the issue still remains unfortunately.

---

### Post by Gregorybekkers on 2010-04-03
can u try to download the one from the ATI site?

---

### Post by AP0ll0UK on 2010-04-03
Hi

Thanks for your reply.

Unfortunately the drivers I mentioned at the start of the thread were the last set of Linux drivers which ATI released for this card.

Thanks again.

---

### Post by amouawad on 2011-01-02
If you want to be able to run this file through the GUI then you'll need to right click it > properties > permissions > enable 'Allow executing file as a program' then close and double click again.

To run from the CLI just cd into its directory and type: ./filename.run and it should run.

---

### Post by cascade9 on 2011-01-02
The video problem is probably caused by the open source drivers.

ATI dropped support for the x1XXX series cards a fair while ago. While they still have drivers up for d/ling, if you're using a newer version of ubuntu then the drivers will not install, no matter what you do. I cant recall when the ATI x1XXX cards got dropped exactly, but I think it was around 9.04 (whihc is out of support so its not a good idea to use it) 

You might do best to spend 30-40 quid on an nVidia card (GT210).

---

