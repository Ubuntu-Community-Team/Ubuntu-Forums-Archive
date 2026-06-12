---
title: "QUESTION: Recoving information from windows using an Ubuntu cd"
date: 2008-09-30
forum: General Help
---

### Post by MandyLea83 on 2008-09-30
I have a problem. I connected my personal laptop at work the other day and the network tried to reimage it with our work image. Now, I'm going to call IT Support in my company but I have a feeling they are going to say I'm screwed and shouldn't have connected my computer.

I know I can just buy a windows OS disk (or install Linux) and get my computer working again that way. I want to try and recover the information from my computer though.

I thought I could try taking the hard drive out of my laptop and putting it into an external hard drive case and getting the information that way, but I'm not sure it will work. And I'm not experienced in taking apart laptops. 

I read on Digg a while ago something about being able to access your information from windows using an Ubuntu disk. 

Does anyone know how to do this? Or does anyone have any ideas about how I can recover the information on my laptop and not just reformat?

Thanks for the help. I look forward to hearing the responses. Any help would be of use right now. 


Amanda

---

### Post by Elfy on 2008-09-30
If you download a linux livecd you should then be able to mount your drive and recover the information from it.

There are many different livecds out there - this is the ubuntu forum, but I'd imagine you'd get help with many of them.

The ubuntu livecd is available from here [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

---

### Post by _sAm_ on 2008-09-30
When you have Ubuntu livecd running;

Open a terminal from Applications > Accessories and install NTFS configuration tool with:
*sudo apt-get install  ntfs-config*

Go to Application > System tools and open NTFS configuration Tool, and mount the drives/partitions that you want. The drives will pop up as icons on your desktop(and you will find them under Places in the toppanel).

Copy the data that you want to an external harddrive, usbkey, network storage or burn them on a cd/dvdrom.

If cant get some of the data you can check out the program testdisk and PhotoRec,  witch you also can run from the Ubuntu livecd: 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Good luck!

---

### Post by 3rdalbum on 2008-09-30
I'd recommend using an Ubuntu live CD to do this, but I just wanted to correct something that you said. If you removed your hard drive and put it into a drive enclosure, you will be able to mount it on another computer. Definitely.

---

