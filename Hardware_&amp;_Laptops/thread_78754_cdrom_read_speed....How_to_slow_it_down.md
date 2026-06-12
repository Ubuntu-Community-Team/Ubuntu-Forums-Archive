---
title: "cdrom read speed....How to slow it down?"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-18
Hi.
I have a dvd player in my comp.. In windows I use nero drive speed control to limit the read speed of the drive. A dvd only need 5x speed to play properly. This make the drive very quiet..
nerolinux had no such option....

In linux the drive runs at full speed when watching a dvd.. Spinning at 56x is way to loud and makes the drive heat up alot....

I have tried....

-hdparm -E1 /dev/cdrom  ........This is suppost to set the speed..I chose the lowest value but its still at 56x?
it confirms that the speed is set to 1, but like i said it does nothing.

-DMA is on...helps with playback but still spins at full speed..
Is there another hdparm option that will fix this? Or another soltuion?

---

### Post by floyd27 on 2005-10-18
I found a app that will do the job..
i have a prob however..
It does not show my dvd drive in the list of drives to change the speed. No drives in fact..
You can do it in a terminal but i dont know what my drive is called..
how do i find the drive mane..
If i put a dvd in it comes up and says..
media/hda
in permissions it says
dev/hda

I only have this one dvd drive on its own ide cable "master"
the HDD is SATA

---

### Post by floyd27 on 2005-10-19
I have tried 4 differnt apps so far..
Either it wont install or doesnt work..
someone please help...

here is where im getting them from..
If someone who would be interested in using one of them would try to get it working maybe we can work it out together...


[http://www.linuxlinks.com/Software/Utilities/CDROM/](http://www.linuxlinks.com/Software/Utilities/CDROM/)

There are several.. set cdrom speed was the one i got the farthest in....

---

### Post by floyd27 on 2005-10-19
This is from a read me file..
I dont know about this eject thing but the actual app itself might work..
How can i copy to the /usr/bin file..
i tried to drag/drop but it didnt work...
I need to have permission?
So far this seems to be as close as iv gotten with any...




Note: recently speed control was also added to the eject command.
cdspeed is therefore now a bit obsolate. 
eject is available from [http://eject.sourceforge.net/](http://eject.sourceforge.net/) but all Linux
disrtibutions include the eject command already.
------------------------
Installation:

to compile type:
make 
to install cdspeed to /usr/bin type:
make install

You can copy the script cdmount to /usr/bin
it will first reduce the speed and then mount the cd.
See the explanations inside the cdmount script for
further details.
-------------------

---

### Post by floyd27 on 2005-10-19
Finally got hdparm to work...
Its not great but at least it works...

---

### Post by pjcarr42 on 2005-10-20
[QUOTE=floyd27]Finally got hdparm to work...
Its not great but at least it works...[/QUOTE]

Hmmm I am having the same issue as well and my computer setup is close to identical as yours..same motherboard and an athlon xp..just wondering if you could explain a bit more how you slowed the drive down. I can't seem to figure out a way to do it and on playback the thing is spinning at full speed...no need for that!

---

### Post by floyd27 on 2005-10-20
well its a bit tricky but it works... Youll have to bear with me..

ok in a terminal...

hdparm -E4 /dev/hda     (-E8 makes 8x and so on.....)

 However you have to know the location of the drive?
If i write hdparm -E4 /dev/cdrom  it will say set cdrom speed to 4x but it wont work?   you have to know the proper loaction and im not sure exactally how to find it.. I used trial and error.....linux assigns drive names based on ide location so im /hda (for primary master)...

Also when watching a dvd if i jsut insert the dvd and play it wont work?
I have to open the dvd folder first then it kicks in, and lowers the speed....Then just close the open folder, and run the dvd through your favorit player..
i dont know why this is but like i said at least it works....
Im sure its a glitch or user error but its as good as iv gottne it to work?
And im not sure about re-boots, i just do it everytime.....but it may hold?

---

### Post by floyd27 on 2005-10-21
Lately iv been having off/on luck..depending on the disk im using?
i dont know whats going on..

---

### Post by pjcarr42 on 2005-10-22
Thank alot for the tips, I will keep in in mind next time I futz around with it but for now I just can't be bothered for a bit...lol

---

### Post by avishalom on 2007-03-17
i was wondering, 
is there anything new since 2005 ?

---

### Post by impert on 2007-08-14
> **avishalom said:**
> i was wondering, 
is there anything new since 2005 ?
Shalom, Avishalom,

This is a very late reply but (in case others are having the same problem):

There is an application called Set CD-ROM Speed  [http://www.kde-apps.org/content/show.php?content=18057](http://www.kde-apps.org/content/show.php?content=18057), which may be good but it depends on Kommander, which for me meant adding 57 Megs of libraries. 
There is also a command line app (in Synaptic) called setcd which allows you to change the speed, and do one or two other things; the overhead of this is 10,7 Kb. 
Alternatively, you can open the terminal, and type eject -x4 (4 is a good low speed in principle) or eject --help for more info. Eject is already included in Feisty, at least.
Note that you can only have certain speeds - my lowest is 10x, but it's a LOT quieter than 40x.

This little bit of info cost me a few hours of stuffing around!

Yours for a quieter world

---

