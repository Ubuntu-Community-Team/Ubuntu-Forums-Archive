---
title: "How to enable Nvidia GeForce GT 630M (Switchable) Graphics Card on ubuntu 12.04LTS?"
date: 2012-12-01
forum: Hardware
---

### Post by acerbuntu on 2012-12-01
Hi guys,

I got an acer aspire 5755G with Nvidia GT630M optimus technology and want to make use of it as that is my last job to get my acer to a complete ubuntu laptop. As I did some research on it and found that there is no official way to do that and came to know that there are some third-party things to make it work.

At present I am only using integrated graphics (Intel HD 3000) and I wanted to check this NVIDIA. As If I did my ubuntu install with integrated graphics, so I didn't get any additional drivers.

And also please let me know the PROS & CONS of force using NVIDIA.

Could you please tell me step by step process to make it work.

Many Thanks in Advance.

---

### Post by ahepas1999 on 2012-12-01
Hi there. You need to install bumblebee [https://github.com/Bumblebee-Project](https://github.com/Bumblebee-Project) there is a PPA install it and follow the instructions. Then you can use your NVIDIA card using a command (optirun). I am using it right now without problems, and you should check your BIOS settings if you want to use only one of the two graphic cards, if your BIOS support this feature...Good luck. It is easy!

---

### Post by BlinkinCat on 2012-12-01
Hi acerbuntu,

Good luck with your project.

Cheers - :P

p.s. No need to reply, you are busy.

---

### Post by acerbuntu on 2012-12-01
> **ahepas1999 said:**
> Hi there. You need to install bumblebee [https://github.com/Bumblebee-Project](https://github.com/Bumblebee-Project) there is a PPA install it and follow the instructions. Then you can use your NVIDIA card using a command (optirun). I am using it right now without problems, and you should check your BIOS settings if you want to use only one of the two graphic cards, if your BIOS support this feature...Good luck. It is easy!
Hi ahepas1999,

Sorry bit busy to get back straight away.Thanks for your information. I followed the link and found loads of files under precise folder and not sure which one to go.

If you don't mind could you please post a detailed guide here.

By the way I only have Graphics with Integrated & Switchable options in bios.So do I have to change it to swaitchable before I proceed with?.

Many Thanks.

---

### Post by BlinkinCat on 2012-12-01
Hi acerbuntu,

I came across this post - I have no idea if it would help -

[http://ubuntuforums.org/showthread.php?t=2069373](http://ubuntuforums.org/showthread.php?t=2069373)

Cheers - :P

---

### Post by acerbuntu on 2012-12-01
> **BlinkinCat said:**
> Hi acerbuntu,

Good luck with your project.

Cheers - :P

p.s. No need to reply, you are busy.
Hello my friend,

Thank you very much for wishing me.

Hope you're having a nice weekend.

Enjoy your day!!! ;)

---

### Post by acerbuntu on 2012-12-01
> **BlinkinCat said:**
> Hi acerbuntu,

I came across this post - I have no idea if it would help -

[http://ubuntuforums.org/showthread.php?t=2069373](http://ubuntuforums.org/showthread.php?t=2069373)

Cheers - :P
I did try this once before I posted my previous thread. There is some thing I'm missing in it.

I also think that it worked only for him or some. Because I see there are no replies to this thread and it was posted recently in October.

Well anyway I'll have a go again.

Cheers :)

---

### Post by acerbuntu on 2012-12-01
> **BlinkinCat said:**
> Hi acerbuntu,

I came across this post - I have no idea if it would help -

[http://ubuntuforums.org/showthread.php?t=2069373](http://ubuntuforums.org/showthread.php?t=2069373)

Cheers - :P
In the above link he mentioned 

> When installed bumblebee my nvidia wasn't shown in hardware drivers on ubuntu 12.04 
and i had system freezes. Then i installed the new kernel. 3.3.6

How to check hardware drivers?

And also will it be any problem if I update kernel version?

---

### Post by Yellow Pasque on 2012-12-01
The bumblebee wiki is here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by acerbuntu on 2012-12-01
> **Temüjin said:**
> The bumblebee wiki is here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Thanks for your help. I found some useful info from it.

However I'm working on blinkincat's link from above post and very near to success. 

Finally to reboot and c if it works. I'll post next.

---

### Post by acerbuntu on 2012-12-01
> **BlinkinCat said:**
> Hi acerbuntu,

I came across this post - I have no idea if it would help -

[http://ubuntuforums.org/showthread.php?t=2069373](http://ubuntuforums.org/showthread.php?t=2069373)

Cheers - :P
SUCCESS !!! I Finally Got It.

So here how I did it ...

First before installing Ubuntu 12.04LTS, go into BIOS set-up change the Graphics mode to Integrated option and then install ubuntu.

[COLOR="Red"]Imp Note: Do not select Graphics Mode to Switchable option until you finish step 1 below. As you're drivers will mess up!!![/COLOR]

Next follow these two steps from doomsword2001 guide below.

> **doomsword2001 said:**
> I recently had problems installing drivers for my Nvidia 630M and i thought i should post the solution for others. I had random system freezes. Please note i can't guarantee it will work for you, but i know it worked for me.

1) Install bumblebee
sudo add-apt-repository ppa:bumblebee/stable
 sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

When installed bumblebee my nvidia wasn't shown in hardware drivers on ubuntu 12.04 
and i had system freezes. Then i installed the new kernel. 3.3.6

2) 
sudo add-apt-repository ppa:upubuntu-com/kernel
sudo apt-get update
sudo apt-get install linux-kernel-64  (thats for 64 bit of course)
need to restart after installing. type uname -r to check the version if you want.

After installing the kernel 3.3.6 i can see the nvidia drivers in hardware drivers (jockey)
This did stop ubuntu from freezing.

Thats all i got it working for me and thought some one may had same problem.
I am not sure if i post it on the right place but i just wanted to help. 
Cheers.
):P

Enjoy your day!!! ;):guitar:

Update: I just found that my fan is getting hotter. I try figure it out asap, bit busy now!.

=D>Thanks to ahepas1999, BlinkinCat, Temujin for sharing their valuable info.

PS: I cannot guarantee it will work for you, but it worked for me.

---

### Post by BlinkinCat on 2012-12-01
Hi,

Glad you got it sorted out - hoping your heating problem is not too bad.

Cheers - :P

---

### Post by acerbuntu on 2012-12-01
> **BlinkinCat said:**
> Hi,

Glad you got it sorted out - hoping your heating problem is not too bad.

Cheers - :P
It's not too bad. But it looks bit more than in windows. Some times when I run XBMC HD films feel like it's going higher.

Not sure how to check fan speed in windows and compare with ubuntu!. Soon I hope will fix it.

Cheers ;)

---

