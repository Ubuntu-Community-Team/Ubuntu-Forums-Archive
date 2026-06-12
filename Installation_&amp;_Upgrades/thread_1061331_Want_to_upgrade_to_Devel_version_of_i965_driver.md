---
title: "Want to upgrade to Devel version of i965 driver"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by mttman on 2009-02-05
Hello,

I'm trying to get OpenGL 2.0 support off of an Intel GM965 card in a thinkpad R61. After doing some research I found that OpenGL2.0 isn't supported under the current stable version of the driver. My question is this - Is there anyway to upgrade my driver without having to recompile half my system manually? Something like a Developers Repo I can pull a deb from or something.

any help would be very much appreciated

Thanks in advance

---

### Post by mttman on 2009-02-12
6 days, 20 views, and no replys. am to guess that this isn't really possible or what?

---

### Post by Dougie187 on 2009-02-12
I'm not sure if this is correct, but im about 90% sure you have to compile a custom kernel for this. But it might just be a module that you can add and have it pick up. I wouldn't be the person who knows though..

Just a question though, are you sure that the new card has support for OpenGL 2.0? Because I ran into a similar problem a while ago and found out I had to get a Discrete card when I was looking to get OpenGL 2.0.

---

### Post by mttman on 2009-02-12
I ran fedora 9 not to long ago on this hardware and had opengl2.0, compiz ran kinda buggy on it but it was there. my impression with ubuntu has always been that there way of doing this is "Make it stable, then add features" which is why they typically use older drivers. i was just hoping some developer somewhere was sympathetic.

thanks anyways

---

### Post by densou on 2009-02-14
Fedora always uses the newer Mesa build for its releases, also if it's still on development status, no doubt it'll lead to a performance gain over Ubuntu/Suse ;)

simply solution: update to Jaunty, it includes all newer stuff (stable or not, e.g. all 2008Q4 packages --> read the list at [http://intellinuxgraphics.com](http://intellinuxgraphics.com) ) :guitar:

---

### Post by mttman on 2009-02-17
I just figured out how to get the new drivers.

and these two repos to your sources in whatever way you perfer

```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
```

copy this key into a file and save the file somewhere easy to get to

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXjVEAEEAN+sXD+rJizF3gXLx3TYQ2eCNEa4PO8Q1gmHbvM6NaKfMQZzvnn2IsUKMpBo
0+CImbVKRvenv2ojkYiqknJ1G7QnFfiMFR4l8y2RCC9PNeX42K4656EBwwdtVgxWjznGcWKC
uN3H4MXJ/aOOoT7WgzSTFuEe4FEnYzevkrZWECjpABEBAAG0L0xhdW5jaHBhZCBQUEEgZm9y
IEludGVsIGdyYXBoaWNzIGRyaXZlciB0ZXN0aW5niLYEEwECACAFAkl41RACGwMGCwkIBwMC
BBUCCAMEFgIDAQIeAQIXgAAKCRBesu3+H8sh23TKA/9ySqN90PTsUQELqKnhmfYSMVi/sLNP
Ji1YuvoMKKMD+o2pPI4vPoj1VT5tmDPVXfNbeT6PU4NnwBXixf4CPkp9ME64ECjcZUVLjpmW
AT5g+2IoO290HB3ngOFxZ0PZ5FrWkNIzoEo39lW3sO5D5j4vftyMKtufqVkqDejVMhZr7g==
=X/G4
-----END PGP PUBLIC KEY BLOCK-----

```

open System -> Administration -> Software Sources -> Authentication
and click the "Import Key File..." button. browse to the file you just made and open it. close the software sources, open a terminal and run the command ```
sudo apt-get update
``` in a minute or two your update manager will want you to update your drivers. Do that, restart and you have openGL 2.x

---

### Post by alfalekos on 2009-03-17
I run ubuntu-studio on ubuntu 8.04 on a Lenovo SL300, Intel GMA X4500HD.
Do you think the same would work for this case? 

Until now everything related to vlc, kaffeine, totem concludes to black screen and obligatory restart. 

No **xf86-video-intel 2.4.0 driver** for mode-setting, 2D, and video.
Neither latest Mesa through the synaptic. Possibly both are included in 8.10 but I would prefer to stay with the more stable Ubuntu 8.04, both for Ubuntu and Ubuntu-Studio reasons.  

thanks
cheers.

---

### Post by mttman on 2009-03-17
your problem sounds more like an issue with gstreamer then your video driver. I would suggest reinstalling the gstreamer packages before working on upgrading your video driver. 

Remember that with this upgrade you will be working with unstable software which could cause more problems then it solves. 

Something else that might be the issue with your video players is the video plugin for compiz. if your running compiz try turning this plugin off and trying again. If it is the plugin there is the possibility that the new driver might fix it

Quick note : next time you have this issue try```
[Ctrl][Alt][Backspace]
``` this will restart X and bring you up to your login screen. It saves time if your machine is still getting data from your keyboard.

Hope this works for you

---

