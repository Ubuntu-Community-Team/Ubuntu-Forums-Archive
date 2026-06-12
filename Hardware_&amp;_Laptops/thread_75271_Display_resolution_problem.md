---
title: "Display resolution problem"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by hackyou on 2005-10-13
Hi, after downloaded and installed the fglrx package, X.org doesn't start at the default resolution of 1280x800 on my laptop with a mobility Radeon 9600 anymore...:( 
Hoary worked fine, what's happened?
That's very sad!
What can I do?

Thanks

---

### Post by JensenDK on 2005-10-13
Hello,

- Are you talking about just the default startup resolution?
- Can you change the resolution at all?

Regards

/Martin

---

### Post by hackyou on 2005-10-13
Hi, i'm talking about the X.org default resolution... with the old fglrx driver in ubuntu 5.04 it works fine with 1280x800, now if I install the new fglrx driver available with ubuntu 5.10 the default resolution is 1024x768 and I can't change it!

---

### Post by JensenDK on 2005-10-13
Try checking out the /etc/X11/xorg.conf configuration file if there is only the one current resolution you are using available in that.  I do not think its a driver issue (I might be wrong though) - you should be able to add more resultions here. 

If you have no idea about what im talking about - have a look at chapter 4 of this guide: [http://www.gentoo.org/doc/en/xorg-config.xml](http://www.gentoo.org/doc/en/xorg-config.xml) 

Regards

/Martin

---

### Post by hackyou on 2005-10-13
I know, I know... in my xorg.conf file the resolution is the right one 1280x800... but X only starts at 1024x768 :( 

I think i'll get back with hoary or try to downgrade the fglrx package.

---

### Post by ivanhoe on 2005-10-15
I'm sorry, but i am quite a begginer with linux and here is my problem. I have Gericom Hummer with intel extreme video card that works only in 640x480. Don't know what to do. This is only resolution avaliable with 60Hz refresh rate.

---

### Post by Joe_lurker on 2005-10-15
Check your /etc/X11/xorg.conf file in the screen section.  Make sure that the default depth has an entry in the subsection display for that mode an resolution.  Also see if you can change mode by using crtl+alt+(+) - using the + on the numeric keypad.

Joe

---

### Post by tseliot on 2005-10-15
Open Terminal or Konsole and type:

sudo dpkg-reconfigure xserver-xorg

When it asks you about your graphic card select it manually (don't do autodetect).

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor (try in google or if you have a manual of the monitor) this is very important.

It will ask you your desired resolutions, select the ones you need by pressing the SPACEBAR.

If you don't know how to answer the other questions you can use the suggested answers (which will work) by pressing ENTER (without typing anything).

3) After you finish, log out and press CTRL+ALT+BACKSPACE

4) log in and see if everything is displayed correctly and if you can select the resolution you need.

Tell me if it works

---

### Post by Shaggy on 2005-10-15
I'm have the same problem as the OP.  Already tried reconfiguring xorg and it did not work correctly.  Currently my only options for resolution are 1024x768, 800x600, and 640x480.  None of which are in my xorg.conf.  The only resolution I have in there is the 1280x800.

Everything is showing up correctly as far as I can tell in glxinfo, and fireglcontrolpanel.

---

### Post by tseliot on 2005-10-15
[QUOTE=Shaggy]I'm have the same problem as the OP.  Already tried reconfiguring xorg and it did not work correctly.  Currently my only options for resolution are 1024x768, 800x600, and 640x480.  None of which are in my xorg.conf.  The only resolution I have in there is the 1280x800.

Everything is showing up correctly as far as I can tell in glxinfo, and fireglcontrolpanel.[/QUOTE]
Try this method then:

[http://ubuntuforums.org/showthread.php?t=76387]("http://ubuntuforums.org/showthread.php?t=76387")

---

### Post by ivanhoe on 2005-10-16
Thanks for help. i did menage to change resolution and now its working fine.:smile:

---

### Post by Kirby on 2005-10-16
Well, I searched around the web for a while and found out, that it seems to be a bug in the fglrx-driver version 8.16.20. It simply isn't able to do widescreen resolutions:
[http://ati.cchtml.com/show_bug.cgi?id=160](http://ati.cchtml.com/show_bug.cgi?id=160)

Looks like a new driver (8.18.6) is released already... I hope it will be in the repos soon, because I use my Notebook for gaming also... can't do that without 3D Accelleration... :???:
Switched back to the standard "ati"-driver. This works with widescreen.

---

