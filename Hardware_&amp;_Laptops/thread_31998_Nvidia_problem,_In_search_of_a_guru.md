---
title: "Nvidia problem, In search of a guru"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by Hieronymus on 2005-05-05
I have a problem with my Nvidia GeForce4 440 Go 64M, the question could be who hasn't....

These are my system specs:

HP Pavilion zv5133ea 
AMD64 3000+ 
Nvidia GeForce4 440 Go 64M
Ubuntu Hoary Hedgehog 5.04 64bit / winXP dualboot

The problem is as follows, my card won't work with drivers higher than version 6111. But this kernel (2.6.10) won't work with version 6111. I don't want to downgrade my kernel but I want to use my videocard to the max. 

I have searched many forums but I can't find the solution. Can anyone help me out?

Grz Hieronymus

---

### Post by kiddo on 2005-05-05
Why not use the ubuntu-provided ones? sudo apt-get install nvidia-glx (from what I understand, you wanted to make the official nvidia binary drivers work)

---

### Post by Hieronymus on 2005-05-05
[QUOTE=kiddo]Why not use the ubuntu-provided ones? sudo apt-get install nvidia-glx (from what I understand, you wanted to make the official nvidia binary drivers work)[/QUOTE]

I'm sorry, I haven't been clear. I have tried the Ubuntu ones as well, but they won't work either.

---

### Post by alastair on 2005-05-05
When you say "don't work" - explain.

If you have any specific problems, or /etc/X11/Xorg.0.log messages, please post them.

As a last resort, you could always upgrade your kernel (isn't 2.6.11 available in some form from Ubuntu, for the brave?). Or even compile yourself.

---

### Post by usergentoo on 2005-05-06
Its seems were in the same boat. The Nvidia drivers 7174 dont work with the 2.6 kernel. It only certain cards it effects. I can say Ive tried it on both my laptops (Gateway GeForce 2go and Dell GeForce 2 go) and its not working.

Its a hard lockup. No control of anything. When you power down and reboot. All log files contain no entries for this occurance. Im a Gentoo person myself but have switched to Ubuntu recently on this laptop. And have tried all the newest linux distro's in the past several months including Mandriva 10.2 le, Knoppix 3.8, gentoo, Suse, Mephis, Fedora, and a few others and still have the same problem.

From researching all of their forums they too have the same problems, and no one can find a answer. Also checked nvidia's forum and there is several pages of the same. 

It happens on the geforce go, geforce 2 go , geforce 4 go , and some of the mx series. 

I did read where some had the 7167 to work they found that it links to a folder of files that are not their. By adding the folder in the correct location and the files it tends to work from what ive read. 

Some in the gentoo forum said its a glitch with glibc, and if you downgrade it the 7174 works. 

In the mandriva forums they said by rebuilding the 2.6 kernel and removing anything to do with power managment tends to make them work.

Now some people also have lockups but its because of nvidia not finding the correct modelines for your card so you have to add them manualy to your xorg.conf. This lockup has a blinking cursor in the top corner so if you see that then this would be the fix for you.

Mine dosent have this mine goes blank like it went into standby mode but you loose all keyboard commands and when you go to power down it takes a long time to respond. 

I do know using gentoo on my other laptop the 6111 drivers work with the 2.6 kernel. And also if you downgrade to the 2.4 kernel the 7174 drivers work on it.

So im at the point on this laptop trying to down grade to 6111 drivers so i can use opengl progs. 

Now if anyone like to help me learn to downgrade to the 6111 drivers I could use some input. Using Ubuntu is alot different then using Gentoo. After using it for several years I thought Id change and try something different. In gentoo id just emerge the 6111 drivers and be done. But this is a diferent setup.


So now Im needing the help.   But like I said no one seems to really have a answer several bug forms have been sent in and yet to be resolved.

---

### Post by Hieronymus on 2005-05-06
I just solved the problem for my situation. 

I installed linux kernel 2.6.11. Next I downloaded the latest nvidia drivers from [ Nvidia.com ]( http://www.nvidia.com/object/linux_amd64_display_archive.html) and installed them. This did the trick for me. No more lockups of me. I hope this will help you.

I have been using Gentoo before Ubuntu as well, and some people find it hard to believe that I think that Gentoo is easier is some views. Anyway, the 6111 driver is also downloadable from the Nvidia site, but it won't install in new kernels. 

Good luck

---

### Post by usergentoo on 2005-05-06
Tell me what I need to do to get the 2.6.11 kernel. If I need to add new repositories or what? Not sure.  Drivers understand how to
 install. But not adding a new kernel or where to get it and what other packages need to be installed.


And your right Gentoo is really easy to use.

Oh by the way which lockup did you have complete or the blinking cursor?

---

### Post by Hieronymus on 2005-05-06
[QUOTE=usergentoo]Tell me what I need to do to get the 2.6.11 kernel. If I need to add new repositories or what? Not sure. Drivers understand how to
 install. But not adding a new kernel or where to get it and what other packages need to be installed.


And your right Gentoo is really easy to use.[/QUOTE]

Well, I installed it by going to System >> Administration >> Synaptic Package Manager en there I searched for 2.6.11. Next I installed the packages I needed and rebooted. Once you reboot the grub bootmenu will (ofcourse) popup and you have now also the posibility to chose for the new kernel.
I don't know if you need new repositories but here is my /etc/apt/sources.list which worked for me. 

```

root@home:/home/dusty # cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

#deb ftp://ftp.nerim.net/debian-marillat stable main
#deb ftp://ftp.nerim.net/debian-marillat unstable main
#deb ftp://ftp.nerim.net/debian-marillat testing main
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

Good luck

---

### Post by usergentoo on 2005-05-06
I thankyou for the help.

Maybe by this afternoon when I wakeup I can use some opengl stuff.
Till then Im gona sleep and think positive while this finishes installing.

---

### Post by Hieronymus on 2005-05-06
I was celebrating to early. I installed the Nvidia drivers and rebooted, no problem. But after the second reboot X failed due to the following error:

```

(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found

```

I'm pulling my hair out here, can anybody tell me how to fix this?

---

### Post by Hieronymus on 2005-05-06
Solved it, but it's a mystery to me why.

I have again reinstalled the older kernel version 2.6.10-5 and the Ubuntu version of the latest Nvidia drivers. Now everything works. 

Thx for your help

---

### Post by usergentoo on 2005-05-06
I didnt have any luck. Still the same, hard locks. Oh well im gona try the 6111 drivers and see what happens.

---

### Post by nomad311 on 2005-07-26
i agree that gentoo is easy ...on the right hardware
..with the help of a gentoo regular i had it up n runnin on my pavilion ze43xx in a day ...then i compiled kde overnight and i liked it

now when i got my zv5xxx i had a flood of problems and went through fixin em one by one till i got to this problem with 32bit apps... so i searched for another distro and found this one ...i like it extremely simple when your not n the mood to play around but based on debian so you can always alt-tab over to a term and go at it

 the only prob im experiencein is wit the nvidia driver but now ...dunno how i missed it on my first look through the synaptic packages im gonna upgrade to the 2.6.11 ...i might even skip it and get the 2.6.12 source ...nah i dun wanna tempt fate LOL

but just wonderin how you guys are gettin along with ubuntu in the 'long-run' --i installed it yesterday HA

-nomad311

---

### Post by usergentoo on 2005-07-26
So far I havent had any problems with it on my laptop or my other computers and I am still a happy ubuntu user. Actualy so happy with it I may never switch again.

Maybe I should get a new name since I nolonger use gentoo. 

I also switched my son's computer over to ubuntu from mandrake and he likes it
Plus I changed my server from gentoo over as well.

All I have to do is convince my wife to switch. She just signed up to start beta testing M$ Longhorn or is it Vista tommorow, I guess they will make up there mind on the name sometime.

---

### Post by nomad311 on 2005-07-26
well i did the whole nvidia thing ...i ended up dlin the driver from nvidia and building it myself ...the deb binary didnt seem to work for me but thats done wit

...now to get xmms on esd (i think everything else is)
...but i dun think i can do dvds yet ...havent tried but i do know that libcss2 ...or whatever the guide says (i copyed and pasted) isnt up nemore so ill see whats up

i really gotta say im not missin gentoo ...tonight ill proly get it off the old laptop (ze4300) cause all of a sudden none of the xmms themes/plugins/updates will compile ...but no problem wit firefox --go figure!!!!

plz oh plz oh plz let my new card be here when i get home!!!!
BROADCOM SUX!!!! GO ORINOCO!!!

-nomad311

---

### Post by JayCnrs on 2005-07-26
I have the latest Nvidia drivers 7667 working with my Dell 2650 with a GeForce2Go card. There were quite a few changes to make it work with my laptop, the only problem I am having is once in a while my battery doesn't register correctly, could be the dsdt file, hasn't been at the top of my priorities to fix that.  Anyway I have put a link in to my post on Linux Questions, because I'm feeling a little lazy and don't want to write out everything again I was suffering from just a black screen when shutting down and the Ubuntu drivers caused this right at bootup:

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=337774&highlight=nvidia+black+screen](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=337774&highlight=nvidia+black+screen)

---

