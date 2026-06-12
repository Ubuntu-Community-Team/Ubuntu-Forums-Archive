---
title: "Inspiron 5160 Display Settings"
date: 2008-04-30
forum: Hardware
---

### Post by toilet_duck on 2008-04-30
Greetings, all.  Long story short, I'm using xubuntu 8.04 on a Dell Inspiron 5160.  I've installed the restricted nVidia driver.  The laptop's display supports a maximum resolution of 1440x1050, but I am only able to choose a maximum of 800x600.  I recall that using previous versions of linux, it was sometimes necessary to manually edit your video configuration...but when I looked at my xorg.conf, I was confused.  I didn't see the values for hsync, vsync, resolution modes, etc.

Could someone give me a hand with this?  Here is my current xorg.conf:

[http://pastebin.com/m77029f6a](http://pastebin.com/m77029f6a)

Thanks for your time!  :)

toilet_duck

---

### Post by bdalzell on 2008-04-30
I am having the same problem with Xubuntu on an old Pentium 3 1GHZ Sony VIO (993L). I wanted to try Xubuntu on it because the PIII seems a bit sluggish with Ubuntu. When I first installed Ubuntu I was stuck with the 800 x 600 screen also but I found an application under "Applications > Other" called Screens and Graphics (displayconfig-gtk)* which has allowed me to reconfigure the display for Ubuntu. Now to see if I can get it working with the Xubuntu.

To clarify: there were two separate installations in two different partitions Ubuntu in one(hda5), Xubuntu(hda7) in another. Using displayconfig-gtk I was able to get the Ubuntu display to 1024 x 768 which is the capability of this laptop. Using only the tools I could find with Synaptic I could not figure out how to get Xubuntu out of 800 x 600 mode.

So I logged into the Ubuntu boot and then used Synaptic to add Xubuntu-desktop to that boot. Then restarting the computer and choosing a Xubuntu session  from the hda4 install resulted in the Xubuntu display manager having access to a 1024 x 728 screen.

So now I can do a Xubuntu desktop in the 1024 x 728 size.

But it is a bit of a workaround.

*Why "Screens and Graphics" isn't under System>Admin is a mystery to me.

I need to admit that my setup is probably more complicated than it needs to be. I had my equally ancient and slow Gateway 6200 laptop die and just took the harddrive from it and put it into the Sony. Amazingly the thing actually booted into Ubuntu command line but X did not work. So I installed Ubuntu again into the / (hda5) partition. from a CD.

Later I tried installing Xubuntu from a CD and it made its own partition (hda7) which I now need to get rid of except that hda7 is the partition in which the system looks for the GRUB at boot.

---

