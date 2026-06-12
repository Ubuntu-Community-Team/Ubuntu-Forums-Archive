---
title: "Input/Output error with a USB hard drive"
date: 2010-07-13
forum: Hardware
---

### Post by razorj7 on 2010-07-13
Hello everyone,

So I have the following:

HP mini 2140
Ubuntu 10.04 Netbook Edition
Western Digital TB USB drive

So this is what happened:
I have a ton of movies on my TB drive and I have never had any problems before. This morning I connected the drive to my girlfriend's Macbook Pro (the new one) and played a movie off my my TB drive through it. After we finished watching the movie, I connected it back to my Netbook to place some files on it. However, when I went to access my Movies in their folder, the folder is empty. My movies are in Videos/Movies which holds up to 100+ movies. But now the folder is empty but when I plug the drive into my girlfriend's Macbook, the files in Videos/Movies show up. Why do they show up on her Mac and not my Netbook?

Also, on my girlfriend's Mac, it will not let me CUT the movies or delete them from the drive.

Please help, I want to be able to access my movies on my drive.

Thanks in advance

Also, when I tried to use the "cd" and "ls" in the Terminal to access the files I get this error in the Videos/Movies folder: 
ls: reading directory .: Input/output error

I can access and change everything else on the drive except for that folder

---

### Post by Peterkorse12 on 2010-07-14
I think you have a virus in your USB drive. So you should scan it with any best antivirus software and then make use of your USB hard drive. Some kind of virus has infected your files on your drive and I think you got them from your girlfriend's MAC. The only solution to solve your Input/Output Error is just scan out your drive make it free from the virus.

---

### Post by WSGrant on 2010-10-30
I'm having the same issue with a Seagate 1TB USB drive and Maverick server. Works fine for a day, sometimes two, then starts giving the same input/output error. Tried refreshing fstab with no luck. Only thing that gets it working again is to restart the system; then it works for another day or two. 

The only services running are mediatomb and deluge which are reading and writing to the USB drive.

---

### Post by Nabo00o on 2011-02-24
Hi people I really need your help, I got exactly the same problem, at least almost.
I have a dual boot system, Ubuntu 10.04/Vista, but I have only used Ubuntu for the last year or so.

This problem just happened today. I have a 1 TB hdd with lots of backups in it, and all works fine, expect for my music ;(
First I used the standard filesystem nautilus but it crashed it all the time, then I used ls in the commandline, which got me the input/output error on every folder inside (I stopped it because it took so long).

I can't believe that the music is infected somehow, and how can a harddrive have a virus anyway!? I thought it only existed as part of the main system or something....
I also thought Linux was basically virus free, and that stuff from mac or windows wouldn't jump over....
So if its in the music, how do I get rid of it? Is it even possible to delete it?

Thanks in advance 
Julian

---

### Post by Nabo00o on 2011-02-24
I'm using vista now to search for errors on the hdd and correct them if possible (since the filesystem is NTFS), I got that advice somewhere else. Hopefully it will solve the problem.

---

