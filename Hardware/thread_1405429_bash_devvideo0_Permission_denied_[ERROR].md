---
title: "bash: /dev/video0: Permission denied [ERROR]"
date: 2010-02-12
forum: Hardware
---

### Post by Mecasickle on 2010-02-12
Hey guys,

I've been stuck on this problem for 2 days, and have benn searching all over the web for forums and a correct answer, without finding one. So here it goes:

I'm using some sample code from OpenCV, and I've succesfully compiled it, however, there seems to be a problem with my webcam when I tell the terminal to use my webcam as an input for the FAce tracking program.

Basically it's kinda of wierd, because my WEBCAM DOES WORK on Cheese, and on amsn. Camorama oddly doesn't detect it, and when I type the following statemente on the terminal:

./Face_tracking /dev/video0

The webcam seems to turn on, and the green light goes on, but no window pops up or appears. And the computer doesn't frezze but I don;t get any response...

On the  other hand, when I type in :

/dev/video0

I get the following message:

bash: /dev/video0: Permission denied


---

Am I missing something?? I mean my lapotop clearly detetcts the device, but maybe I'm missing another driver?? Any suggestions? 

Thanks a lot!

---

### Post by BCtom on 2010-02-13
I'm getting the same problem too. The only way I can run programs and connect to the camera, is to run everything in root. I've tried changing the permission of /dev/video0 manually,  and changing it in "Users and Groups" and then running the programs in my user-name, but for whatever reason this still doesn't allow permission.  I'm hitting the wall too: ](*,)

---

### Post by Ayuthia on 2010-02-13
Are you part of the video group?  You can check and see if your username shows up:
```
cat /etc/group|grep video
```
If it does not show up, you can add yourself to the group:
```
sudo gpasswd -a username video
```
You will then need to log out and log back in to have the settings take effect.

I am not for sure if this is the solution to the problem or not, but it should give you permission to the device.

---

### Post by BCtom on 2010-02-13
I am part of "Video" in the group. This was one of the very first steps I did when I first upgraded to 9.10. Maybe it should look different?  Here is my output:

```
tom@tom-desktop:~$ cat /etc/group|grep video
video:x:44:tom

```I know this is not my thread, but thanks.

---

### Post by Mecasickle on 2010-02-13
I found the answer on a webpage

open the terminal from the folder you have your openCV program

then type this:

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

after that type

camorama

and camorama will run with your webcam showing a picture of you.

Worked for me!

Heres the webpage: [http://forums.quickcamteam.net/showthread.php?tid=1051](http://forums.quickcamteam.net/showthread.php?tid=1051)

CHeers!

---

### Post by Mecasickle on 2010-02-13
Btw BCTOM, don't worry if it ain't your thread, I'm sure there are tons of people out there who have or will have the same probelms, so don't hesistate and keep posting! :D

---

### Post by BCtom on 2010-02-14
Thank you Mecasickle, there have being other threads where I was flamed on the Ubuntu forums, so I ask now to avoid the negative attitudes towards my newbieness. 

I am happy for you that you were able to solve your problem; however, my problem is still a problem. I just tried Easycam, and it is not so easy to use. In fact, I do not understand it--does anyone have an English copy? And Easycam does not fix my /dev/video0 permission issue either.

EasyCam seems to have an "error" that pops up when I try to install the gspca, and the  V4L modules/drivers. Of course the French text prevents me from understanding it. I can't tell what it's really doing when the Easycam pop-up window comes up-I know it is an error, but I can't tell you what it is saying. 

I read, doing a Google search, that there is a bug with the Ubuntu 9.10 Kernel that prevent the module/driver from working. Hopefully the next upgrade of Ubuntu will have it sorted out.

For now the webcam works fine in root.

---

### Post by Pablo Somebody on 2010-02-15
I had a similar problem for months, and tonight I finally found the cause and temporary workaround. See post #7 in the following link
[https://bugs.launchpad.net/ubuntu/+source/xawtv/+bug/488455](https://bugs.launchpad.net/ubuntu/+source/xawtv/+bug/488455)

---

### Post by no2498 on 2010-02-17
before you can do anything you need to close the program you have running
that is for the cam

On the other hand, when I type in :

/dev/video0

I get the following message:

bash: /dev/video0: Permission denied

thats why he got that

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2

click the bottom test button

get a program to use the cam with

cheese we all have in the repose ( getdeb ) has wxcam

1 of the 2 will see your cam

---

