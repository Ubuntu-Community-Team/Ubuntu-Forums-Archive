---
title: "im in trouble."
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by lakeyboyben on 2008-03-08
Hi, i have an ASUS A6R entertainment laptop. it has an ati radion xpress 200M Grpahics card and XP installed.

I have had trouble trying to install any kind of linux system.

I put in the live CD, click start and install ubunutu, and then im left with the flashing underscore... which should then lead to the system loading up to install, but it doesnt.

Ive been told that this could be due to a number of reasons and have tried every solution offered to me and i have had no joy... one person suggested that it might be my CD drive losing its hardware ID and basically like "OK, Ive got my hard drive and linux, now where did i put my CD Drive"

PS "Sorry, it's a DVD drive... my bad."

but anyway, im wondering if updating or flashing my bios would help, and if not, then does anyone have suggestions.

---

### Post by seshomaru samma on 2008-03-08
do not play with your BIOS 

can you tell us which solutions you have tried?
if the CD doesn't work you can try [Unetbooting ]("http://lubi.sourceforge.net/unetbootin.html"), just install a small file on windows reboot and your installation will begin.
there are also different things you can do with the CD , graphic safe mode etc..
but first ,which solutions have you tried?

---

### Post by lakeyboyben on 2008-03-08
well i have tried some guides and stuff such as using vesa mode and the boot options... but i just tried the net one u recommended and it does the same thing.. i get this on my screen, and it hangs and does nothing.



[http://img247.imageshack.us/img247/2285/dsc00256jc2.jpg](http://img247.imageshack.us/img247/2285/dsc00256jc2.jpg)

basically, this is the problem i have had all along and i am wondering why it is doing it

---

### Post by lakeyboyben on 2008-03-08
this message seems to show everything is ok, but does nothing.. so realy shows its not my cd drive if it wont work from my hard drive either......

i did post some things on kubuntu forums a while a go and was given some advice, but nothing worked... they were asking me to do things on the CLI when i couldnt even access it, because nothing loaded up... it loads into that screen in the previous post, and then nothing happens....


This is the topic, 



lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
kubuntu wont install... left with a flashing underscore
« on: January 27, 2008, 09:57:35 am » 	Reply with quote Modify message Remove message
I have quite a recent laptop (Asus, 1 gb ram, celeron d processor - 2.0 GHz.. bought about feb 06) and downloaded kubuntu gutsy from the kubuntu wesite. downloaded the installation cd. burnt the iso image as a bootable cd and it boots fine. i choose to start and install kubuntu from the initial menu and then the flashing underscore / cursor appears. nothing happens. left for 2 hours and nothing happens... was wondering if there is anything i am missing or if i need something on my laptop to make sure it works... checked the BIOS and everythign seems fine to install kubuntu but it doesnt want to run the installation... (i have windows xp prof sp2)

please help me
	Report to moderator   83.166.160.50
dibl
Kubuntu Veteran
*******
Offline Offline

Posts: 4033


That which does not kill me makes me stronger ...


View Profile Email Personal Message (Offline) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #1 on: January 27, 2008, 10:17:09 am » 	Reply with quote
Welcome!  Perhaps this will help:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

 Smiley
	Report to moderator   Logged
	Intel Core 2 Extreme @3.45GHz on Intel D975XBX2
Nvidia GeForce 8800GTS
Kubuntu 8.04, Mepis 7, Sidux 2007 4.5

64-bit Linux!
Kubuntu User #20703
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #2 on: January 27, 2008, 11:53:12 am » 	Reply with quote Modify message Remove message
I will try this and see if this works, if it does, Thankyou so much... if not, would you have any other ideas cos i am a bit of a noob

sorry
	Report to moderator   82.34.18.227
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #3 on: January 27, 2008, 11:57:14 am » 	Reply with quote Modify message Remove message
Just to add a note, i havent even been able to install... i put disc in, screen shows with the multiple options of what you would like to do.. i press start kubuntu which should take me to live CD but doesnt and i get the problem which i told you about above.
	Report to moderator   82.34.18.227
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #4 on: January 27, 2008, 12:02:22 pm » 	Reply with quote Modify message Remove message
sorry dibl. didnt work.. the keyboard is tottally unresponsive... tried alt f1 and ctrl alt f1 and nothign happened... then used the fn key and numlok to see if i could activate anything on the keyboard and i cant even put on numlock...


open to ANY suggestions as i Really want LINUX
	Report to moderator   82.34.18.227
dibl
Kubuntu Veteran
*******
Offline Offline

Posts: 4033


That which does not kill me makes me stronger ...


View Profile Email Personal Message (Offline) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #5 on: January 27, 2008, 12:26:50 pm » 	Reply with quote
Try the Alternate Install CD, instead of the Live CD.  Burn the ISO image at no more than 4X speed.  The problem is detection of your video card.  It may be that one of the boot options on the Alternate Install CD will let us see what's going on (VGA mode, maybe) and get the basic installation done.  Once you get the system installed, then you can deal with the video driver.

What is your graphics card?
	Report to moderator   Logged
	Intel Core 2 Extreme @3.45GHz on Intel D975XBX2
Nvidia GeForce 8800GTS
Kubuntu 8.04, Mepis 7, Sidux 2007 4.5

64-bit Linux!
Kubuntu User #20703
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #6 on: January 27, 2008, 03:14:36 pm » 	Reply with quote Modify message Remove message
ATI as far as i can see...

Its an asus A6 Series entertaintment notebook

er... i did bring up a screen somehow, cant really remember how i did it but i got a message saying about a panic kernel or something...

i cnt put the image in atm but it says :

"vfs: cannot open root device "<NULL>" or unknown block(104,1)
[  84.732357] Please appened a correct "root= " boot option; here are the available partitions:
[  84.732415] Kernel Panic - not syncing: VFS: unable to mount root fs on wn-block(104,1)

any ideas?

	Report to moderator   82.34.18.227
dibl
Kubuntu Veteran
*******
Offline Offline

Posts: 4033


That which does not kill me makes me stronger ...


View Profile Email Personal Message (Offline) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #7 on: January 27, 2008, 03:26:09 pm » 	Reply with quote
That's bad.  Was this when you were trying to run a live CD, or after you installed it?

If running Live CD, this means we're gonna have to talk about your optical drive:
Quote
"vfs: cannot open root device "<NULL>" or unknown block(104,1)
[  84.732357] Please appened a correct "root= " boot option; here are the available partitions:"
« Last Edit: January 27, 2008, 03:29:35 pm by dibl » 	Report to moderator   Logged
	Intel Core 2 Extreme @3.45GHz on Intel D975XBX2
Nvidia GeForce 8800GTS
Kubuntu 8.04, Mepis 7, Sidux 2007 4.5

64-bit Linux!
Kubuntu User #20703
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #8 on: January 27, 2008, 04:18:34 pm » 	Reply with quote Modify message Remove message
live cd... downloaded from kubuntu.com and its the cd version... probs the live cd.

and by optical drive, you mean my cd drive? cos i have an external burner whcih reads cd's and dvd's so i can try that if it might help?
	Report to moderator   82.34.18.227
dibl
Kubuntu Veteran
*******
Offline Offline

Posts: 4033


That which does not kill me makes me stronger ...


View Profile Email Personal Message (Offline) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #9 on: January 27, 2008, 04:24:55 pm » 	Reply with quote
Well, I have seen threads on this and other fora that indicate there are a few species of optical drives (CD and CD/DVD) that simply "lose" their hardware identity at a point after they boot the CD, but before the installer sets up to install on the hard drive. In other words, it's "hello Mr. Hard Drive, now where did I lose that CD drive?".

But, if you're not even getting to the splash screen, it's possible that a boot option might remedy the situation. Did you try "safe graphics" mode?  Is there a "VGA Mode" or a "VESA Mode" (it's been awhile since I actually had my hands on a Live CD).
	Report to moderator   Logged
	Intel Core 2 Extreme @3.45GHz on Intel D975XBX2
Nvidia GeForce 8800GTS
Kubuntu 8.04, Mepis 7, Sidux 2007 4.5

64-bit Linux!
Kubuntu User #20703
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #10 on: January 27, 2008, 04:30:39 pm » 	Reply with quote Modify message Remove message
Well i tried in safe graphics... nothing, and if i press f6 i can choose which resolution to run at. it says VGA and then alot of resolutions... i can access the cli fromt he first screen, and if i press esc, i can access the text based install (i think thats whats its called) but if press esc, it tells me im leaving the gui install
	Report to moderator   82.34.18.227
dibl
Kubuntu Veteran
*******
Offline Offline

Posts: 4033


That which does not kill me makes me stronger ...


View Profile Email Personal Message (Offline) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #11 on: January 27, 2008, 04:42:37 pm » 	Reply with quote
If you can get to the "character mode" installation routine, as used in the Alternate Install CD, I find it pretty easy to use.  It's not really "text mode", as in a CLI session, it has menus and boxes to "X" and stuff like that.  If you can get the OS to install, then I think we can cope with the video issue and get a driver installed.

If the ONLY thing you can get to is the CLI, then I guess you can log in as "demo" and the password is "demo", and then issue this command to see if you can configure a VESA display:
Code:

sudo dpkg-reconfigure xserver-xorg


On the first screen answer "NO" to the autodetect question, then on the second screen choose "VESA" as the display type. You can accept defaults on everything else until you get to the Monitor -- on that you want to "X" only a single resolution that will be comfortable on your LCD or CRT, like 1280x1024 or 1024x768.  Then on the refresh rates, pick safe ranges for your LCD or CRT.  When it dumps you back to the CLI, enter "startx" and you should get a GUI desktop.   Smiley
	Report to moderator   Logged
	Intel Core 2 Extreme @3.45GHz on Intel D975XBX2
Nvidia GeForce 8800GTS
Kubuntu 8.04, Mepis 7, Sidux 2007 4.5

64-bit Linux!
Kubuntu User #20703
lakeyboyben
Always Learning
*
Online Online

Posts: 14


View Profile Email Personal Message (Online) 	
	
Re: kubuntu wont install... left with a flashing underscore
« Reply #12 on: February 16, 2008, 08:59:36 am » 	Reply with quote Modify message Remove message
sorry, my bad... it wasnt a cli... i get the message "boot:" and then i can type in some boot options...

i tried the boot: live vga771 noapic no lapic... and no joy with that... im jus boggled as to why it wont work. It will install and run on other pc's but not mine... i tried the external CD/DVD drive and that didnt work either... i think it might be my laptop.. it just doesnt seem to want to load anyting other than windows.

If any help can be made, i would appreciate it so much because i love linux to peices. i have used it before and stopped for some reason... dnt know why, but i want it back.

---

### Post by seshomaru samma on 2008-03-09
it's difficult to read - can you just post the links to your kubuntu forum posts?

---

### Post by Yellow Pasque on 2008-03-09
On the screen shot you show, it appears the last lines deal with hpet (high precision event timer). I don't know if that's the actual cause of the problem, but you might try turning this off in the BIOS if it's an option (it is in my BIOS) or booting the kernel with the noacpi option.

---

### Post by Yellow Pasque on 2008-03-09
Scratch that last thing about noacpi. Use hpet=disable.

Do a web search for 'asus a6r hpet' if you want to see some other folks complaining of the same thing.

---

