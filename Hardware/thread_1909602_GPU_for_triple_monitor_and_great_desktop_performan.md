---
title: "GPU for triple monitor and great desktop performance"
date: 2012-01-15
forum: Hardware
---

### Post by dbarreth on 2012-01-15
Hi!

I'm running Ubuntu 11.10 64-bit on a fairly good Desktop at work.
I'm  going to upgrade to be able to run a triple monitor setup. But have  close to no experience on GPU's in Linux, and the experience i have is  mostly bad. So I need some advice.

Except the three monitors i  want a good graphical performance boost to, since I'm not satisfied atm.  Never really been very happy with the graphical performance on Ubuntu.  Which probably is most due to I've mostly have been running on laptops  and desktops with budget ATI-cards. Even though I usually have quite new  and good hardware.

I'm using it at work. I don't run graphical  demanding applications. But want perfect or close to perfect desktop  performance, even though I don't use a lot of eye-candy I want my new  GPU to be able to handle it very good.

So my problem is to find  this GPU. I have found that to be running triple monitor on a single  GPU, which is the plan, is that it needs to have a combination of  VGA/DVI/Displayport. A HDMI port wont be usable.

I have been searching a lot. But what I'm having problems finding is:
1. If the GPU can run three monitors in Ubuntu/Linux or not
2. How good the desktop performance is in Ubuntu (hard to find reviews or other references)

Best would be if someone had first hand experience with a card that meets the standards. But all tips are welcome.

My system today is about 12-18 mounts old, not sure
**The system:**
**CPU**: Intel Core i7
**RAM**: 12 Gb DDR3
**Mobo**: Fairly good Intel mobo (about $100 when bought)
**GPU**: ATI HD 5450 (with HMDI, not displayport as third port)
**HDD**: 128GB SSD and 750GB 7.2kRPM HDD

With two 24" monitors (think they are 1920x1024, but could be 1920x1200, not sure) and will be adding a third 22" 1920x1024.

---

### Post by papibe on 2012-01-15
Hi dbarreth. Welcome to the forums,

At this moment (things may change with 12.04) you can set up to two monitors at a time (Check this [thread]("http://ubuntuforums.org/showthread.php?t=1823256&highlight=monitors"), and this [question]("http://askubuntu.com/questions/25954/is-it-possible-to-use-more-than-two-monitors") on AskUbuntu)

However, I know there are external devices that you can use to acomplish that (for example [Matrox TripleHead2Go]("http://www.matrox.com/graphics/en/products/gxm/th2go/")).

Just some thoughts.
Regards.

---

### Post by dbarreth on 2012-01-16
Hi!

Thanks for your warm welcome for my first post. We joined this forum nearly at the same time, I rarely post, just needs to be able to search =)

Matrox TripleHead2Go seems like a good backup if other alternatives runs out. But since i want to upgrade my GPU anyway, I will if possible buy a card for the same money or less with all support needed for this

About support for three monitors i know that it's possible.
You can see this here: [video]("http://www.youtube.com/watch?v=NgffqjbTEo8"), [video2]("http://www.youtube.com/watch?v=0G0fJVyxtcc")
> Catalyst 10.7 adds support for Eyefinity on Linux: [http://www.phoronix.com/vr.php?view=ODQ0OA](http://www.phoronix.com/vr.php?view=ODQ0OA)
  This will allow you to have 3 monitors on one AMD/ATI graphics card with 3D acceleration.
 
Source: [Superuser.com]("http://superuser.com/questions/95884/ati-eyefinity-under-linux")

So it is possible already to do this. Haven't found much on nvidia on a single card, so don't know whether its possible or not. But it's important to use combination of VGA/DVI/DisplayPort (any combination of the three should work, usually today is 3-4 Displayports or two DVI + one DisplayPort on graphic cards). Your reference forum post where trying to get it working with s-video as third output.

I'm quite interested to give Nvidia a go for this desktop, due to all good recommendations. But not sure if the difference in good drivers in ATI vs Nvidia on linux is still big.

---

### Post by dbarreth on 2012-01-16
Another reference:
[http://superuser.com/questions/144867/3-or-4-monitors-with-nvidia-and-ubuntu](http://superuser.com/questions/144867/3-or-4-monitors-with-nvidia-and-ubuntu)
But still no good info on Nvidia

And it's not important at all to do this under Nvidia. It's important to get as good desktop performance as possible.
Just that I have stared extra at Nvidia since there seems to be better support/drivers for them in linux.

---

### Post by dbarreth on 2012-01-16
Well after more searching it seems that one nvidia card and >2 monitors aren't best friends at all, certainly not on Linux. You are forced to use more than one card in SLI wich brings other problems. As losing compiz or be forced to use separate x-screens.

So I seem to be stuck at choosing an ATI-card with support for eyefinity in Linux to get my three monitors from one card. Any one to prove me wrong are _very_ welcome =)

So narrowed down then:
Are ATI-cards that choppy that I've come think?
And anyone with good experience when it comes to performance of any specific card?

Is it a good idéa to go for a new card or should i look for a model with at least a few mounts on the market?

---

### Post by dbarreth on 2012-01-16
Seems like some got it to work with a HD6870 wich I've already have looked in to ([http://ubuntuforums.org/showthread.php?t=1900178)]("http://ubuntuforums.org/showthread.php?t=1900178")

So I think i will go with that, since I have other orders to make today. Just gonna research how good it performs first.

I will get back and tell how it works.
[]("http://ubuntuforums.org/showthread.php?t=1900178")

---

### Post by papibe on 2012-01-16
Very interesting! Keep us posted.

---

### Post by dbarreth on 2012-01-17
GPU installed and all three montiors works quite well right out of the box. _Perfect_ desktop performance with compiz after installation of ATI-drivers (didn't try with the open source drivers, but my experience with ati and multi-monitor is that the catalyst does this best).

[B]What i did:
[/B]
**First and formost**. To my knowledge, you need an ATI-card with one DisplayPort*, and two DVI ports or one DVI and one VGA for this to work. And with that, if one of your monitors don't support DisplayPort, the adapter you use SHOULD be an active one (means it also has an USB-cable to get extra power).

** there are some ATI-cards with three or four DisplayPorts, this should work to. But you  think twice before buying these cards, since if your monitors don't support DisplayPort you will need to buy one expensive adapter for each monitor!*

I used a Radeon HD 6870 (with two DVI ports and one DisplayPort)

1. Uninstalled old flgrx drivers with ```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```2. shutdown 
3. Swapped the cards
4. Installed my three monitors and booted up
after this I had a cloned display on all three monitors
5. Installed ATI-drivers from amd.com, reboot!
6. Made the display-setup from Catalyst (administrative). Reboot or "relogon"
Done! no need for extra hacks

After this I needed to optimize Compize a little. Partly due to earlier tweaks to get it to work with my earlier low-end ATI-card. Some good advise on how to set up compize good for ATI-drivers (don't know if this applies to nvidia also) can be fond _[here]("http://askubuntu.com/questions/38028/performance-being-really-choppy-with-ati-drivers")_.

Some state to set refresh rate to same as monitors, some get better results with monitor refresh rate x2.
In my case my monitors are all 60hz, and the same setting in compiz works great. Though if you have a low-end card, half your refresh rate may be your only good choice, this gets OK smoothness, but not very good.

**Conclution:** I now have a three monitor setup, with one GPU powering all my monitors, i also use a DisplayPort->DVI adapter since none of my monitors supports DisplayPort. Compiz is working _perfect_ and the installation was quite straight forward.
The GPU i bought may be a little overkill for the job, don't know.
Have not tested any games, and don't plan to run any. So you have to go elsewhere for those results

**Costs:** about $180 for the GPU and $80 for the adapter (had the adapter already)

PS. Feel free to wright a blog post about this or spread the info in other ways. Theres not much good easily found info on this on the Internet at this moment.

---

