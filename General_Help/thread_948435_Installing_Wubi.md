---
title: "Installing Wubi"
date: 2008-10-15
forum: General Help
---

### Post by Dracion on 2008-10-15
Hi,

I've been thinking of installing Wubi for a while now, mainly because it's the easiest option given the position I'm in. To cut a long story short, I use a shared computer with some important stuff on it. Anyway, before I go ahead and install, I have a couple of questions.

1) I've been told that fragmentation slows down Wubi. I defragment my the files on my hard drive daily and the freespace about once every 2 weeks. Is this enough to ensure that Wubi isn't slowed or would I need to defragment more often?

2) I'm a bit unsure about graphics drivers. I have a Nvidia Geforce 8600GT 512MB graphics card, so would the linux drivers from the Nvidia support site work or would I need to use something else?

3) How much HDD space would I need? I'm not planning to install that much, so is 10GB sufficient? Can I increase the amount of space if need be?

Added; 4) Could I access my windows stuff in Ubuntu?

And help would be appreciated, thanks :)

---

### Post by howefield on 2008-10-15
Should be little fragmentation on your disk given your regime, but just defrag before you do the install. 

I use an nvidia 8500GT and works fine, with the Nvidia drivers, so I'd guess the 8600GT would likewise.

Personally, I'd give it 15 to 20gig, but if you really aren't installing that much, then 10 should be fine. Not sure about resizing a Wubi install so can't comment.  

And you will be able to access your windows files from Ubuntu just fine.

---

### Post by Ms_Angel_D on 2008-10-15
You may want to check out [this guide]("http://www.ubuntugeek.com/the-extremely-simple-guide-to-installing-ubuntu.html"), it's a very easy to follow Wubi How To.

---

### Post by Dracion on 2008-10-15
Thanks for the advice :)

I downloaded the wubi installer today, however I'm unable to start downloading. I entered all the required information and select Kubuntu-KDE4, since I prefer the look of KDE 4 to GNOME, but when I try and install all I get is "The download was interrupted with the error". Any ideas what's going wrong?

Thanks.

---

### Post by howefield on 2008-10-15
Not sure about downloading direct from the Wubi site, but you can download the Ubuntu CD from ubuntu.com and burn to cd.

Place cd into your drive with windows booted up and you should get 3 options, the middle of which is to "Install inside Windows". (Wubi)

---

### Post by Dracion on 2008-10-15
Yes, but I'm trying to install Kubuntu with KDE4, as opposed to Ubuntu. It doesn't have the option to install inside Windows on the Live CD.

---

### Post by ago on 2008-10-15
For kde4 you are better off using wubi 8.10 rev 11:

[http://wubi-installer.org/devel/minefield/Wubi-8.10-rev511.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev511.exe)

Note that it requires a new ISO, also note that you might have to edit menu.lst manually to boot (should be fixed with tomorrow's ISO).

---

### Post by numbercruncher86 on 2008-10-16
concerning the driver you can also check it with a live cd

---

### Post by ago on 2008-10-16
They have changed the kde4 urls server-side, this is fixed in wubi 8.10.
You have to use rev 512.

---

### Post by Dracion on 2008-10-19
Oh well, I decided it would be easier just to install Kubuntu then get  KDE4 from there. Thanks anyway though.

---

