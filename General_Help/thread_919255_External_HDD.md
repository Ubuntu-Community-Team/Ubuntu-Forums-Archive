---
title: "External HDD"
date: 2008-09-13
forum: General Help
---

### Post by metalmaniac248 on 2008-09-13
my current machine only has a 80GB HDD, And i have recently filled it up and this has of course posed some problems for me 


i am planing on getting a 500 GB External HDD to give me some space,


my internal HDD, has  Ubuntu (which is my main OS) Vista (i only keep that for iTunes) and of course all my files, 


when i add this external HDD, what is the best of way of incorporating it, 


if possible i would like to have set up so that its like iv just got a 580GB HDD



thanks

---

### Post by mb_webguy on 2008-09-13
The external drive should be automatically mounted under /media when you plug it in.  You can then make symlinks to the drive or folders on the drive from your home directory if you want.

---

### Post by Metaleks on 2008-09-13
What kind of external HD will you be getting? If you get one of those USB hard drives the performance from it won't be as good as the 80gb you currently own. If you really want more space *just* for your computer, then get a second hard drive (if you have the room for it). If you want to carry your data around and like the feeling of portability (and who doesn't?) then get the USB hard drive (they're pretty cheap nowadays, I got my 500gb western digital hard drive for about $130.)

As for making it act like one drive? Not possible, I think. They'll be treated like partitions. There is no way to "link" two different hard drives and make a system believe that they are just two parts of a whole.

A word of avice. Before you buy the external hard drive, do a little searching to see if people have had luck with it on Ubuntu. Some external hard drives have problems with Ubuntu and doing something like this beforehand makes you a smart consumer ^_^

Hope this helps! :)

---

### Post by metalmaniac248 on 2008-09-13
thanks so would you say that i'm best to just but all my music, picture, document files,

in the external and then just have the OS's on the internal,


PS. Is firewire a better option do you think? Is it faster?




Also i cant upgrade the internal because im on a laptop

---

### Post by mb_webguy on 2008-09-13
> **metalmaniac248 said:**
> Also i cant upgrade the internal because im on a laptop

Well, actually you could buy a larger hd for your laptop and an enclosure that accepts a slim hd, then clone your current hd onto the larger hd and swap them out.  Then you'll have a larger hd in your laptop, and an 80GB external drive to use for whatever you want.

---

### Post by metalmaniac248 on 2008-09-13
hmmm,



is that a big job,


is it risky?



Also while im here, how do u get that comment at the end of your message?

---

### Post by mb_webguy on 2008-09-13
It's not too bad.  There are various applications available, with Partimage being the first to come to mind.  Though on second thought I don't know that I'd actually clone the drive.  I think I'd just partition it similarly to your current installation, and then copy everything over.  That allows you to resize your partitions to better suit the fact that you have a larger drive while keeping everything intact.  And actually swapping out the drives once you have everything copied over is easy.

And the bit at the bottom of the post is a signature, which you can set by clicking "User CP" at the top of the screen, and then "Edit Signature" on the left.

---

### Post by metalmaniac248 on 2008-09-14
thanks for the advice

---

### Post by metalmaniac248 on 2008-10-03
another question, i have settled on a external hard drive, 

what should i format it too, and how would i go about doing it?

as i have said previously i will be using it for both vista and ubuntu, 

i have heard fat32 is the best, but i have also heard people having issues with that, i'v also heard ext3 suggested.



thanks

---

### Post by Kain000 on 2008-10-03
> **metalmaniac248 said:**
> another question, i have settled on a external hard drive, 

what should i format it too, and how would i go about doing it?

as i have said previously i will be using it for both vista and ubuntu, 

i have heard fat32 is the best, but i have also heard people having issues with that, i'v also heard ext3 suggested.



thanks

Fat32 file system is primarley a windows file system, where as ext3 is used in a linux environment.  

Laptop drives are pretty simple, usually they are just under a pannel on the side of your laptop and can be removed without much effort.  

An external HDD however large will preform alot slower than would a sata or IDE inter phase.   In My opnion an internal HDD would be alot better, one because your laptop is portable, and as such an external Hdd would just be more in your bag.  Check out Ebay, there is alot out there for great prices.  I recently ran into the exact same problem with my server's 40 GB drive, that I replaced with a new 400GB drive for arround $70.

Of course if you do get a used or new drive from ebay, do remember to completely format it, I suggest using a program called Deriks boot and nuke.

---

### Post by scouser73 on 2008-10-03
Hi, I would suggest that you format it to reiserFS.

---

