---
title: "1920x1080 Screen Resolution"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by bobkny on 2009-04-10
After a few hiccups, I got 64 bit Ubuntu 8.10 installed as a dual boot with XP on my 64 bit Intel media server PC. I connect to a 52" Magnavox HD TV through the HDMI output of an ATI Radio HD 4550 video card. The screen requires a 1920 x 1080 pixel resolution. I am able to get this resolution with XP -- but not Ubuntu 8.10. I posted a request on the media forum; but so far no replies. I read several other postings and a WIKI on similar high-res ATI problems; but they were all too confusing for a noobie like me. I need a step by step explanation of how to fix this problem; or I guess this Ubuntu installation is destined to be deleted. Too bad; because I like my Ubuntu -netbook installations, and I would really like to get rid of Windows on all of my computers.

---

### Post by markbuntu on 2009-04-10
You should install the latest 9.3 driver from ati, it has better HDMI/HDTV support.

---

### Post by bobkny on 2009-04-11
I installed the Catalyst ATI configurator; and it failed because it could not find the proper ATI driver.
I went to the ATI support web site and downloaded the driver installer; but when I tried to execute it from the desktop it failed.
I then opened a terminal and tried to execute it from the terminal, but I got a message " permission denied".
I'm making some progress; but I'm way over my skill level and stuck.
Help!!!

---

### Post by markbuntu on 2009-04-11
In the terminal navigate to the folder where the driver is downloaded and run

sudo sh /.ati-driver-installer-9-3-x86.x86_64.run

type in your password at the prompt and the driver should install itself.

---

### Post by bobkny on 2009-04-11
Mark - thanks. I have also been helped by another angel - see my other thread. But here is a copy of my last reply:

Surprise, when I re-booted the system, I was able to run the Catalyst control center. Don't know why it worked, but I guess the driver installation actually was successful. Now my only problem is that even when I specify 1920 x1080, it doesn't fill the entire screen. There is a narrow black band on either side of the screen, but at least the aspect ratio is correct, and the image is very sharp. Almost there! Thanks again for all of your help.

---

### Post by markbuntu on 2009-04-11
A lot of tvs use overscan to fill the screen you can type

aticonfig --help

to see what to do about that.

---

### Post by bobkny on 2009-04-13
You identified the problem but the aticonfig-help didn't have a fix. To fix you need:
aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0.

It took awhile  to find this fix, but I hope that this can help someone else with this problem. Thanks again.

---

### Post by markbuntu on 2009-04-13
aticonfig has more stuff with every release and the --help does not always keep up. But anyway it is good you could fix your problem.

---

### Post by bobkny on 2009-04-14
Thanks again for the help on this. Unfortunately, having Ubuntu hooked to my HD revealed another problem. One of the TV screen  illumination bulbs is becoming dim. I didn't notice this when watching video's transmission from FIOS, but it is very noticeable on computer white screens. Fortunately, the TV is still under the Costco extended warranty. But I'm not looking forward to schlepping this back to Costco. At least Costco wont hassle me much about a refund.

---

### Post by djuke04 on 2009-04-14
I have a question about tv connectivity.  I hooked my intrepid machine up to my Sony LCD via HDMI and it worked, but the screen stretched over the edges where I couldn't see the menus etc.  In retrospect, I should have started with the tv... and changed the "zoom" or whatever first, but I didn't.

I changed the resolution of the output, bumped it down a notch, and now the tv says "Unsupported signal" and I can't see Ubuntu anymore.  Now here's the issue - literally, I'm stranded in Japan and have only two laptops plus this Ubuntu machine.  I need to get it working on the tv again, how can I convince Ubuntu to renegotiate the resolution with the tv, or just reset the resolution - WITHOUT having a monitor as an interface?

---

### Post by bobkny on 2009-04-15
This may be a case of the blind leading the blind - I'm no expert! But there may be a way to use RTP from one of your other computers to fix the computer resolution on your temporary display-less machine. Depends on whether you can connect the computers through a network. Good luck.

---

### Post by djuke04 on 2009-04-15
Alright, how would I go about trying that? They are connected on a wired network if that is a factor.

---

### Post by speed32219 on 2009-04-15
One way is if you installed ssh (you really should as a backup when playing with display devices), you can download a program called putty (putty.exe) and ssh into your ubuntu machine.  You need the network address of the ubuntu machine and use port 22 in the setup with putty.

Then you just connect and get a CLI in which you can fix what is broken including re-installing ATI/Nvidia display drivers.

---

### Post by djuke04 on 2009-04-20
I ended up getting a regular PC monitor cable (VGA/D-Sub) to do the trick.  Luckily the tv had the input! Now here's another puzzling thing: the PC input with the VGA cable looks MUCH better than the HDMI! Also, the HDMI doesn't fit the screen right, is that just crappy graphics processing? It's onboard... I know I know... but it's x4500HD and has integrated HDMI out so I thought I'd try it.  I'll order up another graphics card, but this one is handling compiz fine thru the D-Sub.

---

