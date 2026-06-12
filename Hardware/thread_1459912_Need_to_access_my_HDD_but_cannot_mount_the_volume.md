---
title: "Need to access my HDD but cannot mount the volume"
date: 2010-04-22
forum: Hardware
---

### Post by argento on 2010-04-22
Hello, this is my first post here so I'm sort of a noob. Anyway, my windows 7 just recently crashed on my laptop and will not let me start up the OS. So I'm currently using the live boot from a usb thumb drive I made a while back so i can retrieve my files and reinstall Windows. Now, I've searched for this same problem, but I get things that are similar, but not the same. I'm not too sure on how to explain. I took a screenshot of what message I get when I try to open my hard drive. Hopefully this helps. I'm not too sure what it all means.



 
[IMG]http://i234.photobucket.com/albums/ee228/Sonicboom53/Screenshot.png[/IMG]

---

### Post by bacchusmarsh on 2010-04-22
Try seeing the device in TestDisk (open terminal and type: sudo apt-get install testdisk, then type: sudo testdisk , and expand the terminal window to run), where you can test the disk's integrity. some times getting the disk recognised in such a program is enough to then be able to mount it from the desktop.

Also, if you can easily, try taking the disk out and usb mount the disk on a windows computer. Then be sure to safely remove it. This has worked for me in the past, with disks that won't mount ...

...but then i am pretty new to all this too, sorry i can't offer much more than that.

---

### Post by argento on 2010-04-22
So, when you say to expand the window to run, what exactly do you mean?

---

### Post by bacchusmarsh on 2010-04-22
when you open your terminal (applications/accessories/terminal) and run testdisk, it will not work unless you are logged in as root. ie. type "sudo" before typing testdisk and type in your password (although if you are running off usb live then you probably won't have a password), nor will it run testdisk in the small terminal window, it will expect you to expand the window by pressing the little button with the square in the top right corner of the window (same as in Microsoft Windows).

---

