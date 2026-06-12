---
title: "Nvidia 7600gt"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by m1ck on 2006-12-12
Hi all, can some help me as im not sure which driver i need for it.

its an Nvidia 7600gt pci Xpress.

any help would be much appreciated.

---

### Post by adaptr on 2006-12-12
What do you mean by "driver" ?

In the text console, any video card will do.
When you first installed Ubuntu, it will have loaded the "nv" driver for you, so X works.
(I presume X works, but I can't be certain, of course - you provide absolutely no information.)
If what you want is ***accelerated OpenGL graphics***, you need to install the **linux-restricted-modules** package and use the "nvidia" driver instead of the "nv" one.
Next install nvidia-glx and edit your xorg.conf to also use the nvidia driver.

---

### Post by m1ck on 2006-12-12
its ok, i can't even install Ubuntu anyway i get this error and can proceed no further.

Failed to start x server (your graphical interface).

It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem


machine specs:

amd semprom 3400+ (not overclocked)
nvidia 7600gt pci Xpress video card
asrock mainboard K8NF4G-SATA 2

160gb hard drive
dvd rw drive

Sorry about this im a total newbie

---

### Post by Craig Caldwell on 2006-12-12
> **m1ck said:**
> its ok, i can't even install Ubuntu anyway i get this error and can proceed no further.

Failed to start x server (your graphical interface).

It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem


machine specs:

amd semprom 3400+ (not overclocked)
nvidia 7600gt pci Xpress video card
asrock mainboard K8NF4G-SATA 2

160gb hard drive
dvd rw drive

Sorry about this im a total newbie

Do a quick search for automatix 2.
you can use it to install the nvidia drivers

---

### Post by adaptr on 2006-12-12
I'm afraid Craig completely missed the point of your previous post.
You can't install *anything* until you have Ubuntu itself installed.

The best thing you can do is what it suggests, and post the output here.

---

### Post by m1ck on 2006-12-12
> **Craig Caldwell said:**
> Do a quick search for automatix 2.
you can use it to install the nvidia drivers


Thanks for that, but i cant install Ubuntu because of the said error, thanks for trying to help though. much appreciated.

---

### Post by m1ck on 2006-12-12
> **adaptr said:**
> I'm afraid Craig completely missed the point of your previous post.
You can't install *anything* until you have Ubuntu itself installed.

The best thing you can do is what it suggests, and post the output here.

ok will do, thankyou.

---

### Post by MetalMusicAddict on 2006-12-12
Are you using the Live disk or the text disk?

---

### Post by m1ck on 2006-12-12
here is the output:

X window system version 7.1.1

Release date: 12 may 2006

X Protocol Version 11, revision 0, release 7.1.1

Build operating system: Linux 2.6.15.7 i686

Current operating system: Linux Ubuntu 2.6.17-10-generic #2 SMP Fri

Oct 13 18:45:35 UTC 2006 i686

Build date: 07 july 2006

		before reporting problems, check [http://wiki.x.org](http://wiki.x.org)

		to make sure that you have the latest version.

Module loader present

Markers: (--) probed, (**) from config file, (==) default setting,(++) from command line, (!!) notice, (II) informational

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==)log file: "/var/log/xorg.0.log", Time: Tue Dec 12 20:47:34 2006

(==) Using config file: "/etc/X11/xorg.conf

By live disk i take it you mean loading and running ubuntu straight from cd?, if so i get the same error.

---

### Post by MetalMusicAddict on 2006-12-12
I think its because the free driver doesnt support your card. Odd because my 7900GT works.

If you installed from the text based disk you should be able to install the nvidia drivers from a terminal.

So did it install and you just get no screen? Terminal only?

---

### Post by m1ck on 2006-12-12
what happens is i run the Ubuntu cd, select install then i get the Ubuntu logo the progress bar completes and then i get the error.

---

### Post by MetalMusicAddict on 2006-12-12
This is with the "Desktop" cd right?

---

### Post by Rodneyck on 2006-12-12
That is odd, because my 7600gt card worked. 

Isn't there an option on start-up of the live cd to boot into some sort of safe mode?  It's been awhile since I have ran the thing. This might bootup with a generic video driver to at least get you in the door.

---

### Post by m1ck on 2006-12-12
@ Rodneyck: yes there is, but i get the same error.

---

### Post by m1ck on 2006-12-13
Erm so is that it then?.:???:

---

### Post by Craig Caldwell on 2006-12-13
Ok, note to self fully read post before typing.

I think I can be of more help this time. 

I had the same problem when I first picked up my new computer with a nvidia 7600gt. 

But with the latest ubuntu 6.10 every thing is fine. I would suggest downloading the alternate install cd and try again.

And then.... check out automatix 2 to get the nvidia drivers.

It took me several tries to get any linux distro working when I first started so don't give up it is worth it.

You will be compiling from source before you know it.

---

