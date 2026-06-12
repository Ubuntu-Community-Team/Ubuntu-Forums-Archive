---
title: "nVidia &quot;non-sucky&quot; driver"
date: 2008-06-05
forum: Hardware
---

### Post by ProbablyX on 2008-06-05
Hello!

My friend tells me the nVidia driver version (169) that ships with hardy is junk, having issues with some texture data and so on, and that I should downgrade to a "version that is older than 169 or newer than 175"

I'm using the nvidia-glx-new driver, on an amd64 system with a 8600GT card and I'm also having problems with 3D apps crashing. So I think that a driver change really could do something good.

Is there any repository that offers any driver that meets the above demands? So that I dont have to install drivers manually? I mean so that when Ubuntu releases new drivers I can just apt-get upgrade and get them?

Thanks!
PS. I'm also told that the gutsy driver is very old, so I'd like a version that's not too old :)

---

### Post by TheLions on 2008-06-05
try "newest" beta [http://www.nvidia.com/object/linux_display_amd64_173.08.html](http://www.nvidia.com/object/linux_display_amd64_173.08.html)
works great with 7600GT

---

### Post by stchman on 2008-06-05
> **ProbablyX said:**
> Hello!

My friend tells me the nVidia driver version (169) that ships with hardy is junk, having issues with some texture data and so on, and that I should downgrade to a "version that is older than 169 or newer than 175"

I'm using the nvidia-glx-new driver, on an amd64 system with a 8600GT card and I'm also having problems with 3D apps crashing. So I think that a driver change really could do something good.

Is there any repository that offers any driver that meets the above demands? So that I dont have to install drivers manually? I mean so that when Ubuntu releases new drivers I can just apt-get upgrade and get them?

Thanks!
PS. I'm also told that the gutsy driver is very old, so I'd like a version that's not too old :)

I use the 169.12 nvidia-glx-new driver and it works very well.  All my 3D gmes play.  I was playing Open Arena the other night.

---

### Post by ProbablyX on 2008-06-05
> **TheLions said:**
> try "newest" beta [http://www.nvidia.com/object/linux_display_amd64_173.08.html](http://www.nvidia.com/object/linux_display_amd64_173.08.html)
works great with 7600GT

I hear that driver is having OpenGL issues too for some..

The reason I'm not getting any pointers from my above mentioned friend is because he's not using ubunu - if anyone's wonering :P

And if I was to try that - it's an "nVidia binary" and I'm using an "nVidia binary by Ubuntu" that is the 'nvidia-glx-new'  via aptitude - won't it mess up my so called by Ubuntu driver? I hear that it's either the ubuntu one or a manual install. Mixing them will make your system roll over and die...

Thanks =)

---

### Post by Unix_Slayer on 2008-06-05
> **ProbablyX said:**
> I hear that driver is having OpenGL issues too for some..

The reason I'm not getting any pointers from my above mentioned friend is because he's not using ubunu - if anyone's wonering :P

And if I was to try that - it's an "nVidia binary" and I'm using an "nVidia binary by Ubuntu" that is the 'nvidia-glx-new'  via aptitude - won't it mess up my so called by Ubuntu driver? I hear that it's either the ubuntu one or a manual install. Mixing them will make your system roll over and die...

Thanks =)

The best driver is the latest. NVIDIA-Linux-x86-173.14.05-pkg1.run

---

