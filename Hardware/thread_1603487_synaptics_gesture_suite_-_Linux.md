---
title: "synaptics gesture suite - Linux"
date: 2010-10-22
forum: Hardware
---

### Post by blondyman1503 on 2010-10-22
synaptics says that the gesture suite is available for Linux. I've downloaded it for Windows, but i can't figure out how to get it for Linux.
Where would I go about finding this?

---

### Post by AuP%*qb!# on 2011-06-11
I see this is an old thread, I am looking for the same thing.
Have you already found  a place to get this or are you still looking? Anyway, Hopefully someone is likely to reply, and there is no point starting a new thread as I am looking for exactly the same thing, and any replies will also be helping the thread author if he don't already have it and if he is still use Ubuntu, which I guess he would be as Ubuntu is really user friendly.

I have the new beautiful 11.04 on my acer aspire one.

I have an ipod touch and iMac and am getting so confused with how to work windows and linux pc mice and keyboards. I used to be good with windows way but have got so relaxed with my iMac and iPod as they are much easier to understand then the ways other PCs work.

I really need this as much as it sounds that he/she wants it.

Thanks for the help

Jwarn

---

### Post by blondyman1503 on 2011-06-11
I haven't been looking in a while. I haven't found anything.

---

### Post by aakash.ece on 2011-06-22
bump.

Me too, looking for the same. The possibilities with synaptics touchpad are tantalizing, but couldn't find enough OS support yet (I have a thinkpad edge E420 + ubuntu 11.04)

Still, sharing what I found -
- install gpointing-device-settings package to get the circular scroll and two finger scroll working.
- The complete possibilities can be seen with the command:
xinput list-props "SynPS/2 Synaptics TouchPad"

Though complete description for these I couldn't find.

---

### Post by varunrajan on 2011-06-22
Cross reference from [http://ubuntuforums.org/showthread.php?p=10967868](http://ubuntuforums.org/showthread.php?p=10967868)
> **J4K4 said:**
> [ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar](ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar)

here is the driver...

This link gives a rpm package of the official synaptics driver. I tried to convert it to deb using alien but failed. Can someone who knows how to manually convert between rpm and deb please make the conversion?

Thanks

---

### Post by Kbloch on 2011-09-17
> **varunrajan said:**
> Cross reference from [http://ubuntuforums.org/showthread.php?p=10967868](http://ubuntuforums.org/showthread.php?p=10967868)


This link gives a rpm package of the official synaptics driver. I tried to convert it to deb using alien but failed. Can someone who knows how to manually convert between rpm and deb please make the conversion?

Thanks

I was refereed to this driver by HP a few months back and I only recently learned about what package really meant, like .deb vs .rpm.

I also tried to use Alien, but it kept failing. Somebody suggested that it may be because that .rpm is a 32-bit/i386 package, not 64-bit like my OS. Converted packages need to be the same bit density (technical term?) as the Alien version and OS being used.

Okay, so I spent the past few hours on this but I think I finally got something. Here's a kind of journal of what I've been through to get this done.

:popcorn:I finally got something that looks like it worked, ***[COLOR=black]maybe[/COLOR]***. I had to run a live 10.10 i386 Netbook version I had on hand.[INDENT]Here's what I did:
[/INDENT]sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i[INDENT][COLOR=DarkRed]**you'll have to substitute your directory instead of using mine**[/COLOR]
[/INDENT][INDENT]and this is the output I got:
[/INDENT]ubuntu@ubuntu:~$ sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i
    dpkg --no-force-overwrite -i synaptics-touchpad_15.1.4.0-14_i386.deb
Selecting previously deselected package synaptics-touchpad.
(Reading database ... 125451 files and directories currently installed.)
Unpacking synaptics-touchpad (from synaptics-touchpad_15.1.4.0-14_i386.deb) ...
Setting up synaptics-touchpad (15.1.4.0-14) ...
Recognized Device SYN1E18
Successfully Generated Registry Files
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
ubuntu@ubuntu:~$

-BTW, what is "bamfdeamon" is that a a deamon that's a BAMF? LOL!

This is the first time I've ever ran it without any errors. I found the Synaptics icon in my Applications but it doesn't do anything at all. I'm thinking that it's because I'm running 10.10 i386 LIVE, can't be sure. Maybe a restart is required, but as I'm running LIVE that would undo everything, right?
[INDENT]Next I converted the .rpm and let Alien save the .deb to the default directory.
[/INDENT]sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -d -c

When I went to go get it, t wasn't there. So I ran a search for the file and it was found at "/home/ubuntu" (probably because I'm running a LIVE version, dunno).

And that leaves me at the part where I upload it to the Ubuntu Forums and get sued by Synaptic. I mean, it is proprietary software right? Either way, I'm not fully comfortable with redistributing **their** software. After a thorough read of their licensing agreement I'll decide what do to do next.

Sorry for the bad formatting and other errors, I'm still such a n00b when it comes to using terminal or doing write-ups. Please PM me right away if this work for you! I really hope this adds to us finally getting the official driver and program up and running in Ubuntu.:P

---

### Post by AuP%*qb!# on 2011-10-01
I tryed doing that but this is my output when i type first line

XXX@XXX:~$ sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i
sudo: alien: command not found


I really really want this as I am now taking it to college with me.

---

### Post by nothingspecial on 2011-10-01
Hi :D,

Your error is due to the fact that you don't have alien installed.

```
sudo apt-get install alien
```

Whether or not the fix in this thread will work once you have installed alien......... I don't know.

---

### Post by parth.s on 2011-10-02
> **Kbloch said:**
> I was refereed to this driver by HP a few months back and I only recently learned about what package really meant, like .deb vs .rpm.

I also tried to use Alien, but it kept failing. Somebody suggested that it may be because that .rpm is a 32-bit/i386 package, not 64-bit like my OS. Converted packages need to be the same bit density (technical term?) as the Alien version and OS being used.

Okay, so I spent the past few hours on this but I think I finally got something. Here's a kind of journal of what I've been through to get this done.

:popcorn:I finally got something that looks like it worked, ***[COLOR=black]maybe[/COLOR]***. I had to run a live 10.10 i386 Netbook version I had on hand.[INDENT]Here's what I did:
[/INDENT]sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i[INDENT][COLOR=DarkRed]**you'll have to substitute your directory instead of using mine**[/COLOR]
[/INDENT][INDENT]and this is the output I got:
[/INDENT]ubuntu@ubuntu:~$ sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i
    dpkg --no-force-overwrite -i synaptics-touchpad_15.1.4.0-14_i386.deb
Selecting previously deselected package synaptics-touchpad.
(Reading database ... 125451 files and directories currently installed.)
Unpacking synaptics-touchpad (from synaptics-touchpad_15.1.4.0-14_i386.deb) ...
Setting up synaptics-touchpad (15.1.4.0-14) ...
Recognized Device SYN1E18
Successfully Generated Registry Files
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
ubuntu@ubuntu:~$

-BTW, what is "bamfdeamon" is that a a deamon that's a BAMF? LOL!

This is the first time I've ever ran it without any errors. I found the Synaptics icon in my Applications but it doesn't do anything at all. I'm thinking that it's because I'm running 10.10 i386 LIVE, can't be sure. Maybe a restart is required, but as I'm running LIVE that would undo everything, right?
[INDENT]Next I converted the .rpm and let Alien save the .deb to the default directory.
[/INDENT]sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -d -c

When I went to go get it, t wasn't there. So I ran a search for the file and it was found at "/home/ubuntu" (probably because I'm running a LIVE version, dunno).

And that leaves me at the part where I upload it to the Ubuntu Forums and get sued by Synaptic. I mean, it is proprietary software right? Either way, I'm not fully comfortable with redistributing **their** software. After a thorough read of their licensing agreement I'll decide what do to do next.

Sorry for the bad formatting and other errors, I'm still such a n00b when it comes to using terminal or doing write-ups. Please PM me right away if this work for you! I really hope this adds to us finally getting the official driver and program up and running in Ubuntu.:P

Sorry to cut-in. I have a similar thread going on for being able to use multi touch gestures....anyways, i followed the steps:
1 installed alien
2 downloaded the package and ran the first alien command on the .rpm package, even i see the synaptics icon in the application..and im not running live but an installed version, its not responding
3 used alien again to convert it to a .deb package.

But when i try to install, it says its already installed for me (i might have installed it earlier)...so what to do next...

btw im using Natty on an Asus laptop...

---

### Post by Kbloch on 2011-10-05
Honestly, I gave up on this driver. I finally got it to run and install in Ubuntu 10.10 -32, but it doesn't seem to do anything at all.
I tried again and got a message that it was already installed too. I don't know what to do at this point.
I even installed OpenSuse because it uses the unconverted .rpm package instead Ubuntu's .deb. The driver installs with no problem, there's even an icon to start the program, but clicking it does nothing, even after restart. There was an update to this driver too, I believe it's a .bin file but I can't get it to install in Suse. So I didn't even bother trying in Ubuntu.

I'm not familiar with Asus's customer support or warranty service, but I'd try getting them to provide you with the driver and installation directions. That's how I originally got the Synaptics driver from HP. Per recommendations from many other users on the forums, I'd also recommend using only the 32-bit versions of Ubuntu unless you know how to write your own drivers or convert packages manually.

I really hate giving up, but I don't know enough (yet) to move on and get something useful out of this.

---

### Post by Kbloch on 2011-10-05
> **AAA said:**
> I tryed doing that but this is my output when i type first line

BBB@CCC:~$ sudo alien /media/8GBCruzerB/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i
sudo: alien: command not found


I really really want this as I am now taking it to college with me.

DDD,
--This may be in vane as I couldn't get it to make any notable changes to my system, but...

First, like nothingspecial says, make sure you have alien installed first.
Be sure to use your own directory when trying to do this.
In my n00b opinion, I'd do it this way:
Open Gedit (it's a notepad -like basic text editor)
type this into the first line, no quotes. "sudo alien" place just one space after that.
Next, go to you driver file with the name ending in ".rpm"
right-click that file and open the properties window. Copy the file path listed next to 'Location:'. It'll look something like "/home/username/downloads" now paste that into Gedit immediately following the space you entered earlier.
Without adding any spaces, place an additional "/" at the end of the file path you just pasted.
Now, go back to the properies window and copy the file name and paste that right into your Gedit file, no spaces, right after the "/" you just added and put just one space at the end of this.
Finally add the options, no quotes. "-c -i" to the end of this.
It should look exactly like what you had before, save for the changes you've made in where alien is going to look for the file.

Truth be told, I moved on from Maverick to Natty. Natty uses the Unity desktop, it's weird at first, but I got used to it. It also has better cickpad right-click functionality out of the box. You just tap with two slighly seperated fingers on the clickpad to activate right-click menus. Which is GREAT when your roomate is sleeping 'cause you're not making clicking noises keeping them up, while they silently plot your demise for keeping them awake at night. The next release is coming out very soon, this month actually. It'd be worth checking out Natty Live to see if you like it. I highly recommend it as the next release uses the Unity desktop and has the same clickpad functionality as Natty.

Good luck in college :guitar:, let me know if calculus has gotten any easier!

---

### Post by parth.s on 2011-10-17
> **Kbloch said:**
> 
I'm not familiar with Asus's customer support or warranty service, but I'd try getting them to provide you with the driver and installation directions. That's how I originally got the Synaptics driver from HP. Per recommendations from many other users on the forums, I'd also recommend using only the 32-bit versions of Ubuntu unless you know how to write your own drivers or convert packages manually.

I really hate giving up, but I don't know enough (yet) to move on and get something useful out of this.

I really believe that ASUS wont be able to much here. Also if its working for an HP it should also work for an ASUS right? 

And I am using a 32-bit version. And im not giving up yet...

---

### Post by baapoo on 2011-11-02
i do same bt i got this 
mansoor@mansoor-lappy:~$ sudo alien /home/mansoor/Desktop/synaptics-touchpad-15.1.4.0-13.i386.rpm -c -i
[sudo] password for mansoor: 
/home/mansoor/Desktop/synaptics-touchpad-15.1.4.0-13.i386.rpm is for architecture i386 ; the package cannot be built on this system
mansoor@mansoor-lappy:~$

---

### Post by lewtds on 2011-11-17
I get the Synaptics driver from HP [here]("http://www.hp.com/cgi-bin/bizsupport/wgbu-eula1.pl?Path=ftp://ftp.hp.com/pub/softpaq/sp54001-54500/sp54309.tar"). Normal tar extraction wouldn't work and I have to use Archive Manager to copy the RPM files in there out (there are both 32 and 64bit versions). I used alien to convert and install it. The driver doesn't seem to work and I look a bit into its binary (/opt/Synaptics/bin/SynTPCpl) using ldd and found that a library is not existing: "libwx_gtk2u-2.8.so.0 => not found". This library seems to belong to the libwxgtk2.8-0 packet but it doesn't. It seems they use a different version of libwxgtk that is incompatible with Ubuntu. Unless we can find some way to get libwx_gtk2u-2.8.so.0, this thing wouldn't work.
ps. I've tried symbolic linking other similarly named libraries in that package to libwx_gtk2u-2.8.so.0 to no avail...

---

