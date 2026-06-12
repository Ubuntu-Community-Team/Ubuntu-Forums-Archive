---
title: "ATI mobility radeon HD 4250"
date: 2010-08-22
forum: Hardware
---

### Post by Jan051 on 2010-08-22
[SIZE=1]Hi, I'm think of buying the [/SIZE][SIZE=1]Acer Aspire 7551-P323G32MN laptop. It comes with an ATI mobility radeon HD 4250 graphics card, and I was wondering whether or not that card is supported by ATi to work in Ubuntu. In the release notes, all I could find was that the Ati mobility radeon HD 4200 was supported, it didn't state anything about the 4250. Does anyone know whether or not the proprietary driver will work in ubuntu?

[/SIZE]

---

### Post by rufuz on 2010-09-25
i got an acer as 5551 with same graphics card and i am wondering the same, will this card work with latest ubuntu, i am though gonna do a clean install right now with ubuntu 10.04, and test and will report back as soon as i know anything :) but from what i can read there is a issue with this graphics card on ubuntu, if anyone has a fix please post it here ^^

---

### Post by tadaskr on 2010-09-25
It could be same as mine. Yes, you can install ubuntu/kubuntu with HD4250 like I can on HD3470, but I can't install drivers from ati website or using hardware drivers. You will get errors and be worse than run without drivers

---

### Post by coffeecat on 2010-09-25
> **rufuz said:**
> but from what i can read there is a issue with this graphics card on ubuntu

Where did you read this? From what I can make out the mobility HD4250 is very little different from the HD4200 and the HD4200 in my laptop works just fine in both Lucid and Maverick. Posting with it now.

> **tadaskr said:**
> It could be same as mine. Yes, you can install ubuntu/kubuntu with HD4250 like I can on HD3470, but I can't install drivers from ati website or using hardware drivers. You will get errors and be worse than run without drivers

Both my HD4200 on this laptop and my HD4350 in my desktop give me enough acceleration and 3d to run compiz with the default open-source driver. That's in both Lucid and Maverick. The only reason I can see for using the proprietary driver - with my two cards at any rate - is if you play games. Which I don't.

I tried to install the fglrx driver once. I nearly lost the will to live. :(

---

### Post by tadaskr on 2010-09-25
It could be problem with ati drivers, because in past i could install drivers and everything work, but now i can't. Maybe time to wait for new drivers

---

### Post by IC2D on 2010-09-26
Hello,

It's been a while since I've used Ubuntu so excuse me if I seem a little naive. I was planning on buying the Acer AS5551 and am wondering if any proprietary drivers would be made available soon to install via the "hardware drivers" menu in "administration". Because I need this laptop for school and I am not planing on doing any major modifications on it. Even though it works fine with the generic open source drivers, it would be nice to use this computer at its full capabilities. Has there been instances in the past where proprietary drivers were made available via the "hardware drivers" menu in "administration" after the GFX card was released?

Cheers,

IC2D

---

### Post by coffeecat on 2010-09-26
> **IC2D said:**
> Even though it works fine with the generic open source drivers, it would be nice to use this computer at its full capabilities. Has there been instances in the past where proprietary drivers were made available via the "hardware drivers" menu in "administration" after the GFX card was released?

What do you mean by "full capabilites"? Are you intending to do some serious gaming on it? If not the open source driver will be more than enough for your needs. I believe that ATI/AMD themselves are involved in the development of the open-source driver, so if it meets your needs you needn't bother with the closed-source driver. More information here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Don't let that page let you think that setting up the ATI driver is difficult. All I had to do with both my ATI cards was to install Ubuntu. I even had the basic compiz effects such as transparency enabled by default. To get the other gee-whiz stuff such as the rotating cube I simply had to install  the compizconfig-settings-manager package.

My experience with the proprietary fglrx driver in Ubuntu 9.10 (Karmic) with the HD4200 card was less than happy. Its performance was far worse than the open-source ati driver, even though the version of the ati driver that came with Karmic didn't give me compiz. I don't know what the version of fglrx that Lucid would install is like with the HD4200. I didn't bother to try it because Lucid's more recent ati driver was giving me everything I wanted.

If you search the forum, you'll find that's a pattern with the ati and fglrx drivers - performance and experience varies with card and version of Ubuntu. So I can't guarantee that the HD4250 will behave the same as the HD4200.

There is one thing you could try. Are you able to get your hands on an Acer AS5551, say a demo machine in a shop? The  sales staff  may let you try booting up with a live CD or live USB. If you do, the ati driver will be the default and you could test it. Desktop performance is sluggish in the live session so make allowances for that. While you're about it you can test all the other hardware such as wireless, Fn keys, trackpad and so on. Experience with Acers seems to vary model to model. Everything works on mine but the trackpad performance is appalling. But so it is in Windows 7, so that's down to the trackpad. Owners of other Acer laptops seem to experience hardware issues, so it's worth testing if you can.

---

### Post by Ingotian on 2010-11-22
I have a HP 62 laptop with a HD 4250 graohics card. Initially I found the only version of Ubuntu that would boot without a blank screen was Karmic. All attempts at downloading and installing the ati-driver installer have failed. No proprietary driver installed is reported from the system - admin - hardware drivers and the display config tool just gives unknown "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" Clicking yes says problem initialising catalyst control centre. no Ati hardware installed. So I'm stuck with no display out eg for a data projector and 1024 x 768. 

I can try an upgrade and hope it's fixed with Maverick but last time I tried I got a blank screen so could do nothing. 

So I would say avoid HP laptops with ATi graphics, it's not worth the hassle.

---

### Post by WilliamNY on 2010-11-24
> **Ingotian said:**
> I have a HP 62 laptop with a HD 4250 graohics card. Initially I found the only version of Ubuntu that would boot without a blank screen was Karmic. All attempts at downloading and installing the ati-driver installer have failed. No proprietary driver installed is reported from the system - admin - hardware drivers and the display config tool just gives unknown "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" Clicking yes says problem initialising catalyst control centre. no Ati hardware installed. So I'm stuck with no display out eg for a data projector and 1024 x 768. 

I can try an upgrade and hope it's fixed with Maverick but last time I tried I got a blank screen so could do nothing. 

So I would say avoid HP laptops with ATi graphics, it's not worth the hassle.

That's unfortunate. I am thinking about getting a Sony Vaio E-series ([FONT=Verdana][SIZE=2][COLOR=#ff6600]**Sony VPCEE23FX**[/COLOR][/SIZE][/FONT]), also with ATI Radeon 4250 HD. I haven't tried it myself, but try this: 


[LIST=1]
[*]To do this, enter in a terminal:
glxinfo | grep rendering
[*]If 3D acceleration is working, the following will be displayed:
direct rendering: Yes
[*]If it doesn't work, follow the steps to activate 3D acceleration.
[LIST=1]
[*]Install the xorg-driver-fglrx package from the "Restricted" repository
[*]To set up the new driver, enter in a terminal:       *sudo dpkg-reconfigure xserver-xorg*
Agree to automatic detection of your video, and choose the driver fglrx when asked.
[*]Restart the computer for the changes to take effect.
[/LIST]
       
[/LIST]
  Please note:  AMD has just released the latest [AMD Catalyst 10.10 for Linux x86/x64]("http://www.*****************/driver/articles/amd-catalyst-10-10-8-872-download-for-ubuntu-10-10.html"), this release provides support for Linux Operation System which can support openSUSE 11.3 and [Ubuntu 10.10]("http://www.*****************/driver/download/14936,ubuntu-10-10-driver.html").           With ATI Radeon HD 4250 gfx card on board, we recommend you to download  this driver, which will also avoid the 3D Acceleration problem.

Actually, version 10.11 is out. Do a google search. Try installing the proprietary driver manually. Does that work?

---

### Post by mastablasta on 2010-11-24
> **Ingotian said:**
>  
So I would say avoid HP laptops with ATi graphics, it's not worth the hassle.
 
Here 62 (HP G62-b55SM 2,4 GHz (XF377EA)) comes with Radeon HD 5470, 512 MB and Suse Linux preinstalled. :p
 
Similary 72.... wish i had the money...

---

### Post by djpurity on 2011-08-10
> **WilliamNY said:**
> To do this, enter in a terminal:

[LIST=1]
[*] glxinfo | grep rendering
[*]If 3D acceleration is working, the following will be displayed:
direct rendering: **Yes**
[/LIST]
I tried this out, since I have been running my **Acer Aspire 5251-1805** which has an **AMD 64-bit processor** at **2.2 GHz** and **3 GB DDR3 Memory**. It does have the **ATI Mobility Radeon HD 4250 Graphics Card**, and I started with this laptop running a mere 250 GB HDD with **Windows 7** **Home Special Edition** (seems so long ago, I probably am imagining that there was anything "special" about the installation tacked onto it)on it. I seemed to have um, disrupted the installation of the Windows 7, and while looking for a way to fix it (_**hint**_: *to begin with, _never_ get frustrated with a slow-running Internet connection by striking your keyboard with your fists when a deadline approaches and passes you by in anger*), I came across a possible data recovery resource was to run a "love" **Ubuntu CD**, which I made and ran off another laptop. I was unable to mount the HDD, but I really enjoyed the Ubuntu 10.10 so much that I got a brand new HDD (a **WD 500 GB**) for the laptop, used the "live" boot disc and installed **Ubuntu 10.10 64-bit** on the entirely fresh formatted HDD out of the box! 

Now that's how you "sell" (promote) an O/S!! Open Source, _*FREE*_, and freely available and fully documented! Now as a Computer Science graduate (started my schooling at GA Tech in ATL), I used to live and breathe in **UNIX** and fiddle with **Red Hat Linux** back in the day .... 1996-2003), but then I got into graphic design (since I also am an artist and musician of electronic music, naturally :KS), and my interest in computer programming and web programming fell to the wayside. So Ubuntu was a great way to reintroduce myself to the UNIX and Linux worlds I used to live inside of and really enjoy.

But wow, I have really filled my head with so much other information, that all the **UNIX/Linux** stuff got squeezed out, and my comp sci degree feels useless really at this point. Anyway, I never had one issue running **Ubuntu 10.10** "live" or installed on my laptop, and when I upgraded to **11.04**, it still is working. NO ISSUES!

I can run **Compiz Config** and do all those great special effects and everything on it, although playing with it usually got me stuck without a launchpad bar or a top bar, and sometimes just a cursor on a screen with the option to create a new launchbad if I knew the command..... which I usually did not. So I left well enough alone, refreshed my installation of **Ubuntu 11.04 AMD 64-bit** to as nearly a fresh install as I can get without formatting it from scratch all over again, but it's never given me issues.

Actually, I use my **HDMI** port to send my graphics to my **Emerson 22" HDTV** with **HDMI** and all kinds of I/O-Ports, and use that as my **HD monitor**. Since it _*IS*_ an **HD** **graphics** card. And it works great! An external keyboard and wireless mouse, and I can just tuck my laptop away and have the thinnest desktop computer ever (well, *without* the *better* specs of a desktop). The only complaint about running it like this is that I have a fan constantly blowing on the computer and I keep its rear lifted in the air to keep the hardware cooled off best I can underneath it. But so far, it's been great!
> **WilliamNY said:**
> 
Please note:  AMD has just released the latest [AMD Catalyst 10.10 for Linux x86/x64]("http://www.*****************/driver/articles/amd-catalyst-10-10-8-872-download-for-ubuntu-10-10.html"), this release provides support for Linux Operation System which can support openSUSE 11.3 and [Ubuntu 10.10]("http://www.*****************/driver/download/14936,ubuntu-10-10-driver.html").           With ATI Radeon HD 4250 gfx card on board, we recommend you to download  this driver, which will also avoid the 3D Acceleration problem.

Actually, version 10.11 is out. Do a google search. Try installing the proprietary driver manually. Does that work?

[CENTER][FONT=Impact][SIZE=3][COLOR=Purple]Actually 11.04 is out! I want to hear reviews about this new AMD Catalyst support for Linux x64 for Ubuntu 11.04. Anyone know anything on it before I blow up my computer?[/COLOR][/SIZE][/FONT]
:popcorn:
[/CENTER]

---

### Post by TheCiD on 2011-12-08
Hi there, uhh there are 3 link that can help I think...
[ATI Catalyst&#8482; Proprietary Display Driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")  For drivers
[ati.run - Documentation Ubuntu Francophone ]("http://doc.ubuntu-fr.org/ati.run")
[catalyst - Documentation Ubuntu Francophone]("http://doc.ubuntu-fr.org/catalyst")
Good luck
Are french pages but I think that there are there English versions

---

