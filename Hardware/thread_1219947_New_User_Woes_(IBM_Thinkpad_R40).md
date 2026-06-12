---
title: "New User Woes (IBM Thinkpad R40)"
date: 2009-07-22
forum: Hardware
---

### Post by EtherBoo on 2009-07-22
Hello all, I've used Linux off and on, but I finally convinced my supervisor (AV Department at a University) to put Linux on some of the older laptops to help with performance and to use them primarily as Power Point flippers.  He agreed as long as I could -make it simple- for a regular user.  So instead of a Windows XP install, I put 9.04 on the laptop.  It loaded pretty nicely, and ran great.   

Then came the fun stuff.  First was to get MS Office 2007 installed.  I lurked a bit, and found a nice tutorial and installed it, which was easier than I thought.  This is where everything went downhill.  

Performance went to crap with wine, which I'm not really surprised at, but I figured I could at least get OpenOffice working.  OpenOffice ran a bit better, but not by much.  I was pretty disappointed to be honest.  What really killed it for me was that OpenOffice did not appear to have any of the theme's used by MS Office, so the presentation skins would not work on the Power Point.  

My next, and biggest problem came with the VGA output.  We have projectors all around school in every classroom on campus.  I connected the laptop to a VGA cable, and I can't get it to output to the projector, or detect it in the Display Settings.  I did some seaching, and found nothing.  Any suggestions on how I can improve performance and get VGA output working?  If it makes a difference, I'm about halfway certain that this particular IBM R40 has an Intel Centrino and an Intel video output device, as opposed to those who got it with an ATI video accelerator.

---

### Post by pro003 on 2009-07-22
Good that you made to convince your professor about linux.. Now I would recommend you to install 8.04 LTS because at least from my experience it runs better wine and other crossover apps. I'm running 9.04 now and I can tell you that when I open some MS app through wine, my cpu's are high at 99%, and to be honest I never traced that problem as I don't use wine that much...

Someone with a bit more experience should help you with problems you're facing considering Ubuntu 9.04.

Good luck.

---

### Post by EtherBoo on 2009-07-22
Thank you for the advice.

I'll give that a try and see how it goes.  I had a feeling an older version might be better for an older laptop, which makes sense.

Do you have any idea on how I might be able to get the VGA output working?  If I could get office running smoothly, and VGA output, I think my supervisor will want to switch the older machines to Ubuntu for that purpose.

Also, I've heard a lot of mixed things, but what are the advantages of using Kubuntu or Xubuntu?  I read that x is much more lightweight, but some people say there are more features while others say there are less features.

Really, I just need the best for older systems at this point.  One of the appeals of Linux is that the laptops will not be as susceptible to users installing whatever software they want, and not needed to bog down the system with anti-virus (since it's an older system).

If this goes over well, we also might consider doing dual boot for when something more than Power Point is needed, but we would want to password protect the Windows partition so users could not just reboot into it if they did not like Linux.

---

### Post by pro003 on 2009-07-23
As far for flavors of ubuntu, that depend on users needs and taste. Of course some are lightweight some are not, some have more of this, some don't, but what's really matter is what are your needs. I would therefore recommend you take a look of them on [ubuntu's main site]("http://www.ubuntu.com") and see what's suits for you.

And for dual booting, ubuntu/linux users by default must enter root password in order to access windows partitions, although the first user is by default during and after installation of ubuntu 'a root'. So if you want to make any restrictions you should first go to System > Administration > Users & Groups and there make changes, i.e. edit roots properties and assign a different password and add more users and administrate their rights.

I'm not sure I can help you with VGA output from laptop while in ubuntu, I never tried such things and better not talk about it, but I would suggest you to make a new thread/post and put right in the subject a direct question like "Help with VGA output" or  you'll think of something am sure...

---

