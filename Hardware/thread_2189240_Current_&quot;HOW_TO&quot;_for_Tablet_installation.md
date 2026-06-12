---
title: "Current &quot;HOW TO&quot; for Tablet installations available ???"
date: 2013-11-21
forum: Hardware
---

### Post by WinRiddance on 2013-11-21
Hi everyone. I've been using computers since 1991 and finally decided to get my first tablet with a 10.1" screen on which I'd like to run XFCE. I'll run Ubuntu or Debian if XFCE isn't possible but I'd much rather stick to XFCE (or even LXDE since that's supposed to be super fast with my specs). While knowing little to nothing about tablets, I do know that in theory my new tablet should have all of the required power to run Linux without a problem. There's a 1.6 Ghz. dual core processor with 1 GB of dedicated DDR3 ram and 8 GB of internal "hard disk" space. Wifi 811 b/g/n/ as well as HDMI and USB ports are also included which means that I shouldn't have a problem hooking up a wireless mouse & keyboard combo ... even though I'd prefer to use the touch screen if that's at all possible after installing XFCE? The tablet comes pre-installed with Android 4.1.1 (but I haven't actually received the tablet yet).

Does anyone know of a reasonably simple to follow step by step Linux installation for a tablet? One of the main reasons for doing this is to conserve more energy. Running a 35 watt tablet for most of my everyday stuff certainly beats running my 400 watt desktop all day long. Another reason for doing this is that I've been using Komodo IDE for the past 4 years and I'd really like to install that on the tablet too. Last but not least, Gimp is another programm that I use almost daily for work and I don't see any reason why I shouldn't be able to run Gimp in a more reduced manner on a tablet with 1 GB of dedicated Ram. Any productive advice would be sincerely appreciated. Here's a screenshot to the specs of the tablet ...
Thanks.

---

### Post by oldfred on 2013-11-21
You do not have an Intel chip which will make it very difficult.

[http://en.wikipedia.org/wiki/Rockchip](http://en.wikipedia.org/wiki/Rockchip)
The *Rockchip* RK30xx series use a dual core ARM Cortex-A9 *CPU* core.

Most tablets use ARM for low power with decent performance.
Some newer small PC that are convertible may use Intel.

---

### Post by WinRiddance on 2013-11-21
Well, the UEFI link doesn't really do me any good since Android isn't even mentioned there. And when you look at the nitty gritty detail specs of the Rockchip CPU that this tablet has, it's all the more reason to think that it should be possible to run Linux on it. I just haven't been able to find any decent links which explain how to root a tablet in order to use it like just another "computer" that can be tweaked any number of ways? Although, I just thought of another question that's related to this thread ...
If the tablet was rooted, wouldn't it be possible to boot a flash based version of Linux from a TF card?
That would completely eliminate the need of installing an actual Linux on the tablet drive space ...

.

---

### Post by oldfred on 2013-11-21
Understand that with different cpu, no code is compatible.

Since most code is now higher level and not machine based it may be able to recompile, but idiosyncrasies may require some custom changes to make it work.

Since Ubuntu is trying to develop tablet systems, it has released some ARM base development tools, but I think those are directed for specific new product development systems, not any currently released systems. 

This mentions the new 64 bit version, not sure about 32 bit which all current devices have.
[https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes](https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes)

>  64-bit ARM architecture

   Ubuntu 13.10 includes a new port to 64-bit ARM systems (the "arm64" architecture, also known as AArch64 or ARMv8) as a developer preview. This is an incomplete port which we expect to develop further in the future, but it is useful today for development work and for experimenting with server workloads. The Ubuntu Core arm64 image provides a root filesystem which may be booted in the ARMv8 Foundation Model, with the addition of a kernel (not provided in Ubuntu 13.10).

   Due to time constraints, only a subset of the Ubuntu archive has been built for arm64; compared to armhf, 94% of the binary packages in the "main" component are available, and 69% of the binary packages in the archive as a whole. We expect this to be much more complete for Ubuntu 14.04. 





---

### Post by WinRiddance on 2013-11-22
Alright, so then what about my last question? Since I can use up to 32 GB external TF card, would it be possible to boot into Linux directly that way? I could create my own boot Linux with pre-installed programs and then save any work that I do on a separate 4 GB Ext4 partition ... in order to copy that work onto my main system afterwards. Does anyone know how to boot a tablet into an attached (external) TF card?

---

### Post by oldfred on 2013-11-22
An Arm chip is not compatible with the Intel/AMD x86 family of compatible chips. 

You have to have an operating system based on ARM.
Or a tablet based on x86 compatible processor.

[http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture)

For specific ARM systems:
[URL="http://www.ubuntu.com/partners/arm"]http://www.ubuntu.com/partners/arm
[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)
[/URL]

---

### Post by WinRiddance on 2013-11-22
I wish someone else would join this conversation because now I'm getting even more confused. I've read several posts Online where people are talking about hacking into their Android via root and then installing Linux on top of Android, similar to being installed in a virtual box. A couple of those threads stated that that was only possible with Android 4.0 and higher. That was one of the reasons why I opted for a tablet with Android 4.1.1 ... but I don't even want to go as far as installing it if that's not possible. Am I understanding you correctly ... you're saying that Linux can' even be booted from an external drive?
Then how come people with RaspberryPi can boot into Debian?
Shouldn't my tablet be at least as compatible a device as a Raspberry Pi?

.

---

### Post by WinRiddance on 2013-11-23
Okay, on the 8th of November "Tizen" released version 2.2.1 of its Linux based platform for Smartphones, Tablets, TVs, and so on. I'm getting closer but it's really a shame that more people won't show any interest for getting Linux running on ARM based tablets. I found a video too, by a guy who had an ARM based 7" tablet running the previous version of Tizen. The video was of pretty bad quality though. Anyway, here's the link to the Tizen site ... open source of course:
[https://www.tizen.org/about/devices](https://www.tizen.org/about/devices)
[https://www.tizen.org/](https://www.tizen.org/)

Check out their blog too, it has some really interesting stuff.

PC world has a really cool article on the new Ubuntu Server based on ARM or utilizing ARM processors or whatever you want to call it. It's Ubuntu and that's good enough for me. Again, I'm very surprised that more people are not interested in these low power alternatives and that a forum as huge as this one doesn't have more techies who are into this, considering that I feel like a dinosaur with some of the new technology that's going on. Here's the link to that article:
[http://www.pcworld.com/article/2064940/ubuntu-linux-server-with-arm-processor-rolled-out-by-boston-limited.html](http://www.pcworld.com/article/2064940/ubuntu-linux-server-with-arm-processor-rolled-out-by-boston-limited.html)

Here another link, this one to the "premiere" Linux ARM site:
[http://www.linux-arm.org/](http://www.linux-arm.org/)

And last but certainly not least, this link here to a page full of news & information about Linux systems with the ARM processing architecture. Now all I have to do is find someone who can help me "arm" my Tablet with an ARM Linux solution.
[http://www.linux-arm.info/](http://www.linux-arm.info/)

Also came across this link for mounting most Android 4.x devices from numerous different *buntu flavors and versions. I'm also including a link to the descriptive Wiki page of MTP that's related to the link below this line:
[http://community.linuxmint.com/tutorial/view/1185](http://community.linuxmint.com/tutorial/view/1185)
[https://wiki.archlinux.org/index.php/MTP](https://wiki.archlinux.org/index.php/MTP)

Oops, one more, possibly the most promising link of all ... Kali Linux for Android Tablets:
[http://www.kali.org/how-to/kali-linux-android-linux-deploy/](http://www.kali.org/how-to/kali-linux-android-linux-deploy/)

.

---

### Post by WinRiddance on 2013-11-23
And that's why it is so important to actually know what one is talking about, before shooting down an idea or making remarks about complexities that are bordering on impossible for people like me who are not hackers or tablet gurus. See following links ... solution found:

Read the whole page, play the video too. It'll blow your mind:
[https://play.google.com/store/apps/details?id=com.zpwebsites.linuxonandroid&hl=en](https://play.google.com/store/apps/details?id=com.zpwebsites.linuxonandroid&hl=en)

Then there's this link with more useful information. I think now I'm "ARM"ed with everything that I needed to know:
[http://sourceforge.net/projects/linuxonandroid/](http://sourceforge.net/projects/linuxonandroid/)

.

---

