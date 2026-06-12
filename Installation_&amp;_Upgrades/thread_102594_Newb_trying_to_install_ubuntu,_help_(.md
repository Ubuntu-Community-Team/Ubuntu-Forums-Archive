---
title: "Newb trying to install ubuntu, help :("
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by gl0be on 2005-12-12
I've decided to try dual boot ubuntu with windows 98 on my awful laptop.

--specs--
celleron 550mhz cpu
64mb ram
6gb hdd

My friend gave me a breezy disc (official) which didn't work. I had to flash the bios which took me ages. Then breezy froze during install. I read a post that said use 5.04. So i dled that and burnt it. Md5 checksum match and the cd integrity was successful. Tried to resize windows partition to 4GB froze. Went back into windows and used partition magic to do it. Started installing 5.04 again set up a new 2gb partition (Primary, begining) for ubuntu. Started to install base system all was going well until red screen at 64%. It goes red when its installing "iptables" and says at the top "Not installing to unclean target".

Ive googled it but nothing came up so it thought i might seek the answer myself. As you can tell im a complete n00b with linux. My inital plan was to boot using "server" and go thru this guide for miniram systems [http://ubuntuforums.org/showthread.php?t=42873](http://ubuntuforums.org/showthread.php?t=42873)

Please help me im so frustrated :???: :???: :???:

---

### Post by NotJustANewbie on 2005-12-12
Resizing a partition using the software from the partition you are doing it form is never a good idea.  The best thing to do is to use the partition tool helpfully given to you with the Ubuntu installer - and format the partitions from there.

---

### Post by gl0be on 2005-12-12
[QUOTE=NotJustANewbie]The best thing to do is to use the partition tool helpfully given to you with the Ubuntu installer - and format the partitions from there.[/QUOTE]

Yea that was what i intended to do but it froze on 0% every time I tried to resize the windows partition. I felt partition magic was my only option.

---

### Post by gl0be on 2005-12-12
so "Not installing to unclean target" means what exactly?:confused: 

How can I fix it?:???: 

Please help me I want ubuntu so BAD:(

---

### Post by stuporglue on 2005-12-12
> --specs--
celleron 550mhz cpu
64mb ram
6gb hdd

What I do on systems with low RAM like that is instal the Ubuntu server package from CD first. Type "server" at the CD prompt when booting, instead of just hitting enter. 

Once that's installed, log in, edit /etc/apt/sources.list, then install xubuntu-desktop. Xubuntu uses XFCE which will work much better than Gnome with your 64Mb of RAM. 

Here's what we do at stuporglue.org. 
[http://stuporglue.org/lowmem.php](http://stuporglue.org/lowmem.php)

Adding the physics.byu.edu line won't help since you won't be on BYU campus, I'm guessing. :-) Also, use whatever username and password you want. The rest should be the same. 

Getting more RAM would be ideal though. With 256, you could run Gnome very well.

---

### Post by gl0be on 2005-12-12
[QUOTE=stuporglue]What I do on systems with low RAM like that is instal the Ubuntu server package from CD first. Type "server" at the CD prompt when booting, instead of just hitting enter. 

Once that's installed[/QUOTE]

I do acctually type server in. And the probelm is I get an error 64% way through installig the base system. The error is called "Not installing to unclean target". Fun

Now will some one please help me?:(

---

### Post by simon_is_learning on 2005-12-12
Is there anything on yot disk that you must save??

Otherwise are you chossing to "Delete all" thats on your HDD when you're in partition mode??

---

### Post by gl0be on 2005-12-12
[QUOTE=simon_is_learning]are you chossing to "Delete all" thats on your HDD when you're in partition mode??[/QUOTE]

Ive created a 2gb partition for ubuntu. I want to keep windows 98.

---

### Post by NotJustANewbie on 2005-12-12
What filesystem is your 2Gb for Ubuntu? Have you made a swap area?

---

### Post by Qrk on 2005-12-12
Before resizing a windows drive be sure to run ckdisk in windows. Sometimes, if your windows drive is corrupted repartitioning fails. 

I don't know what utilities win98 has because it is fat32; but I'd try runing whatever it has. 

Another good thing is to get a live cd and run fsck on your ext3 partition for Ubuntu.

(and Like NotJustANewbie said, swap is important)

---

### Post by NotJustANewbie on 2005-12-12
When making a swap area, it should be roughly double your RAM. ;)

---

### Post by gl0be on 2005-12-12
thanks for the help guys

heres my plan, correct me if its wrong
1.Do some kind of disk check on win 98 for errors
2.Start installing ubuntu
3.Delete old ubuntu partion
4.Make a new 1.5gb partition for ubuntu?
5.Make a new 0.5gb partition for ubuntu? ( how do i make a swap partition??)
6.Hope it will install

---

### Post by NotJustANewbie on 2005-12-12
Chop your 2gb to 1.5 and 0.5 and with the 0.5 partition format it, choose swap area instead of ext3.

---

### Post by gl0be on 2005-12-12
do i partition with ubuntu or with partition magic?

---

### Post by NotJustANewbie on 2005-12-12
Ubuntu

---

### Post by gl0be on 2005-12-12
thanks ill try it out now, ill post tmoz probally its getting a bit late for me

---

### Post by NotJustANewbie on 2005-12-12
Good luck!

Just read everything that is written on your monitor and you should be okay. It is supposed to be dummy proof ;)

---

### Post by gl0be on 2005-12-13
it worked ^^ 

now im trying to figure out how to use these server commands..

---

### Post by NotJustANewbie on 2005-12-13
Good, well done and welcome to the community!

---

