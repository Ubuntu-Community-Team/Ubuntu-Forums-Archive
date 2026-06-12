---
title: "[SOLVED] Ubuntu Downloading, Please HELP!!!!!"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by kendo_water on 2008-12-21
Since no one helped me on me Xubuntu post, I uninstalled Xubuntu and got regular Ubuntu. Still, I cant download things and an error comes up.

Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!

I tried to download flash player and the same error came up:"Error Wrong architecture 'i386'

Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!Please!!!!!Please!!!!PLEASE!!!!!!!!!!! HELP!!!!!!!!!!!

---

### Post by howefield on 2008-12-21
Have you installed 64 bit Ubuntu ?

---

### Post by Sprut1 on 2008-12-21
Thats an insane post...

Anyhow, seems like you are trying to install a 32bit version on a 64bit system, am I right?

Edit: I don't know if this will help you, but I found this:
[http://www.howtoforge.com/installing-flash-player9-on-64bit-linux](http://www.howtoforge.com/installing-flash-player9-on-64bit-linux)

---

### Post by 2hot6ft2 on 2008-12-21
You must have installed the 64 bit and that's why you got the error trying to install a 32 bit package on a 64 bit OS.

Why are you downloading a flash player in the first place. Programs are installed thru Synaptic System>Administration>Synaptic Package Manager, update manager Applications>Add Remove, and thru the terminal Applications>Accessories>Terminal. With few exceptions.

If you want all your multimedia to work here's the guide that will fix you right up. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by kendo_water on 2008-12-21
I don't know how to do these things, I just wanted to watch videos on you-tube, and I'm sick of people saying I'm an idiot!!

I have been on all sorts of other posts and no answers from any of them, this is the first time anyone has actually answered!!!

I just cant take it any more, I just started Ubuntu, and I'm starting to think it was a bad idea!

---

### Post by 2hot6ft2 on 2008-12-21
I didn't read where anyone said you were an idiot. Did I miss a post?

You obviously have the 64 bit OS installed just follow the instructions in the post here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) for 64 bit and what ever version of ubuntu you installed 8.10 Intrepid, 8.04 Hardy and you'll have all your multimedia working.

It's no worse than having to install codecs to watch videos in windows, or a certain program to access something.

---

### Post by 2hot6ft2 on 2008-12-21
Matter of fact if you'll tell me which one you're using I'll post the command from there that will have it working in minutes.

So which is it? 8.10 Intrepid Ibex or
8.04 Hardy Herron

---

### Post by kendo_water on 2008-12-21
I'm pretty sure its 8.10

I got it off of the Wubi installer....thing

---

### Post by albinootje on 2008-12-21
> **kendo_water said:**
> I don't know how to do these things, I just wanted to watch videos on you-tube, and I'm sick of people saying I'm an idiot!!

I have been on all sorts of other posts and no answers from any of them, this is the first time anyone has actually answered!!!

I just cant take it any more, I just started Ubuntu, and I'm starting to think it was a bad idea!

According to the Adobe website there's no 64bit flash-player10 for Linux yet (Also not for Mac and Windows).

Are you using Ubuntu 8.04/Hardy Heron or 8.10/Intrepid Ibex ?

Can you please post the output of :
```

uname -a

```

---

### Post by Sprut1 on 2008-12-21
Edit: albinootje beat me too it.

Terminal:
```

lsb_release -a
```

---

### Post by 2hot6ft2 on 2008-12-21
How to use this:
Open a terminal by going to:
Applications > Accessories > Terminal
then highlight the appropriate code below, right click and copy
Then go to the terminal window and right click and paste
and hit Enter
Type in your password when prompted (it wont be displayed just type it in and hit Enter)
when it asks if you want to proceed hit the letter Y and hit Enter
When it finishes just close the terminal window and you're all set but a reboot would be a good idea anyway.

Use these 2 first

> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


NOW USE ONLY THE ONE THAT APPLIES TO WHAT YOU'RE RUNNING BETWEEN THESE 2

8.10 Intrepid Ibex
64-Bit Ubuntu Users:


> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar


Sit back and enjoy

---

### Post by kendo_water on 2008-12-21
I'm a little confused, What is the difference Between 8.10 Hardy and the other one?

I appreciate the help, and I thank you for this.  

I understand that the terminal is the command prompt of Ubuntu, so do I copy and paste those codes you put down  in those posts?

---

### Post by kendo_water on 2008-12-21
The first one says:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package non-free-codecs

---

### Post by 2hot6ft2 on 2008-12-21
I forgot you'll need to do these 2 commands first in a terminal. Sorry

> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

It's like windows 98 and windows xp they are different in some ways but you want to use the things for what you have and not for something else

---

### Post by 2hot6ft2 on 2008-12-21
hold on let me fix my post

---

### Post by kendo_water on 2008-12-21
second one said:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
E: Couldn't find package libflash-mozplugin

---

### Post by 2hot6ft2 on 2008-12-21
Ok, it's fixed. Refresh the page and follow the instructions. Sorry about that I got ahead of myself.

---

### Post by albinootje on 2008-12-21
> **Sprut1 said:**
> 
```

lsb_release -a
```

Cool, i didn't know this command, thanks :)

(I already wondered why Ubuntu kept on having /etc/debian_version and not doing something about that.)

---

### Post by albinootje on 2008-12-21
> **kendo_water said:**
> The first one says:
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic

Okay, you're using Ubuntu Intrepid Ibex, also known as 8.10

The Adobe website says that there's no flash-player version 10 for 64bit Linux (And also not for Mac and Windows).
Can a 64bit Ubuntu user help out ?

And kendo_water, will you be needing Java later on ?

---

### Post by kendo_water on 2008-12-21
one second..............

---

### Post by djbon2112 on 2008-12-21
> **albinootje said:**
> Okay, you're using Ubuntu Intrepid Ibex, also known as 8.10

The Adobe website says that there's no flash-player version 10 for 64bit Linux (And also not for Mac and Windows).
Can a 64bit Ubuntu user help out ?

And kendo_water, will you be needing Java later on ?

There's an alpha out, you can get it here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) Though it's an alpha, I've been using it for almost a month and haven't had a problem yet. You do have to manually install it, though.

---

### Post by Sprut1 on 2008-12-21
> **albinootje said:**
> Cool, i didn't know this command, thanks :)

(I already wondered why Ubuntu kept on having /etc/debian_version and not doing something about that.)

Np, always fun the noob helps :KS

---

### Post by kendo_water on 2008-12-21
it's just not working at all........

---

### Post by 2hot6ft2 on 2008-12-21
> **kendo_water said:**
> The first one says:

The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.

You see where it said this part. apt-get autoremove and apt-get update are 2 common terminal commands the first one would be used like this
```
sudo apt-get autoremove
```
which removes packages that are no longer needed such as once a program is installed the original program that it was installed from can be removed without affecting your system.

The other one used like this
```
sudo apt-get update
```
Updates your sources so that the list is more up to date and you can get the latest software to install.

It's a good idea to keep more than 1 kernel. One reason for having more than 1 kernel is that if something stops working with the new kernel you can go back to the one that worked.

For me kernel 2.6.27-9-generic made my wifi keep dropping signal but when I boot with kernel 2.6.27-7-generic it stays connected. Go figure.

So I keep them both until a newer one comes out that works then I'll uninstall 1 and still have 2.

---

### Post by 2hot6ft2 on 2008-12-21
> **kendo_water said:**
> it's just not working at all........
Which part isn't working?

---

### Post by kendo_water on 2008-12-21
as soon as i type
 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

all sorts of weird codes come up(and I didn't type ENTER key either), it never gives me the chance to type:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar

---

### Post by 2hot6ft2 on 2008-12-21
Ok step by step. You're running 8.10 so put this in the terminal (You don't TYPE Enter you just hit the Enter key)
> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list 
Hit Enter and when it finishes
then this
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update 
Hit Enter and when it finishes
then this
> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar
It should be working

---

### Post by albinootje on 2008-12-21
> **kendo_water said:**
> as soon as i type
 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

all sorts of weird codes come up(and I didn't type ENTER key either)

It is a bit weird looking indeed.

You should type "y" (without the "" characters) at a certain point where it asks you "N" or "y".
After that hit the enter key.
When all of that is finished, then you can copy & paste the long line you didn't have a chance to type in.

---

### Post by 2hot6ft2 on 2008-12-21
You may not even have to hit enter as long as it started doing it you're alright.

---

### Post by 2hot6ft2 on 2008-12-21
> **albinootje said:**
> It is a bit weird looking indeed.

You should type "y" (without the "" characters) at a certain point where it asks you "N" or "y".
After that hit the enter key.
When all of that is finished, then you can copy & paste the long line you didn't have a chance to type in.
You got it. Correct

---

### Post by kendo_water on 2008-12-21
After I type all that down it asks me for the password, I type it in, hit enter key then............Nothing..........

---

### Post by 2hot6ft2 on 2008-12-21
You should just be copying and pasting (helps prevent typos) the only typing would be your password and the letter y

---

### Post by kendo_water on 2008-12-21
Wait............... now its saying it an invalid operation.

---

### Post by albinootje on 2008-12-21
> **kendo_water said:**
> Wait............... now its saying it an invalid operation.

Can you copy & paste the complete error message in here please ?
Thanks.

---

### Post by 2hot6ft2 on 2008-12-21
> **kendo_water said:**
> Wait............... now its saying it an invalid operation.
You probably had a typo

---

### Post by kendo_water on 2008-12-21
Wait........... now it says:

 The update command takes no arguments



???????????????????????????????????????????????????

---

### Post by kendo_water on 2008-12-21
I am typing this exact code in my computer:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get updatesudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar 

it says:OK
E: Invalid operation updatesudo 

are you sure YOU don't have any typos?

---

### Post by 2hot6ft2 on 2008-12-21
There were no arguments in the command unless you hit the y before it asked for either a y or n.

---

### Post by 2hot6ft2 on 2008-12-21
They are 3 separate commands not 1. You do each one at a time in the order I gave. I simply copied and pasted them from here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) I didn't change anything.

---

### Post by albinootje on 2008-12-21
> **kendo_water said:**
> I am typing this exact code in my computer:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get updatesudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar 

it says:OK
E: Invalid operation updatesudo 

are you sure YOU don't have any typos?

Thanks for the error-message output.

You or someone else forgot a space between "update" and "sudo".

Please try copy & paste or try again including that space.

Or are you not running a graphical desktop right now ?

---

### Post by 2hot6ft2 on 2008-12-21
> **kendo_water said:**
> I am typing this exact code in my computer:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get updatesudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar 

it says:OK
E: Invalid operation updatesudo 

are you sure YOU don't have any typos?
Break that down don't run them together like that.

Ok step by step.

Step 1
> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
Hit Enter and when it finishes
then this
Step 2
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
Hit Enter and when it finishes
then this
Step 3
> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar

---

### Post by kendo_water on 2008-12-21
OK......... Its working!!!!!!!!!

Thank you SOOOOOOOOOOOOOOOOO much!!!!!!!!!!!!!!

It says its gonna take an hour but.........YES!!!!!!!!

---

### Post by kendo_water on 2008-12-21
now 25 mins

---

### Post by kendo_water on 2008-12-21
Plus.... Im a 5 cups of Ubuntu also!!!!!!!!

---

### Post by 2hot6ft2 on 2008-12-21
Glad to help. Whenever commands are posted separately that means you run them that way. While there are some you can run together like you were trying to do most of the time you run them as a completely individual command.

---

### Post by 2hot6ft2 on 2008-12-21
> **kendo_water said:**
> Plus.... Im a 5 cups of Ubuntu also!!!!!!!!
And all in this one thread. I need a cup now.
:lolflag:

---

### Post by 2hot6ft2 on 2008-12-21
By the way that will make more than just your flash work so now you can watch your you tube videos and more.

---

### Post by albinootje on 2008-12-21
> **2hot6ft2 said:**
> By the way that will make more than just your flash work so now you can watch your you tube videos and more.

Is 64 bit flash-player supported through the package from Medibuntu ?
(It's years ago that I tried 64 bit Linux and FreeBSD)

---

### Post by kendo_water on 2008-12-21
I am so glad everyone helped me through this, and I am extremely grateful!

                   THANK YOU EVERYONE!!

I just hope the thing works!!!

---

### Post by kendo_water on 2008-12-21
How big is this file?

---

### Post by 2hot6ft2 on 2008-12-21
> **albinootje said:**
> Is 64 bit flash-player supported through the package from Medibuntu ?
(It's years ago that I tried 64 bit Linux and FreeBSD)
Yes, I'm running 64 bit right now and it works.

---

### Post by 2hot6ft2 on 2008-12-21
> **kendo_water said:**
> How big is this file?
It's not 1 file but a bunch or them. Each one of these is a package.
alsa-oss
faac 
faad 
flashplugin-nonfree 
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
ia32-libs
icedtea6-plugin
libavcodec-unstripped-51
libmp3lame0
non-free-codecs
openjdk-6-jre

Along with any dependencies they may have

---

### Post by 2hot6ft2 on 2008-12-21
albinootje you should really visit the post where I got all the info from as it has a whole lot of info that you might appreciate. You can find it here.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by albinootje on 2008-12-21
> **2hot6ft2 said:**
> albinootje you should really visit the post where I got all the info from as it has a whole lot of info that you might appreciate. You can find it here.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Thank you for that link! :)

I'm actually wondering how to have a good answer for "embedded" videos. I've tried amongst others mplayer- vlc- totem- xine- and gnome-mplayer-plugins for Firefox, but with various results.
Last thing that i tried was the media-connectivity add-on in Firefox which was pretty OK, but still i am unhappy about the overall result for my desktop users at work.

But I'll post this in a new thread later on.
First i'd like to see whether it's possible to backport Totem + the new BBC-plugin from Intrepid to Hardy.
[edited -> ]
Answer, nope, alas :(
[https://bugs.launchpad.net/hardy-backports/+bug/293563](https://bugs.launchpad.net/hardy-backports/+bug/293563)

---

### Post by 2hot6ft2 on 2008-12-21
> **albinootje said:**
> Thank you for that link! :)

I'm actually wondering how to have a good answer for "embedded" videos. I've tried amongst others mplayer- vlc- totem- xine- and gnome-mplayer-plugins for Firefox, but with various results.
Last thing that i tried was the media-connectivity add-on in Firefox which was pretty OK, but still i am unhappy about the overall result for my desktop users at work.

But I'll post this in a new thread later on.
First i'd like to see whether it's possible to backport Totem + the new BBC-plugin from Intrepid to Hardy.
Search and ye shall find. I've seen that topic before here. Embedded videos that is. And you're welcome

---

### Post by 2hot6ft2 on 2008-12-21
A parting shot of my desktop. Love the theme. HO HO HO

---

### Post by albinootje on 2008-12-21
> **2hot6ft2 said:**
> A parting shot of my desktop. Love the theme. HO HO HO

wow, nice color-scheme ! :)

---

### Post by 2hot6ft2 on 2008-12-21
One of the perks of Ultimate Edition, the theme packs. Now I need to burn the X-mas Edition and use it as an update disc ...lol.

---

