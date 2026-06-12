---
title: "[SOLVED] Compaq laptop problems"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by Ex-windows on 2008-01-02
New LAptop
My new Laptop arrived today and I cant get the live CD to work
 The CD is Good (Freshly Burned and Used on Other comp.)
The Laptop is a Compaq Presario F750us Notebook PC
Spec's are
 AMD Athlon 64 X2 Dual-Core Mobile Technology TK-57 (1.9 GHz, 512KB L2 Cache)
15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
Nvidia GeForce 7000M with up to 287MB total available graphics memory
Up to 1600MHz system bus running at AC/DC mode 35 watt
120GB 5400RPM SATA Hard Drive
32 bit OS with Vista (ugh)

Now for the problem The disc loads to the point where I am asked to Run or Install ubuntu
 I click and it begins to load the kernel
First thing I noticed was a Hardware message that read
"unable to attach Hardware, hardware revision not supported.
Screen moved really fast so I couldn't get more. 
Next is The failed xserver The usual failed to start xserver error message, which end with "No devices detected"
fatal error "no screens found.
 My other compaq and older HP are running unbuntu. Hp is linux friendly as is nvidia, SO what might be the problem. I know the install cd is good. Any help would be greatly appreciated.

---

### Post by newbie2 on 2008-01-03
> **Ex-windows said:**
>  Hp is linux friendly 

hmmm...i don't agree with that --> [http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
:rolleyes:

---

### Post by Ex-windows on 2008-01-03
Thanks for the link , however the thread seems to be more about "gutsy" issues than Hp.  (I didn't all 27 pages but i did read 6 ) All My other computers and printers are Hp and they work extrmely well and the installs went without any problems. And apparently alot of people are running ubunut  on Hp Laptops. I just cant seem to get past this Xserver failed issue.ANy Ideas???

---

### Post by drfox on 2008-01-10
Try using the no fail graphics option and add the line apic=no
Then let me know if it works...I'm looking at that same machine.
BTW, can you tell me what wireless hardware they use?

HTH and thanks 

Larry

---

### Post by Ex-windows on 2008-01-10
Yes that what it took and yes i was able to test run the live cd on it. I tried both fiesty (my fav) and the Gutsy.  I really think the Fiesty will be the ticket when  I actually install.
The wireless= Connect wirelessly 1 with 802.11b/g WLAN  (This is from the site.) 
I cant seem to find if there is an actual manufacturer name. I'll look on the laptop once my wife gets off it lol 
Wait here we go
 Network adapter=Atheros AR50007 802.11b/g wifi adapter
NVIDIAnForce networking controller.. Here is the link top the HP store where I bought mine
[http://www.shopping.hp.com/webapp/shopping/home.do](http://www.shopping.hp.com/webapp/shopping/home.do)
As for me I love it. I cant wait to get Fiesty on it full time.

---

### Post by borahshadow on 2008-01-30
Did you ever put feisty or gutsy on it I'm thinking about getting this laptop and would like to know how well everything works I would probably just put hardy alpha on it though.

---

### Post by Ex-windows on 2008-01-31
NO  But i have run the live cd Fiesty and Gutsy. I have had to do some organising on my other computer and have yet to take the plunge plus I had to make the restore cd's. As for the computer itself It is Great and "FAST" I've never had a comp this fast b4 . The 1 thing I noticed when running the Live Gutsy cd was The "Sound" it was really breaking up and There have been lots of posts regarding this problem. Another reason I'm stalling is to find out more on the wireless issue.  I like HP products But I admit I almost bought the dell with Ubunutu pre-installed However2 things: 1 It has Gutsy and 2 It was More expensive even compared to the same dell model with windows and I thought that was kinda cheesy.  I hope to try this weekend  with dual boot fiesty. If I do I'll repost.
Take care

---

### Post by borahshadow on 2008-01-31
Thanks I would think that gutsy would be the better one to try in fact I plan on just skipping gutsy and going straight to hardy alpha and then beta>final Newer releases almost always improve but that thread about hp is the first time I've heard of so much regression. Wireless should not be an issue it sounds like there are 2 good solutions ndiswrapper or madwifi which seems to be the less ideal other than it is native.
I figure those things are possible to get working things that I don't know about are things like suspend and such and if the wireless (ndis or madwifi) works after resume
                                                                             Thanks for your help

---

### Post by Ex-windows on 2008-01-31
Sorry to take so long. Anyway I hope you have great results. I still have lots to learn about Networking in general and all that ndis wrapping and madwifi is way outta my league at this point. And "alpha" release I'm still scared of beta :lolflag:
Anyway good luck and if you get time post your results.
Later

---

### Post by wtfacoconut on 2008-02-01
yo I gots a solution to your wifi problem.
Just use madwifi. They made a patch so you'll be able to use AR5007.
Here's the guide to getting it up and running:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")
 hopefully this solves one problem. 
Also As a suggestion, Why not try using the distro: Linux Mint Daryna. It's Gutsy based and I found that I had alot less problems when I installed it on the F750US. The ONLY to big problems that I have now is that the speakers won't turn off when I plug in my headphones, and that everytime I reboot, I have to reinstall the kernel modules for my Nvidia card/drivers. If any of ya'll got some tips on either of those 2 things give heads up. who ever figures it out will get a cookie!!!!! XD lolol jk.

---

### Post by borahshadow on 2008-02-01
what problems did that distro solve that gutsy had?
also does suspend work and does network work after resume from suspend?
the speakers probably have to manually be disabled when headphones are plugged in.
Describe what you must do with the nvidia kernel modules please. I* Might*know how to fix it but maybe not.

Oh and would you reccommend this laptop I actually have not bought it yet that is why i'm trying to figure out how well things work. If things don't work too well I might pass for a different laptop

---

### Post by IkaTaii on 2008-02-04
I actually just picked one of these up because it was available at a brick and mortar for the same price range as crazy EPP price directly from HP.
Couple of questions for before I get started:
- Is Gutsy going to go better than Feisty for the install? From the looks of things, if I pass it the "universal frame buffer" type option and the apic=no, it should boot and install fine on Feisty.

-Are you guys using the AMD64 or the x86 versions of the distros? I'm jaded by horror stories of 64-bit driver woes from other OS's, so I downloaded and burned the x86 discs already, but I can see the _64 versions running better with the AMD processor.

---

### Post by borahshadow on 2008-02-04
Hello and I guess good bye :)
I decided to pass on buying this laptop and I guess it is a good thing too because yesterday I got my old laptop working :) 
as for the 64bit thing is you use ndiswrapper you'll need 64bit windows drivers so I would just stick with 32bit.
Keep in mind that gutsy will have newer versions of software and gutsy also has the tickless kernel(but only on 32bit) which might help with battery life but some people think gutsy is bad on hp laptops so if it has compatibility problems those might not make it worth it.

---

### Post by Ex-windows on 2008-02-05
[COLOR="Navy"][B] Well Wont know for  another  1/2 hour or so but I decided to get brave and dual format Using Fiesty.  Wasn't sure if we wanted to try Gutsy, yet. Waiting, now, for the rest of the updates to finish. Our first step will be to check the wireless issues and graphics driver.  
Will keep you posted. [/B][/COLOR]
I meant Dual Boot. LOL

---

### Post by Ex-windows on 2008-02-05
AArrrgh :confused:
OK I got Fiesty Installed did a lil playing around and adding some touches b4 installing the 189 updates. Well after the updates I restart and I see the Grub and Both Vista and Fiesty. I choose fiesty and it begins loading and gets all the way thru the orange status bar and then goes straight to a Blank black screen. WHat did  I do :lolflag:From heaven went I Strate to hell:(
here what I've done thus far.
Prior to updating 
I ran these commands
sudo /usr/share/doc/libdvdread3/install-css.sh

then I ran this 
sudo apt-get install totem-xine libxine-extracodecs
I answered "YES" and terminal began install
THEN
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
 I noticed that I still could not change screen resolution, But wanted to get the update out of the way.
ALSO Restricted drivers shows that the  Nvidia Driver is Checked but  NOT enasbled.

Any idea where i went wrong???

---

### Post by IkaTaii on 2008-02-05
This is totally an offhand guess, but it kind of sounds like you're using the wrong module for the nVidia 7000M that comes in this system. I haven't looked closely enough at Ubuntu's packages, so my only suggestion would be to take a second look at those and possibly fall back on grabbing your kernel source and the driver directly from nVidia.
Is there a command-prompt fallback option with how you set Feisty up so you can reset your xorg.conf back to default?

---

### Post by Ex-windows on 2008-02-05
Thanks You might have a good point. I'll try that. The command  I am familiar with is sudo dpkg-reconfigure xserver-xorg. It doesn't set to default but brings up a gui  so you can manually set up your xorg configuration ( if I;m saying hat right lol)
I'll try this this afternoon:guitar:

EDIT
I guess one could also use the back up xorg file does anyone know  the  command for this

---

### Post by Ex-windows on 2008-02-07
For thos eof u still following this thread, heres the update.
Graphics card issue is solved (user error lol lol))
 As for the wireless issue, In addtion to wtfacoconut's links you may want to check out this thread
[http://ubuntuforums.org/showthread.php?t=688641](http://ubuntuforums.org/showthread.php?t=688641) 
and check out the links in ugm5hr's reply
Another thanks to agm6hr and wtfacoconut for helping out
I will marked this as solved..Take care

---

