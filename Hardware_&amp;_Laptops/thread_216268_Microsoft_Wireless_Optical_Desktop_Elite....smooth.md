---
title: "Microsoft Wireless Optical Desktop Elite....smooth scroll?"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by delfick on 2006-07-15
hello all

I have a Microsoft Wireless Optical Desktop Elite keyboard and mouse set
[http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=016](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=016)

The mouse has a smooth scroll button, which in windows is very smooth
In linux however, it is quite jerky

I was wondering if there was some way of making it smoother in linux?

(and while i'm at it, how to get the scrollbutton on my keyboard working?)

thnx

---

### Post by delfick on 2006-07-17
hmmm, i'll take that as a no?

---

### Post by ORBiTrus on 2006-07-17
Scrollbutton on your keyboard should be able to be handled by evdev.  Some posts in the Howto describe that.  Basic idea is to add an "InputDevice" section to xorg using output from "cat /proc/bus/usb/devices"

Smooth-scrolling is iffy - individual programs are responsible for how they interpret buttons being hit - and the scroll wheel is interpreted as (usually) buttons 4 and 5, with 1,2,3 being left, middle, and right respectively.

Now, if these programs scroll smoothly when you use the keyboard up/down, then it could be a bug to report.  If not, then you need to find something in the program.
eg: Firefox has general.smoothScroll under about:config

Let's not forget that smooth scrolling really is just a nice bit of polish, but it should be possible to do.  Although, I admin, the Windows version of SmoothScroll is actually much smoother than most Linux stuff.  I couldn't care less, but if you want to, see if you can change some constants in the GTK (which probably controls smoothscroll across most programs) to make things "smoother."  Also, don't forget that smooth-scrolling really is a bit of a cpu hog.  Oh, and I am pretty sure that Qt (KDE uses Qt) has smoother scrolling than GTK (Gnome uses GTK).  But I'm not sure.

---

### Post by delfick on 2006-07-18
k then....

thnx for that :D

---

