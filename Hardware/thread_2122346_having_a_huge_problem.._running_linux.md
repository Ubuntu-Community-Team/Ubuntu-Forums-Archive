---
title: "having a huge problem.. running linux"
date: 2013-03-04
forum: Hardware
---

### Post by aarons6 on 2013-03-04
so to begin, im not new to linux.. been using linux as my primary OS on every computer i own for years.. 
recently i upgraded the cpu on my desktop and it broke linux.. here is my story.

first here is my desktop specs..
Gigabyte M61P-S3 motherboard with 4gb (1gbx4) DDR2 ram.. at 5-5-5-15-20-2T Dual channel
AMD x2 6000+ socket am2
eVGA Nvidia Gts 450 1gb pci-e video card
500gb SATA HDD

been running, 12.10 32bit for a couple months with gnome-shell on top of ubutnu.
i have been using the 310 nvidia drivers.

zero issues.. everything is great.

so the other day i got a new cpu.. 
an AMD x2 7750 socket am2+

i put that in and turned on my computer and this is what happened.

first it boots up to the greeter, no problems, takes like 30 seconds.
you log in and the computer freezes up.. no activity for like 3 to 5 minutes.
it then loads for a few seconds, then stops and hangs for another few minutes..

if left, it will finally boot up to the desktop.

if you click on anything, to say open a program or even right click the desktop to bring up the menu, the system will hang for several seconds.. mouse doesnt move or anything.

then after a bit it will start working again.

if you get to open a program, say the file manager.. just moving the window on the screen will cause the system to hang for several seconds. again the mouse doesnt move or anything.

this will go on for a few minutes until finally the computer freezes and you have to force shut down.


before anyone says its the cpu.. 
i installed windows 7 ultimate on a spare hard drive and this is what i am using now..
same setup.. 

its really fast.

7.3 in the index.


so ive tried to reinstall ubuntu 12.10
ive tried to install kubuntu 12.10

i dont know why linux wont run.. 


any ideas?

---

### Post by Bucky Ball on 2013-03-04
You may have more luck getting help if you change your thread title to reflect what you are having a big problem with ... ;)

You can do that by clicking 'Adv Reply' for half an hour after initial posting. Good luck.

---

### Post by Bucky Ball on 2013-03-04
You may have more luck getting help if you change your thread title to reflect what you are having a huge problem with ... ;)

You can do that by editing the first post then 'Go Advanced' for half an hour after initial posting. Good luck.

---

### Post by aarons6 on 2013-03-05
still trying to track down why linux wont run.
it seems video related.. but im not sure why.
every time something moves on screen or creating a window, like opening an app, the computer freezes for several seconds.

---

### Post by Mark Phelps on 2013-03-05
I had a similar 12.10 booting problem when I upgraded motherboards and processor and memory -- all much faster than before.

I read threads about the problem being that the system was simply "too fast" for the Linux boot process (sounds crazy, I know -- but read on) and the solution was to add "rootdelay=nn" (where nn was the number of seconds) to the kernel line in the boot stanza.

So, I did that, starting with 45 seconds -- and it worked!  Instead of it taking several minutes to get to a desktop, it took a little over a minute.  I experimented with lower values until I found that 30 was about right.  Lower values tended to repeat the original problem.

If this works for you, at least you will be able to boot faster.

---

### Post by aarons6 on 2013-03-06
yeah that wasnt it, i ended up putting the old CPU back in.. 

im kinda thinking it has something to do with the cpu and the video card.. maybe power problems with the board. which is strange cause the old cpu is a 125w 90 one and the new cpu is a 95w 65 one.. at anything the board should be liking the new cpu better

i tried to install linux again on a spare drive and every time when i loaded it up after the install the video was scrambled and it was locked up.
the only way to get the video working was with the forcevesa option. at 1024x768 res.

i tried all the nvidia drivers and nothing worked.

it is strange tho that windows 7 worked.. i ran prime95 and the evga video tester for hours with no issues.. 
i played skyrim for hours with no issues.. 

i try to load linux and it goes all messed up.
so i put the old cpu in and linux boots up with no issues.. 


id really like to use that faster cpu tho :(

---

### Post by aarons6 on 2013-03-12
ok i kinda figured out a few things.. i got a newer cpu
amd 64 x2 240 am3

i put it in and it does the same thing.. 
i was playing around in the bios and if i enable cool n quiet linux runs normally
if i disable it, it locks up for several minutes whenever i try to do anything, like open or move a window.

any ideas why cool n quiet would fix the problem?

---

