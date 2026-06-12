---
title: "acer travelmate 2480-2779 celeron laptop"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by oldone on 2007-02-10
OK - this old man just loaded ubuntu dapper on this acer travelmate2480-2779 celeron laptop.

New to linux and ubuntu sincelast night officially. I know zero terminal command line.

any help would be greatly appreciated.  I know notta so be clear and step by step and paint by numbers.  I cannot get the wireless going at all. I am on airport extreme.  I cannot figure the stupid slide switch they have on it either - doesn't seem to work.

Need wireless badly! BADLY!!!!!!

the printer I can work on next.

I also have my trackpad clicking on stuff on pass by and sometimes a bit haywired.I also need the trackpad too.

Thank you

---

### Post by banditti on 2007-02-10
what is the wireless card in the laptop?  Intel?  What model?

---

### Post by banditti on 2007-02-10
if you don't know, from a command line type:

```
lspci
```


copy and paste the results.

---

### Post by oldone on 2007-02-10
linux@linux-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)
0000:0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b
linux@linux-laptop:~$

---

### Post by oldone on 2007-02-10
i am running dapper drake so you know the long term support version.

---

### Post by oldone on 2007-02-10
I also had an issue with the screen resolution too it seems...

the largest setting and defaulis 1024 x768

my screen is 1280 x 800

how can i fix this please?

thank you.

---

### Post by banditti on 2007-02-10
This should help with the wireless.

[http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+Corporation+BCM4318)

---

### Post by banditti on 2007-02-10
As for the Video:

From CLI (terminal) type:

```
sudo apt-get install 915resolution
```

You can also do it from the GUI

System => Administration => Synaptic Package Manager

Find the package by the same name.

---

### Post by oldone on 2007-02-10
OK - Cool! I'll try this!  I really am stuck so you know.  Much appreciated.  and also very Lost!!!!!!


:-))))

---

### Post by oldone on 2007-02-10
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 915resolution
linux@linux-laptop

this didn't work???? any more clues???



looked uner the gui scene too and canot find it amongst everything in theere...Hmmmm.



---------


got to this place:su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit


but always get an authentication failure!  stuck here now big time

---

### Post by oldone on 2007-02-10
I am lost!!!

I tried to follow the links on the wirless post and that took me to another post with a driver link that had no driver link and that was all mumbo jumbo.

It took me 8 years to try to have the guts to attempt linux and the last year in Ubuntu - and 1 day later I am furstrated. Bought books and everything.  I am just lost.

thanks!

---

### Post by banditti on 2007-02-11
sorry, you need to:


```
sudo gedit /etc/apt/sources.list
```

In there, there are a couple of lines that talk to "universe"  Remove the # in front of those universe lines that start with deb.

Then from a terminal window:

```
sudo apt-get update 
sudo apt-get install 915resolution
```

---

### Post by banditti on 2007-02-11
Also, don't sweat it.  There is a mindset change between linux and windows.  You will get it.

---

### Post by oldone on 2007-02-11
Banditti - thank you - I am coming from Os X. I ran the resolution and it seemed to work re: terminal but the resolution doesn't show up in changes. I still cannot CHOOSE that one.

I have to work for part of the day and then I will be back to see whatever posts - the wireless advice I am lost in very badly. esp. the link to get the drivers etc. I do not understand.

thanks for your help and patience.  I am an old fart that anted to try linux for 8 years now...

have unleashed and hackls books - just arrived the other day.

best wishes.

---

### Post by oldone on 2007-02-11
i tried restarting and nothing - I ran this again as you stated and did not have to remove the # signs this time and nothing


I also notuiced I have sounmd but they buttons do not control anything the sound is just ON.

thanks

---

### Post by oldone on 2007-02-11
I also get this when I tried to run wireless assistant...what do I do?

'cannot run wirless assistent due to permission problem or some such thing. did you try sudo?'

the copy paste at times or in terminal or whatever does not always workj so I paraphrased it.

---

### Post by banditti on 2007-02-11
sudo is the command to let you run something as super user.  If you are running it from a terminal, just start the command you want to run with sudo in front of it.  For example:

```
sudo apt-get update
sudo apt-get upgrade
```

if you are running it from the GUI, you can right click on the icon, choose properties and add gksudo in-front of the command.  That will prompt you for a password when you run it.  

Make sense?

Also, I am confused about your post about rebooting.  I am not sure what you are trying to say.  Can you expand?

As for the wireless, can you start with this part and let me know where you have problems and what error message you get back or what you don't understand.

[http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)

---

### Post by banditti on 2007-02-11
on the video:

```
sudo gedit /etc/default/915resolution
```

Then add the following:

```
MODE=5a
 XRESO=1280
 YRESO=800
```

After you save and close, switch to virtual console 1 (alt-ctrl-F1), then

```
sudo /etc/init.d/gdm restart
```

---

### Post by banditti on 2007-02-11
I also think your wireless should work out of the box.  I will research a bit.


In the mean time have you installed network manager?

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by oldone on 2007-02-11
banditto - Ok tried the resouliton stuff crashed linux and the vrowser and froze in Virtual mode. and had to press start button to stop tried again and loaded everything etc. but still no choice for such a resolution.  I am still stuck - the wireless thing I have to work on later today too - I just got in.

no network manager - i did some wireless assistant though.



just installed the network manager... I guess.

---

### Post by oldone on 2007-02-11
tried to set stuff up in wirless and the wireless is active in text but in reality nothing.

---

### Post by oldone on 2007-02-11
re the wirless starting point I did the first 2 sudo command listed ion the thread but do not have no where and which one to get for the acer_acpi module???? I have no clue about where to get this????

I am stuck here ..thank you Banditto...

also the resolution is still where it was initially. no choice is available under screen resolution...

---

### Post by Vorian on 2007-02-11
> **oldone said:**
> banditto - Ok tried the resouliton stuff crashed linux and the vrowser and froze in Virtual mode. and had to press start button to stop tried again and loaded everything etc. but still no choice for such a resolution.  I am still stuck - the wireless thing I have to work on later today too - I just got in.

do this 
```
**sudo dpkg-reconfigure xserver-xorg**
```this will walk you through all your xorg settings
then 
```
**sudo /etc/init.d/gdm restart**
```

Lets see if we can fix this first.

---

### Post by oldone on 2007-02-11
ok give me a chance to do it. I am here.

i do not know what is the desried Xserver driver.... how do I pick the correct one?

i have no clue what the video cards bus identifier is that they are asking me to type in? no what?

help please---- I am stuck in4 different places and had to exit out of a bunch of stuff----ready to say screw it.  either freash install or install visat that came with this new computer and give it away since I refuse to use microsoft in my home.... this experiment with linux cost me mucho bucks...

thank you.

ok - I apprecate all of thehelp but nothing works and I mean it. and I am not a dumbo mother just new to linux.  all of the stuff ends up not working or I cannot complete the steps and all just gets hung or I have to exit or else I have to stop and restart computer so all of thes eloose ends are really sucky!

I reinstalled the OS and now checked back in and still no help.

it is tough to have patience when you are stuck in terminal or virtual terminal or else in the midst of complex steps where something hangs or doesn't work ----that is why linux is not ready for humans and the everday Joe and Granny smith etc. I have a Ph.D. andalso do use computers and some very high end applications; but this is a real nightmare....After 8 years of wanting to do this and finally taking the plung the last 2 days have been OH S$&^ I just threw away hard earned $ for a windows based computer when I could have boughten anther mac that works out of the box and wirless runs and printer and screen resolution etc.

anyone want to by a 2 day old travelmate laptop Ubuntu installed - ytou have to fix the rest???

I am really stuck here!

and the hacks book is beyond me and the threads the stuff doesn't work or are a bit beyond me and the unleashed is over the top and the official book is a joke - the install was nothing like it says in the book.

Frustrated.  I could have had another mac!

any people serious to please help me work through theseissues. I tries the video sudo commands listed above and again it cannot finish running and does not do anything or else cannot finish due to errors. the wireless stuff since I kept getting hung too after many things I did not do due to clean install but the stuff I tried did not complete and work on resolution...

---

### Post by Vorian on 2007-02-11
oldone,

Sometimes it takes time to get some responses.  Please be patient.

Here is a step by step guide with screenshots on "sudo dpkg-reconfigure xserver-xorg"  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

You will need to know what hardware you have.  Look through the page first so you have an understanding of what kind of information you will be required to know.

You can do it:)

---

### Post by oldone on 2007-02-11
OK thank you - I will try again.  still no wireless and that is most important.  all of a sudden the hard wire internet connection icon shows up on top. never did before and when I try everything possible to connect to my airport - notta.

---

### Post by banditti on 2007-02-12
do this from a terminal window.

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by oldone on 2007-02-12
I did a fresh install last night I tried again and i get errors all over the place re: the stuff in the other links you mentioned for the wireless....I have more errors than yesterday.  I am freakin screwed. it is iperative that the wireless work the resoltuion I can live with but wireless is crucial.

I just ran the latest stuff you gave me banditto now what.


thank you.

there is no sign of any wireless in the networks area.  I am reinstaklling for the 3rd time in 3 days ---this is starting to suck!!!

I have tried everything and the few nibbles that I received did not work at all. I could not even complete the tasks that are required due to cannot be found and errors , etc.

is there someone that can stick with me that knows their stuff to work out these problems. This could have been a good thread for this laptop machine to work out 4-5 bugs and hassles for other people.


I feel like an animal in the zoo with someone tossing out little nuggets of crackers at me.

and I am salivating to get this linux happening; but so far it is leaving a tremendously bad taste in my mouth. afetr an 8 years wait and laying out bucks for a laptop to try this with I maight have as well given the money away or flushed it down the toliet....

this is not the user-griendly distro that it is cracked up to be...

---

### Post by Vorian on 2007-02-12
Oldeone,

There is a thread that explains how to get your wireless card working here
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318)

I once again, merged multiple posts you have made.  Please visit the link I posted to resolve your Broadcom 4318 Wireless Cards issues.

---

### Post by banditti on 2007-02-12
> is there someone that can stick with me that knows their stuff to work out these problems

Ubuntu or Linux does not equal people sitting online, at your beckon call with you until you are 100% happy.  This is a forum in which people try and help people.  The answers that have been presented here are MOST likely the fixes to your problems.  Why you don't think there will be a learning curve and blame me for your lack of knowledge is beyond me.  I have stuck with you for 3 pages / 29 responses.  

> This could have been a good thread for this laptop machine to work out 4-5 bugs and hassles for other people.

All of thee suggestions have resulted in fixes for multiple people with the same issues you are experiencing.  Additionally, if you would have searched to forum, you would have seen that.

Again, I am not sure what your expectations are, but the should be reset.

As for me, per your request, I am done > tossing out little nuggets of crackers

Linux isn't for everyone.  Maybe you should return your books and go back to your mac.  If you do decide to stick with it, reset your expectations and maybe try working on one issue at a time.

---

### Post by Mask on 2007-02-23
Hi all,

I installed Ubuntu on my TravelMate 2480 and i have the same problems but let's start with video issue.
After install 915resolution, i restarted my notebook and the login screen appear. I wrote username and password but after a quick refresh, Ubuntu ask again for username and password. I tried different sessions but with the same result. 
What can I do now?

10x

---

### Post by Mask on 2007-02-26
Problem solved.
Now I need audio driver....

---

### Post by Espionage724 on 2007-04-28
I got the same exact laptop. The only problems I had with it was the wireless internet and the sound. These can be easily fixed (if you didnt already fix them). For your sound just go under mixer settings and turn all sounds on and max volume. For internet just find a guide on the fourms somewhere

---

### Post by Espionage724 on 2007-04-28
Also for video issues I just installed the 915resolution driver from APT. It worked for me for a while but for some reason it won't let my screen go back into 1280x800 resolution anymore.

---

### Post by aikidoc on 2007-07-01
Hello!

Does anyone know how to make the external VGA work on the acer travelmate 2480 laptop? thanks!

---

