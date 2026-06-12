---
title: "HP-Split-13-x2-PC Touchpad not working after installing 14.04"
date: 2014-05-05
forum: Hardware
---

### Post by paulravin on 2014-05-05
Hi, I have just bought a HP split, installed Ubuntu 14.04 and found the touch pad is not working.  


 I have searched and found a few touch pad fixes but not for this PC or version of Ubuntu, should I try these fixes anyway? I also found this but it is beyond my comprehension, I think it is identification of a bug regarding this problem:  
 
  [http://www.gossamer-threads.com/lists/linux/kernel/1912054](http://www.gossamer-threads.com/lists/linux/kernel/1912054)

I  followed one post, pasted a (comand?) into terminal and it seems that  the touchpad is recognised. I am useing an external mouse now and the  touch screen seems to work.

Any help for a beginner much appreciated!

---

### Post by paulravin on 2014-05-08
[COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]Strangest thing, the touchpad worked for 5 min!? Once I separated the screen from the base it stopped working again and has not worked since.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]Has anyone got any ideas on how to get my touchpad working?[/SIZE][/FONT][/COLOR]

---

### Post by paulravin on 2014-05-13
Hi, still trying to fix this issue, any help much appreciated!

---

### Post by claracc on 2014-05-17
Have you seen this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1312489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1312489) reported in launchpad about the touchpad?.

I think the situation is the same you describe, it seems there is a problem with kernel. In post 16 there is is a link with the patch to fix the problem.

---

### Post by paulravin on 2014-05-17
[COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]Hi, thanks for the link! [/SIZE][/FONT][/COLOR] 
 

 [COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]I have found a few bug reports that seem to be this same issue, do you know how I apply this info? I can guess but raelly have no idea which bit of that post is the fix and how I would fix my problem with it. [/SIZE][/FONT][/COLOR] 
 

 [COLOR=#1f497d][FONT=Calibri, sans-serif][SIZE=2]Do I copy / past part of it into terminal?[/SIZE][/FONT][/COLOR]

---

### Post by claracc on 2014-05-18
I don't know how to apply the patch.

What I would do is to click on this bug also affects me in launchpad's bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1312489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1312489) and then I would  ask there how to apply the patch to fix problem while the correction is delivered.

---

### Post by paulravin on 2014-05-18
Have done Thanks!!

---

### Post by paulravin on 2014-05-20
I have posted on launch pad, got some replies that I am very great full for and I want to help with bug reports but I just do not understand what is being talked about, links go to links I have no idea what to do with them, pages on how to report bugs again my knowledge of computer language is not up to it. I am reading and trying and just experiencing more problems with 14.04, today the operating system text is 1mm high, I have 6 posts about problems and none solved. 
The fix for my touch pad seems to be there but try and understand how to apply it, it is in another language. 
Anyone know of anyone who does IT work for Ubuntu? I need help quickly getting to the point of installing an earlier Ubuntu or windows.

---

### Post by paulravin on 2014-05-29
Follow up on my multiple posts with all of the issues with this machine. I had about 6 problems with the HP pavilion split, 2 were solved, then the keyboard stopped working and HP refunded my cash. Go HP for customer support, they did not support using Ubuntu and also did not use it as an excuse for a keyboard that would not even work in Bios.  
 

 I have now bought an Acer Aspire V7-582p, it is listed as compatible with ubuntu, runs on live CD no problem. Loaded it up and no screen. So am now a week into trying to solve it via forums with no success, am now looking for tech support for it or lap top shop with pre loaded Ubuntu in Australia that is not double the cost. Sound easy? Try it. It is getting to the point of back to windows, never had issues like this in 4 years of using Ubuntu, 14.04 compatibility with laptops seems to have gone down hill big time!
 

 Motto of my experience:
 

 * Running live cd does not mean it will work on that machine after install. You are taking on a complete gamble.
 * Forum post that a machine works with Ubuntu does not mean it will for me. (I am not stupid with computers but I am not a programmer)
 * Finding payed help with Ubuntu is near non existent.
 * Buying a new Ubuntu pre loaded laptop is near non existent in Australia, I found one shop with computers at 2 x the price. Maybe that just is the price of something that works?

Follow up for posterity.
 

 Everything on this Acer V7 now works. It took me 1 week of half days, communication with _5 different tech support / linux savy people_, lots of trawling the web, posting messages etc to get the screen working.  
 

 Fixed now (by installing on Legacy not UEFI, see other post) just so releaved to not have to go back to the continual headache that is windows. Thank you Acer tech support, credit where credit is due, the guys at Acer 'out of scope' technical support (From Australia 1800 144 519) worked out why my screen would not work and how to fix it in 10 min. They charge $75 and it was worth every cent.  
 

 When trying to fix a HP I also found the best and fastest way to solve problems was HP tech support threats of warranty voiding bla bla but they fixed my computer issues where no one else could.

---

### Post by shane-u on 2014-06-20
Hi paulravin,

Sorry to hear that you had so much issue with getting the touchpad to work on your HP Split x2 and that in the end you had other issues.  Thanks to this thread I have managed to get the touchpad working and it is as simple as updating the Linux Kernel.  Copy and paste the following commands into Terminal... (disclaimer: this worked for me but in modifying your system you take full responsibility for what happens) note, this is for 64bit installations.

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc5-utopic/linux-headers-3.15.0-031500rc5-generic_3.15.0-031500rc5.201405091635_amd64.deb
 
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc5-utopic/linux-headers-3.15.0-031500rc5_3.15.0-031500rc5.201405091635_all.deb
 
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc5-utopic/linux-image-3.15.0-031500rc5-generic_3.15.0-031500rc5.201405091635_amd64.deb

sudo dpkg -i linux-headers-3.15.0-*.deb linux-image-3.15.0-*.deb

Now do a Shutdown and then reboot the machine, do not do just a restart as this does not seem to work.

When you log back in you should now have a working touchpad.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/?C=N;O=D") this is the link to the most up to date kernels, you may want to use the newest.

---

