---
title: "Request for packages: xserver 1.5 for Jaunty i386"
date: 2009-06-06
forum: Hardware
---

### Post by zak on 2009-06-06
I suspect ATI's decision to drop support for older[0] GPUs just in time for the release of distributions based on an X server that requires updated drivers needs no introduction if you're reading this thread.

Using ATI's driver on Jaunty requires downgrading to xserver-xorg 1.5, and I can find no 32-bit packages that are appropriate. There are [64-bit packages](http://www.kdedevelopers.org/node/3942), but that doesn't help those of us with 32-bit CPUs. Something makes me think older CPUs are often found with older GPUs. It would be really awesome if somebody who knows a bit more about building packages than I do were to create a repository.

[0] "Older" evidently meaning that it hasn't been shipped in production hardware for at least a month.

---

### Post by cariboo on 2009-06-06
You can go [here]("http:///packages.ubuntu.com/") to get the packages you need.

---

### Post by zak on 2009-06-06
I'm pretty sure I can't, actually. I did try installing the Intrepid packages, but ran in to all manner of dependency problems. I eventually built my own with apt-build, and they are working at the moment, though I can't get fglrx to enable DRI now.

I'm willing to provide my binary packages to anyone with the same issue, but they're not production quality and might not install smoothly.

---

### Post by Muchacho_Gasolino on 2009-06-06
Funny, I was just looking for the exact same thing. Could I try your packages?

---

### Post by zak on 2009-06-07
[http://64.74.153.35/~zak/x-packages.tar](http://64.74.153.35/~zak/x-packages.tar)

---

### Post by Muchacho_Gasolino on 2009-06-08
Yo Zak, I know you never promised tech support, but...

I screwed something up. I tried to follow the method shown here: [http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942), meaning that I went to the directory that I unpacked your packages in and did:

```
sudo dpkg -r xserver-xorg-video-all xserver-xorg-input-all
sudo dpkg -i *.deb.
```

most of them wouldn't install because of dependency issues, so I added --force-depends. As you might expect, X did not come back after I restarted it. However, an apt-get upgrade -f fixed things. Do you know how I can solve these dependency issues without totally breaking X?

---

### Post by zak on 2009-07-09
I'm afraid I don't. I remember having some issues getting it installed, but I really don't remember the details.

---

