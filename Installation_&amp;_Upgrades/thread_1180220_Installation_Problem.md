---
title: "Installation Problem"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by joyneo04 on 2009-06-06
Dear all,

Today i was trying to install the new version of Ubuntu 9.04,Once reaching to stage 4 of installation i got a blank window,when i press forward key a pop up comes ou stating 
[SIZE=3][B]No root file system is defined
Please correct this from partioning menu.[/B][/SIZE]

Now i want to know where can i get the partitioning menu and how can i correct this problem.Even if i have to delete all data from my harddisk then also i have no issue.Please do help me.

---

### Post by wpshooter on 2009-06-06
Did you do the installation from the ALTERNATE CD version ?

---

### Post by merlinus on 2009-06-06
The partitioning menu *should* have appeared before this.  What happens when you press the back button once, or even twice?

---

### Post by joyneo04 on 2009-06-06
Actually i was trying to install from the cd i have received from the cannonical society recently by post....Version Ubuntu 9.04(Jaunty)

---

### Post by merlinus on 2009-06-06
Try checking the cd for defects from the opening menu.

---

### Post by joyneo04 on 2009-06-06
when i am clicking the back button a pop up is coming stating[B] 
starting up the partiotner.[/B]
this pop up is showing a status bar stating scanning disk.....in this status bar the bar is moving very fast for 50 % and then it stops for a little while and then again i get the same window....means that white window.

---

### Post by joyneo04 on 2009-06-06
Actually when i am running this os directly from the cd then it is working fine...but when i tried to install it i face this problem means this white window.

---

### Post by wpshooter on 2009-06-06
> **joyneo04 said:**
> Actually i was trying to install from the cd i have received from the cannonical society recently by post....Version Ubuntu 9.04(Jaunty)

Do you know if it is the Live "Desktop" CD version or is it the ALTERNATE "text based" CD version ?

In any case, it sounds as though your problem is that you have failed to designate the "/" system partition as **_BOOTABLE_**.

You should make the following 3 partitions:

/ = root, i.e. system partition - make it primary & bootable
/home = , home partition - make it either primary or logical
/swap = swap partition - make it either primary or logical & twice the size of your RAM.

I would use file type as either ext3 or ext4.

---

### Post by joyneo04 on 2009-06-06
wait for a while i am giving you the details of the things written on the task bar of this window.

---

### Post by merlinus on 2009-06-06
It would seem that the partitioner is not able to find partitions on your hdd.  Have you set them up in advance?  Are you running another os?

Can you run from the try ubuntu without installing option?

---

### Post by joyneo04 on 2009-06-06
No i am not running any other os.earlier i was using ubuntu 8.04,Yes i have formatted it before installing this new version.

---

### Post by joyneo04 on 2009-06-06
I am attaching a file which will make u all clear about the window how it is looking like...wait for a while..

---

### Post by joyneo04 on 2009-06-06
Please find attached herewith the view of the window as it is looking like....`

---

### Post by wpshooter on 2009-06-06
It sort of appears as though you are trying to install from the LIVE CD version.

If you have nothing on this computer that you need to save, this is what I would recommend.

Get [www.killdisk.com](www.killdisk.com) and WIPE the drive of the computer completely clean.

Then boot to your Ubuntu 9.04 CD and FIRST thing is that you check the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu - do NOT just assume that because you got it from Canonical that it is valid.

If the integrity test comes back as O.K., then attempt the install again.  If this is the live CD version, then the partitioner section of the install "SHOULD" make your "/" partition bootable automatically.  Make sure that you make the 3 partitions that I mentioned earlier.

P.S. - If per chance it is an ALTERNATE CD version, then you have to specifically designate the "/" partition as bootable.

Good luck.

---

### Post by taladan on 2009-06-06
If you're wanting to use the default partitioning scheme, you need to go back one screen and choose 'Guided partitioning, Use Entire Disk'.  Either that or if you're trying to create your own partition, you need to choose 'new partition' on that screen, then set it up as type ext3 and put the mount point as /.  You'll also want to create a swap partition as well...there are a myriad of ways to partition your drive and everyone who does this long enough has their own favourite way of doing it.  As to the swap partition, I've heard people say do a swap partition the same size as your amount of ram, and I've heard people say to partition enough space equal to double the amount of ram you have.  I've done it both ways in the past and one works as well as the other.

Hope this helps,

Tal

---

### Post by joyneo04 on 2009-06-06
sir how can i run killdisk..currently i dont have any os installed in my pc.what are the commands i need to run and what is the detailed procedure.kindly help me out.

---

### Post by merlinus on 2009-06-06
It seems as though you enough system resources to boot up and run the live cd, but perhaps not enough to install it.  You might try the text-based alternate cd, which requires less resources.

Also, posting system specs might help.

---

### Post by joyneo04 on 2009-06-06
giving you the details when i am trying to install it from live cd...
Booting from CD..
Try ubuntu without any change to your comp.
Install ubuntu
Check disk for any defects
Test memory
boot from first hard disk drive.

press f4 to select alternatives start up and installation mode.
f1help; f2language; f3key map; f4modes; f5accessibility; f6other option.


I press install ubuntu....then comes

Step 1 of 7 Language selection
Step 2 of 7 Time zone selection
Step 3 of 7 layout of keyboard selection
step 4 of 7 starting up the partiotioner...
and then comes the blank window....

now what should i do....

---

### Post by merlinus on 2009-06-06
Did you check the disk for defects?  Once again, however, it seems that you can Try ubuntu without any change to your comp. successfully, but not install from this disk.

If it passes the disk test, then you might try the alternate install cd, which is text-based and does not have the try feature.

---

### Post by joyneo04 on 2009-06-06
When i am pressing boot from first hard disk it is showing....

Booting from local disk
isolinux :  disk error01 , AX=0201, drive 80;
Boot failed : press a key to retry....

---

### Post by joyneo04 on 2009-06-06
how can i check the disk for any sort of defects.....

---

### Post by merlinus on 2009-06-06
It is a choice on the opening menu:  

Check disk for any defects

---

### Post by joyneo04 on 2009-06-06
yes i have done it...there was no defects mentioned after the check was over....

---

### Post by joyneo04 on 2009-06-06
cant get you about the text method....can u explain it in a little details......actually i am a very new beginner user....

---

### Post by merlinus on 2009-06-06
OK.  Can you download and try installing from the alternate cd?  It is an option on the download page, on the right-hand side near the bottom:

[Text based “alternate installer” installation disk]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by joyneo04 on 2009-06-06
thanks for such an explanation and also for providing the url...now i get u...i have tried the same as well...

---

### Post by merlinus on 2009-06-06
So the alternate install disk did not work either?

Please post your system specs, as that may shed some light.

---

### Post by joyneo04 on 2009-06-06
80gb SATA hdd; 256 mb ram,mercury motherboard,intel processor pentium 4,

---

### Post by joyneo04 on 2009-06-06
if u want any more details then u can check my earlier post
[http://ubuntuforums.org/showthread.php?t=1175746](http://ubuntuforums.org/showthread.php?t=1175746)

actually i am facing this problem from a long time means nearabout 5 days....please do help me...

---

### Post by merlinus on 2009-06-06
**Recommended minimum requirements**

 Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor 
[*]384 MB of system memory (RAM) 
[*]8 GB of disk space 
[*]Graphics card capable of 1024x768 resolution 
[*]*Sound card* 
[*]*A network or Internet connection*
[/LIST]
You might try xubuntu, which requires less resources.  Also, there may be an issue with your SATA drive.  I cannot help with that.

---

### Post by joyneo04 on 2009-06-06
thanks  a lot for your precious time and co operation..let me check out with the hdd problem.incase i have any other problem then i will contact this forum again..please do bear with me...your cooperation has made us feel very secure in using this ubuntu....thanks a lot again.

---

### Post by Raygreen on 2009-06-06
I had the same problem getting Ubuntu to load on my computer, it was running Windows XP, I could get it to dual boot with Windows XP with Wubi or run from Live CD but could not get it to load when I used killdisk and wiped the hard drive clean. I could not even get Ubuntu 8.10 to run either. ***[COLOR="Red"]I did get openSUSE, Freespire Linux and Windows XP to reload on hard drive, but could not get Ubuntu to load.[/COLOR]*** Kept getting partition errors. I been posting for over 2 weeks and no one seems to have any responses. I had tested the disk and the download of the iso, everything checked out fine. After loading the other distros, I also had trouble with Mandriva, and Fedora, they also would not load. I tried several times to reload Ubuntu and tried to partition the drive manually without running out and buying Partition Magic or something.

---

### Post by joyneo04 on 2009-06-06
I can understand the problem u r facing.actually i have also postde the problem four days back.u can go through my thread [http://ubuntuforums.org/showthread.php?t=1175746](http://ubuntuforums.org/showthread.php?t=1175746) where u can get the details.i dont know as well how to run killdisk.right ow i am using my system only by running the live cd disk os and not installing it.whenever i require to save anything i connect a flashdrive and save it in that flashdrive.but dont worry.i am not goin to leave.once i get any solution i will definitely let u know as i move through hit and trial.

---

### Post by joyneo04 on 2009-06-06
as you were saying that u have tried xp as well but i am not in a mood to install xp whatever it takes.i will install ubuntu

---

### Post by merlinus on 2009-06-06
Good on you for not giving up, and refusing to install windows!

As I posted, it would seem that you might not have enough RAM to run ubuntu, so you might try xubuntu.  It has a different interface and uses some other programs from ubuntu, but is still very much the same.

Also, it is possible that the installer is not seeing your hdd, and that is why the screen for partitioning does not come up.  Again, that may be a SATA problem, but I do not know.

Good luck!

---

### Post by joyneo04 on 2009-06-06
merlin thanks for the reply and giving me the hope...frankly speaking now actually i was using this ubuntu 9.04 but my experimenting nature just made face this problem today.actually first i was using ubuntu 8.04 and then i got this cd...as part of my curiocity about ubuntu i installed this ubuntu 9.04.it was working very nice but at that time i allocated it with 20 gb.then one day while seeing all application i saw this disk management thing and started experimenting with the partitions.then i thought of making a partition of 8 gb and installing this ubuntu 9.04 out there.so i formatted the drive.then after if you have read my last thread then you can have the idead of that black outlines.then i was unable to install this version once again.please do help me.

---

### Post by merlinus on 2009-06-06
OK.  Another suggestion is to download the live gparted disk.  Burn it as a disk image, and you can boot from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can then delete all your existing partitions, and make new ones.  For example, 10G (which you will use as /), 60G (to be used as /home), and 1.5G (for /swap).  Format them as ext3.

Then use your ubuntu cd, and perhaps the partitioning screen will show these.  If so, click on each one, select edit, and then the mountpoint for that one (e.g. /, /home, swap).

---

### Post by joyneo04 on 2009-06-06
merlin thanks a lot ...lokk no body has given this solution in such a nice manner as u have given me..somebody suggested me to run DBAN as well as somebody suggested me to run killdisk but nobody told me how to run them..all  these softwares were available in .exe format and .exe doesnot run in ubuntu.and as there was no os i my system then how can i run them.hope the link u have given me ...after downloading the material and putting it in cd rom it will run automatically and will work on the hdd.lets hope for the best..

---

### Post by joyneo04 on 2009-06-06
hey not getting any link to download the same gparted from the website...can you give me a little details...

---

### Post by merlinus on 2009-06-06
It looks as though the download servers are not working at the moment.  Check back later.

BTW, dban can be burned to a disk that will boot.  It is used to completely wipe your hdd.

---

### Post by joyneo04 on 2009-06-06
wow that's great...thanks a lot for your active cooperation man.....really hat's off to the effort you gave in solving my problem.....no words is enough to explain the cooperation i get from the member of this forum....[SIZE=3]**.[COLOR=Red]Long live UBUNTU.....lets together make this world rock with ubuntu[/COLOR]**[/SIZE]...but boss incase i face any problem then i will again disturb you all...please do bear with me....

---

### Post by merlinus on 2009-06-06
Glad to help.  That's what we are all here for.

Keep us posted.

---

### Post by wpshooter on 2009-06-06
Joyneo:

[www.killdisk.com](www.killdisk.com)

go to download and then look at the 3rd listing in the 2nd column.  That is what you need to BURN an ISO (bootable) image of Killdisk to a CD, which you can use to WIPE your hard drive.

However, having said that, since you appear to have only 256mb of memory and the system requirements for Ubuntu is 384mb, you "MAY" not be able to install Ubuntu/gnome.  But I believe I would give it another shot after you have WIPED your drive.  Go to the Ubuntu download site and download and burn the ALTERNATE CD version of Ubuntu.  There is a check box which gets you the ALTERNATE instead of the live CD version.  I would recommend downloading it from Perdue University site in USA.  You stand a much better chance of getting it installed with the ALTERNATE version.  When you get to the partitioning section of the ALTERNATE install, choose MANUAL partitioning and partition the 3 partitions as I gave in my earlier post.

If you can not get Ubuntu/gnome to work, then WIPE the drive again and download and try the ALTERNATE version of Xubuntu.

Good luck.

---

### Post by joyneo04 on 2009-06-07
Dear merlin,

First of all thank for the suggestion of gnome partition editor.I was able to boot it but after runing the cd a lot of option was coming.I was unable to find out which one to select and boot.Please do help me in .

---

### Post by Raygreen on 2009-06-07
**[COLOR="DarkRed"]merlinus[/COLOR]** suggestion to try using [COLOR="darkred"]***gparted disk ***[/COLOR]to partition the drive. I am going to have to give that a try. I am going to try one more time to get Ubuntu on that computer. I have tried 3 times so far. Each time I got a partition error. I have successfully loaded freespire on it 3 times after Ubuntu reformated the disk and got openSUSE to load 2 times, and Windows XP to load 2 times. Going to try gparted which I already downloaded. Will burn it to disk and try creating the 3 partitions. Then run Ubuntu 9.94 install disk.

---

### Post by joyneo04 on 2009-06-07
Dear merlinus,
first thank you for suggesting gparted editor as i was atleast able to see the partition editor.Now the partition editor is showing fully white and nothing is shown out there.only two things i can click on was gparted and help.while cliking to g parted i get an option feature....cliking the feature i got a table which was looking exactly like this...now tell me what is this all about....i am attaching the demo of the table for your referrence....

---

### Post by merlinus on 2009-06-07
Hi.  I was not able to open the file you attached to your message.  Can you upload it as a screenshot?

Unfortunately I do not remember all of the options from the live gparted menus, but surely there is one which offers to view and edit your partitions.

Another possibility is to boot from the live ubuntu cd, select try without changing anything, and when it is running open a terminal and post results of:

```

sudo fdisk -l

```

which should show your existing partitions, if any.

---

### Post by joyneo04 on 2009-06-07
**file system** 			**detect** 			**read** 			**create** 			**grow** 			**shrink** 			**move** 			**copy** 			**check** 			**read level** 		 		 			**Ext 2** 			
			
			
			
			
			
			
			
			
		 		 			**Ext 3** 			
			
			
			
			
			
			
			
			
		 		 			**Fat 16** 			
			
			
			
			
			
			
			
			
		 		 			**Fat 32** 			
			
			
			
			
			
			
			
			
		 		 			**hfs** 			
			
			
			
			
			
			
			
			
		 		 			**Hfs +** 			
			
			
			
			
			
			
			
			
		 		 			**jfs** 			
			
			
			
			
			
			
			
			
		 		 			**linux swap** 			
			
			
			
			
			
			
			
			
		 		 			**ntfs** 			
			
			
			
			
			
			
			
			
		 		 			**Reiser 4** 			
			
			
			
			
			
			
			
			
		 		 			**reiserfs** 			
			
			
			
			
			
			
			
			
		 		 			**ufs** 			
			
			
			
			
			
			
			
			
		 		 			**xfs**

---

### Post by joyneo04 on 2009-06-07
check out the attachment for your ref....

---

### Post by merlinus on 2009-06-07
There should be a graphical interface for all this, which shows your hdd, existing partitions (if any), and menu options to create, move, resize, and format.

Select ext3 for the format.

---

### Post by joyneo04 on 2009-06-07
now check it out...m sending it in word format....

---

### Post by joyneo04 on 2009-06-07
merlinus you go through the attachment and till then let me use the command through live cd....

---

### Post by merlinus on 2009-06-07
As I said, I cannot do anythihg with your attachment.  Can you send a screenshot of gparted?  It will usually be in .png format.

---

### Post by joyneo04 on 2009-06-07
sorry to say but only these two options are alive one is gparted and another is help....rest all option are disable....also wait for a moment i am forwarding you the result i received afgter running the command fdisk....wait

---

### Post by joyneo04 on 2009-06-07
After typing fdisk in the terminal i received the following things in the terminal window...
usage:fdisk [-l] [-b ssz] [-u] device
e.g.: fdisk /dev/hda (for the first IDE disk)
or : fdisk /dev/sdc (for the third SCSI disk)
or: fdisk /dev/eda (for first ps/2 ESDI drive)
or : fdisk /dev/rd/c0d0 or: fdisk /dev/ida/codo (for raid devices)

hope this will help you in finding out the problem....

---

### Post by joyneo04 on 2009-06-07
let me try if i can take the screenshot of the same.....

---

### Post by joyneo04 on 2009-06-07
sorry to say merlin...m was unable to take the screen shot....but sending you a file which looks exactly like my partition manager.....please see the attachment.....kindly do bear with this beginner...i will remain ever grateful for your cooperation....

---

### Post by joyneo04 on 2009-06-07
Merlin go through this and you can find out what the hail i have done doing this hit and trial method...
 I was having a 80gb hdd...(40gb+20gb+20gb)and ubuntu 9.04 as well as windows.i thought to go for ubuntu only and remove the xp...so i thought of making a partition of 10 gb in my hdd and install the ubuntu after formatting the whole disk.so i formatted the 40gb and the 20 gb.then there was a part named linux swap in that partition.i deleted that part.then i created a partition containing 10gb space.then i formatted the drive containing linux os.then i tried to move the partition during this operation that the blocks were covered by black outline...i don't know what does it mean....because earlier the partitions were covered with green coloured outline....then i rebooted the system with the live cd of ubuntu 9.04 when i encounter this problem.after taht u know the whole thing.I know i have done somethig massive wrong while following my theory of hit and trial.but it s not one instance that my curious nature has destroyed anything but there are many such instaces...because i want to learn and know by doing practical application not theoriticaly...hope you ll bear with this guy and together we can againg sort out this problem beacuse you and this forum is my only hope..or else my friends are going tolaugh on me....please do assist..

---

### Post by merlinus on 2009-06-07
I was able to open the graphic, but it had a checkered grey background and so I could not see anything.  Sorry.

You might look at the gparted documentation:

[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html)

---

### Post by joyneo04 on 2009-06-07
ok now i will give you the details in other way....

filesystem detect  read  create  grow  shrink  move copy  check  read level

ext2           w         w        w        w      w         w     w        w          w

ext3           w          w        w       w      w        w       w        w         w

fat16          w           w      w         w       w       w       w        w         o

fat32          w          w        w        w        w       w       w       w          o

hfs             w          w        w        o         w       w       w        w         w

hfs+           w          w         o        o         w       w      w         o         o

jfs              w          w         w        w         o       w       w        w         w

linux swap   w         o           w        w        w       w       w        o         o

ntfs             w         w           w        w        w        w      w       w         w

reiser4        w         w           w         o        o        w       w      w          w

reiserfs        w         w           w        w        w        w       w     w           w

ufs              w         o             o        o         o        w       w      o          o

xfs              w         w             w       w         o        w       w      w          w


the table was looking like this if you consider the w=green tick mark and that o=red cross mark.Hope now you can understand and sort out the eaxct problem...

---

### Post by merlinus on 2009-06-07
Format all as ext3, except a 1.5G partition at the end of your hdd as swap.

---

### Post by joyneo04 on 2009-06-07
means if u aanalyse the above table you will find cross mark against the following---
fat16 ,fat32,nfs+,linux swap,ufs were unable to read level;;;;;;nfs+, linux swap, ufs were unable to check ;;;;;;;;jfs,reiser4,ufs,xfs---unable to shrink;;;;;hfs,hfs+,reiser4,ufs---unable to grow;;;;;hfs+ and ufs ---unable to create;;;;linux swap and ufs---unable to read.......rest all in green colour tick.....

---

### Post by joyneo04 on 2009-06-07
unable to get you...where i ca get this option format when i can't see anything or all other option are disable...

---

### Post by merlinus on 2009-06-07
Did you look at the documentation for gparted at the link I sent?  They have graphics that show what you should be seeing.

I imagine you have to first create a partition, then select it by clicking on it, and then choose the format.

---

### Post by joyneo04 on 2009-06-07
thanks a lot merklin....let me go through it in details...in case any problem persist the i ll disturb u again.....

---

### Post by Raygreen on 2009-06-11
tried gparted, and then tried loading Ubuntu 9.04 and still errored when it trys to create partitions again.

I give up!!!!

---

### Post by joyneo04 on 2009-06-13
but i won't ...m still tryin n will try till my last breathe....

---

### Post by Bucky Ball on 2009-06-13
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by joyneo04 on 2009-06-13
Thanks for the link but if my hdd is not detected then how can  use the os...but then also thnks a lot....

---

### Post by merlinus on 2009-06-13
Hi again.  I probably do not remember everything you have tried, but does the live cd work on your machine?

If so, you might use dban to completely wipe out everything on your hdd, then gparted to format the entire disk as ext3, and then try installing.

Also, the alternate text-based install disk might work.

dban -- [http://www.dban.org/](http://www.dban.org/)

alternate install -- [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

gparted -- [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by joyneo04 on 2009-06-13
sir,
really hats off to you for ur response.atleast u remember me...sir i ve tried but actually g parted is showing that there is no hdd...so today i ve changed the cable and now trying the g parted once again...let me see wt happens...

---

### Post by merlinus on 2009-06-13
If changing the cable does not work, then try dban.  It is a live cd, although text-based, and if it does not detect your hdd then you probably need to get a new one.

More info about dban available at the link I provided.

---

### Post by raymondh on 2009-06-14
Hello Joyneo04,

I am trying to re-read your thread as well as your other thread.

You used to have 8.04 installed in/with 20-20-40 partitions, since then, have you erased all partitions, including swap? 

Can you post a screenshot of what the gparted window shows?  You will need to boot into the liveCD and in live session ..
* Detach any external HD please

1.  Access partition editor (system > administration)
2.  Gparted will pop-up.  Allow it to scan all the disks. Leave it open.
3.  Now, see in the top left of the desktop panel, go to applications > accessories > take a screenshot
4.  A screenshot window will pop-up. Select GRAB THE CURRENT WINDOW.  Position the screenshot window away from the gparted window.  Click on the gparted window to highlight it.  Then, on the screenshot window, click on TAKE SCREENSHOT.
5.  You will be asked to save it someplace .... on desktop is OK.
6.  Still in live session, access the internet and this thread and post back attaching the screenshot you just took.  To attach to a thread reply, click on the attach button in the menu bar (beside the smily) ... browse for the screenshot you just saved in desktop .... click upload.

My request for the screenshot is to help with a visual of what you are saying/stating.

I know gparted will not give you any option (hence give you greyed-out options) to manipulate the partition (or HD) if it is mounted, even swap.  Maybe, you still have an active partition in there.  Also, if the HDD has bad sectors, it will also not touch it, even after running check disc from windows.

Thank you Mr.Sarkar.  I hope we can find a solution to your issue/s.

---

### Post by joyneo04 on 2009-06-14
thanks a lot sir for your active response.Its nearabout 3:00am in india and i am going to sleep now as tomorrow i have to go to office.I will post the screenshot tomorrow.Lets hope that withe active cooperation of u all i can sort out the problem...Thanks a lot again..Till tthen take care and have a great day.....

---

