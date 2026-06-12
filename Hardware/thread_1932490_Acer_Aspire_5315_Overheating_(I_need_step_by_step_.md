---
title: "Acer Aspire 5315 Overheating (I need step by step instructions)"
date: 2012-02-27
forum: Hardware
---

### Post by whatisupposetodo on 2012-02-27
Hi,

I`ve been using windows for all of my life and now I do use Ubuntu 11.10 (32bit). I`ve been using it Few months only. I`m  totally newbie and I cant use it at all. I am sorry for asking this same question again because there is a lot of threats about this problem but I couldnt find an easy step by step solution for newbies for overheating problem (fan wont work) It works after one crash when I open computer again.

 If you can also tell what programs I should use, how to open locked folders if necessary, what text do I have to write etc.

Ps. I can open a terminal and gnome-terminal as a root thats about it.

Is there anyone who can help me?

---

### Post by ahallubuntu on 2012-02-27
First of all, ANY laptop (Windows or Linux or otherwise) that's more than a few years old should probably have its CPU heat sink cleaned out - they get dusty and dirty over the years, and depending on how well the cooling was designed for your Aspire, it may be more prone to overheating.  I've cleaned a couple of old laptops out and it's amazing what difference it can make in keeping them from overheating.

Taking a laptop apart can be scary, though.  Some are easier than others to be able to get to the fan and heat sink.  Sometimes you have to take the keyboard off, etc.  Sometimes the fan is accessible from the bottom.  Really depends on the design.  What you want to do is try to remove the fan (jeweler's screwdriver needed, tiny screws in there) and try to blow the dirt OUT with compressed air.  Some people even recommend removing the heat sink from the CPU and replacing the thermal grease but I have found simply cleaning out around it and removing the fan to do so most effective.  You should consider doing this at some point.

Of course, the fan must still work to keep the CPU cool.  It works in the BIOS Setup (and worked in Windows) but not in Ubuntu?  Have you tried installing all Ubuntu updates that are recommended?  If overheating keeps shutting down the laptop to prevent updates, try putting a fan on it, blowing into the CPU cooling event if possible and propping up the bottom of the laptop a little to let it cool better.  Sometimes newer kernels (installed as part of installing all Ubuntu updates) will fix problems with APCI and fan issues.

---

### Post by whatisupposetodo on 2012-02-27
> **ahallubuntu said:**
> First of all, ANY laptop (Windows or Linux or otherwise) that's more than a few years old should probably have its CPU heat sink cleaned out - they get dusty and dirty over the years, and depending on how well the cooling was designed for your Aspire, it may be more prone to overheating.  I've cleaned a couple of old laptops out and it's amazing what difference it can make in keeping them from overheating.

Taking a laptop apart can be scary, though.  Some are easier than others to be able to get to the fan and heat sink.  Sometimes you have to take the keyboard off, etc.  Sometimes the fan is accessible from the bottom.  Really depends on the design.  What you want to do is try to remove the fan (jeweler's screwdriver needed, tiny screws in there) and try to blow the dirt OUT with compressed air.  Some people even recommend removing the heat sink from the CPU and replacing the thermal grease but I have found simply cleaning out around it and removing the fan to do so most effective.  You should consider doing this at some point.


Of course, the fan must still work to keep the CPU cool.  It works in the BIOS Setup (and worked in Windows) but not in Ubuntu?  Have you tried installing all Ubuntu updates that are recommended?  If overheating keeps shutting down the laptop to prevent updates, try putting a fan on it, blowing into the CPU cooling event if possible and propping up the bottom of the laptop a little to let it cool better.  Sometimes newer kernels (installed as part of installing all Ubuntu updates) will fix problems with APCI and fan issues.

thanks for your answer. 
There are several threats about this same issue. I have cleaned fan few times already and it should be clean enough. Flashing bios sounds too hard for me as a noobie. Fan is working perfecly with windows. 

this is for 11.04 but it should work for 11.10 as well. I couldn`t install it properly.

[http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521)

---

### Post by ahallubuntu on 2012-02-27
I wasn't suggesting you flash the BIOS, but someone in that thread you linked to claims a BIOS updated fixed their problem.  If you still have a way to boot up Windows, updating a BIOS is super easy: just download the file from Acer and run it.  You have to be careful that you're running on AC power and that you don't interrupt the update, though - a BIOS update gone wrong can turn a computer into a "brick" if you are careless.

I'd really update the BIOS as your ultimate solution, so you don't have to mess with kludgey (but well-intentioned) scripts that will probably break again after future Linux releases - but a BIOS fix should be permanent.

There may be ways to update the BIOS safely with Ubuntu but I've not explored them.  The safest thing to do is get some version of Windows running again and then install the BIOS update that way.  I have the luxury of some spare laptop hard drives laying around; what I'd do in your situation probably is install Windows on a spare drive, do the BIOS update, then swap drives back. You may not have that luxury - yes, I'm aware of that...

---

### Post by whatisupposetodo on 2012-02-28
[http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521)

---

