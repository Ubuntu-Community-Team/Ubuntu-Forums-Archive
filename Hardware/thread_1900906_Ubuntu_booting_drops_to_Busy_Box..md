---
title: "Ubuntu booting drops to Busy Box."
date: 2011-12-27
forum: Hardware
---

### Post by nico932 on 2011-12-27
Hello!

I've been happily using Ubuntu for a little more than a year. About two months ago, some weird black screen started showing up in about 80% of restarts (Busy Box). Formatting and reinstalling didn't solve the problem. I tried several different Ubuntu versions, at the moment running 11.10. 

After some research I found out that it might be related to some root delays issues, and typing "exit" after a while prompted me to normal ubuntu login. The problem used to come and go, sometimes showing up, sometimes not (normal restars w/o busybox).

Now it's been getting worst. Sometimes I cant even normally boot, having to restart the computer up to 4 times before the "exit" command actually works. It's really moody, sometimes working, sometimes not. In the end I always manage to log in, but its taking ages!

The computer is an HP dv6000 series, that worked like a breeze until a few months ago the motherboard overheated. It was fixed and the computer worked normally for a while. The current hard drive is an Hitachi approx 1 year old. 

I've run some simple tests and everything seems to be working fine. Once logged in I have no problems like system locking, apps crashing or whatsoever. This leads me to think that it's not a hardware problem.

Besides when I replace the hard drive with a "Windows one", there are no problems in windows booting or functioning. The problems loggin in persisted when I mounted the Ubuntu drive in an external case and tried booting from there.  

Sometimes the busybox shows the following lines: 
udev [various 3 digit numbers]: timeout: killing '/sbin/modprobe -bv pci (or usb) [various 3 digit numbers] (and then comes a long list of numbers and letters)

Any help or insight on how to solve this would be greatly appreciated.

Thanks in advance!

---

### Post by marcus89 on 2012-02-19
I am not a proficient user of this Ubuntu but it is my main operating system now as my other computer has died.
I have been having the same problem recently.
I formatted an older installation (10.someting) that had some problem with me using the wrong drivers for a video card on this computer and installed the latest 11.10 version to start from a new installation.
The 11.10 live cd worked but after installing and restarting I would get to busybox with the same /sbin/modprobe (usb or pci) things that you had.
Your post is the first place I read to type exit after that to get it loading again and it got it working for me to load to the desktop like in the live cd but I still face the same startup issues.

---

### Post by ahallubuntu on 2012-02-19
Have you tested the hard drive?  If not, do so.  If you can boot into Ubuntu again, try installing GSmartControl and checking out the S.M.A.R.T. status of your drive.  If you can't boot into Ubuntu anymore (ever, just get busybox always), try launching SmartControl (basically same thing as above) from Parted Magic - which you can get on the Ultimate Boot CD.

SmartControl should show you S.M.A.R.T. attributes in your hard drive.  Any that are HIGHLIGHTED (in pink I think) are the ones you should worry about.  You can also run S.M.A.R.T. tests like the Extended Test which may take a few hours.

---

