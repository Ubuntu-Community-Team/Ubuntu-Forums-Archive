---
title: "I am a newbie~ wireless internet problems appriciate the help!"
date: 2008-10-28
forum: General Help
---

### Post by kylehannah on 2008-10-28
I recently downloaded wubi to my windows vista laptop. now i want to connect to the internet using my wireless home network. i have already gone through all the websites that say to click on the netwprk manager icon select your wireless network enter the wep key .... i have already done everything that has been posted on other websites...now i know its not my wireless card on my laptop and i know its not the router...obviously because i am online right now...and also because when i click on the network manager my home network shows up...i enter the wep key and then it shows like a blue firebal looking thing that spins round and round through two blue dots and then it asks for the wep key again...i enter it and nothing happens...well actually i shouldn't say that...what used to happen is i would no longer be able two type or click using the built in keyboard and mouse (i am using an older IBM Thinkpad with the little red button in the middle of the keyboard located near the G,H and B keys)...then after about 2 or three minutes i can type (maybe because it finally timed out) and then everything that i clicked opens...or the other thing that happen as well as everything i've said above what happens is in a window thats opened where there is someplace to type it types **1** and one letter only over and over again....like this uuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu except it keeps going and going ...you get the point...i have just uninstalled wubi and i am trying this again...(i have reinstalled wubi) ...the same thing has happened...i am a newbie and i really want to eventualy get a copy of Linux...but i want to learn it first....so if anyone can help id be very greatful!!!....also i have two other question maybe someone could answer in the response message to the above

question one is : What is a "shell command"

question two is : eventualy i want to create a ubuntu linux disk unistall windows vista a just use ubuntu linux...how do i create that disk? and does that disk work like any other OS disk you would use (i.e when you want to install windows vista u get a dick you pop it into a drive and it goes through the setup) is that how that all works .... the person(s) who respond to me are very brave {lol:) } and i appriciate all you have done for me

thanks a billion!

kylehannah ~ Ubuntu Newbie

---

### Post by Orlsend on 2008-10-28
What Version are you trying?

Its so we can help you.

---

### Post by kylehannah on 2008-10-28
The version of wubi ubuntu linux?...if thats what your asking i am trying version 8.04.1

---

### Post by kylehannah on 2008-10-28
I am Trying version 8.04.1 of wubi ubuntu linux!

---

### Post by kylehannah on 2008-10-28
Please people this means alot to me...i would really appreciate some help with this stuff!

---

### Post by kylehannah on 2008-10-28
I recently downloaded wubi version 8.04.1 to my windows vista laptop. now i want to connect to the internet using my wireless home network. i have already gone through all the websites that say to click on the netwprk manager icon select your wireless network enter the wep key .... i have already done everything that has been posted on other websites...now i know its not my wireless card (my card is a linksys wireless notebook G adapter v.2.0) on my laptop and i know its not the router...obviously because i am online right now...and also because when i click on the network manager my home network shows up...i enter the wep key and then it shows like a blue firebal looking thing that spins round and round through two blue dots and then it asks for the wep key again...i enter it and nothing happens...well actually i shouldn't say that...what used to happen is i would no longer be able two type or click using the built in keyboard and mouse (i am using an older IBM Thinkpad with the little red button in the middle of the keyboard located near the G,H and B keys)...then after about 2 or three minutes i can type (maybe because it finally timed out) and then everything that i clicked opens...or the other thing that happen as well as everything i've said above what happens is in a window thats opened where there is someplace to type it types 1 and one letter only over and over again....like this uuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu except it keeps going and going ...you get the point...i have just uninstalled wubi and i am trying this again...(i have reinstalled wubi) ...the same thing has happened...i am a newbie and i really want to eventualy get a copy of Linux...but i want to learn it first....so if anyone can help id be very greatful!!!....also i have two other question maybe someone could answer in the response message to the above

question one is : What is a "shell command"

question two is : eventualy i want to create a ubuntu linux disk unistall windows vista a just use ubuntu linux...how do i create that disk? and does that disk work like any other OS disk you would use (i.e when you want to install windows vista u get a dick you pop it into a drive and it goes through the setup) is that how that all works .... the person(s) who respond to me are very brave {lol } and i appriciate all you have done for me

thanks a billion!

kylehannah ~ Ubuntu Newbie

---

### Post by rob-h on 2008-10-28
You don't need to start two threads:
[http://ubuntuforums.org/showthread.php?t=961709](http://ubuntuforums.org/showthread.php?t=961709)

---

### Post by kylehannah on 2008-10-28
i'm sorry for posting two threads...i am a newbie and i figured if i said that in my thread title people might want to help me more!

---

### Post by Catalyst2Death on 2008-10-28
> 
question one is : What is a "shell command"


A shell command is a command that you enter in a shell :P seriously, though it is!  If you have a command, you can enter it by accessing your terminal.  You can do this by going to Applications>Accessories>Terminal  Welcome to your shell! you should see a window that has something like this:
```

username@computername:~$
```

Sometimes people prefix commands with $ or # to let you know what kind of user you need to be, $ is normal users and # root user, or super user.  You *don't* want super user privileges for daily use!!  Also, make sure that you don't enter dangerous commands.  Be sure that you know what the commands that your entering are!

Question 2:
You want to partition your hard drive.  It can be done like this (as you transition):

Install Ubuntu on its own Partition
Get Comfortable with Ubuntu (ie you *never* use Vista)
Format Vista Partition
Edit Grub (you'll know about this when your ready)
Use a Live CD to re-grow the Ubuntu Partition to the whole hard drive (BACKUP DATA!!)

For more on partitioning your hard drive:
[http://www.linux.ie/newusers/beginners-linux-guide/partitioning.php](http://www.linux.ie/newusers/beginners-linux-guide/partitioning.php)

Good Luck!

---

### Post by Orlsend on 2008-10-29
Go to **System>Administration>Hardware Drivers** And make sure you Wireless card drivers are enabled.

---

### Post by ago on 2008-10-29
You might want to try 8.10 that generally has better support for wireless

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

Uninstall everything, defrgament your drive, run chkdsk /r in windows, then install 8.10.

A command shell is a command you type in a terminal, you get a terminal in applications > accessories > terminal or by pressing ctrl+alt+f1. Even if graphical tools are available for almost any task under the sun, it is easier to provide commands to paste in a terminal rather than guiding users through a forest of dialogs, so you will see command lines very much in vogue in these forum.

---

### Post by kylehannah on 2008-10-29
Thank you orlsend i appreciate your help but like i say...i have already done everything the internet has told me (including several books i have downloaded) when i go to hardware drivers it says something like there are no drivers in use...i know my wireless card is working because when i click on the network manager icon on the GNOME menue bar it shows all the wireless networks that are in range

---

### Post by ago on 2008-10-29
It might be that the encryption (wpa) of your card is not well supported so that you cannot authenticate, or maybe you are using the wrong encryption type, or you misstyped the passphrase.

---

### Post by atomizer on 2008-10-29
Maybe you could check if it is an 64-bit or 128-bit key or maybe a passphrase.(can choose between them at the window you type your password)
But first try to connect unencrypted (make it an insecure network on your router) to test if it connects at all
I know first time I tried connecting, I used a 64-bit key to connect to a 128-bit encrypted network. This didn't work. It was a stupid mistake I made, but can be easely overlooked.


And I recommend using a WPA encryption.

---

### Post by kylehannah on 2008-10-29
I'm only 15....but i do know this...my network is encrypted by WEP key...and it's a 128 bit 26 digit encryption key....but its all numbers no letters no spaces periods dashes etc...its looks like this  example 123456789 ect now is tha ASCII i am pretty sure the one i should select in the window is 64/128 bit passphrase or whatever it says...is there a difference between 8.04.1 and 8.10...a difference in this window i am talking about...like what is the difference between the one i was using and the one you recomended?

---

### Post by atomizer on 2008-10-29
the 8.10 ubuntu has a new network manager, haven't used it yet (tomorrow everyone can upgrade from ubuntu 8.04 to 8.10, so will I)
As far as I know (has been while ago since I used WEP) ,you can choose between 64 and 128 bit.
And a 64 or 128 bit key is usually with the numbers 0~9 AND the letters A~F.
Maybe it IS a passphrase?
You are 15, so your parent won't let you put the security off to test without encryption?

---

### Post by kylehannah on 2008-10-29
NO THEY WANT SECURITY...WHERE I LIVE EVERYONE USES WIRELESS....WHAT DO YOU MEAN EVERYONE CAN UPGRADE TO 8.10....I AM DOWNLOADING THAT RIGHT NOW AS WEEK SPEAK!!! But i live i Canada so maybe thats the difference!!!....am i not installing the right one???....because right now as i am typing this 2 you i am downloading wubi 8.10

---

### Post by atomizer on 2008-10-29
U can download 8.10, yes thats right, but tomorrow it will be official and the users of 8.04 can upgrade "safely"
As I say, it has a new networkmanager, witch I have no experience with.
maybe it can select the network automaticly, they say it is improved.
In the old version 8.04 and before you can choose between ASCII passphrase/64-bit/128-bit.

---

### Post by kylehannah on 2008-10-29
okay so i downloaded wubi v 8.10 and it boots up to create like the share files and whatever else it does and it locks my computer and the numlock and caps lock lights on my laptop...(there the green lights that come on when caps or num locks are on) and they flash...and nothing happens...i downloaded Wubi-8.10-rev515.exe from the link you gave me...which one should i download?

        Wubi-8.10-rev507.exe	
	Wubi-8.10-rev509.exe	
	Wubi-8.10-rev510.exe	
	Wubi-8.10-rev511.exe	
	Wubi-8.10-rev512.exe	
	Wubi-8.10-rev513.exe	
	Wubi-8.10-rev514.exe

I don't know if it matters but maybe ull know...

---

### Post by brandon88tube on 2008-10-29
A quick question that I don't know was stated or not. What wireless card are you using? There are issues with some wireless cards in linux *cough of course mine, well I haven't tried 8.10 yet, but still.

---

### Post by kylehannah on 2008-10-30
I am using a linksys Wireless-G Notebook Adapter 2.4 GHz 802.11g WPC54G Ver.2

---

### Post by brandon88tube on 2008-10-30
You might need to install the ndiswrapper to get it working properly. I had to do that with my Broadcom one. Here is a link to see about your card. Scroll down to the WPC54G section. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

Edit: Couldn't get the link to work, Think its fixed now

---

### Post by atomizer on 2008-11-04
Linksys wireless G works very well, just click on system>hardwaredrivers and enable and follow the instructions. (so click yes i mean)
Have the same card, no problems (dont forget to reboot)

---

