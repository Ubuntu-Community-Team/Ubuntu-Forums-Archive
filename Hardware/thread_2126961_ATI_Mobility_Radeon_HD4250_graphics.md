---
title: "ATI Mobility Radeon HD4250 graphics"
date: 2013-03-18
forum: Hardware
---

### Post by onilink422 on 2013-03-18
Hello all, I am on a dell inpiron M5030 which runs ATI Mobility Radeon HD4250 graphics. The fglrx drivers worked great on 10.04, however running the latest release just for the sake of Unity, I can't install them on the xserver this is running because amd decided to go legacy. I am wondering if I would be able to downgrade the xserver in order to install my amd drivers. I understand this is not recommended, but I really enjoy unity and I would love to have the proper video acceleration that my graphics card is capable of.

---

### Post by Cheesemill on 2013-03-18
You could do an installation using the 12.04.1 CD.

12.04 was the last version released with support from ATI for the 2/3/4xxx series chips. It's also an LTS release meaning that it is supported until 2017.

Just make sure you use the 12.04.1 CD to install, not the more recent 12.04.2 CD as the latter comes with the upgraded graphics stack that is incompatible with your GPU.

The 64-bit download of 12.04.1 can be found here...
[http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04.1-desktop-amd64.iso](http://old-releases.ubuntu.com/releases/precise/ubuntu-12.04.1-desktop-amd64.iso)

---

### Post by onilink422 on 2013-03-18
Oh, thanks but after searching a bit online I came across this article that had exactly what I was looking for
[http://steamcommunity.com/app/221410/discussions/0/864960354325873942/](http://steamcommunity.com/app/221410/discussions/0/864960354325873942/)
I followed it to the letter and my drivers now work. By the way, I was already on a fresh install of 12.04
Anyway, I should probably mark this as solved.

---

### Post by Cheesemill on 2013-03-18
Had you installed from the 12.04.1 disc instead of the 12.04.2 disc then none of that would have been necessary.

As it is now you have a kernel from outside the repositories which wont get any bug fixes or security updates, you'll have to keep an eye out for any updates to the 3.4 kernel and install them manually.

---

### Post by xaliqen on 2013-03-18
Just whatever you do, don't upgrade to Raring.  As of now, there are no shortage of headaches related to getting ATI legacy fglrx drivers working in Raring, and AMD made it clear they don't particularly care about legacy support on new kernels (for those of us with 4000-series and older GPUs, they pretty much want to forget we exist).

So, unfortunately, stick with the LTS for now and hope someone finds a suitable workaround.  For Quantal and Precise, [Tomasz Makarewicz's PPA]("https://launchpad.net/~makson96/+archive/fglrx") will help downgrade X-Server and provide proper patches for kernels ~3.5. I recommend it.

---

