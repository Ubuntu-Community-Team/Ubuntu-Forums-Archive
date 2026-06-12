---
title: "Using WINE and Mounting ISO's"
date: 2008-09-02
forum: General Help
---

### Post by neko-master on 2008-09-02
Ok, now that I have my other hard disks working now, now I have another problem, how do I open up WINE so I can open up Windows Programs or something? Or is there a way so that when I open the .exe of the program WINE steps in and Emulates Windows (like its suppose to).

Also, I would like to konw how you mount iso'sm Ive tried the command
```

mount -o loop -t iso9660 file.iso /mnt/test

```
but when ever I set it to where my iso is it says that it cant find it

no such file or directory or something like that, if theres a Program Out there that can mount isos like Daemon Tools or Alcohol 120% (or 52%) then plz tell me and link. I rlly wanna play my games!!!

---

### Post by joenix on 2008-09-02
The command you mention should work. Make sure to run it as root (sudo). Can you post the output of the command?

---

### Post by S.A.A on 2008-09-02
1- To use wine just double-click your program (like in windows), this should work..

2- I use this program to mount iso's:
  
   sudo apt-get install gmountiso

---

### Post by yjwong on 2008-09-02
When mounting ISOs, make sure the *mount point* exists. The mount point is the folder/directory at which the ISO can be accessed. In your command, the directory "/mnt/test" should exist prior to running that command. Which means, you'll have to do this:

```
sudo mkdir /mnt/test
mount -t iso9660 <iso file> /mnt/test -o loop
```

Good day.

---

### Post by viktor4124 on 2008-09-20
I just posted a answer that may help you in an other thread.
I'll repost it here:


Hey,

I had a similar problem recently, which was solved the following way. Let's hope it will work for you too:

Wine manages a directory $HOME/.wine/dosdevices where symbolic links for mapping Windows-drives to locations in your filesystem are held. Just enter the directory in a terminal and examine it yourself (ls -l command).

There are links that have one colon (e.g. E:) which are refering to the mapping directory in your filesystem, and there drive-letters followed by two colons, which are used to point to a actual physical device (e.g. D: -> /dev/cdrom).
So I not only tried to loop-mount my iso and bind it to drive E:, but also to bind the "physical drive" E:: to the iso itself, so that the windows software may find the cd's serial and stuff. And guess what, it worked ;-) at least for me

```

$ sudo mount -o loop /home/viktor/image.iso /mnt/iso
$ cd $HOME/.wine/dosdevices
$ ln -s /mnt/iso e:
$ ln -s /home/viktor/image.iso e::
$ wine explorer

```

unfortunately I somehow couldn't start the software with
```

wine /mnt/iso/setup.exe

```
I had' to use wine explorer, navigate to drive E: and start setup.exe by double-clicking it.

good luck.

---

### Post by mb_webguy on 2008-09-20
In reference to the mount command...  The command you posted should work assuming the mount point (/mnt/test) exists and you are in the directory in which the iso file is located.  A better option would be to use the full path of the iso file, as in the following command.```
mount -o loop -t iso9660 /path/to/file.iso /mnt/test
```
Of course, "/path/to/" should be replaced with the actual path to the file.

However, I second the suggestion of gmount-iso.  It simplifies the process greatly.

---

### Post by Ripfox on 2008-09-20
I always use 

> cd /media/cdrom0

> user@ubuntu:/media/cdrom0$ wine setup.exe (or whatever)

Also, I believe the command "wine eject" comes in handy when switching media.

Of course this is if the cd is in the drive and not an iso file :)

---

