---
title: "Creatting Image From ISO makes .exe"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Ltrra on 2008-12-18
So here is my problem, I am currently working on old (3 years) Linux machine (Dell optiplex 170L).  The machine has no floppy drive nor a cd/dvd (either or) drive.  Our network does not support Linux machines so I can not access the internet to get updates unless I take the machine home.  I have connected a portable DVD/CD combo to a USB port to use.

Now, I downloaded the ISO from the Kubuntu website and used software (Roxio) to make a LiveCD.  I popped it into my desktop (Windows based) and it launches and i get to test out Kubuntu 8.10. I LOVED IT.  So, I decided to make that the operating system for the Linux machines we would be updating (4 of them).  So I take the LiveCD and put it into the external drive on the Linux.  Machine reads it and all seems well, so I restart the computer and hit F12 and try to load from CD. To my uder suprise it won't allow me.  I get into the OS and look at the files on the CD and take note of the fact that the LiveCD is in .EXE format.

What do I do?  How do I make an LiveCD that will run on a Linux with a Windows machine?

---

### Post by logos34 on 2008-12-18
> **Ltrra said:**
> To my uder suprise it won't allow me.  I get into the OS and look at the files on the CD and take note of the fact that the LiveCD is in .EXE format.

What do you mean 'won't allow me'? -- no option to boot cd or there is but when you select it nothing happens?  Maybe the Bios doesn't support USB optical drive boot (although most computers from the last 7 or 8 yrs support USB hard drive boot).  

the .exe you saw was just the program executable so you can open the disc on the windows desktop.  You should be able to boot the disc on any machine

Maybe try a different burning program like Infrarecoder [as explained here.]("https://help.ubuntu.com/community/BurningIsoHowto#Windows")

---

### Post by jenkinbr on 2008-12-18
The executable that you see is simply either the wubi installer, or possibly the mini-preview of ubuntu.  Your disk should still be valid.  Are you sure F12 is the key you need to press - on my system at home, it is, but I have worked on some that require the DELETE key or F2, F1, or F10 (or a combination).  Check the documentation for your PC, and also see if there is any text displayed anywhere when you first turn the machine on that tells you what key you need to press.

---

### Post by Ltrra on 2008-12-18
> **logos34 said:**
> What do you mean 'won't allow me'?

the .exe you saw was just the program executable so you can open the disc on the windows desktop.  You should be able to boot the disc on any machine

Maybe try a different burning program like Infrarecoder [as explained here.]("https://help.ubuntu.com/community/BurningIsoHowto#Windows")


Thanks for the update on what the .exe is.  When I choose to boot from CD it reads the disk and says there is no valid boot (or something to that extend, not near the machine to check)

I'm assuming now that the disk may be a bad burn or such.  I'll make one with Infrarecoder and see what that does.  

Is there anyway to launch the LiveCD from a terminal?  Maybe I could use that as a work around if the external CD drive is causing problems.

---

### Post by logos34 on 2008-12-18
> **Ltrra said:**
> 
Is there anyway to launch the LiveCD from a terminal?  Maybe I could use that as a work around if the external CD drive is causing problems.

well, if you can't get it to boot the external cd drive, you could copy the .iso to the hard drive and run it from there:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
('Live CD')

The only problem I see is that unless you have some unused/unpartitioned space on the drive or another partition you can unmount and shrink, you'll have to shrink / and that requires you boot from a live cd to create the extra partition (/ cannot be mounted during resize), which is something you can't do.

What about making a live USB flash drive ubuntu installer?  Is that an option?

---

### Post by Ltrra on 2008-12-18
> **logos34 said:**
> well, if you can't get it to boot the external cd drive, you could copy the .iso to the hard drive and run it from there:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
('Live CD')

Oh wow, thank you so much!  I will try this ASAP

---

### Post by Ltrra on 2008-12-18
> **logos34 said:**
> 
What about making a live USB flash drive ubuntu installer?  Is that an option?

The computer has usb ports and reads them so I would say yes.  But how do I do that?

---

### Post by logos34 on 2008-12-18
If for any reason you can't make a small partition on the hdd, and you have a USB flash drive, you can make a live usb like this from windows:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

good luck

---

### Post by Ltrra on 2008-12-18
> **logos34 said:**
> If for any reason you can't make a small partition on the hdd, and you have a USB flash drive, you can make a live usb like this from windows:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

good luck


Thanks again.  It shouldn't be a problem there is 32gigs left on the hard drive.

---

### Post by jenkinbr on 2008-12-18
> **logos34 said:**
> well, if you can't get it to boot the external cd drive, you could copy the .iso to the hard drive and run it from there:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
('Live CD')


Thanks! I myself will have to try this.

*Runs to do this on my P4 512MB rig*

---

