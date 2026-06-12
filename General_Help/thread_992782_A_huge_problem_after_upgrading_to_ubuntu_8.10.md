---
title: "A huge problem after upgrading to ubuntu 8.10"
date: 2008-11-25
forum: General Help
---

### Post by metzuyanut2000 on 2008-11-25
Hi guys... I'm really desperate.

3 weeks ago I upgraded my ubuntu version(from 8.04) to 8.10.
The upgrade process seemed to go well, just as previous ubuntu upgrades I did before. 

As restarted my computer I got into my new ubuntu login... 
and then there was a problem: after I entered my username and password, my screen turned black with strange purple horizontal lines, then turned all pink and then returned once again to the login(asked me again to enter username&password).

I tried to solve this problem in different ways, but none of them worked: the screen always get stuck this way and then returns to the login. As you can understand, I can't reach gnome, and the funny command line I could actually use didn't help me at all.
 
I prefer not to use the solution of formatting the whole disk and installing ubuntu again, I have a lot of important data and it will be a really big deal to burn it all.

Hope u can help me. I'll appreciate it very much, especially since it's very urgent and for now I must use the horrible vista OS that makes me sick instead.

Thank's a lot for the helpers...

---

### Post by kpkeerthi on 2008-11-25
Are you choosing the right kernel that came with 8.10 from GRUB menu?
What graphics card do you have? Try reinstalling the graphics driver from the Recovery Mode in GRUB.

---

### Post by metzuyanut2000 on 2008-11-25
Thank you,

I have 4 different kernel versions in grub, none of them works(and how do I know which one should I use?).

Anyway, I tried reinstalling the graphics before, but it didn't help... 

- sudo dpkg-reconfigure xorg didn't help.
- sudo dpkg-reconfigure xserver-xorg didn't help(maybe I'm not choosing the right options?).
- sudo Xorg -conf gave me an error message
 Xorg: symbol lookup error: /usr/lib/xorg/modules/drivers//nsc_drv.so: undefined symbol xf86GetPciVideoInfo


I'm sort of a beginner(need ubuntu for work&study and don't deal much with the technical stuff) so maybe I'm not doing it properly. Is there another way?

I have dell inspiron 6400 laptop with intel 945GM graphics drive if that means something.

thank's again.

---

### Post by Zorael on 2008-11-25
Upgrading is always a risky business, sadly.

Does it work if you run it off a live cd/usb stick?

---

### Post by linux_tech on 2008-11-25
Can you post output of-
```
lspci | grep VGA
```
```
cat /etc/X11/xorg.conf
```

---

### Post by kpkeerthi on 2008-11-25
> **metzuyanut2000 said:**
> Thank you,

I have 4 different kernel versions in grub, none of them works(and how do I know which one should I use?).


The one that has the version number latest.

---

### Post by kleeman on 2008-11-25
Try the workaround in the last post in this bugreport

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-nsc/+bug/265035](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-nsc/+bug/265035)

i.e. the renaming trick

---

### Post by metzuyanut2000 on 2008-11-25
Thank u all.

zorael:
it works from live cd of 8.10 I burned, but as a "new OS" and I can't(or don't know how I can) reach my data from there.

kpkee:
OK, that's what I'm doing.

tech:

lspci | grep VGA   ->
00:02.0 Vga compatible controller: Intel corporation mobile 945GM/GMS , 943/940 GML Express Integrated Graphics controller(rev3)

cat /etc/X11/xorg.conf   ->
(the file's content)

Section "Device"
        identifier "Configured Video Device"
        option  "use FBDev" "true"
endsection


Section "Monitor"
        identifier "Configured Monitor"
endsection


Section "Screen"
        identifier "Default Screen"
        Monitor  "Configured Monitor"
        Device  "Configured Video Device"
endsection

---

### Post by jimreynold2nd on 2008-11-25
uhh... seems like a problem with compiz to me. because you have the GDM loaded, graphic driver working (at least to display the login screen). TRY to disable compiz some way from tty1 (Ctlr-Alt-F1).
Fast way I was able to think of is:
```
find / -name 'compiz'
```
there is a file with name of just 'compiz'. Do a sudo mv to rename it to something else and relogin. If it works, you at least have something to work on that is not the command line.

---

### Post by kpkeerthi on 2008-11-25
Remove the folder ~/.config/autostart and reboot.

---

### Post by metzuyanut2000 on 2008-11-25
jim: 
I didn't find a "just compiz" file, only directories. Where can it be?

kpkee:
I don't have such folder

edit:
I tried the renaming trick. It did create me a new xorg file but even after I moved it to /etc/X11/xorg.conf nothing has changed.

---

### Post by MeURi on 2008-11-25
Maybe a useless note, but the ~ means your home, so the real folder is /home/<username>/.config/autostart.

Also, post here the contents of your Xorg.0.log, placed in /var/log/, if you don't solve your problems, so that we can see the errors you got.

And enclose the messages in [code] tags, it improves the post's readability ;-)

---

### Post by metzuyanut2000 on 2008-11-25
I know what ~ means, and still I don't have an "autostart" folder neither in my user's and root user's "home".

thank's anyway.

is there something else I can try?

---

### Post by eeeek on 2008-11-25
Others will have a much better idea of how this is done, but...

Keep in mind that, I think, your home directory is on a different partition that your OS. So you might think about doing a fresh install, but leave your /home partition alone. 

Granted, I think you would lose all the additional software that you've installed.

---

### Post by directcharitycontribution on 2008-11-25
can u get some terminal access from boot menu, or with a rescue disk?

---

### Post by metzuyanut2000 on 2008-11-25
I can get to a white strange looking terminal after I get the login screen. But why? what's wrong with the recovery mode?

---

### Post by jimreynold2nd on 2008-11-25
If you find something in the form of something/bin/compiz then that's it. And it's not a directory, it's a file without any extension.

And the autostart, if you use gnome, it should be in ~/.config/autostart/
Notice the little dot before "config". It means that it's a hidden directory and will not show up in Nautilus and ls by default.

---

### Post by metzuyanut2000 on 2008-11-26
jimreynold2nd, you are god!!!!!!!!!!!!!! :KS:KS:KS:KS:KS
the problem was that stupid compiz indeed.

Thank you sooooo much....
now I can work freely again :)



(and for the record: I know how hidden folders look like, and I did easily find /.config in both my user's and root's home directory, but still-no "autostart" in both places)

---

### Post by jimreynold2nd on 2008-11-26
Well, nice to hear that it's working. BUT (yea, there're always but's) the problem is not fully fixed :(. You still have some incorrect configuration and you won't have desktop effects at best (compiz is desktop effect) or even some other problems later. But if that doesn't affect your works, then :)

Sorry ruining your excitation lol. But good job! You're half way of fixing it.

Anyway, try to dig around the forum for fixes on graphic card drivers and monitor problems - at least it's easier now with Gnome working :)

---

### Post by metzuyanut2000 on 2008-11-26
I understood that, and I don't need compiz. 

I tried using different kinds of compiz features in my previous ubuntu version a little bit, but as a matter of fact I'm not really a huge fan of graphical effects. Just need my OS for "usual" work.

Hope there won't be additional problems later.
Thank's again.

(I'm sort of a beginner, but not a complete fool... I know what are hidden folders and what is compiz)

---

