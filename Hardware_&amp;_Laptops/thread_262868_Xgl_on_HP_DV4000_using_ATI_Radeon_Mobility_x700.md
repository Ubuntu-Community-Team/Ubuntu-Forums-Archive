---
title: "Xgl on HP DV4000 using ATI Radeon Mobility x700"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by Bagboy23 on 2006-09-22
I'm really confused and about to give this another go, but can someone direct me to any posts, documents that is guaranteed to make this work on my Linux. 

I'm quite eager to see what all the fuss is about.

---

### Post by MetalMusicAddict on 2006-09-22
I would just try to get your driver working properly 1st.

I have a nVidia setup so Im gonna wing it.

Im gonna assume you are still using the 386 kernel.

[LIST]
[*]To to Synaptic [SIZE="1"]System>Admin>Synaptic Package Manager[/SIZE]
[*]In the "Search" field look for FGLRX
[*]Check **fglrx-control, linux-restricted-modules-2.6.15-27-386** and **xorg-driver-fglrx**
[*]Make sure your using the "2.6.15-27-386" kernel first. If not search for it and get it.
[*]After that hit "Apply"
[*]Now after everything is installed do this first.
[*]From a terminal (I know) **sudo dpkg-reconfigure xserver-xorg**. Copy and paste that in.
[*]Answer the defaults to most things except these: When it askes about the video driver to use, answer fglrx. When it gets to a screen where its askes you about resolutions, press the spacebar where you want a x for the res's you want. Then after that pick the default res and refresh. When it askes, pick the medium mode.
[*]Reboot.
[/LIST]

Post back after that.

---

### Post by Bagboy23 on 2006-09-22
> **MetalMusicAddict said:**
> I would just try to get your driver working properly 1st.

I have a nVidia setup so Im gonna wing it.

Im gonna assume you are still using the 386 kernel.

[LIST]
[*]To to Synaptic [SIZE="1"]System>Admin>Synaptic Package Manager[/SIZE]
[*]In the "Search" field look for FGLRX
[*]Check **fglrx-control, linux-restricted-modules-2.6.15-27-386** and **xorg-driver-fglrx**
[*]Make sure your using the "2.6.15-27-386" kernel first. If not search for it and get it.
[*]After that hit "Apply"
[*]Now after everything is installed do this first.
[*]From a terminal (I know) **sudo dpkg-reconfigure xserver-xorg**. Copy and paste that in.
[*]Answer the defaults to most things except these: When it askes about the video driver to use, answer fglrx. When it gets to a screen where its askes you about resolutions, press the spacebar where you want a x for the res's you want. Then after that pick the default res and refresh. When it askes, pick the medium mode.
[*]Reboot.
[/LIST]

Post back after that.

Ok thanks mate.

My Ubuntu is now installed, but my resolution is 1024 x 768 where  the native resolution should be 1280x800. Will your trick sort out my resolution?

---

### Post by MetalMusicAddict on 2006-09-22
> **Bagboy23 said:**
> Ok thanks mate.

My Ubuntu is now installed, but my resolution is 1024 x 768 where  the native resolution should be 1280x800. Will your trick sort out my resolution?

If you follow what I posted it should. There has to be some understanding on your part. If you break something, it can be fixed. Just try to follow what I wrote.

---

### Post by Bagboy23 on 2006-09-26
Ok done, now does anyone know how to get XGL and Compiz to work on this setting?

---

