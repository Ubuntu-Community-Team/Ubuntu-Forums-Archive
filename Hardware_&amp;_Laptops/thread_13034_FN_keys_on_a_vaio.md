---
title: "FN keys on a vaio"
date: 2005-01-28
forum: Hardware &amp; Laptops
---

### Post by dave9191 on 2005-01-28
Hey, Im pretty new to linux and i am determined to get linux working on my laptop. I have a PCV-505DP. Ubuntu is the best distro that i have tried so far and supports lots of nice stuff out the box for me. My wireless card, cpu freq scaling and many more things i like. I even got to like Gnome a lot, I used to use KDE under other distros. I have a few more things that i need to get working, and among them are my Fn key combinations. I have been browsing the web for a solution for the last couple of hours but i have not found anything that works. 

I have the sonypi module insalled and running, changes my screen brightness nicely ;) But so far nothing with the Fn keys. I would like to be able to change my screen brightness by hitting Fn + F6/F7 , change volume and maybe set up some other shortcuts using them. I have tried to listen for the keys using xev, but it doesnt do anything when i hit the Fn key. I am aware that there may be a solution for KDE, but im used to Gnome now :) I need a step by step idiots guide :) 

Help ...

---

### Post by Yoda_Oz on 2005-01-30
have you tried the keyboard shortcuts control panel in gnome?

---

### Post by dave9191 on 2005-01-31
Yes, that was one of the first things that i tried :)

---

### Post by knappen on 2005-01-31
Have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=6204](http://ubuntuforums.org/showthread.php?t=6204)

I have the same problem but I am just happy that I can change the brightness of my screen :-)

Please post your findings!

---

### Post by dave9191 on 2005-02-03
I read that thread as one of my starting points. I still have no luck with the Fn keys tho. I have tried hotkeys util and having several programs try to recognise them. All to no avil.

The hardware ones work like Fn+Right arrow for End, but not Fn+F3 for muting. If I could setup n+ key combos i would be one happy bunny :)

---

### Post by knappen on 2005-02-03
Sorry but I have not been able to get mine working either.

Perhaps it will work better with the new release.

---

### Post by valadil on 2005-02-04
Try using the fn keys outside of X.  My laptop bitches and moans about all those keypresses that it doens't recognize.  If those do work you should be able to use xev to set up xmodmap and then (and only then) you can use gnome's keybinding tool dealie thing.

---

### Post by dave9191 on 2005-02-07
Hey, how would i go about checking if the key combinations work outside x? I though xev was only for monitoring x events. Thx

---

### Post by dave9191 on 2005-04-27
Ok, I decided to take another look at the Fn key combos on my Vaio. Now that I know more about Linux then I did before reading sites makes more sense. 

For those interested... Sony Vaios have a Sony Programable Interface inside them that deals with things like screen brightness, jog wheel (if you have one), battery, memory stick and the FN key combos. So first thing first, you need to have the Sonypi module loaded into the kernel. With the 2.6 kernel and ubuntu its already there, you just have to load it up. 
[B]
sudo modprobe sonypi[/B]

Then we need an application that will monitor the module for signals that it produces and an application that will let us control aspects of the module. Sonypid is a basic deamon that will output to a console what signal has been recieved. So if you download and compile and run the deamon, you will see the key combos displayed on the screen, great for righting scripts. But Im guess for the most of us, not that useful. 

Then there is spicctrl for controling the screen brightness and getting battery levels. Again command line app, great for scripts, but also needed for other programs to control your screen brightness. 

And most importantly, I came accross 'rsjog' in the repositories. Lovely program written in ruby, you need to read the INSTALL file to set it up proerly tho. Has a config file where you can spesify what command you want executed when a signal is picked up (eg. what to do when you hit FN + F4). 

And there is a way to have the FN key combos being picked up by X as keyboard keys  for assigning to short cuts in the short cut manager. But that envolves recomipiling your kernel and patching it. I dont want to do that and I prefer to have a config file with commands, so if you want to try this, you are on your own. 

So load the sonypi module, get spicctrl and rsjog, configure them and you can have you FN keys working on a viao :D Im having some minor teething problems tho. If I load the module myself it works, but if i put it into the modules file to load up on start up, it decides not to work for some unexpained reason. Maybe its the KDE deamon taking control of it (im running kubuntu 5.04).

Hopes this helps people out :) 

Dave

---

### Post by fpm on 2005-05-04
You can easly control Brightness with Fn Keys on Sony Vaio (I use VNG-S1XP).
Go [link](http://etc.nkadesign.com/pmwiki.php?pagename=Linux.SonyVaio) and write the sonystuff script follow instructions and move it to the rcS.d directory.
Everything runs like miracle... Well the Brightness FN5 FN6 (and the CD eject button for some vaio models).
I am trying now to use s1, s2 and s3 Buttons... please give me luck
Good luck!

Useful links on subject:
[http://popies.net/sonypi/](http://popies.net/sonypi/)
[http://sol4.net/linux/pb-sonypi.shtml](http://sol4.net/linux/pb-sonypi.shtml)
[http://www.linux-on-vaio.8m.com/jslupski-vaio/sonykeyd.html](http://www.linux-on-vaio.8m.com/jslupski-vaio/sonykeyd.html)
[http://sonyfx.sourceforge.net/sonyfxd.html](http://sonyfx.sourceforge.net/sonyfxd.html)
[http://people.freenet.de/obauer/](http://people.freenet.de/obauer/)
[http://www.stray.ch/site/laboratory/wheel.html](http://www.stray.ch/site/laboratory/wheel.html)

---

### Post by dave9191 on 2005-05-05
Those look like some nice reasources. I dont think that i found them all in my searches. Ill be putting a guide together in a couple of weeks about this stuff, so that will come in real handy. I might also use the perl script as a bases for my own code :)

---

### Post by G_u_s on 2005-05-30
i'm upping this thread hoping that people have new resources available...

i have a vaio (PCG-K215B), and have spent a good 12 hours straight trying to figure out stuff. but being a newbie to Linux and Ubuntu, i just couldn't make it... so if anyone feels like creating a guide for dummies, i would really, really appreciate it (and i'm sure all the other VAIO users would too ;) )

thanks in advance =)

---

### Post by dave9191 on 2005-05-30
[QUOTE=G_u_s]i'm upping this thread hoping that people have new resources available...

i have a vaio (PCG-K215B), and have spent a good 12 hours straight trying to figure out stuff. but being a newbie to Linux and Ubuntu, i just couldn't make it... so if anyone feels like creating a guide for dummies, i would really, really appreciate it (and i'm sure all the other VAIO users would too ;) )

thanks in advance =)[/QUOTE]


Hey, did you manage to load sonypi without problems (sudo modprobe sonypi). If it doesnt say anything and just give you a command line then it loaded fine. 

Next have you intsalled sppictrl and rsjog? to install them you can use 

apt-get install spicctrl

They might not be in the default repositories, so you might have to add extra one. You can find how to do that on the ubuntu guide [http://ubuntuguide.org/](http://ubuntuguide.org/) You can get rsjog using apt-get or download it here [http://linuxbrit.co.uk/rsjog/](http://linuxbrit.co.uk/rsjog/)

You will have to copy the example config files to your home directory (And copy the sample .rsjogrc and .rsjog.menu to your home directory and
tweak.)

Once they are installed run rsjog after modprobing sonypi and your FN keys should do whatever is set in the config file for rsjog. 

Tell me which part you need more help with and Ill write it out with more detail. 

Dave

---

### Post by G_u_s on 2005-05-31
hello dave, and thanks for helping me =)

i can follow you until you reach:
"You will have to copy the example config files to your home directory (And copy the sample .rsjogrc and .rsjog.menu to your home directory and tweak.)"
well, i don't know what those config files you are talking about are =/
in the directory where the spicctrl and rsjog executables are, there is nothing else related to them. in the other directory returned by "locate spicctrl", there is nothing related to spicctrl but an archive. in one of the directory returned by "locate rsjog" (/usr/share/rsjog) there is a brightness.xpm and volume.xpm. are those the config files you're referring to ? but then, i don't know how to tweak them. and i have no clue where .rsjogrc and .rsjog.menu are either =/

sorry for being such a nuisance, i switched to ubuntu 2 days ago and am a bit lost =)

EDIT: ok, i suck more than i thought =) so "locate" actually starts from the dir you launch it... right ^^ i found the rsjog sample files... will work on it and let you know if i still need help...
god i am so stupid =)

EDIT2: ok, i have edited them (more copied, since for now the config was enough for me), however, after having copied .rsjogrc and .rsjog.menu to my home directory, and having "sudo modprobe sonypi", the keys still don't work...
just to make sure: i have only found the sample.rsjogrc and sample.rsjog.menu files, no other config files, nothing about spicctrl for example.

---

### Post by dave9191 on 2005-06-01
Dont worry, you arent a nusience. It took me a while to figure this stuff out myself. 

locate doesnt start from the dir you launch it from, but checks the whole system as far as I know. There is a database that keeps all files and locations that it checks. After installing something you need to update that database. sudo updatedb will do this for you. Then locate will be able to see the newly installed stuff. 

Spicctrl is application for checking battery status and chaning the screen brightness. I think that rsjog needs it installed. to check that its installed, then just try to run the program sppicctrl in the command line. 

Once you have added the sonpypi module into the kernel (sudo modprobe sonypi) then run the rsjog application with the rsjog command. The rsjog menu file is only useful if you have a jog wheel on the laptop. If you dont, you only want the .rsjogrc. Note that you want to rename the files to get rid of the sample in the file name. So it looks like

.rsjogrc

Then the Fn keys should do whatever is spesified in the rsjogrc file. I think that Fn+F4 and Fn+F5 are setup be default. 

Dave

---

### Post by G_u_s on 2005-06-01
hello dave =)
well, for locate, you're probably, i must have messed up something else for it not to work in the first place ^^
anyway, i've done exactly what you say and it still does nothing =/
i launch rsjog, but nothing happens when i press the Fn keys. do i need to, i dunno, change the rights on the .rsjogrc file or something ?

---

### Post by dave9191 on 2005-06-01
My .rsjog file is owned by root, so it shouldnt make any difference as long as you can read it. 

Ok, try to install sonypid. And run that instead of rsjog. When that runs it should simply just output whatever keypress you made into the console. This way we can see if the sonypi module has loaded and is working fine. Im not sure that its in the repositories, but you can get it from 


[http://popies.net/sonypi/index.html](http://popies.net/sonypi/index.html)

Dave

---

### Post by G_u_s on 2005-06-04
hey dave

i'm sorry i couldn't come back on you about this sooner, but i'm overbooked this week =P

i will try to install sonypid when i get back home, and see how it goes.

btw, i've just noticed now that we're in the Warty forum. i am using Hoary myself. i don't think it should change anything, but then again, i'm ignorant =D

---

### Post by dave9191 on 2005-06-04
Im runnign hoary too, i started this tread when i was running warty. Hence its here :) And dont worry about it, Im doing some redocorating and I dont acccess the net that often now. 

Dave

---

### Post by G_u_s on 2005-06-08
[QUOTE=dave9191]Im runnign hoary too, i started this tread when i was running warty. Hence its here :) And dont worry about it, Im doing some redocorating and I dont acccess the net that often now. 

Dave[/QUOTE]
 hey dave =)

sorry, i have installed sonypid, i modprobe'd sonypi, and then launched sonypid, but when i hit Fn and a Fx key it does nothing. when i hit the Fx keys without holding Fn, it works, and displays some weird code that, i guess, represent the F1 to F12 code, but that's all.

any idea ?

---

### Post by psychosematic on 2005-06-10
Hey Dave,

I am just getting started with kubuntu and linux in general. I was trying to follow along with your instructions & I have stopped on the first step on starting sonypid.

Error info in the terminal window
```
FATAL: Error inserting sonypi (/lib/modules/2.6.10-5-386/kernel/drivers/char/sonypi.ko): No such device
``` 

Here is a little info about my laptop:
PCG-FX210
AMD Duron 800mhz
164MB RAM
10GB HDD
Newest Kubuntu Hoary 386 install

Another Quick Q: I have read that i should get the k7 addon because it has better instructions for the duron cpu, would you know anything of this sort?

TIA!
-psychosematic

---

### Post by psychosematic on 2005-06-13
No Comments by anyone?

---

### Post by dave9191 on 2005-06-13
[QUOTE=G_u_s]hey dave =)

sorry, i have installed sonypid, i modprobe'd sonypi, and then launched sonypid, but when i hit Fn and a Fx key it does nothing. when i hit the Fx keys without holding Fn, it works, and displays some weird code that, i guess, represent the F1 to F12 code, but that's all.

any idea ?[/QUOTE]

Hey sorry guys, Ive been a little busy for the last few days. The weird codes are just F1-12 represented. You get hat in any console. If sonypid is not getting any input from the sonypi module then I dont know. Maybe you need to modprobe sonypi with permissions spesified, but thats beyone me :( Sorry I couldnt get it to work for you. 

Dave

---

### Post by dave9191 on 2005-06-13
[QUOTE=psychosematic]Hey Dave,

I am just getting started with kubuntu and linux in general. I was trying to follow along with your instructions & I have stopped on the first step on starting sonypid.

Error info in the terminal window
```
FATAL: Error inserting sonypi (/lib/modules/2.6.10-5-386/kernel/drivers/char/sonypi.ko): No such device
``` 

Here is a little info about my laptop:
PCG-FX210
AMD Duron 800mhz
164MB RAM
10GB HDD
Newest Kubuntu Hoary 386 install

Another Quick Q: I have read that i should get the k7 addon because it has better instructions for the duron cpu, would you know anything of this sort?

TIA!
-psychosematic[/QUOTE]


Hey, you said you stopped on the first step starting sonypid. Did you type "sudo modprobe sonypi" or "sudo modprobe sonypid". If you did sonypi and it failed then maybe your laptop doesnt have a sonypi module ? Which would be strange for a sony laptop unless it one of the new ones and they have something else which the sonypi driver doesnt support. 

And it would make sense to get the k7 addon to provide the extra instruction set for the k7 cpu you have. As for how you would do that I don't know as I have never had to do that. 

Dave

---

### Post by psychosematic on 2005-06-13
Hi Dave, 

Thanks for your response .... well i ran both "sudo modprobe sonypi" & "sudo modprobe sonypid" ... the first with the error explained from above and the second one came back with "FATAL: Module sonypid not found."  

My laptop is probably 5 or 6 years old ... is there a way that i can compile or install sonypi onto my laptop in order for the function keys to work?

Thanks for your response,

-psychosematic

---

### Post by dave9191 on 2005-06-13
From what I understand it, sonypi comes shipped with 2.5kernel or so. And ubuntu hoary kernel is beyond that. You can read the dev page about sonypi [http://popies.net/sonypi/](http://popies.net/sonypi/). Maybe your laptop has something else controlling the function keys that isnt compatiable with sonypi. 

Dave

---

### Post by G_u_s on 2005-06-14
[QUOTE=dave9191]Hey sorry guys, Ive been a little busy for the last few days. The weird codes are just F1-12 represented. You get hat in any console. If sonypid is not getting any input from the sonypi module then I dont know. Maybe you need to modprobe sonypi with permissions spesified, but thats beyone me :( Sorry I couldnt get it to work for you. 

Dave[/QUOTE]

hey Dave

please do not be sorry ! you have been a great help, and you have spent quite some time helping me, and i really want to thank you about that.
as for the problem itself, well, i guess i'll wait for Breezy then =D

thanks again a whole lot for your time and kindness.

---

### Post by dave9191 on 2005-06-14
Im planning on redoing my system hopefully soon, but Ive got a lot of work lined up. When I do, ill make a step by step guide. Maybe there is something I have missed or forgotten about. Ill post it here if i ever get it done :)

Dave

---

### Post by psychosematic on 2005-06-14
Yes Dave Thank you for your time as well ... it is much appreciated.

---

