---
title: "Post 9.04 Upgrade: Login Prompt not shown. Only a Busy Cursor Shown."
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by jvijayv on 2009-05-10
Hi all,

 I upgraded my xubuntu laptop from Gutsy to Hardy to Ibex to Jaunty. During my final install of Jaunty, unfortunately due to my mistake, my laptop's battery just died when it was in the middle of installing some packages. (Until that, all 2 upgrades i.e. Hardy and Ibex went fine in terms of the graphics display)

 So, when I restarted the laptop, it started up in command line mode. I looked through the forums and completed the upgrade somehow. (I got some message related to partial upgrade completed)

 Now, when I restarted, I was happy to see that blue login screen show up with a busy cursor. I waited a while to see if the login prompt would show up. But it never did. All I see is a blue screen with a busy (rotating) cursor.

 I tried going into command prompt and stop gdm and running startx manually. This brought up my wallpaper background correctly. But I do not see any mouse or any response to keyboard action. Some people were missing the XFCE-Panel. So, I tried using ALT+F2 to start the panel by hand but ALT+F2 did not have any effect in my x session.

 I have gone through this forum and tried a lot of work-arounds before posting this. I have even removed/purged the gdm package and tried re-installing xubuntu-desktop in vain. 

 People seem to have similar issues **AFTER** logging in. In my case, I can't even see the login prompt.

 My laptop has the following graphics card NVIDIA® GeForce™ 7000M.

 Any help would be appreciated.

Thanks,
-Vijay

---

### Post by orange-wedge on 2009-05-11
man i've been trying to wrap my head around this one for a while...  i doubt your video drivers are the problem.  seems like there is some xfce depency causing the issue, but thats really strange your keyboard/mouse do not work.  how does the output of your boot scripts look?  You can turn off the ubuntu splash screen by removing the word "splash" from the grub boot options:

For example change the following from
[html]/boot/vmlinuz-2.6.28-11-generic root=UUID=fb09e7b6-1128-4cea-8b19-2b82
1d65ed5c ro quiet splash[/html]to
[html]/boot/vmlinuz-2.6.28-11-generic root=UUID=fb09e7b6-1128-4cea-8b19-2b82
 1d65ed5c ro quiet [/html](Personally, I prefer to boot with no splash screen.)

what happens when you do the following:

[LIST=1]
[*]kill and restart GDM
[*]switch over to tty1 (Ctrl+Alt+F1)
[*]export your display and run xterm (export DISPLAY=:0.0; xterm &)
[*]then switch back to tty7 (Ctrl+Alt+F7)
[/LIST]
An xterm window should pop-up.  just trying to test the state of your X11 server.

finally is re-installing an option b/c this is real bad?

---

### Post by jvijayv on 2009-05-13
Hi!
 Thanks for the ideas. So, I tried starting without the splash screen and it seems like everything went fine except towards the end when I got the message asking me to check the syslog. So I did. And, I find this message in there - 
gdm[5007]: WARNING: Couldn't authenticate user 
last message repeated 13 times
...

gdm[5007]: WARNING: Couldn't authenticate user
last message repeated 26 times...

To me it looks like gdm is trying to auto login or something of that nature. But I have to enter my username and password to login. I never set it up for auto login. And it keeps repeating... So, I am going to check the forum for this message. During all this, the busy cursor keeps spinning with the blue background in the Graphical View. (tty7)

I stopped gdm from /etc/init.d
I tried the export DISPLAY.. command but I get this message
xterm Xt error: Can't open display: :0.0
I looked in tty7 after than and there is only a blinking cursor on tty7.

So, could it be that my Xserver is the problem here?

Well I could re-install all of it but I would prefer not to since I have a lot of stuff installed on it as I had been using it for over a year and half now.

Thanks,
-Vijay

---

### Post by jvijayv on 2009-05-14
I was able to install kde using apt-get since my wireless was still working. KDE startup user name prompt came up as expected. But when I tried to login into my username, it complained about unable to write to /home/username/.XICEauthority file. When I looked at the user on the file it was root. This probably happened because I installed kde using sudo maybe?? 

Anyways, changing this owner of the file from root to <username> helped me get a desktop with the KDE theme etc...

But one catch though - I can see my files on the desktop and open the file like pdf/doc etc using appropriate programs when I double click on them. But I am unable to navigate into my home directory. I get a message saying loading Thunar File manager or something to that effect. That window shows up on the taskbar for a while and later disappears.

I am unable to start firefox, terminal emulator, software update manager etc... I have a feeling some how my home directory permission is jacked up or one of the programs doesn't have the correct group id... Maybe...

Internet is working because I am able to add widgets to the desktop and get latest news etc...

Anyways going to zzz now. If any body has any advice on this issue, I would really appreciate it. Last option, I may end up re-installing 9.04 from scratch after backing up data even though I hate to do that...

Thanks,
-Vijay

---

