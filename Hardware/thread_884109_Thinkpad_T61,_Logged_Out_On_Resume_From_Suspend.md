---
title: "Thinkpad T61, Logged Out On Resume From Suspend"
date: 2008-08-08
forum: Hardware
---

### Post by Zeike on 2008-08-08
I have a ThinkPad T61, model 7662CTO laptop, with an nVidia NV140m.

I am running a fully upgraded Hardy Heron amd64/x86_64.

I have successfully (almost) gotten suspend to RAM working following the instructions found here: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Suspend_with_Nv140m](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Suspend_with_Nv140m) .

However, when I resume from suspend I find that I am currently logged out of my gnome session.

Has anybody else had similar problems or fixes?

Thanks.

EDIT:  I've also noticed that when resuming X11 switches from vt7 (ctrl-alt-7) to vt9 (ctrl-alt-9), or from 9 back to 7.  (It would probably take 8, but 8 is being used.)

---

### Post by cdiggity on 2008-09-09
I'm having the same problem. I didn't run any updates between june 26 and august 14th, and then I did them all and I believe the problem started after that.

I'm running another 24 updates today (Sep 9) to see if that helps.

Did you figure it out!?

I should note I have a Lenovo R61i with intel graphics

---

### Post by cdiggity on 2008-09-22
I followed the instructions on thinkwiki for the changes to make to for proper resume/suspend on hardy, especially with regards to some S3 settings.  My acpi file was different than what they recommended on thinkwiki because of changes I had to make to get suspend/resume working on gutsy.

fixed now, and faster!

---

