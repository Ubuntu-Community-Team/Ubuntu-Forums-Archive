---
title: "please tell me i didnt destroy my new laptop with sudo rm -rf /"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by jasoniscool on 2006-01-28
okay so I installed ubuntu fine using a network install.  i was setting it up and following this guide: 

[http://www.ubuntuforums.org/showpost.php?p=502685&postcount=48](http://www.ubuntuforums.org/showpost.php?p=502685&postcount=48)

i was trying to log in as the root user through the terminal and entered the command sudo rm -rf /  now i thought it would let me log in as a root user, but im not sure what this command actually does but now i can't boot into ubuntu at all i get a screen that says 'no inittab file found enter runlevel' and whatever number i hit it says 'no more processes left in this runlevel' and then the laptop freezes.  i want to completly reinstall ubuntu but i can't because this laptop has a non-functional cd-rom drive, no floppy drive, and doesn't support USB flash boot devices.  the two options in the bios are HDD and Realtek Boot Agent.

I am completly freaking out here, someone please help me thanks.

---

### Post by drummer on 2006-01-28
lol... sorry. Well, you didn't damage any harware by running that command, but what it does do is delete every file in the root ( / ) partition... which is everything. So you have no more Ubuntu install now, just an empty hard drive. You will have to reinstall Ubuntu i beleive, sorry.

---

### Post by s0lid on 2006-01-28
dude you're screwed. :) rm -rf / just delete everything from your root directory which is /. 


read the manual of rm.
[http://www.pvv.ntnu.no/~steinl/vitser/rm.html](http://www.pvv.ntnu.no/~steinl/vitser/rm.html)

if you can boot on USB get an external cdrom so you can boot it or an external hdd with ubuntu on it then just dd it to your laptop.

---

### Post by jasoniscool on 2006-01-28
okay someone NEEDS to change that article.  it doesn't say anywhere that that command deletes your entire hard drive.  I am going to attempt to reinstall ubuntu off a usb drive now.  wish me luck =[

---

### Post by RavenOfOdin on 2006-01-28
> 
Re: please tell me i didnt destroy my new laptop with sudo rm -rf /


What? You want me to lie?!?

---

### Post by s0lid on 2006-01-28
> 
Can you see where this can be a bad thing yet? I already gave the example of
[QUOTE]
Code:

sudo rm -rf /


right? Yah thats what I mean. 
[/QUOTE]

well there's already a "so called" warning.

---

### Post by drummer on 2006-01-28
[QUOTE=drummer]You will have to reinstall Ubuntu[/QUOTE]
Unless it's possible to undelete files?? I'm sure you can on a FAT FS with ghost or something (never done it myself)... not sure how ext3 handles deleted files, but maybe possible. But then reinstalling might be just as easy.

---

### Post by jasoniscool on 2006-01-28
my USB flash drive is only 128 megs...

is it possible to install ubuntu from that somehow?

---

### Post by jasoniscool on 2006-01-28
okay i used syslinux for the memorystick and then extracted this to it: [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso)

and then used a net install!  and now ubuntu is installed again! hooray!!!

---

### Post by Galoot on 2006-01-28
You typed the command in without reading the paragraph before it? Why?

The article doesn't need to be edited, it needs to be read.

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=Galoot]
The article doesn't need to be edited, it needs to be read.[/QUOTE]
I disagree. Someone misread it and trashed his/her drive. that's enough prooffor the need edit the article to put a big warning in caps and bold. Anyway, I pm'ed the poster, he's the one who should make the decision. 

Also, thanks to OP for posting his/her solution. There is also DSL (damn small linux) that you might wanna get into your flash / memory stick and carry around just in case something else happens.

---

### Post by Galoot on 2006-01-29
[QUOTE=Galoot]
The article doesn't need to be edited, it needs to be read.[/QUOTE][QUOTE=towsonu2003]I disagree. Someone misread it and...[/QUOTE]
I'm glad we agree.

---

### Post by Kyral on 2006-01-30
Okay I feel like complete shithead (mods let this one slide I'm calling myself one :P) that someone read that and actually rm -rf'd themselves. I have added in a MASSIVE warning in there now (You can't miss it and if you do its your own fault now :P)

---

### Post by public_void on 2006-01-30
Not suprisingly, there is a google video of a guy do the same thing, and with an Ubuntu box, [link]("http://video.google.com/videoplay?docid=464540691509009245&q=Linux").

---

### Post by linuxfanatic1024 on 2006-06-30
Dude, are you NUTS??? You need to pay more attention to what you read!

---

