---
title: "ubuntu 9.04 and windows vista ultimate dual boot"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by joelswatson on 2009-03-22
hi, i am a noob to ubuntu, i have used it half a dozen times, but i have always gone back to windows vista 64bit, but one of my friends said why dont i dual boot ubuntu 64bit and vista 64bit.
now what i want to ask is which is the best way to dual boot the two, do i install vista 64bit or ubuntu 64bit first? how do i do it, and how should i have my dual hard drives set up,

i have 2x 500gb wd 2.5" drives
the first drive is set up as
250gb ntfs for windows ( c: )
250gb ntfs for utorrent ( d: )
the second drive is set up as
500gb ntfs for storage ( e: )

now i would like to keep the second drive as one 500gb drive, and i was thinking to redo the first drive as follows
100gb for windows vista 64bit (ntfs)
100gb for ubuntu 64bit (ext4)
and 300gb for utorrent (ntfs)

how do i do this, if someone could give me step by step instructions or refer me to a guide that would be great.

now here is something else i was hoping to do.
access the 500gb ntfs storage drive and the 300gb utorrent drive from both windows 64bit and ubuntu 64bit, is this possible?

also do i have to a /swap partition? or can i have it all in the one partition like windows does it?

any comments or links to guides would be great.

please no flaming as i am only new to ubuntu 64bit and i know this might of been posted already, but i thought i would ask again, cause of the way i would like my drives setup.

also one last thing, i want ubuntu 9.04 64bit as the default boot, so if i want vista 64bit i have to select it from the list.

many thanks

---

### Post by spandon on 2009-03-22
Hi Joelswatson,
I have 6 units either dual or triple booting with Ubuntu without any probs.
Firstly, what order should the OS be installed:
Vista (so there is no need to disturb your present Vista installation) should be first, then Ubuntu.
I have never used more than 12 gig to install any of the flavours of Ubumtu in the last 4 years.
If I was installing on your setup, I would shrink the last partition of the first drive by 12 gig, then create 2 partitions.
The first of 10 gig formatted to ext3
The second of remaining 2 gig formatted as swap.
As for Ubuntu to be the default boot, this is the installation default anyway, so no worries there.
hope this helps - enjoy
Don

---

### Post by joelswatson on 2009-03-22
hi, thanks for that,
i am needing to format and reinstall windows anyway, so i was going to wait til ubuntu 9 came out, and do it all then, and i wanted to increase my utorrent drive as well.

how come you have never needed more than 12 gig? i was going to have some linux only games installed too, 

what about 175gb for vista and and 25gb for ubuntu, and then 300gb for utorrent.

what about accessing the utorrent and storage drives from both vista and ubuntu? do i have to do anything extra, or can i access them by default?

---

### Post by spandon on 2009-03-22
Hi juelswatson,
The size of partition you create for ubuntu is according to what you want to use ubuntu for, I only use the programs it comes with plus the edubuntu add on so 10 gig is more than enough for my needs.
The main thing is that I find it works better to install Ubunto at the end of the drive.
with regards to vista reading files on the  ubuntu partition- it can't due to it not being able to see the Ubntu drive.
To get round this, I make another partition (fat32 or NTFS) that I can place any files (from Open Office for eg) I want to use in Windows from Ubuntu.
Hope this helps you in what you wish to do with the two OS?
Don

---

### Post by joelswatson on 2009-03-22
hi spandon, thanks for that,
what i want to do, is use ubuntu for everyday usage, like mail net games, blah blah blah, but also have vista for stuff that cant run on ubuntu or wine.
so in the case of ubuntu being able to read vista, but vista not able to read ubuntu, i think i will partition my 2x 500gb hdds like this

200gb windows vista (ntfs) 40%
30gb for ubuntu (ext4) (just for ubuntu) 6%
18gb home (ext4) (for ubuntu only files) 3.6%
2gb swap (ext4) 0.4%
250gb utorrent (ntfs) 50%

also i have 4 gb of ram, will a 2gb swap partition be enough, or should i go gig for gig as the swap (4gb swap)?

i know it sounds a bit messy, but it kinda makes sense to me.

what would other people do in my case, but that sounds good to me.

---

### Post by spandon on 2009-03-23
Hi Noelswatson,
Sorry for the delay in replying.
from my experience with Ubuntu what has worked for me would be the the following, but your conclusion may also work, but I certainly would not allocate more than 80 gb for Vista.
If I were to partitioning your drive, I would do it this way:
80  gb  Vista          NTFS
120 gb  data           NTFS
250 gb  Utorrent       NTFS
30  gb  Ubuntu         Ext3
2   gb  swap           Swap
18  gb  Ubuntu files   Ext3 (have never found the requirement for this).

I have up to 4 gb in my machines, but have only ever used more than max of 2 gb for swap, perhaps a more techie Ubuntu person can advise on this one?
To clear up what I stated earlier, Windows (up to ver7)can't see or recognize a Linux drive, but  Linux (Ubuntu can see/write to a fat, fat32. or Ntfs drive/partition.
Hope this helps with your forthcoming installation?
have fun
don :D

---

### Post by joelswatson on 2009-03-23
hi spandon, thanks for your reply, i dont know if i have already said this, but i have 2 500gb hard drives in my laptop, so i wouldnt need a 120gb data drive, cause i already have a 500gb storage drive.
i was wondering that did you mean by "18  gb  Ubuntu files   Ext3 (have never found the requirement for this)"? what i mean for the 18gb ubuntu files, is for storing files so stuff like linux installers for games and apps, etc.

thanks
joel 

> **spandon said:**
> Hi Noelswatson,
Sorry for the delay in replying.
from my experience with Ubuntu what has worked for me would be the the following, but your conclusion may also work, but I certainly would not allocate more than 80 gb for Vista.
If I were to partitioning your drive, I would do it this way:
80  gb  Vista          NTFS
120 gb  data           NTFS
250 gb  Utorrent       NTFS
30  gb  Ubuntu         Ext3
2   gb  swap           Swap
18  gb  Ubuntu files   Ext3 (have never found the requirement for this).

I have up to 4 gb in my machines, but have only ever used more than max of 2 gb for swap, perhaps a more techie Ubuntu person can advise on this one?
To clear up what I stated earlier, Windows (up to ver7)can't see or recognize a Linux drive, but  Linux (Ubuntu can see/write to a fat, fat32. or Ntfs drive/partition.
Hope this helps with your forthcoming installation?
have fun
don :D

---

### Post by spandon on 2009-03-23
Hi joelswatson,
Why I sugested the data drive of 120gb is that I find that windows gets very slow after awhile if the partition is over large, so I adjusted your original figure of 200gb down to 80gb, so if you do not wish for the data drive ( could have called it "Misc" instead of data), then another idea could be to extend the Utorrent partition to 370gb.
The 18gb partition for Linux files etc, never had a call for this type of partition - so I cannot recommend from experience as to where to place the partition in relation to Ubuntu and swap drive.
You requested advise, I gave from what I know works, there are other users who have done things differently and still got the system weorking OK, so at the end of the day the ball is in your court how you partition your disk to suit YOUR requirements.
Hope all goes well
Don

---

### Post by joelswatson on 2009-03-23
can someone explain in plain english what the following means?

/       Root file system. Should just contain /bin, /sbin, /dev,
        /root,
        /lib, and /etc.
/usr    Programmes and source code.
/var    Variable data, such as spools, man pages, news and mail
        queues, database data.
/boot   Boot kernels.
/home   User data and "stuff".
/tmp    Temporary file locations

---

### Post by ambdeep on 2009-03-23
never give windows more than 20 gb of space....it reduces the speed of the os.......insted give it lesser space and create a new drive and install all softwre there....i know it sounds crazy but it is a fact........in case of linux...100gb sounds good as you cannot install software on any other drive(that is if you are going to install so many software).Also 2gb of swap should be enough unless you have more physical memory and choose to run VERY heavy apps.



> can someone explain in plain english what the following means?

/ Root file system. Should just contain /bin, /sbin, /dev,
/root,
/lib, and /etc.
/usr Programmes and source code.
/var Variable data, such as spools, man pages, news and mail
queues, database data.
/boot Boot kernels.
/home User data and "stuff".
/tmp Temporary file locations
that would depend on what you need them for...a piece of advice stay away from those folders....they are like the windows folder in c drive.

---

### Post by joelswatson on 2009-03-23
> **ambdeep said:**
> never give windows more than 20 gb of space....it reduces the speed of the os.......insted give it lesser space and create a new drive and install all softwre there....i know it sounds crazy but it is a fact........in case of linux...100gb sounds good as you cannot install software on any other drive(that is if you are going to install so many software).Also 2gb of swap should be enough unless you have more physical memory and choose to run VERY heavy apps.




that would depend on what you need them for...a piece of advice stay away from those folders....they are like the windows folder in c drive.


heya, the reason i going to have a 120gb windows dir, is cause my current windows dir is about 107gb,
the reason i asked about those differnet is cause i have been goolging, lol, and i remembered something from red hat years ago.
so when i install ubuntu which partition do i install it to? is it the " / " partition? and what do i call the partition which i want to store my personal ubuntu files on? is that " /home or /usr "?

---

