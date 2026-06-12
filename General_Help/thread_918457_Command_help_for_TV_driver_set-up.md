---
title: "Command help for TV driver set-up"
date: 2008-09-12
forum: General Help
---

### Post by Knot_Sharpe on 2008-09-12
Hello all, 
I'm a relative Ubuntu newbie, but was trying to follow a guide, copy&pasting commands to get drivers working for a Hauppauge TV tuner card, then getting Mythubuntu working on my system.

Here are the instructions I'm following:

Then, in a terminal, do sudo su to become the root user. Install the necessary packages to build em28xx kernel modules:

aptitude install mercurial build-essential linux-source

Download firmware version 4, necessary for USB tuner cards:

[COLOR="Blue"]wget -q [http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz)
&#8618;-O /usr/local/src/firmware_v4.tgz
[/COLOR]
Unpack the firmware files into /lib/firmware:

[COLOR="Red"]tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware[/COLOR]

Grab the latest copy of the V4L DVB source code from mcentral.de:

[COLOR="YellowGreen"]cd /usr/local/src
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)

Compile the V4L DVB drivers:

cd /usr/local/src/v4l-dvb-kernel
make
make install[/COLOR]

And, finally, reboot the system.
**************************************

I have a problem getting the command line in blue to work.  What am I getting wrong?  The first part of the command gets the file, I think. Then there is a funny arrow which I have tried to use (copy/paste) and tried to take out, neither of which worked.  I don't know what -O command is, but I think its telling me to create a path/directory for the file.

Next, I'd like to ask if the commands in red make sense ... I assume this place the required file in the correct directory.

Finally, I assume using the commands in green, that I will be able to retreive and install the mentioned files into the correct directories and be good to go.

I sure would appreciate it if anyone can confirm all of this!Right now, I'm stuck on the "blue" command lines.  I think the get operation worked, but I have no idea about the -O line. 

Please help if U can, many thanks in advance ...

---

### Post by tgm4883 on 2008-09-12
> **Knot_Sharpe said:**
> Hello all, 
I'm a relative Ubuntu newbie, but was trying to follow a guide, copy&pasting commands to get drivers working for a Hauppauge TV tuner card, then getting Mythubuntu working on my system.

Here are the instructions I'm following:

Then, in a terminal, do sudo su to become the root user. Install the necessary packages to build em28xx kernel modules:

aptitude install mercurial build-essential linux-source

Download firmware version 4, necessary for USB tuner cards:

[COLOR="Blue"]wget -q [http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz)
&#8618;-O /usr/local/src/firmware_v4.tgz
[/COLOR]
Unpack the firmware files into /lib/firmware:

[COLOR="Red"]tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware[/COLOR]

Grab the latest copy of the V4L DVB source code from mcentral.de:

[COLOR="YellowGreen"]cd /usr/local/src
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)

Compile the V4L DVB drivers:

cd /usr/local/src/v4l-dvb-kernel
make
make install[/COLOR]

And, finally, reboot the system.
**************************************

I have a problem getting the command line in blue to work.  What am I getting wrong?  The first part of the command gets the file, I think. Then there is a funny arrow which I have tried to use (copy/paste) and tried to take out, neither of which worked.  I don't know what -O command is, but I think its telling me to create a path/directory for the file.

Next, I'd like to ask if the commands in red make sense ... I assume this place the required file in the correct directory.

Finally, I assume using the commands in green, that I will be able to retreive and install the mentioned files into the correct directories and be good to go.

I sure would appreciate it if anyone can confirm all of this!Right now, I'm stuck on the "blue" command lines.  I think the get operation worked, but I have no idea about the -O line. 

Please help if U can, many thanks in advance ...

You should probably do that all on one line.

wget -q [http://konstantin.filtschew.de/v4l-f...irmware_v4.tgz](http://konstantin.filtschew.de/v4l-f...irmware_v4.tgz) -O /usr/local/src/firmware_v4.tgz

---

### Post by Knot_Sharpe on 2008-09-12
Thank you  ygm4883, 

I copy pasted your suggestion, but it didn't seem to work.

Does the "..." in the firmware command make a difference, should I modify the link to eliminate the "..." and just use the word "firmware"?

Thanks for your suggestions!

---

### Post by mb_webguy on 2008-09-12
> **Knot_Sharpe said:**
> Thank you  ygm4883, 

I copy pasted your suggestion, but it didn't seem to work.

Does the "..." in the firmware command make a difference, should I modify the link to eliminate the "..." and just use the word "firmware"?

Thanks for your suggestions!

You should use the actual URL, whatever it is.  The ellipsis shouldn't be there.

---

### Post by Knot_Sharpe on 2008-09-13
> **mb_webguy said:**
> You should use the actual URL, whatever it is.  The ellipsis shouldn't be there.

Thanks for the suggestion, I tried the URL as it was, but no go.  I eliminated the "arrow", but I have no idea what the "-O" command is supposed to do, can't find it in linux commands, could it be a typo?

Thanks, 

Knot_Sharpe  .... as you can tell! ~LOL~

---

### Post by mb_webguy on 2008-09-13
All wget does is download the file.  Just click on the link and download the file as you normally would, and unpack it where it's telling you.

---

### Post by Knot_Sharpe on 2008-09-13
> **mb_webguy said:**
> All wget does is download the file.  Just click on the link and download the file as you normally would, and unpack it where it's telling you.

Tried that, this is what I got back:

root@gary-ibm:/home/gary# tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
root@gary-ibm:/home/gary# 
root@gary-ibm:/home/gary# 

Any ideas??

Thanks in advance, I know this is a wonky application ...

Knot_Sharpe

---

### Post by mb_webguy on 2008-09-13
What are the permissions on the /lib/firmware directory?  You might need to be root to write to it.  If so, append "sudo" onto the beginning of that command.

---

### Post by Knot_Sharpe on 2008-09-13
> **mb_webguy said:**
> What are the permissions on the /lib/firmware directory?  You might need to be root to write to it.  If so, append "sudo" onto the beginning of that command.

Yeah, I thought I  WAS the root.  Tried twice, as root first, then as you suggested, see below:

gary@gary-ibm:~$ sudo su
[sudo] password for gary:
root@gary-ibm:/home/gary# sudo tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
root@gary-ibm:/home/gary# sudo su tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware
su: invalid option -- C
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

root@gary-ibm:/home/gary# 


***************

****, this shouldn't be so difficult, should it?
Going back to the original instructions, do the commands look reasonable?
Do all the parts seem standard?  I have no inkling what the -O command is...

Close to bagging the whole thing, seems like a clusterfuck to me ...

I apppreciate your efforts to help, though!  Kindest regards,

Knot_Sharpe

---

### Post by mb_webguy on 2008-09-13
The "-O" isn't a command, it's an option for wget.

And you're right.  You were root.  I forgot about the "sudo su" bit.  Can you open the tar.gz file using Archive Manager?

---

### Post by Knot_Sharpe on 2008-09-13
> **mb_webguy said:**
> The "-O" isn't a command, it's an option for wget.

And you're right.  You were root.  I forgot about the "sudo su" bit.  Can you open the tar.gz file using Archive Manager?

I looked in synaptic package mgr, but couldn't find it.  Can't find "Archive manager".  

This is where I get lost cause I need specific instructions to follow, sorry for being so lame.

Might be time to quit this. Original post of instructions seemed clear, my 7.10 was fully updated, I don't get it ...

I appreciate your repeated suggestions and replies, though!

If you feel this isn't going anywhere, just reply, "Good Luck"

I can try some other methods I've seen to get the driver set-up and mythTV going for Linux.  I was just hoping this guys instructions would work/be easy.

Thanks again,

Knot_Sharpe

---

### Post by mb_webguy on 2008-09-13
MythBuntu uses Xcfe, right?  So you should have the Xarchiver archive manager.  I don't know exactly where it would be in your menu, but you should be able to use it to open the archive by using Thunar (your file manager) to navigate to the directory where you downloaded the file, and either double-clicking on the file, or right-clicking on it and selecting to open it with Xarchiver.

If you don't have Xarchiver, you can install it with "sudo apt-get install xarchiver".

If you can open the file using Xarchiver, extract it to somewhere convenient, then in the terminal as root move all of those files to /lib/firmware using "sudo mv /somewhere/convenient/* /lib/firmware/", replacing /somewhere/convenient/* with the actual path to the directory where you extracted the files.

---

### Post by mb_webguy on 2008-09-13
By the way, what specific Hauppauge tuner card are you trying to install?  I found the following packages in the repository:

**xserver-xorg-video-ivtv**
> This package provides the driver for the overlay framebuffer provided
by the iTVC15 family of MPEG codecs. The iTVC15 family includes the
iTVC15 (CX24315) and iTVC16 (CX24316). These chips are commonly found
on Hauppauge's WinTV PVR-250 and PVR-350 TV capture cards.

**ivtv-utils**
> The IVTV project develops a kernel driver for Linux and a driver for
X11 for hardware based on Conexant's CX23415/CX23416 codec chip such
as the Hauppauge PVR 150/250/350/500 models and other supported hardware.

**ivtv-source**
> The IVTV project develops a kernel driver for Linux and a driver for
X11 for hardware based on Conexant's CX23415/CX23416 codec chip such
as the Hauppauge PVR 150/250/350/500 models and other supported hardware.

This package contains the module source for the ivtv-fb framebuffer
driver and the saa717x tuner driver and are compatible with kernel
version 2.6.22.  These drivers can be built from it using
module-assistant or make-kpkg.  The main ivtv driver is now merged
upstream and is available in 2.6.22 and higher.

---

### Post by Knot_Sharpe on 2008-09-13
> **mb_webguy said:**
> By the way, what specific Hauppauge tuner card are you trying to install?  I found the following packages in the repository:

**xserver-xorg-video-ivtv**


**ivtv-utils**


**ivtv-source**

Thank you I really appreciate your efforts - way beyond my expectations! 

The Huappauge card is their USB device, WinTV-HVR 950, its a USB plug-in, worked OK in my kid's laptop, but wanted to get it going  in my Ubuntu 7.10 system.  Decided on Mythbuntu, but need to get the firmware, driver stuff right to make the USB tuner card work.This is the link to the info I'm trying to follow:

[http://www.linuxjournal.com/article/10078](http://www.linuxjournal.com/article/10078)

You've really done way more than I could expect and I appreciate your efforts. I might be done for the night, will check again tomorow.  its late and there is hurricane crap going on to deal with, too,

Thanks again,

Knot_Sharpe

---

### Post by tgm4883 on 2008-09-13
> **Knot_Sharpe said:**
> Thank you I really appreciate your efforts - way beyond my expectations! 

The Huappauge card is their USB device, WinTV-HVR 950, its a USB plug-in, worked OK in my kid's laptop, but wanted to get it going  in my Ubuntu 7.10 system.  Decided on Mythbuntu, but need to get the firmware, driver stuff right to make the USB tuner card work.This is the link to the info I'm trying to follow:

[http://www.linuxjournal.com/article/10078](http://www.linuxjournal.com/article/10078)

You've really done way more than I could expect and I appreciate your efforts. I might be done for the night, will check again tomorow.  its late and there is hurricane crap going on to deal with, too,

Thanks again,

Knot_Sharpe

The link should be

```
wget -q http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz -O /usr/local/src/firmware_v4.tgz
```

---

### Post by Knot_Sharpe on 2008-09-13
> **tgm4883 said:**
> The link should be

```
wget -q http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz -O /usr/local/src/firmware_v4.tgz
```

Thank you very much tgm4883! I think I got that line right finally. The next step is now giving me problems:

"root@gary-ibm:/home/gary# tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
root@gary-ibm:/home/gary# "

I believe this should unpack the firmware files and put them into the firmware directory.  I don't understand what the gzip and tar errors are telling me or how to fix it.

Do you have any ideas??  Thanks much.

Knot_Sharpe

---

