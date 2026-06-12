---
title: "Gnome 13.10 Blank Screen when resume from suspend"
date: 2013-10-31
forum: Hardware
---

### Post by VideoRoy on 2013-10-31
I have been searching for a few days and and even thought my problem was related to a reported bug but it seems different.

I apologized if this is reported already and I missed it.

When I resume from suspend UbuntuGnome 13.10 x64 the screen is black and I cannot recover without power down.

1. This is my home built desktop and I have Nvidia GT9800 video card and I have tried both Nouveau and proprietary Nvidia 3.19 driver which I used previous in Ubuntu 12.10 (not Gnome)
2. My monitor is getting a signal on resume because it comes out of sleep mode.  In fact it goes from the gray screen to solid black after resume.
3. Ctrl+Alt+F1 does Not bring up a tty session.  Going back to Ctrl+Alt+F7 does not help either.
4. I tried changing Settings > Brightness & Lock to Never turn off screen but no help.
5. During normal operation if I let the screen blank after 5 mins (not suspend) it works just fine.
6. I have been using this desktop for many years and suspend with Ubuntu 11.x, 12.x (not Gnome) was no problem.

I have Ubuntu Gnome 13.10 32 bit running on a laptop and it resumes fine although I am not sure that means much for this problem.

My next step is to try Ubuntu 13.10 live usb key and see if I can suspend / resume.  I will try the same version Gnome Ubuntu 13.10 on a live key and see what happens there as well.

Any other ideas?

Thanks in advance.

---

### Post by VideoRoy on 2013-11-02
Update on my testing

**_Desktop Computer with Nvidia GT9800 video card with Nouveau or Prorietary Nvidia Driver_**

Ubuntu Gnome 13.10 x64 & 32bit = Fail to Resume
Ubuntu 13.10 = Fail to Resume
Xubuntu 13.10 = Fail to Resume

Ubuntu 13.04 = Successfully Resumes
Ubuntu 12.10 = Successfully Resumes
Ubuntu 12.04 = Successfully Resumes

**_very old Laptop Test Computer_**
Ubuntu Gnome 13.10 = Successfully Resumes

_**Netbook Computer **_
Xubuntu 13.10 = Successfully Resumes

I was thinking this was a Gnome problem somehow but that is not correct. I was willing to go to Xubuntu since I use it on my Netbook very successfully but that will not help.
 
Conclusion is something is broken in any of the Ubuntu 13.10 versions I tried for my Desktop computer.

---

### Post by VideoRoy on 2013-11-02
Spent a few more hours troubleshooting  and I have spent way too much time on this problem already. I will wait to see if it is resolved in a later update.  I am really enjoying Gnome Ubuntu 13.10 and this is the only item I have not been able to resolve.

My work around is going to be Hibernate.  I quit using Hibernate years ago since it was unreliable and really slow but after running some tests and getting it added to the menu it seems to work pretty well.  My computer boots pretty fast any way so this is only a 2 minute delay.

---

### Post by VideoRoy on 2013-11-10
Update on 2 more tests.

Loaded updated Nvidia 319.60 driver in Ubuntu 13.10 but suspend / resume still fails

Run live version of Gnome Ubuntu 13.04 Raring and suspend / resume works normally.

So the video driver makes no difference in Ubuntu 13.10.  This version has something else broken.

Previous versions of Ubuntu 13.04, 12.10, 12.04 and 11.10 all work fine on the computer an video card.

I have sent the crash report in.

---

### Post by Grendel336 on 2013-11-16
Any word on this? I am having same issues. 

Never had a problem with any previous release. Updated to 13.10 and any time I close lid on laptop and re-open I have a black screen which is completely unresponsive to any input.

I have to using "off" button to completely shut down my laptop and then restart after waiting a minute. 

Would love to hear some suggestions on how to fix this.

---

### Post by VideoRoy on 2013-11-16
No progress at all for me.  My older laptop that I tested does work fine but my desktop just will not work.

I believe my old laptop is using Intel graphics instead of Nvidia though.

---

### Post by Grendel336 on 2013-11-24
So here's what I think I've found. 

I upgraded from 13.04 to 13.10 through my wi-fi with the standard update kinda thing. After trying unsuccessfully to "fix" issue, I made a larger boo-boo and ended up doing a complete re-install from a live-cd I made. 

All my issues appear to be solved. (knocking on wood.....) 

I'd suggest trying a complete re-install from a current live-cd if you are still having issues.

---

### Post by VideoRoy on 2013-11-28
Thanks but I did a complete fresh install to start with.  I can run any 13.04 version of Ubuntu, Xubuntu, Gnome Ubuntu from a Live USB key and it will suspend / resume perfectly.  If I run any 13.10 of the same flavors it fails.  I have used every version of Nvidia driver available as well as the open source Nouveau and they all fail on 13.10.  It is not the video driver and it is not my hardware which a has run perfectly on previous versions going back to 11.10.

---

### Post by Kangburra on 2013-12-04
Any news with this, I am also stuck with it not working despite trying various "fixes" I still get the black screen on resume :(

---

### Post by k2chris1983 on 2013-12-05
Yes, any news on this? I have a laptop with the same issue on a Toshiba Satellite S75-A7221.

---

### Post by VideoRoy on 2013-12-14
No fix for me.  I have tried the latest upstream 3.12 kernel and it does not work either.

I really do not want to drop back to 13.04 at this point so I just shutdown if I am going to be away from the desk for an hour or more.

---

### Post by VideoRoy on 2014-01-22
Finally resolved but I am not quite sure what the fix was.  It was one of these 3 things.

1. My monitor was set to 59Hz and I changed to 60Hz - Not likely the fix but it fixed another problem I had.
2. Last update software update from the repositories. - More likely but my first test after the update did not seem to make a difference.
3. Changed USB attached mouse and keyboard as well as new USB attached KVM switch - More likely although the crash reports were not pointing this and my tests bypassing the KVM and direct connect did not make a difference before.

The strange thing was I can still boot to USB key with 12.04 or 12.10, 13.04 and resume no problem.  So it seems that something broke in 13.10 in support of the HW I had.

Regardless I am not going to mess with figuring out anymore what was broken.  Spent way too much time already.  Marking thread closed.

---

### Post by chaushev on 2014-03-03
Running Ubuntu 13.10 x64 Unity on a Lenovo G560 laptop. Nvidia 310M GPU. I fail to resume with Nouveau or nvidia 319 proprietary. Any idea on how to resolve this? Suspend/sleep/hibernate is an option I really miss from Windows 7.

---

### Post by The_Autonomist on 2014-03-08
Also having the same issue. When i open my laptop, i get a black screen with a blinking caps lock light. the only thing that "fixes it" so far is covering the vents and essentially letting it run hot until it cuts off. then. when i turn it on. it works perfectly...until the next time it happens. :/ any ideas??

---

### Post by gordintoronto on 2014-03-08
Doing thermal shutdowns will eventually damage the computer. If you lean on the power button, it should shut down within 10 seconds.

---

### Post by The_Autonomist on 2014-03-08
Yeah, but just doing a hard shut down via the power button doesn't help either. When you turn it off and turn it back, it goes to the same hanging black screen and flashing lights. 

thermal shutdown has been the only thing that "fixes" the issue so far.

---

### Post by thee-patrician on 2014-03-27
I have been having issues with hibernate and resume for months, blank screen or just blinking cursor after "successful" resume. 
I tried installing/uninstalling all the various packages for it, the kernel option and the userspace option all to no avail.

After I read that OP had changed his USB attachments [B]I tried resuming without my external mouse/keyboard plugged in and it works fine now.

[/B]I have a Microsoft Natural Multimedia Keyboard 1.0A and a Gigabyte GM-M6800 Mouse.

---

### Post by Peter_Janson on 2014-06-27
I had this problem as well after fresh install of 14.04.

Finally found this answer [http://askubuntu.com/a/129041](http://askubuntu.com/a/129041) (i.e. Turn off screen lock in the "Brightness and Lock" settings.) and that worked for me.

---

