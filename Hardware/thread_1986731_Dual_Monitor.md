---
title: "Dual Monitor"
date: 2012-05-25
forum: Hardware
---

### Post by xcrunner78 on 2012-05-25
Hello all,

I am sort of new and am still learning how to use Ubuntu.  I recently downloaded the latest LTS 12.04.  Yesterday everything was working great.  Today I cannot get dual monitor to work.  When I plug my laptop into an external monitor, the laptop goes blank and only the monitor displays.  I go to display and click on the laptop and turn it on, then I hit apply.  Nothing happens.  I close Display and re-open it and the laptop is turn off.   Does anyone have any ideas what I am doing incorrect here?  What sort of other information do I need to put down here to get this corrected?

Thanks!
Jason

---

### Post by xcrunner78 on 2012-05-27
So, I tried a few things.  In the displays, I click on the laptop and turn it on and click on the monitor and turn that off, then my laptop works.  When I click back on the monitor and turn it on, my laptop displays turns off, but it says it is on in the display windows.  I got aggravated and re-installed and that did not fix the problem.  I have no idea what to do and I have a Master's Defense this Thurs.  Please help if you can!

Thanks,
Jason

---

### Post by alphageek6 on 2012-06-10
I just started having this problem.  I used to be able to power up with an extenal monitor installed and I would get an dual Monitor setup.  Recently whenever I plug in an external monitor my laptop monitor turns off.  Attempting to turn it back on in the display settings does nothing.
 
I am a rather new Linux and an considering moving away from M$ but need a little help.  I am using Ubuntu 12.04 and these monitors have been working fine.  It is not the laptop monitor as if I detach the external monitor the internal monitor comes right on.
 
Would appreciate any help.

---

### Post by xcrunner78 on 2012-06-11
Hi alphageek6,

I learned that it is a bug:  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796030](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/796030)

I was told try disabling kernel mode setting.  But I didn't know how to do this, so I went back to 10.04 until the newest version of 12.04 is released with the 12.04.1.

Sorry that I am no help.

Jason

---

### Post by Ashrael on 2012-06-12
I have some problems too with a dual monitor setup (netbook+21").
If I start the machine with the 21" attached to it, it only gives two black screens with a pointer. Then if I physicaly remove the monitor cable and re-attach it after 5 seconds it starts to work as I desire (and set in the settings). I have installed Jupiter applet, which gives me options for video also, try that I say...
Also: [http://ubuntuforums.org/showthread.php?t=1987792](http://ubuntuforums.org/showthread.php?t=1987792) I WANT IT NOW! :P

---

### Post by areUKEidding on 2012-06-15
I also have problems with the recent updates and my external monitor. Except for me, ubuntu does not recognize the external monitor at all. I can boot into Windows and everything works as before but already at GRUB only the laptop display works.

I am a bit fed up with this, is it really so complicated to implement dual monitor support in ubuntu? I was already confused when everything worked great using the live CD, but after installation just like now only the laptop display works. I was so relieved when I got everything to work, and now all of that is for nothing again. What happened?

---

