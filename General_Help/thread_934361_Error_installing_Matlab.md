---
title: "Error installing Matlab"
date: 2008-09-30
forum: General Help
---

### Post by athrpf on 2008-09-30
Hey,

I am a new linux convert. Up until now everything has worked out fine after a little research in the forums, but now I have encountered a problem that I cannot find a solution for. 

I am trying to install the linux version of MatLab R2008a on my hardy ubuntu from an ISO. I have no problem mounting the ISO, setting up a directory for matlab (I use /usr/local/matlab/ ), copying the license.dat file and starting the installation via

sudo sh ./install 

The installation routine then starts, gets all the licensing information, but whenever it tries to actually install the files I get the following messages:

Error installing installer files.

Error installing MATLAB for Linux (x86)

Error installing MATLAB for All

Quitting the installation, the program prints out:

Error installing installer files.

Error installing MATLAB for Linux (x86)

Error installing MATLAB for All

-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        [prod6784.cmp]
          End-of-central-directory signature not found.  Either this file is not
          a zipfile, or it constitutes one disk of a multi-part archive.  In the
          latter case the central directory and zipfile comment will be found on
          the last disk(s) of this archive.
        unzip:  cannot find zipfile directory in one of prod6784.cmp or
                prod6784.cmp.zip, and cannot find prod6784.cmp.ZIP, period.
        [/usr/local/matlab/prod16861.cmp]
          End-of-central-directory signature not found.  Either this file is not
          a zipfile, or it constitutes one disk of a multi-part archive.  In the
          latter case the central directory and zipfile comment will be found on
          the last disk(s) of this archive.
        unzip:  cannot find zipfile directory in one of /usr/local/matlab/prod16861.cmp or
                /usr/local/matlab/prod16861.cmp.zip, and cannot find /usr/local/matlab/prod16861.cmp.ZIP, period.
        [/usr/local/matlab/prod16866.cmp]
          End-of-central-directory signature not found.  Either this file is not
          a zipfile, or it constitutes one disk of a multi-part archive.  In the
          latter case the central directory and zipfile comment will be found on
          the last disk(s) of this archive.
        unzip:  cannot find zipfile directory in one of /usr/local/matlab/prod16866.cmp or
                /usr/local/matlab/prod16866.cmp.zip, and cannot find /usr/local/matlab/prod16866.cmp.ZIP, period.

-------------------------------------------------------------------


Some people in other threads said Matlab installs might fail due to permissions, so I tried, as recommended, copying the whole disk in a folder and the setting all permissions to max, which didn't help at all 

Can anyone please help me with this? I am afraid I cannot use any alternative like octave.

Thanks alot!

---

### Post by alberto ferreira on 2008-09-30
Try installing the program in your home folder, although you are running the install as sudo it could be that the routines inside the installer don't have permission to write.

Try it then say something

---

### Post by athrpf on 2008-09-30
No luck - same error

---

### Post by alberto ferreira on 2008-10-01
Look at this thread:
[http://ubuntuforums.org/showthread.php?t=781078](http://ubuntuforums.org/showthread.php?t=781078)

I tried it however I hope it helps you out because I have never installed that program

I read a bit of the article and there's no explanation to install java. If you don't have java run this command:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts



Hope it works

---

### Post by athrpf on 2008-10-01
Thanks for helping out, alberto

Installing Java was definitely a good idea, I didn't think of it, but that still wasn't the problem - I get the same error as in the initial post. 

Most of the posts on other threads are about getting matlab to work after installing it, but I can't even get it installed! I am clueless. I tried google on the .cmp files, but there was noone at all having a similar problem to mine. I think it must have something to do with my system settings, or maybe another package besides java missing that I need for installing this. Anyone any idea on that?

---

### Post by alberto ferreira on 2008-10-02
Think I found the solution, go to the end of this thread, don't expect much though, it might not be enough, but, go to the last topic of that thread:
[http://backports.ubuntuforums.com/showthread.php?t=906667](http://backports.ubuntuforums.com/showthread.php?t=906667)

I think that you can't install because you are only running the install as root, however you need to mount the disk with every root permission and in that forum you'll find how to do that, hopefully.

I hope it works this time :) and then tell us how it went

---

### Post by athrpf on 2008-10-03
Thanks alberto. 

I tried that, but unfortunately, it didn't work either. 

The new thing to that solution was including the exec option to the mount command, which seems to be aiming at the permissions issue, which I don't think is the case since I copied the whole disk to my computer and gave everyone chmod 777 permission for each file. 

From the error I get I rather think that it has something to do with a packet I am missing, like a certain version of unzip or something of the likes. I cannot find anything on the web regarding those prod# filenames and there is few on the End-of-file-error.

Does anyone know if there is maybe a way to install matlab manually, so I can do it step by step and figure out where exactly the stuff goes wrong?

---

### Post by alberto ferreira on 2008-10-03
what i meant to say in the last post is that you should try installing it directly from the cd.
Just be careful because (sudo mount cdrom or whatever) is said to not be able to mount the contents of this specific cd, at least I read in a thread that you have to manually mount the cd editing the fstab file.


Also, in here your problem is mentioned (install itself cannot access one of the files due to it's permissions thus being unable to install):
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)


------------
I'm sorry but I've run out of ideas, hope someone else can help you out.

Good luck

---

