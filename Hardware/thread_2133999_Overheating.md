---
title: "Overheating"
date: 2013-04-09
forum: Hardware
---

### Post by Evil Larney on 2013-04-09
Hi all,

I have installed Ubuntu 12.10 today on my laptop. When Im just browsing the web or doing something simple my laptop gets really hot and overheats. The fan is also acting like crazy. I dont have this problem on Windows 7 though.. Can anyone help me figure out the problem?

---

### Post by QIII on 2013-04-09
Hello and welcome to the Forums!

It would be quite helpful if you could post the specs of your machine, such as OEM, model, hardware (especially graphics).

Thanks,


QIII

---

### Post by ppjdee on 2013-04-09
You may also want to install something like pSensor or lm-sensors to monitor your system temps.

---

### Post by Evil Larney on 2013-04-10
I have an intel i3 2.1ghz quad-core with an ATI mobility radeon HD 5165 and 4gb RAM. And its a Toshiba sattelite 500. Windows 7 64-bit. 

I know that these arent the best specs but I just watch movies or browse the web on my laptop, and I have a strong PC for all the gaming and the hard work. 

Thank you for trying to help me =]

---

### Post by Evil Larney on 2013-04-10
So,  no one can help me? :(

---

### Post by QIII on 2013-04-10
Hello again!

Please remember that we are a world-wide community of people who do this voluntarily and on our own time as we have time.  Don't take a delay to be a slight.  It could be that the person with the best answer for your issue lives in Kolkata or Oslo and is either asleep, eating, working or spending time with family at the time that you post.  The general expectation is that users will wait 24 hours before bumping to let the post make the rounds.

OK.

Do you have the proprietary ATI fglrx driver installed?

---

### Post by Evil Larney on 2013-04-10
Im sorry for that, it wont happen again. 

I am completely new with this kind of stuff so I dont exactly know what I am doing. That said, I dont have that installed, I cant find information on the AMD site if my graphics card is supported or not. I did find a guide on the ubuntu wiki on how to install it.

again, thank you for your help.

---

### Post by QIII on 2013-04-10
No need to bother with the AMD site at the moment.  Your GPU is supported -- if you are running 12.04.1 or earlier.  That series is based on an overclocked HD 4000 series (mysteriously, AMD calls that a "Mobility HD 5000 series), which is not supported from 12.04.2 forward without a kernel patch, the legacy driver and a downgraded X Server.

Does your machine have Intel graphics as well, or just the ATI graphics?

---

### Post by Evil Larney on 2013-04-10
It has just the ati graphics card. So is this easy to fix for someone like me?

---

### Post by QIII on 2013-04-10
Which version of Ubuntu are you using?

Edit -- I looked back up at your first post.

You have three options:  

1.  Continuing to use the open Source Radeon driver and adding a utility called Jupiter to manage power consumption (and, thereby, heat).

2.  Attempting to install the ATI proprietary driver to see if it will work with that GPU.

3.  The option I recommend highly against:  Using one of the many scripts that will patch your kernel, downgrade X Server and install the ATI Legacy driver.

Would you like to try Jupiter first?

---

### Post by QIII on 2013-04-10
I'm going to be incommunicado for a bit, so I'm throwing this out there...

A bit of background information so you know why this is a problem and don't think we are all crazy.

AMD/ATI decided to stop development of the drivers that support all GPUs prior to the HD 5000 series and put those GPUs in a legacy driver branch.  They did that for both Windows and Linux.  In Windows you would have to install a legacy driver, too.

The folks who use Windows are fortunate in that the cessation of development means only that there will be nothing new added to the legacy driver.  It will still work with Windows because of the way Windows operates.

Not so good for Linux.  Not just Ubuntu, but the entire community using distros that have moved forward with X Server.  Because development has ceased, there is no new code to handle X Server 1.13, which is used in Ubuntu 12.04.2 and beyond.  The legacy driver simply will not work with X Server any longer and newer drivers will not work with the older GPUs.

I really recommend against option 3 because it effectively breaks your 12.10 installation and the future ramifications are unclear.

Option 2 might work.  If it doesn't, I'd have to talk you back out of the bramble patch.

The first option, using the open source driver with Jupiter, is the most likely to avoid frustration.

If you look [here](http://www.webupd8.org/2012/09/webupd8-ppas-packages-uploaded-for.html) and scroll down a bit to the Jupiter link, you'll see how to add webupd8.org's PPA and install Jupiter.  Webupd8.org is well-known and trusted, so don't worry that I am sending you someplace you will regret going.

Follow the instructions at the link above and use the utility.  Let us know how it goes.  We'll decide what to do from there.


Best wishes!

---

### Post by Evil Larney on 2013-04-11
Yes,  I would like to try Jupiter first. I have to go to work now and I'll try it when I'm home.  Many thanks for your help!  I'll let you know if it worked.

---

### Post by Evil Larney on 2013-04-11
Well I am trying Jupiter right now, and its not really working. My laptop still gets incredibly hot and to be honest I kinda lost my hope that those other options will work. Ill just stick with Windows on my laptop since I just use it for regular browsing and such. Thank you for your help, have a good day. =]

---

### Post by QIII on 2013-04-12
Another option might be to use the open source Radeon driver and vgaswitcheroo.

---

