---
title: "Problem mounting Ipod Touch"
date: 2008-05-18
forum: Hardware
---

### Post by Nate9009 on 2008-05-18
Hi everyone!  I'm trying to find a effective way to sync my jailbroken Ipod Touch (version 1.1.4) in Ubuntu.  I have installed the ipod-convenience package and all the necessary dependencies, as well as installed the appropriate programs on my Ipod. When I run the mount command this is what I get : ```
 me@computer:~$ ipod-touch-mount
ssh_exchange_identification: Connection closed by remote host
read: Connection reset by peer
```

I have given my Ipod a static IP of 192.168.1.107 and have installed ssh.  Does anyone have any idea as to what is going wrong?  I'm completely baffled.

---

### Post by Nate9009 on 2008-05-18
Also, has anyone tried using SSH to move files from a Linux computer?  I looked into and saw that the music folder was changed when I originally synced my Ipod with Itunes.  The song names where changed and arranged in different folders, I don't know if simply moving mp3's to the Music folder would work. :(

EDIT:

Just tried to connect to my Ipod via SSH and got this error message. 

"Could not open location 'ssh://root@192.168.1.107/'  

I/O error"

---

### Post by Nate9009 on 2008-05-19
No ideas from anyone...?

---

### Post by Nate9009 on 2008-05-20
Here is the output I got after trying to manually ssh into my Ipod.

```
<me>@<my computer:~$ ssh 192.168.1.107 -l root -v
OpenSSH_4.6p1 Debian-5ubuntu0.5, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.107 [192.168.1.107] port 22.
debug1: Connection established.
debug1: identity file /home/nathan/.ssh/identity type -1
debug1: identity file /home/nathan/.ssh/id_rsa type 1
debug1: identity file /home/nathan/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
<me>@<my computer>:~$
```

---

### Post by MaindotC on 2008-05-20
I'm confused as to why you are trying to use ssh.  SSH is for connecting to a server remotely - like across a networked medium.  Does your Ipod connect to your computer via CATV cable to the Ethernet port?  I thought they plug in via a USB cable?

Edit: nm - I googled and I see it now.  The Touch must have some sort of Linux-based distribution on it.  I'm googling an answer for you.

---

### Post by Nate9009 on 2008-05-21
I just nmapped the Ipod to ensure that the ssh service was indeed running. (Which it is, thankfully).  Google has turned up nothing useful as of yet, although I am still searching for an answer.

Nmap info : ```
PORT   STATE SERVICE
22/tcp open  ssh
```


At least somthing is working :-D

---

### Post by badfish591 on 2008-05-21
well i have never tried this(it's on my list though) but from all the information that i have read, the very first time that you try the ipod-touch-mount command you have to have your ipod touch connected via usb. you have to do this "as the USB connection is used to generate a hash required by the iTunes Database on your ipod"..... or so i've read. maybe this step was forgotten??

---

### Post by Nate9009 on 2008-05-22
It's always been connected via the USB cable, but it still doesn't mount properly.

If this has any meaning/significance at all, when ever I plug it into the computer a window pops up saying a camera has been detected and it wants to import photos, although the ipod hasn't been mounted...?  (at least the computer can recognize something is there)

---

### Post by Nate9009 on 2008-05-22
Also, the output of the mount command is different than it has been in the past.  This is what it has been saying now... : ```
iPod is not responding to pings at 192.168.1.107.
Please set the environment variable IGNOREPING if you want to ignore this.
```

I rechecked the ipod-convenience package, and its still set up with the same static IP the ipod has always had.

---

### Post by manuelzs on 2008-05-27
was anyone able to solve this problem. if so please help me...:)

---

### Post by jjdarling on 2008-06-03
I seem to be having the same problem with my iphone. Any advice would really help.

---

### Post by Nate9009 on 2008-06-07
I think I'm just about out of ideas, I don't have a clue as to why it won't mount.  All my other mp3 player mounted perfectly. This ipod just doesn't seem to want to cooperate.

---

### Post by mrsudo on 2008-06-17
any luck as of now??  i have no clue what i could be doing wrong.... same problem as you!

---

### Post by questionaire on 2008-06-19
hardy heron
jailbroken touch 1.1.4
all necessary downloads
amarok

I'm also getting the no ping response error.  

SOS!

---

### Post by tesna on 2008-06-19
have u install openssh server from installer on the ipod? can u ping the ipod from the terminal? I think so far U can ping and ssh to the ipod the mounting will works. 

I can connect with my ipod touch using wifi without connecting the usb cable. Thanks to you also, I figured out how to mount ipod touch and display the songs in rythymbox music player. (I haven't tried to sync it though). Wohooo say goodbye to itunes and windows!! But I wonder the speed of syncing over wireless.

```

tesna@zorg:~$ ipod-touch-mount 
root@10.1.0.200's password: 
root@10.1.0.200's password: 
You don't have a Firewire GUID, so we will create one
[sudo] password for tesna: 
tesna@zorg:~$ cd /media/
tesna@zorg:/media$ ls
cdrom  cdrom0  ipod
tesna@zorg:/media$ cd ipod/
tesna@zorg:/media/ipod$ ls
com.apple.itunes.lock_sync  iGoSGF     iPod_Control  iTunes_Control  TTR
DCIM                        Installer  iTunes        ROMs

```

---

### Post by Nate9009 on 2008-06-21
> **tesna said:**
> have u install openssh server from installer on the ipod? can u ping the ipod from the terminal? I think so far U can ping and ssh to the ipod the mounting will works. 

I can connect with my ipod touch using wifi without connecting the usb cable. Thanks to you also, I figured out how to mount ipod touch and display the songs in rythymbox music player. (I haven't tried to sync it though). Wohooo say goodbye to itunes and windows!! But I wonder the speed of syncing over wireless.

```

tesna@zorg:~$ ipod-touch-mount 
root@10.1.0.200's password: 
root@10.1.0.200's password: 
You don't have a Firewire GUID, so we will create one
[sudo] password for tesna: 
tesna@zorg:~$ cd /media/
tesna@zorg:/media$ ls
cdrom  cdrom0  ipod
tesna@zorg:/media$ cd ipod/
tesna@zorg:/media/ipod$ ls
com.apple.itunes.lock_sync  iGoSGF     iPod_Control  iTunes_Control  TTR
DCIM                        Installer  iTunes        ROMs

```

This is the *ideal* setup I wish I could have.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Lately there was this bug with ssl, so... They changed all certificates and authenticities made with bad old crackable version. Removing old authorization files fixes these issues. Ssh has its autorisations in ~/.ssh/knownhosts and renaming or removing knownhosts should fix ssh authorization issues. Maybe it has some impact on ipod's mounting. I have really no other clue. Also coping files with "scp file user@host:/<path>/file" opens new ssh session just for file transfer, but if ssl is busted then you shouldn't be able to ssh or scp.

I hope it will help somehow. Good luck!

---

### Post by questionaire on 2008-06-21
I am very unfamiliar with the linux/ubuntu os, so if anyone overcomes the ping problem could you please post a detailed description of how you did it?

I really just want to get rid of windows/itunes...

---

### Post by Nate9009 on 2008-06-27
> **questionaire said:**
> I am very unfamiliar with the linux/ubuntu os, so if anyone overcomes the ping problem could you please post a detailed description of how you did it?

I really just want to get rid of windows/itunes...


Ditto. :)

---

### Post by Nate9009 on 2008-06-27
Nmap is showing that ssh is indeed running on my Ipod.  :confused:

```
Not shown: 1713 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
```

---

### Post by tesna on 2008-06-28
You can follow most of the instructions in [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Rhythm box works fine with it. Just issue the commands, run rhythmbox, my ipod is there! Make sure that when first connecting to the ipod/iphone you got usb cable plugged to your computer, or the ipod will refuse to read the library. 

-First thing is, set up static IP on the ipod to make things easier. 
-Then try to ping with the ipod IP, if you got a reply then try to ssh login to the iphone manually by typing 
```
ssh <your ipod IP>
```
(first time connection can take about 1 minute, I think it has something to do with key generation perhaps?). 
-If successfull you can try to mount your iphone/ipod touch, but you need to plug the usb cable to your computer during initial connection. It should works if you can ping and SSH to your ipod manually.

---

### Post by goten60 on 2008-08-29
Anyone could solve this problem? I have the same issue, and I followed everything in [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
I can use ssh in putty but not in a console.

---

