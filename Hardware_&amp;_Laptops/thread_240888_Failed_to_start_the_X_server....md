---
title: "Failed to start the X server..."
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by Grayfox777 on 2006-08-21
I just recently received an Ubuntu CD in the mail, which fixed a previous problem I had. Unfortunately, I now have a new problem. ](*,) Here's the message I get...

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
There's also a bunch of other weird characters on the screen and new lines of text don't start in the right place. 
After it shows me the error, it goes to ubuntu@ubuntu:~$
Anyone have any ideas? :confused:

---

### Post by majesticturkey on 2006-08-21
What kind of graphics card do you have?

A temporary fix idea would be to type at the prompt (that ubuntu@ubuntu$ thing), sudo dpkg-reconfigure xserver-xorg. Press enter. It'll guide you through a setup program. All you need to worry about is when it gives you a list of video drivers to use, try "vesa." The default answers for the rest of the questions should work just fine. When we get some more information or some more knowledgeable folks come by, it'll get fixed.

(when it asks if you want to view the output to diagnose the problem, that information is very helpful for people trying to help you. if you can, getting that info here would be very good.)

---

### Post by Grayfox777 on 2006-08-21
My video card is an Intel 82830M Graphics Controller

Okay, after I set the color depth, I get this...
> 
xserver-xorg postinst warning: overwriting possibly customized configuration
file; backup in /etc/x11/xorg.conf.20060821164228

Then it goes back to the ubuntu@ubuntu:~$ prompt. If I try again without restarting, the reconfiguration fails somewhere through it with the following error...
> 
The X server is now disabled. Restart GDM when it is configured correctly. 
After that, it goes back to the screen before it told me " Failed to start the X server..." and seems to lock up, though it lets me use ctrl+alt+del to shutdown everything that has loaded. I'll try it again when I get the chance and I'll copy down the output if it gives me a chance.

---

### Post by notoriousdbp on 2006-08-21
I'm having the same problem all of a sudden today on my Acer Aspire 3002.  I've been using dapper since release and today I received an update which was certainly something to do with x though I can't remember the full title.  Now X fails to start saying there are "no screens found" in the log.  I thought it was me so I reinstalled Dapper, got my wireless up and running and did a full update and then, lo and behold, it has failed again.  Can anyone helo get me back up and running?

---

### Post by mihaisofti on 2006-08-21
This is exactly the problem I have.  Is there a way to roll back to a previous working system?

---

### Post by rgcrowley on 2006-08-21
I'm having the same problem.  I let the automatic update run and it crashed the xserver.  If anyone has a quick fix it would be appreciated.  The laptop that crashed is the one I desperately needed for work tomorrow.:twisted:

---

### Post by phido on 2006-08-21
For the update trouble
[http://ubuntuforums.org/showthread.php?t=241126](http://ubuntuforums.org/showthread.php?t=241126)
Just in case u didnt see it already ;)

---

### Post by Grayfox777 on 2006-08-22
Okay, there was a lot of stuff, but I'll post what seemed important. I think the stuff after the markers is the important stuff. If something else from the output screen is needed, tell me and I'll post it. 
> (==) log file: "/var/log/Xorg.0.log", Time Tue Aug 22 14:36:56 2006
(==) Using config file: "/etx/X11/xorg.conf"
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

---

### Post by 1oki on 2006-08-22
> **Grayfox777 said:**
> I just recently received an Ubuntu CD in the mail, which fixed a previous problem I had. Unfortunately, I now have a new problem. ](*,) Here's the message I get...


There's also a bunch of other weird characters on the screen and new lines of text don't start in the right place. 
After it shows me the error, it goes to ubuntu@ubuntu:~$
Anyone have any ideas? :confused:

whenever I have an xserver problem I just reconfigure it...

"sudo dpkg-reconfigure xserver-xorg"

It helps to know what video card you have:

"lspci | grep VGA " That will give you the type of video card and you can than match it with the appropriate drivers!

nv = Nvidia
I belive i740/i810 = intel
and the rest is self explanitory

you complete that and start the server with "startx"

follow the onscreen instructions and there ya go! lemme know if that helps...

L

p.s. I get xserver problems a bunch being that I am always tinkering...

---

### Post by stuker on 2006-08-22
this has happened to me as well after this package upgrade.

nooo xxxxx!! :(

I have a Sony VAIO with an NVIDIA graphics card.  I have run the xserver reconfig app but still have the same problem when i do an xstart or reboot

any ideas?

thanks
Stuart

---

### Post by r4ik on 2006-08-22
> **stuker said:**
> this has happened to me as well after this package upgrade.

nooo xxxxx!! :(

I have a Sony VAIO with an NVIDIA graphics card.  I have run the xserver reconfig app but still have the same problem when i do an xstart or reboot

any ideas?

thanks
Stuart

Please read,

[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

Good luck !

---

### Post by stuker on 2006-08-22
thanks

i did this before i saw your post and it worked

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

reboot

saw it in another post here

[http://ubuntuforums.org/showthread.php?t=241126](http://ubuntuforums.org/showthread.php?t=241126)

thanks anyway
Stuart

---

### Post by mpvano on 2006-08-22
A bad update was uploaded yesterday. It's been corrected by a later update. Unfortunately, the bad update was not removed for several hours.

I fixed my system by using the command line update commands to download the fixed packages. Try this before you do anything else. It may be the easiest way to fix the problem.

sudo apt-get update ; sudo apt-get upgrade

At this point, it can't do any harm to try to get the corrected upgrade.

hope this helps...

Mario

---

### Post by Grayfox777 on 2006-08-23
I think my problem with Ubuntu is related to the problem I'm having in Knoppix. For Knoppix to have 32-bit color, I can't get better than 640x480 resolution. And I'm afraid this is all a BIOS related problem. :(

---

### Post by theDentist on 2006-08-23
Just to let everyone know it has also happened to me last night after the recent upgrade.  How do we solve it, is there going to be and upgrade to put it right and if there is what do I type at the prompt to get the updates?      :-x

---

### Post by Gio2k on 2006-08-23
thedentist: It's already been fixed.
try:
sudo apt-get update
sudo apt-get upgrade

---

### Post by tivolives on 2006-08-23
I'm having the same problem with an IBM ThinkPad T41 with an ATI Radeon R250 LF graphics card. I've been running Ubuntu for at least a month with no problems. I followed 1oki's instructions, but when I startx I get:
no device detected
no screens found
X10: fatal IO error 104 (Connection reset by peer) on X server :0.0

---

### Post by tivolives on 2006-08-23
I tried this too:

sudo apt-get update
sudo apt-get upgrade

The update works fine, but the upgrade gives me a 404 not found
message.

---

### Post by tivolives on 2006-08-23
Nevermind:

After several tries, this worked:

sudo apt-get update
sudo apt-get upgrade

I believe I just had a spotty Internet connection.

---

### Post by mjezell on 2006-08-23
This is a problem with the last update for x-server.  Check your version of x-server-xorg-core and if it is 10.3 do a sudo aptitude dist-update,  This will install version 10.4, reboot and the problem should be solved.

---

### Post by theDentist on 2006-08-23
Thanks everyone, the problem is solved. I ran the update and upgrade commands and it worked        :grin:

---

### Post by Grayfox777 on 2006-08-23
Anyone have any new ideas? I'm 99% sure that my problem has nothing to do with the update because I'm just trying to boot from the live cd. I haven't installed Ubuntu and there's not point in doing so if I can't get it to work. :frown:

---

### Post by dabbner on 2006-08-23
Try re-configuring the X server:

in terminal, type "sudo dpkg-reconfigure xserver-xorg"

hope that helps.

---

### Post by Grayfox777 on 2006-08-23
Well, I tried that a few times already and it didn't work (I even tried it in Knoppix). I'll try it again if I get the chance. But does anyone have any ideas I haven't tried yet?

---

### Post by killgoreph on 2006-08-24
I am also experiencing the same problem.  downloaded the ISO, burned it, tried to install it and get failed to start X server.

Even with the proposed fix, i get the same outputs.

My specs are the following:

Gecube ATI X800 GTO 256mb
Epox Motherboard 9NPA3 Ultra
Athlon 64 3000+ Venice Core
1 gb RAM

I hope someone can point us to the right direction... i really wanted to try a linux system

---

### Post by Grayfox777 on 2006-08-25
I can't do "sudo apt-get update" It gives me a "Temporary failure resolving..." error three times, then it says "Some index files failed to download, they have been ignored, or old ones used instead" I get these errors even though Ubuntu does recognize my wireless network card.
My laptop is such a piece of crap... yet it seemed so great a few years ago when I got it. :(

---

### Post by Grayfox777 on 2006-08-29
Does anyone have any new ideas I can try?

---

### Post by tseliot on 2006-08-29
> **Grayfox777 said:**
> I can't do "sudo apt-get update" It gives me a "Temporary failure resolving..." error three times, then it says "Some index files failed to download, they have been ignored, or old ones used instead" I get these errors even though Ubuntu does recognize my wireless network card.
My laptop is such a piece of crap... yet it seemed so great a few years ago when I got it. :(

The problem is just your /etc/apt/sources.list

---

### Post by Grayfox777 on 2006-08-30
So the defaults are wrong? How do I replace them with the correct servers? And what are the correct servers? :-k

---

### Post by Grayfox777 on 2006-09-07
How do I replace the sources in the list? :confused:

---

### Post by Grayfox777 on 2006-09-15
Can someone please give me a walkthrough of how to check and replace the sources in /etc/apt/sources.list ....?

---

### Post by Grayfox777 on 2006-10-26
Well... I guess I'm just going to give up on Linux for now... maybe until I get a new computer. I just don't think it's going to work on this one. No clue when I'll be getting a new one though, but it will probably be a while. :(

---

