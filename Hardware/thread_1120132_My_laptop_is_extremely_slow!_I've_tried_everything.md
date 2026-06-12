---
title: "My laptop is extremely slow! I've tried everything I can think of!"
date: 2009-04-08
forum: Hardware
---

### Post by tonyW303 on 2009-04-08
I have a Compaq Presario 2100 laptop with 1024 MB for RAM, an AMD Athlon Mobile processor, a Belkin wireless internet card, and Ubuntu 8.10 (obviously). I had Windows XP on this laptop just a few months ago; I switched because Windows was so slow. So I thought that Linux would be much faster and better. Normally, that's true... For me, Linux is as slow as Windows was. I have given it the maximum RAM available (according to Best Buy's database), removed a ton of stuff off the hard drive, I run virus scans daily, and I leave it plugged in all the time (it runs even more slow when running from battery). ](*,) Help please?!? Thank you! 

P.S. For those of you who are going to tell me to get a new laptop, I don't have money for one and this economy isn't helping. Thanks again!

---

### Post by simtaalo on 2009-04-08
you run virus scans on your linux machine?

---

### Post by riza hylviu on 2009-04-08
Try using xubuntu that is lighter, ubuntu is not heavy as windows but is not exactly a light os.If it does not work maybe Vector linux is the right choice. There are Damn Small Linux and Puppy linux too, but too light.

---

### Post by abn91c on 2009-04-08
are you running it without compiz, and the correct video card drivers

---

### Post by tonyW303 on 2009-04-08
> you run virus scans on your linux machine? 
Ya. I use ClamAV GUI. Got it from Applications > Add/Remove Applications.

> are you running it without compiz, and the correct video card drivers 
I have Compiz-Emerald Fusion. And I'm pretty sure I have the correct drivers.. When I go to Hardware Drivers in System, it brings up one driver for my wifi card which I already have installed.

---

### Post by chessnerd on 2009-04-09
You could try installing the xfce desktop environment. It's lighter than gnome and could help your computer run faster (I'm running it on an 8 year old Dell with 1.7Ghz P4 and 256MB of RAM and it runs pretty well). Download the xubuntu-desktop package under Synaptics and, once that's done, log out and choose the option for the xfce desktop before you log back in.

Another option is that you could try some lighter applications. For instance:
Using Abiword instead of OpenOffice Writer
Using Gnumeric spreadsheets instead of OpenOffice Calc
Using the Galeon webrowser instead of Firefox
And using the Thunar file manager instead of Nautilus

Most of these aren't as good as their more resource intensive counterparts, but they open and run faster.

Hope this helps.

---

### Post by snowpine on 2009-04-09
Windows XP is much older than Ubuntu and was developed at a time when the average desktop computer had lower specs than today. Ubuntu has higher system requirements than XP and will not necessarily be any faster. 

That being said, there are lots of ways to speed up Ubuntu. The obvious is to turn off anything that uses system resources but you don't need. There are two ways to do this: 1) Start with a full install of Ubuntu, then manually tweak the system: turn off unneeded services, install a lightweight desktop environment like LXDE, try faster applications like Abiword and Opera, etc. or 2) Try a different Ubuntu-based distro like Xubuntu or Crunchbang that does this work for you.

If you really want a fast system with old hardware, check out DSL, Puppy, SliTaz, etc. These mini-distros are not necessarily as full featured as Ubuntu, but are great for basic computer tasks like surfing the web.

---

### Post by jojo1224 on 2009-04-09
> **tonyW303 said:**
> Ya. I use ClamAV GUI. Got it from Applications > Add/Remove Applications.


I have Compiz-Emerald Fusion. And I'm pretty sure I have the correct drivers.. When I go to Hardware Drivers in System, it brings up one driver for my wifi card which I already have installed.

With linux you don't need anti virus because there are no virus's targeted at linux. Even really nasty windows virus's wont do anything to linux. The only reason anyone would run anti virus on linux is for scanning there emails so they don't send a windows user a virus when they forward an email.

---

### Post by askreet on 2009-04-09
Disabled Compiz-Emerald Fusion.

Your system isn't terribly fast, so you have to disable some of the advanced features.  1GB of RAM is pretty much the minimum for a usable 8.10 machine.

Stop using ClamAV, it's wasting resources.  How much other stuff do you have running?

---

### Post by tonyW303 on 2009-04-09
> 
Disable Compiz-Emerald Fusion.

Stop using ClamAV, it's wasting resources. How much other stuff do you have running?  
ClamAV is now uninstalled. Compiz-Emerald Fusion is disabled, too. I have Pidgin running pretty much all the time with AIM, Yahoo, Hotmail, and Facebook accounts. I'm not sure if this counts as "other stuff" but when I run anything that uses Flash on Firefox, my computer slows down EVEN MORE than the slug that it already is...

> Download the xubuntu-desktop package under Synaptics and, once that's done, log out and choose the option for the xfce desktop before you log back in.
Will I be able to run all the same programs that I was running on GNOME?

---

### Post by Skara Brae on 2009-04-09
I do "better" than chessnerd, with an ancient Compaq Armada with a PIII 500 mhz, 256 MB RAM and a tiny Ati Rage Mobility with 8 MB RAM (or is it 4 MB?) :p

Tonyw303, Xubuntu (with XFCE) looks just like Ubuntu (Gnome), so you would hardly see (much) difference. Xubuntu runs fine with me (albeit a tiny bit slower than I would like, but then again, this here is an old machine), so it will run even better on your Compaq.

Are you sure the slow speed is not some hardware issue?

---

### Post by kerry_s on 2009-04-09
i'd make sure the cpu is running at full speed> cat /proc/cpuinfo

check your bios make sure the settings is performance and the cpu set to full. i've in the past were the boot up speed gets set as the top speed, because the cpu throttled.

---

### Post by 00b00nt00 on 2009-04-09
Tony, help us a little by defining 'slow'. Are we talking about screen re-draws or system hangs? (Or both, even). You have plenty of RAM, 512MB is enough to run a vanilla install of Ubuntu happily how about processor speed?

Another thought tells me that as XP was also slow on your computer, there may be a hardware fault - specifically your hard disk may be causing problems. go into the terminal and type: sudo hdparm /dev/sda1 -t -T

Report back with the figures.

---

### Post by chessnerd on 2009-04-09
> **tonyW303 said:**
> Will I be able to run all the same programs that I was running on GNOME?

GNOME programs should work fine under Xfce. I use OpenOffice, Firefox, and plenty of other programs that were designed for Gnome just fine under Xubuntu. The only difference will be the desktop environment (ie the window borders might be different, the panels and icons will work a bit differently, and some of your buttons might have different images), but overall you shouldn't notice a huge change.

Xfce and Gnome have a lot in common and the good news is that, if you don't like it, you can always change the settings to go back into Gnome and then uninstall the package through Synaptics as though you never changed a thing. :)

---

### Post by billfreeboy on 2009-04-10
:mad: My Dell Latitude CPx is slow too! And I'm not used to taking Laptops apart.

---

### Post by tonyW303 on 2009-04-28
> **00b00nt00 said:**
> go into the terminal and type: sudo hdparm /dev/sda1 -t -T

Report back with the figures.
I noticed that there are also /sda2 and /sda5 in /dev. I don't know if it will help you or not but I posted hdparm results for those two as well.

sda1 results:
[INDENT]/dev/sda1:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 7296/255/63, sectors = 115202052, start = 63
[/INDENT]

sda2 results:
[INDENT]/dev/sda2:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 7296/255/63, sectors = 2, start = 115202115
[/INDENT]

sda5 results:
[INDENT]/dev/sda5:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 7296/255/63, sectors = 2008062, start = 115202178
[/INDENT]

Thanks 00b00nt00. Hope this helps

---

### Post by jmate24 on 2009-04-28
You don't need to install a different OS just to make it go faster...

Just go to services System>Administration>Services>Unlock>Type Password and uncheck the things that you don't use, for instance I have a Lenovo Y510 and it has no Bluetooth adapter so I uncheck the 'Bluetooth device management', and I don't use the 'Remote backup service' so i uncheck that,
I personally don't use 'Samba' so I uncheck 'Folder Sharing Service'.

Then i go to System>Preferences>Startup Applications and since I don't have a Nvidia Graphics Card i uncheck 'Check for new hardware drivers' and I make sure that I uncheck 'Bluetooth Manager' then I uncheck Gnome Splash Screen', 'Remote Desktop', 'Tracker' and 'Tracker Applet', and finally 'Visual Assistance'

Make sure to restart!!

Now it can boot up faster and things run smoother and I can do almost anything. If you have a Nvidia card, I recommend Disabling the Visual Effects because your Video card uses 'Share Memory' from your RAM that is why it shows Less RAM that what is actualy installed.

jmate24--

---

### Post by emacbri on 2009-05-11
Hi,

   I am also running a Compaq Presario 2100, except mine has a Intel Celeron and only 512 mb of RAM. I Just re-installed Ubuntu on my computer and I noticed it is considerably faster. You should try reinstalling Ubuntu could help, just don't forget to backup your stuff first.:)

---

### Post by Language on 2009-05-11
> **kerry_s said:**
> i'd make sure the cpu is running at full speed> cat /proc/cpuinfo

check your bios make sure the settings is performance and the cpu set to full. i've in the past were the boot up speed gets set as the top speed, because the cpu throttled.

Definitely follow kerry_s' advice and check the proc speed; My 1.5ghz laptop was running pretty sluggishly until I noticed that it was only running at 600Mhz. For some reason auto-scaling wasn't working correctly, and it sat at 600Mhz no matter how high the load got. Cranking it manually made it perform much better, and thankfully with 9.04 it scales automatically on its own now :)

---

### Post by abn91c on 2009-05-11
you problem maybe all those chat programs you have running, they are usually resource hogs, same if you are downloading torrents in the background, plus all the flash crap people load in their myspace & facebook pages also eat your RAM.

---

### Post by roger_1960 on 2009-05-11
Hi

I run a similar spec machine (25% less RAM, same processor) with 8.04LTS.  It used to run XP.  I reckon it goes a bit quicker than XP.  If I run puppylinux, I goes MUCH quicker, but the stuff I do doesn't really need much speed and I like the Gnome desktop (perhaps because I remember having to turn pages in newspapers and books, I'm not so impatient!)  Seriously, try puppy - it runs from a live CD (in RAM) and doesn't change anything to try it.

---

