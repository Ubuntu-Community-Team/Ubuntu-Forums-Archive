---
title: "WPA Supplicant and Intel 2200B/G"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by scottylans on 2005-05-26
Hi guys,... didn't want to post here as I know how much "RTFM" applies to most problems with linux however the guide's are not helping me.

Anyhow I'm following this guide specifically
[SIZE=2]http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en[/SIZE]

Which I was linked to from the bottom of this guide.
[SIZE=2]http://www.ubuntulinux.org/wiki/WPAHowto[/SIZE]



I am up to setp 7 "compile driver" and I'm getting the following error


root@laptop:/home/user/inteld/ipw2200-1.0.4 # make 

make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS=/home/user/inteld/ipw2200-1.0.4
MODVERDIR=/home/user/inteld/ipw2200-1.0.4 modules

make: *** /lib/modules/2.6.8.1-3-386/build: No such file or directory.  Stop.

make: *** [modules] Error 2
root@laptop:/home/user/inteld/ipw2200-1.0.4 #



I've tried manually making a /build and a /build/modules directory within the /2.6.8.1-3-386/ directory but this just chages the error to something else nasty.

Any idea's?

---

### Post by Stealth on 2005-05-26
hey scotty, I just recently built my drivers and stuff and got WPA working too. That error was because I didn't have the Linux source. I don't know if its jsut that, but what I did was just download the source, image, and headers for my kernel version, and it worked from there :)

---

### Post by luca_linux on 2005-05-26
You need: gcc, build-essential, kernel headers, kernel source.
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by scottylans on 2005-05-31
[QUOTE=luca_linux]You need: gcc, build-essential, kernel headers, kernel source.
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]



Luca, thank you for the help but I'm stuck.

"Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted."

I was in a console session, typed remove-old - nothing.
I tried double clicking on the file but it looks like a batch file - it's obviously a script but I don't know how to execute a script and your instructions don't say anything?

(I don't expect you to give full info but perhaps for the real newbies you could change your tutorial to say "use xyz package to execute the script"  - then they can go google the package?? )

either way i don't know how to run the script :(



EDIT:

Update,......
Someone told me to type this.
"/bin/sh remove-old.sh"

While that didn't work, I took out the .sh at the end and it SEEMS to have worked.

It didn't find some files, but this is a BRAND new 5.04 install (just re-downloaded a new iso)  so I guesss I may not have even had some of the files it's trying to delete - that does make sense.

---

### Post by scottylans on 2005-05-31
Still the same problem :(

Just a reminder.
fresh install of hoary 5.04 as of today (downloaded the iso 5 hours ago)
haven't installed anything else (don't know how anyhow)




root@laptop:/home/user/2200/ipw2200-1.0.4 # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/user/2200/ipw2200-1.0.4 MODVERDIR=/home/user/2200/ipw2200-1.0.4 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
root@laptop:/home/user/2200/ipw2200-1.0.4 #

---

### Post by luca_linux on 2005-05-31
Yes, you have to type "sudo sh script_name" in order to run a script, so in our case:
```
sudo sh remove-old
```
Have you installed the packages I suggested above with Synaptics or apt-get?

---

### Post by scottylans on 2005-05-31
[QUOTE=luca_linux]Yes, you have to type "sudo sh script_name" in order to run a script, so in our case:
```
sudo sh remove-old
```
Have you installed the packages I suggested above with Synaptics or apt-get?[/QUOTE]


I tried the synaptic package manager but couldn't find a disctinct package called "kernel source" or "kernel headers"

I do have "linux-kernel-headers" 2.5.999-test7-bk-17
I do not have the kernel source loaded - nor can I figure out a way to do it in synapic
The first 2 packages you mention however, I did install fine.


thanks so far btw.

---

### Post by luca_linux on 2005-05-31
The packages are: linux-headers and linux-tree. The version depends on your configuration.

---

### Post by scottylans on 2005-06-01
[QUOTE=luca_linux]The packages are: linux-headers and linux-tree. The version depends on your configuration.[/QUOTE]


I have downloaded both of these using Synaptic and running "make" is STILL failing with the same error.

root@laptop:/home/user/ipw2200-1.0.4 # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/user/ipw2200-1.0.4 MODVERDIR=/home/user/ipw2200-1.0.4 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2
root@laptop:/home/user/ipw2200-1.0.4 #



So  I now have
"linux-headers-2.6.10.5"  
 and
"linux-headers-2.6.10.5-386" installed (green box) in synaptic.


plus

"kernel-tree-2.4.27"
"linux-tree"  (2.6.10.7)
"linux-tree-2.6.10"
"linux-tree-2.6.11"



As for my configuration, I've already mentioned that,  I have a FRESH install of Ubuntu Hoary 5.04, downloaded only yesterday, burnt and installed with default install options.

I really think you should change your tutorial to make it easier for newbies - not trying to be offensive but outline at the start

"requirements, linux-headers / source be installed via synaptic" etc?

So what now?

---

### Post by luca_linux on 2005-06-01
Try:
```

ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-386/build

```
Then:
```

cd /usr/src/linux
sudo make oldconfig

```

---

### Post by scottylans on 2005-06-01
[QUOTE=luca_linux]Try:
```

ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-386/build

```
Then:
```

cd /usr/src/linux
sudo make oldconfig

```[/QUOTE]


I have checked this but it won't work.
I have a file called

linux-scource-2.6.10.tar.bz2
I can't figure out how to extract the contents into /usr/src/linux-source.2.6.10 :(
(I'm going to guess this ln command makes some kind of link / alias right?)

anyhow - I can't extract it - not enough access to write to that folder using the gui based extraction tool and i even gave myself root permission (I think) still let me extract it >:(

I don't know the console command to unzip a bzip file.

---

### Post by luca_linux on 2005-06-02
```

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2

```

---

### Post by sbukka on 2005-06-11
Hi!

Actually i installed ubuntu yesterday . i got the problem with WPA key. I have a high speed internet connection in my house. But i wasn't able to connect to my wireless network which WPA encryption. I came here and followed all the steps but finally i stucked at /usr/src/build directory. 
I didn't install any linux headers and  that stuff. if u know please tell me wher i can get them online. 

next 

I followed as u said in the end that two 'ln -s'  commands.
But it doesn't create any directory linux in /usr/src. 
Its some different one. ( i think its a link something)
But it is not showing .tar.bzip as an extension. So the 'sudo tar --bzip2 -xvf  ' command is also not working for me.

So help me in this

---

### Post by luca_linux on 2005-06-11
Go to System --> Administration --> Synaptic.
Sysnaptic is a GUI for apt (the package manager of Debian-based systems).
So, run it and search for the needed packages, such as linux headers, gcc, build essentials and so on.

---

