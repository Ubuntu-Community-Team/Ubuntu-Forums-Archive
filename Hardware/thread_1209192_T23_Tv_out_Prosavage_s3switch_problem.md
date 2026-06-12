---
title: "T23 Tv out Prosavage s3switch problem"
date: 2009-07-10
forum: Hardware
---

### Post by RedSh on 2009-07-10
Dear ppl, 

im sorry for opening up a new thread, but i i cant find any answer on this forum that i need, and on the others with similar problem i cant post.

i have sisters laptop, IBM T23, prosavage inside. im trying to get picture on her tv. 

I did put S3switch and tv output works great. 

BUT i dont see video, i just get green screen in Movie player or VLC crashes. 
i guess thats because i need PAL not NTSC.
for doing that i need to apply patch that goes with S3switch for T23. BUT i dont know how to apply that patch as i never done it before.

> 
[LIST]
[*]T23 users may need to apply [this patch]("http://ck.org.ua/dev/s3switch.patch") to avoid a Segmentation Fault
[/LIST]
 To apply the patch you will first need the source code for s3switch. 



$ patch s3switch.c s3switch.patch 
$ make 
# mv s3switch /usr/local/bin
This is not working for me, so im wondering HOW to do it and apply it and finally get my video pic. im hoping thats the only problem i need to solve, i need pal.

Look what this guy says
[http://www.danieleocchipinti.com/blog-linux-php-lamp-web/linux/debian-ubuntu-kubuntu/tv-out-thinkpad-t23-linux-and-windows](http://www.danieleocchipinti.com/blog-linux-php-lamp-web/linux/debian-ubuntu-kubuntu/tv-out-thinkpad-t23-linux-and-windows)

but still its not clear to me :)

i did have the same problem on my pc with ATI, but i solved it very easy, and now im struggling with this one for 4 days so far and i cant seem to find answer to my question on any board so far. HOW TO apply that patch!?

if you have any ideas or advices feel free to enlight me.

Thanx in advance.

---

### Post by ale_b on 2009-09-25
Hi,
my laptop (fujitsu-siemens) has a ProSavage too, and I'm trying to set the system up to use it as a (small) mediacenter.
Until a week ago, I had XP and Kubuntu 7.04 in dual boot, and used Kubuntu to play video files to the TV set. I just pressed the fn+F12 and it switched to the tv, the pressed again and voila' to the lcd. I did not install anything else than K.

Now, I just installed linux mint and the fn+F12 doesn't work anymore. Dunno why.
Installed s3switch and I can now switch to the tv play, but it's a little infortunate.
More: K 9.04 doesn't install: locks in multicolor unreadable screen during install).

More: boxee doesn't start (glx segmentation fault), xbmc requires at least 24bit color (and I don't know how to set).

I think we need a fix in graphical drivers...

---

