---
title: "3D corruption with mobility Radeon ATI cards"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by azdo on 2007-04-21
Hello,

after upgrading to 7.04, I have noticed display corruption when I running OpenGL programs, as Blender. I'm using the *radeon* free driver. The problem has been reported previously in

[http://ubuntuforums.org/showthread.php?t=372414]("http://ubuntuforums.org/showthread.php?t=372414")

and even someone posted a bugreport at 

[https://bugs.launchpad.net/ubuntu/+bug/105183]("https://bugs.launchpad.net/ubuntu/+bug/105183")

However, it is currently not assigned to anyone, what can i do? :(

---

### Post by ccoppenbarger on 2007-04-26
Same problem here, with Blender, Wings3D, and K-3D. Although K-3d is supposed to run on Kubuntu, I installed it anyway and discovered the same problem.

I'll look through the various fixes for the drivers, but the last time I did that, I corrupted the X windows

---

### Post by Puru on 2007-05-02
Same problem here, on a radeon 7000. I "solved" by downgrading libgl1-mesa-dri and libgl1-mesa-glx to 6.5.1, now everything runs fine. 

Find 'em here

[http://packages.ubuntu.com/edgy/libs/](http://packages.ubuntu.com/edgy/libs/)

download the packages, open terminal, go in the directory you saved em in, type

sudo dpkg -i *.deb

(that's if you don't have other .deb packages in current directory, otherwise use the names).

Couldn't do anything to lock the version, so that silly upgrade icon keeps camping there, but it's a minor problem, now.

By the way, k3d is not related to kubuntu nor to kde... I don't know for what the K is, the author considered to change name in kika (Kika is not a kde application), but I htink it was a joke.

bye!

---

### Post by azdo on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/109405](https://bugs.launchpad.net/ubuntu/+bug/109405) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Puru, I think you hit the nail on the head. I filed a bug report about this ([https://bugs.launchpad.net/ubuntu/+bug/109405](https://bugs.launchpad.net/ubuntu/+bug/109405)) and I was told Mesa 6.5.2 was the culprit and that compiling 6.5.3 solved the problem. I did, an indeed it fixes the problem. However I think your downgrading suggestion to 6.5.1 is much cleaner, thank you for sharing the tip :).

Well, I have tested more thoughtfully 6.5.3 and it leads to crashes when leaving *edit mode* in Blender, so I reverted to 6.5.1. However I can't find *libgl1-mesa-dev* version 6.5.1 :(

---

### Post by Puru on 2007-05-06
Find it in libdevel section!

[http://packages.ubuntu.com/edgy/libdevel/libgl1-mesa-dev](http://packages.ubuntu.com/edgy/libdevel/libgl1-mesa-dev)

---

### Post by ccoppenbarger on 2007-05-08
> **Puru said:**
> Same problem here, on a radeon 7000. I "solved" by downgrading libgl1-mesa-dri and libgl1-mesa-glx to 6.5.1, now everything runs fine. 

Find 'em here

[http://packages.ubuntu.com/edgy/libs/](http://packages.ubuntu.com/edgy/libs/)

download the packages, open terminal, go in the directory you saved em in, type

sudo dpkg -i *.deb

(that's if you don't have other .deb packages in current directory, otherwise use the names).

Couldn't do anything to lock the version, so that silly upgrade icon keeps camping there, but it's a minor problem, now.

By the way, k3d is not related to kubuntu nor to kde... I don't know for what the K is, the author considered to change name in kika (Kika is not a kde application), but I htink it was a joke.

bye!

Thanks, that works great. Has anyone filed a bug with the Mesa people yet? Oh yeah, I had trouble with even making the Mesa drivers. It was a pain. I'll guess we'll have to wait for the repository version.

Thanks for the hint on K3D.

---

