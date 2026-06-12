---
title: "Installation Maham."
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by timeagan on 2009-09-03
Hello everyone, I just recently invested in a brand new Eee pc (900a) that had a Linux OS on it. I had my eyes on putting Eeebuntu right from the moment I got it. 

Problem is here: Computer has been working fine ever since I got it until this morning. Issue is when I boot up, I get the opening screen that tells me that F2 is to enter DOS etc etc.. after that, the screen goes black (back light is still on) and it just stops. It's not completely black though, it has the little _ at the top left of the screen. Also, I noticed when this happens that if I press "escape" some sort of ancient greek dialect come up (its obviously not greek, it's geek.. but it's too complicated for me x)).

Although, here's the thing: I had download the OS off the platform and onto my desktop, in the .iso file, converted it too function through an external disc drive. So I try it out on my desktop, and I get the the installation wizard thing, so it works fine. I was going to wait until this weekend to mess with the installation.. but it has become slightly more urgent. Trying to be smart, I thought: I know how to fix this! I'll just plug the external hard drive into the netbook, press "esp" as it boots up and load the external hard drive and install Eeebuntu, that'll solve my issues! Obviously.. it failed. I get the same screen as when it boots normally. One little difference though: When it boots up on the hard drive, when the screen blocks on _ it flashes and it looks like it restarts. On the other hand, when I boot up with the external hard drive it stays steady (just a little more information).

Not being very competent I'm not sure what to do now. I'd like to avoid having to bring it to get repaired if someone could quickly help me out on this if it is not asking too much. I want to change from the original Linux OS, and install Eeebuntu from the external hard drive. Although, I really need the computer up and running for tomorrow, so anything that can pull me through tomorrow would be awesome. BTW I live in France, so it's 9PM here, just in case you are all from different time zones. I'm blabbering now sorry.

Regards,
Tim

---

### Post by earthpigg on 2009-09-03
can you go over what steps you took to install eeebuntu, please?

the 'standard' netbook method of installing Ubuntu, or an Ubuntu derivative from an already existing ubuntu system (you said you had it working on your desktop):

1 - download the .iso.
2 - plug a usb thumb drive in
3 - system -> administration -> usb startup disk creator
4 - done making the installation media.


5 - turn your netbook on.
6 - press 'del' or 'f2' or whatever it is to 'enter setup'
7 - from the bios setup, configure it to boot from a usb drive. 'boot priority' or 'boot order' are the key words you are looking for.


8 - boot from the thumb drive to desktop.
9 - press 'install'




that is probably the easest way. if you are still having problems, please be very specific about where exactly you are getting stuck.

---

### Post by timeagan on 2009-09-04
Thanks for the quick answer.

Okay, let me detail explicitly what exactly isn't working. When I boot up the net book and dont press anything it goes through the regular boot up until I get to the point where it shows my cursor which is a X on a black screen. Immediately after that, the screen goes black, flips on and it seems like it reset and keeps on giving me a screen like a command prompt. It gets stuck right there. If I press buttons such as esc, or backspace, it writes in something I dont quite understand. 

That's the issue.

Since there is currently Linux, and I am trying to put Ubuntu, I downloaded the Eeebuntu file I want, put it on my external hard drive, and converted the file from a .iso file to regular prgram that will allow to install from and external disk drive. I know it works because when i boot up my desktop, the program runs fine.

That's what I am trying to do.

When I turn on the computer and go into the DOS (at least thats what I think it is) I've tried several things:

  - 1: I put the default boot settings, to no avail.
  - 2: I put the external hard drive to boot first.. nothing happened.

That's what I've done so far.

Is this explicit enough, I am not sure what you want me to tell you about the problem. I'll type it up if this isn't enough. Thanks for your help and time.

Tim,

---

### Post by earthpigg on 2009-09-04
> When I boot up the net book and dont press anything it goes through the regular boot up until I get to the point where it shows my cursor which is a X on a black screen. Immediately after that, the screen goes black, flips on and it seems like it reset and keeps on giving me a screen like a command prompt.

> 
- 1: I put the default boot settings, to no avail.
- 2: I put the external hard drive to boot first.. nothing happened.

did you use "USB Startup Disk Creator" on that external hard drive? it will destroy all data on it, which is why people usually use a thumb drive, but that's what you have to do.


> 
Since there is currently Linux, and I am trying to put Ubuntu, I downloaded the Eeebuntu file I want, put it on my external hard drive, and converted the file from a .iso file to regular prgram that will allow to install from and external disk drive. I know it works be
Since there is currently Linux, and I am trying to put Ubuntu, I downloaded the Eeebuntu file I want, put it on my external hard drive, and converted the file from a .iso file to regular prgram that will allow to install from and external disk drive. I know it works because when i boot up my desktop, the program runs fine.cause when i boot up my desktop, the program runs fine.

can you describe how you did that, please?


have you tried making the bootable disk drive over again? a single 0 or 1 in the wrong place can cause something like this... and yes, it *can* happen to you :D

---

### Post by timeagan on 2009-09-04
No I didn't, and know I know what it probably doesn't work! I have two external disk drives.. so I can store all my crap on the other one while I do this :p. 

Simple really.. i used the winRAR application. Nothing crazy. 

I didn't do any sort of formatting or anythign so i didn't touch anything with 1's or 0's. So should I start backing up the extrnl hard drive and the wipe it- and THEN add the non .iso file I have? Or do I need to use the .iso one?

Thanks for the fast replies! :))

---

