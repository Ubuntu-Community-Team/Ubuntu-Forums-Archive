---
title: "Not Authorised"
date: 2011-04-13
forum: Hardware
---

### Post by pieboy on 2011-04-13
I recently installed ubuntu 10.04(lucid) on my friends  dell inspiron n5010 it installed without any problems but now it is causing big problems in disk mounting ,sound drivers etc.
i need to mount the disks(windows drives and usb drives) from command line
and even some other tools are also denying from access for authorization problem 
plz help me to solve the problem .some times it sows there is audio device and gives sound properly some time it gives problem that there is no audio device.
I love ubuntu i don't want to shift to windows if it doesn't gets cured he will simple remove it from his laptop 
something good in this is wifi drivers were installed successfully and the Internet is accessible
here are some pics explaining the problem

[IMG]http://img828.imageshack.us/img828/4238/screenshot2vf.png[/IMG]


[IMG]http://img689.imageshack.us/img689/1336/screenshot4vos.png[/IMG]

---

### Post by pieboy on 2011-04-14
I recently got another problem shutdown isn't working this is ridiculous i can't shutdown my own system this is the worst problem i have ever faced when i click shutdown it just log off form my account i need to execute shutdown command even then also it showing some annoying message with out shutting down in the terminal it termed all applications but it freezes  after  that

---

### Post by hsoulen on 2011-04-14
First off... Welcome!

You will find very good advice in these forums and we all want you to stick with Ubuntu as with any operating system you will have issues but you won't always find a community to support you.

Need a bit more information to assist.

[LIST]
[*]Hardware Details (What model computer, sound card, video card etc.) Output of "lspci" is pretty helpful
[*]Error messages (output from logs always helps)
[/LIST]

Looking forward to your reply.

Hank

---

### Post by coffeecat on 2011-04-14
> **pieboy said:**
> I recently installed ubuntu 10.04(lucid) on my friends  dell inspiron n5010 it installed without any problems but now it is causing big problems in disk mounting ,sound drivers etc.
i need to mount the disks(windows drives and usb drives) from command line

No, you shouldn't need to mount any of those devices from the command line. They should automount without any problem or any authorisation error when you click on the entry in the Places sidebar as your screenshot shows you have done. Something has gone wrong with your installation.

I see you have extensively modified the theming. Have you also installed any apps to do with automounting or mounting USB devices? Some of these interfere with the perfectly adequate automounting functionality built into the gnome desktop.

Or - with all your other problems, I wonder if your installation medium was faulty. Did you check the md5sum of the downloaded ISO? If you used a CD, did you burn this at slow speed? Also - if you try booting with the CD and tap the spacebar as soon as the two small icons appear, you get the old live CD text menu. You can do a CD integrity check from that - third option if I remember correctly.

---

