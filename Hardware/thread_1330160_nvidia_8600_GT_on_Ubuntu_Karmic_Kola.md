---
title: "nvidia 8600 GT on Ubuntu Karmic Kola"
date: 2009-11-18
forum: Hardware
---

### Post by iRounak on 2009-11-18
I am a complete linux newbie.
Intel Core 2 duo
Intel G33 motherboard
nvidia 8600 GT
I installed Karmic Kola using amd64 DVD.
No graphic drivers were recommended unlike when I used i386 Karmic Kola live CD.
I opened System>>Hardware but it was empty. No driver was listed there.
The next day, I went to nvidia's website and downloaded driver for 64 bit linux.
I began installing it but it made one excuse after another:
1. be root
2. exit X server
3. run at run level 3
at which point I gave up. I opened System>>Hardware again and this time I found that nvidia drivers were recommended to me just like the live CD did. This was annoying because it should have happened earlier.
The two nvidia drivers were revision 173 and revision 185(recommended). I let Ubuntu download and install revision 185.
Restarted Ubuntu. It did not shut down. I saw scrambled screen with many colors and symbols like dollar sign, hash etc and numbers.
Now, when I try to boot Ubuntu, I see the Ubuntu logo but after that I only see a blank black screen.

---

### Post by realzippy on 2009-11-18
Boot in recovery mode,log in at terminal.Run:

[B] rm /etc/X11/xorg.conf
[/B]
then:

**nvidia-xconfig**

reboot.

---

### Post by iRounak on 2009-11-18
Hi,
Thanks for the reply.
> **realzippy said:**
> Boot in recovery mode,log in at terminal.Run:

** rm /etc/X11/xorg.conf**

I did this.

> then:

**nvidia-xconfig**

reboot.
could not do this. I got some error saying it was not found (or could not write) in etc/X11.

I still get the blank screen.

---

### Post by realzippy on 2009-11-18
I asked you to run *nvidia-xconfig* also in recovery mode,
where you are root.Try again...
or type:

**sudo nvidia-xconfig** when you are not at root shell to get permission to write to /etc



*rm /etc/X11/xorg.conf* removes (eventually) existing xorg.conf,*nvidia-xconfig* makes a new one,
if nvidiadriver is installed.

---

### Post by realzippy on 2009-11-18
If it fails due to misinstalled nvidiadriver,you might try envy (script that installs nvidiadriver):

Start in recovery mode,at root-shell type
(you need internet connection):

[B]apt-get install envyng-core
[/B]
when you got it:

**envyng -t**

the rest is self-explaining

---

### Post by iRounak on 2009-11-18
> **realzippy said:**
> I asked you to run *nvidia-xconfig* also in recovery mode,
where you are root.Try again...
or type:

**sudo nvidia-xconfig** when you are not at root shell to get permission to write to /etc
.
this worked but did not solve my problem.

> If it fails due to misinstalled nvidiadriver,you might try envy (script that installs nvidiadriver):

Start in recovery mode,at root-shell type
(you need internet connection):

[B]apt-get install envyng-core
[/B]
when you got it:

**envyng -t**

the rest is self-explaining 	

i followed these steps.
At first, i did not remove the drivers. I got a list with 3 drivers. 
1. Rev 185 Compatible Recommended & Installed
2. Rev 173 Compatible NOT Recommended
3. Not compatible not recommended

I selected 1. It did not reinstall the same driver. It just finished its task within 5 seconds. 
I rebooted.
Removed installed nvidia driver.
Finally I was able to boot into Ubuntu.

Now is there a reason why a driver which is recommended and compatible should fail? Should I try again? 
Would using Rev 173 result in non-core performance of the graphic card?

---

### Post by realzippy on 2009-11-18
On my machine (9800 GTX) the 173 driver is rocksolid.The 185 driver has less FPS performance measured with glxgears,the 190 driver does not even run..

I do not understand;is your nvidia driver now installed or are you using the "free" driver?


edit: since 2.6.31-15-generic the 190.42 is running fine.

---

### Post by iRounak on 2009-11-18
Hi,
Thanks again for the reply.

> **realzippy said:**
> 
I do not understand;is your nvidia driver now installed or are you using the "free" driver?

No, currently no driver is installed. Now, I will try 173.

---

### Post by iRounak on 2009-11-18
installed 173 successfully. Would you please suggest me any game that I should try to test the graphics performance?

---

### Post by realzippy on 2009-11-18
quakelive?

[http://www.quakelive.com/](http://www.quakelive.com/)

you can also install all those fancy compiz plugins and enable desktop effects e.g. rotating desktop cube....

**glxgears**   (run in terminal)

is kind of benchmark for FPS under linux...

---

### Post by iRounak on 2009-11-18
user@ubuntu:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
24110 frames in 5.0 seconds
23853 frames in 5.0 seconds
24251 frames in 5.0 seconds
24180 frames in 5.0 seconds
24313 frames in 5.0 seconds

Is this ok?

My resolution is 1280x720 and refresh rate 60 Hz

---

### Post by realzippy on 2009-11-18
..here in the forum somewhere is a thread people posting glxgears benchmarks..
watch out for it,but do not take it for serious; your hardware acceleration seems to be running.

My 9800 GTX makes something around 35.000 frames /5 sec ...

Please set thread as solved,if it is...and vote for the ubuntu washing machine:

---

### Post by iRounak on 2009-11-19
thanks for all the help. I will do what you said

---

