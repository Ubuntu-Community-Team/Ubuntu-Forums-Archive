---
title: "Upgrade headaches"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by chuckp on 2006-01-08
I'm new to Ubuntu and the Forums, so please bear with me.  I'm also pretty much a newbie to Linux, although I've been attempting to use it for a few years.  I mostly worked with Debian, but I had configuration issues with some of my hardware that I simply couldn't solve, nor could the local LUG.  Ubuntu solved those issues, so that's why I'm here.  Although, if I can't get this upgrade problem solved, I may go back to Debian and try again, because I never had problems like this with them.

First, I'm on dial-up, so downloading takes a l-o-o-o-ng time (24 hours+), plus the usual hassles of disconnects, etc.  So I really don't want to have to go through multiple sessions of this.  And when I add in a normal 14 hour day at the job, I don't have time or energy to hassle with this very much.

I installed Hoary and didn't have any problems, but upgrading to Breezy has been, to say the least, extremely frustrating.

I'm using Synaptic.  I changed the distribution info in repositories from hoary to breezy, selected smart upgrade and then install.  btw, I'm only downloading the main repository (main/restricted), and its still 1000+ files and nearly 500M.  I'll get the other repositories (upgrades, security, universe, etc.) after I get the base upgraded.

I managed, eventually, to get all the files downloaded today.  However, for some reason, the files were NOT saved correctly, the install failed, and I get to start over.

I do apologize, I failed to write down the exact error message, but it was an invalid file error, possibly size, and the error code was 9 iirc.  I haven't closed Synaptic, so if the error message is recoverable and someone will tell me where it is, I'll be glad to post it.

I could really use some help, here.

Chuck, the confused :confused:

---

### Post by Zeroedout on 2006-01-08
[quote=chuckp]I'm new to Ubuntu and the Forums, so please bear with me. I'm also pretty much a newbie to Linux, although I've been attempting to use it for a few years. I mostly worked with Debian, but I had configuration issues with some of my hardware that I simply couldn't solve, nor could the local LUG. Ubuntu solved those issues, so that's why I'm here. Although, if I can't get this upgrade problem solved, I may go back to Debian and try again, because I never had problems like this with them.

First, I'm on dial-up, so downloading takes a l-o-o-o-ng time (24 hours+), plus the usual hassles of disconnects, etc. So I really don't want to have to go through multiple sessions of this. And when I add in a normal 14 hour day at the job, I don't have time or energy to hassle with this very much.

I installed Hoary and didn't have any problems, but upgrading to Breezy has been, to say the least, extremely frustrating.

I'm using Synaptic. I changed the distribution info in repositories from hoary to breezy, selected smart upgrade and then install. btw, I'm only downloading the main repository (main/restricted), and its still 1000+ files and nearly 500M. I'll get the other repositories (upgrades, security, universe, etc.) after I get the base upgraded.

I managed, eventually, to get all the files downloaded today. However, for some reason, the files were NOT saved correctly, the install failed, and I get to start over.

I do apologize, I failed to write down the exact error message, but it was an invalid file error, possibly size, and the error code was 9 iirc. I haven't closed Synaptic, so if the error message is recoverable and someone will tell me where it is, I'll be glad to post it.

I could really use some help, here.

Chuck, the confused :confused:[/quote]

If you know which file, did you try deleting it and downloading it again? You probebly don't want to hear this, but with me, on both my laptop and my main box, i wasn't able to update it with switching the repos for some reason, it gave me an error, and when i had to restart, i couldn't get back into X. I had to download the cd, and update from that (switch the repos in apt to only read the cd).

---

### Post by chuckp on 2006-01-15
Thanks for the reply, zeroedout.

It wasn't one file, it was all of them.  I was searching around on Ubuntu and found a small note to the effect that upgrading from hoary to breezy is not supported.  And since I am not particularly happy about doing a clean install every time I upgrade, I just switched back to Sarge.

It isn't worth the hassle, Debian lets me do an upgrade without any special requirements.  I just need to get my printer and scanner working now.  Everything else is fine.

Those two pieces of hardware were why I tried Ubuntu to begin with, since I couldn't get them working in Sarge.  They worked fine with Ubuntu, but if I can't upgrade, I'm not willing to use the system.  Also had a lot of problems being able to do desktop configuration items, like adding or changing icons in the Applications menu, adding links to the panel, etc.  Just too many 'idiot-proofing' changes for me to use it.

My thanks to those who read my message, and to zeroedout for replying.

Chuck

---

