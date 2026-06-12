---
title: "Ubuntu 64 bit compatibility  with Lenovo X 220 and W 520"
date: 2012-04-05
forum: Hardware
---

### Post by expatver on 2012-04-05
Many thanks to for the expertise and diligence of all of you here on the forum.  I currently run Ubuntu 11.10 on a couple of my machines and have moved away from another distro that I used for many years. 

Currently I am considering purchase of a new laptop. Before posting this question I checked both the laptop compatibility thread  here on the forum (104 pages) plus the Ubuntu hardware certified listing available online.  I did not find anything on the thread here on the forum or with a forum search. What I found in "Certified Hardware" was confusing  so I thought I would ask before deciding on my purchase. 

Thew two machines are Lenovo Thinkpads- the two models under consideration are the X220 and the W 520.  Under the Certified Hardware list, the X220 is shown compatible   with  Ubuntu 32 bit, although it is 64 bit architecture.  The closest we come to the W520 is  showing the W510 compatible with 32 bit although its 64 bit also. I also have read a couple of threads on the Lenovo forums and here dealing with  wireless, graphics and screen brightness, mostly things that have been solved with workarounds. 

I was wondering if anyone had any opinions or experience with 12.04 and how compatible either of the platforms I am considering MIGHT be. 

If the platform wont run Ubuntu well I dont want to buy it. I do photo editing and want Ubuntu and the tools available there (RawTherapee mainly) for in field work.  Any comments or recommendations are deeply appreciated. Once again many thanks to every one here.

Expatver

---

### Post by Paddy Landau on 2012-04-05
What I do is create a Live USB with persistence, run Update Manager to install all updates, and install all the programs I need to check.

I go to the store and ask permission to boot off my Live USB (I state that it won't modify the hard drive in any way, which is true, and the store assistant is usually very curious to see what I'm doing).

I boot, test thoroughly, and decide yay or nay.

---

### Post by expatver on 2012-04-05
Paddy Landau

Thanks for the info. I have not  used Persistence. I do however have bootable  CD's of 11.10 32 and 64 bit plus 12.04 64 bit, and intended to do exactly as you suggest. 

However there is only one problem. no one within any reasonable distance of where I live has either model for display. The only other thing to do of course is order one from some place such as Amazon, try it and return the machine if it does not or can not be made to work.  I've had physical hands on  every laptop that I have ever purchased--  before purchase. So in spite of the idea that it could be returned to some one like Amazon, the concept seems a little alien to me. I also have been surprised that none of these models are around anywhere, even at a couple of the Lenovo authorized business resellers.  So its definitely a quandary.

Thanks very much for the suggestion on Persistence. I have never used it but am going to check it out this afternoon. What to do about my problem however, I am not sure. I live in the Southeast and it is almost reminiscent of some places I lived in Latin America many years ago.

Regards
Expatver

---

### Post by Paddy Landau on 2012-04-06
> **expatver said:**
> I have not  used Persistence ... am going to check it out this afternoon ... I do however have bootable  CD's ...
Looking at the instructions on the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download"), it seems that you can use persistence only when installing from Linux. So, load Ubuntu and follow the instructions to load it onto a USB with persistence ("Stored in reserved extra space"). Use the latest stable version (11.10). Use the largest value that your USB stick allows.

Boot into the Live USB. Install all updates and reboot (again into the USB). Install ubuntu-restricted-errors (if not already done), and all programs you would need to have working, e.g. Cheese (to check the webcam).

When you use the USB on your proposed computer:

[LIST]
[*]Try to connect to the Internet wirelessly. (If you are in the store, you probably won't have Internet available, but at least check that the wireless card seems to respond properly.)
[*]Open Additional Drivers in case that computer needs proprietary drivers (this won't work unless you are connected to the Internet).
[*]Open a terminal and enter the command:```
/usr/lib/nux/unity_support_test -p
```You need to see all green "Yes" responses there to be sure that your graphics card is fully supported.
[/LIST]
 > **expatver said:**
> ... no one within any reasonable distance of where I live has either model for display. The only other thing to do of course is order one from some place such as Amazon, try it and return the machine if it does not or can not be made to work.
You may have a problem with that, as Amazon won't guarantee that the computer will work with Ubuntu; only with Windows.

You could have a look at [companies that specifically support Linux]("http://www.pcworld.com/businesscenter/article/212014/how_to_buy_a_computer_preloaded_with_ubuntu.html"), such as System76. I've never used them, but have read plenty of good comments about System76.

---

### Post by cbennett926 on 2012-04-30
Hello, 

I have a w520 (specs are in the sig) and I love it! The only curiousity I have is I can tell when the fan runs more on windows than ubuntu, but the temps are just fine!

---

