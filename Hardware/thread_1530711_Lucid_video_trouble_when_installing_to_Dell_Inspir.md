---
title: "Lucid video trouble when installing to Dell Inspiron 5160"
date: 2010-07-14
forum: Hardware
---

### Post by timnugent on 2010-07-14
Hello, I've bought a Dell Inspiron 5160 with 1 GB of RAM and an 80 GB hard drive. All is well. It came with Windows XP Pro, but I bought it with the intention of putting Lucid Lynx on it, and giving to him as his college laptop.

Installed Ubuntu and Xubuntu from both the LiveCD disks and the Alternative installation disks but had the same result in each case: a lit screen with a kind of mesh-like pattern, as if I were looking through a dirty window screen, and fading to darkness around the edges... I could make out the Ubuntu/Xubuntu logo(s) but the system seemed dead in the water, and the clarity was so bad I don't think I could read normal sized text had it been there.

I surmised that the problem was with a driver for the video card.

Searching around the forums I found a few other people having similar troubles with their Inspiron 5160 machines, and some *vague* suggestions for fixing it, but no solutions per se.

I had a CD with Mepis AntiX 8.5 and booted off of that... No problem! The screen shows up fine, everything working like a charm. I have to say I'm disappointed. I really wanted to give David an Ubuntu machine because of superior support, documentation, and general excellence of the product, but I can't resolve this video problem.

It's AntiX if I can't get help from someone here. We need to have this to him in 4 days.

I gather that installing using the alternative installation disk may be the way to go, and then configuring or downloading the software I need to make the video work right, but I don't know how to do this. When I finish the install with the alt. disk, I just get the same bad screen problem.

If AntiX can handle the hardware, why not Ubuntu?

Help!

Thank you--

Tim Nugent :???:

---

### Post by mörgæs on 2010-07-14
Please post the output of 

```
 hwinfo --gfx
```

---

### Post by timnugent on 2010-07-15
> **mörgæs said:**
> Please post the output of 

```
 hwinfo --gfx
```
Thank you, mörgæs. I tried that command, but it said 'command not found'. Keep in mind that right now I'm running Mepis AntiX 8.5 and it says I've got the bash shell running--at least the prompt before the output says "bash: hwinfo: command not found"...

I've tried Ubuntu as both a Live CD and alternate install, and I've tried Xubuntu the same two ways, Edubuntu as a live install only. I haven't tried Kubuntu yet. I'll try Kubuntu both as live and alternate installs.

Thank you for your attention. Is there another command I should use to get that gfx info?

Tim Nugent

---

### Post by mörgæs on 2010-07-15
I was looking for information on the screen card. I don't know what the similar command is in Mepis.

Don't waste your time trying Kubuntu. If the other ones did not work, Kubuntu will most likely not either. I assume everything was the 10.04 release.

It is worthwhile to try older (but still supported) Ubuntus like 9.10 and 8.04. You can download the ISO here:
[www.releases.ubuntu.com]("http://www.releases.ubuntu.com")


If your want something Ubuntu-like you could also take a look at Linux Mint.

---

### Post by mörgæs on 2010-07-15
By the way, when burning a CD best is to burn at a slow speed and to check the MD5 value.

---

### Post by timnugent on 2010-07-15
Thanks again. Yes, I was using 10.04 in each case. I'm burning at 4x speed. OK, I'll give Mint a try. I've liked it before, just hadn't thought of it. I'll post the results.

I'm sure there is some driver solution since Mepis does the job, and I believe it's based on Debian.

As far as I'm concerned, Ubuntu is the Rolls Royce of systems--I'd very much wanted to give it to my nephew, but Linux Mint is a pretty close second, so I'll try that. Thank you.

Tim Nugent

---

### Post by mörgæs on 2010-07-15
You are welcome. 

Again, I believe that it pays to try a few of the later releases when testing a distro. Regressions do appear, even in Linux :-)

[http://www.linuxmint.com/oldreleases.php](http://www.linuxmint.com/oldreleases.php)

---

### Post by timnugent on 2010-07-16
Hi mörgæs,

As far as I know I'm not directly related to anybody in Seattle. We're from the northeast. It's an old Irish name, and I know we're scattered around the US and elsewhere!

Tried Mint, but had the same results. I may just have to resort to Mepis. I'll try a couple of the older distros, too.

Thanks for your help here. 

Tim N.

---

