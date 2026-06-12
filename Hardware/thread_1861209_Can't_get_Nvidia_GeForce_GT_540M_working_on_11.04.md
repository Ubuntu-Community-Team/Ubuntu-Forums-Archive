---
title: "Can't get Nvidia GeForce GT 540M working on 11.04"
date: 2011-10-15
forum: Hardware
---

### Post by Sidrabs on 2011-10-15
Hi, 

I have acer TravelMate 5760G Laptop, with Nvidia GeForce GT 540M graphics on it.
Unfortunately, I can not get it to run with Nvidia drivers, what prohibits to run it with OpenGL. I need to make the OpenGL working so that I can work with Blender (3D design/render software).

What I did:
I tried to install the original drivers downloaded from [www.geforce.com/Drivers]("http://www.geforce.com/Drivers") (NVIDIA-Linux-x86-285.05.09.run), and upon finishing install, it asked if I want to activate the newly installed driver. I indeed did, but after restart the system stalls shortly after "Checking battery" status msg (screenshot attached).

My Xorg.config file (what fails to load) and Xorg.log attached, maybe those contain something useful to debug this.

I really hope this is not as beew says in this thread, an "unsolvable matter": [http://ubuntuforums.org/showthread.php?t=1699939](http://ubuntuforums.org/showthread.php?t=1699939)

---

### Post by benpaka on 2012-02-08
Did you find a solution to your problem?

I have the same laptop at my work and I really need 3D for some CAD applications.

---

### Post by Sidrabs on 2012-02-08
Yes, in fact.

The solution is called Bumblebee, you can find it here:
[https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)

The installation might be non-trivial, but the good news is it's working.

Here are the installation instructions I used to install it on my Ubuntu 11.10:
[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

Good luck!

---

