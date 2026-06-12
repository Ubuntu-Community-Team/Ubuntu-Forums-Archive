---
title: "Random pixels in random colors flashing all over display in GeForce/Intel Bumblebee"
date: 2014-03-10
forum: Hardware
---

### Post by Karl_Lerud on 2014-03-10
Hi, I'm new to the forum and to Ubuntu as well, I hope I'm posting this in the best place. I recently got an MSI GE70 20E, which has an nVidia 765M card as well as the onboard Intel graphics chip, I think running Optimus by default in Windows 8.1 (I'm dual booting 12.04 LTS). I think Ubuntu put the Bumblebee drivers on by default when I installed, and everything was fine for a couple weeks, although I wasn't sure if it was actually accessing the nVidia card, and I wondered the same thing in Windows. But recently, in Ubuntu, I went to a website with some live-streamed HD camera (whatever it was, apparently graphically-demanding), and these randomly colored and placed pixels showed up everywhere. Occasionally shapes and textures will briefly distort too. It looks a lot like this picture someone else posted on a different site:

[http://i.imgur.com/CG0or.png](http://i.imgur.com/CG0or.png)

I restarted, to find the condition exactly the same. Then I booted into Windows, and it was happening there too. After finally getting the right drivers in Windows for the nVidia card, I can keep it to a minimum by telling the nVidia software to prefer the GeForce card over the onboard chip. It still happens though, for instance browsing through google maps in satellite view. When this started I tried all kinds of driver options in Ubuntu, and I'm honestly not quite sure where I ended up...but nothing changed the basic problem. I think I ended up with Bumblebee still installed but with Nouveau installed also. I also tried shutting down and removing the battery for half an hour; when I booted back up, it looked for a second like it was gone, but came right back after I started using software. 

So my question is whether this sounds sufficiently like a hardware issue that I should just back up and RMA the machine. I don't know much about drivers or video cards, so I don't know if there's some way to check if the Intel chip is permanently damaged, and/or if there's some way that a fixable driver issue in Linux somehow affected the chip's performance in a different OS. I also don't know which chip it is, because I don't know how Bumblebee/Optimus work. 

Appreciate any thoughts, thanks.

---

### Post by Karl_Lerud on 2014-03-10
One more note: In Windows I can disable the Intel chip, and then the artifacts go away completely (but it tells me I'm not using an nVidia card if I try to open the GeForce control panel, even though that's presumably the only chip I'm using now...), but I don't know how to do the equivalent thing in Ubuntu.

---

### Post by Karl_Lerud on 2014-03-11
bump...? I'll simplify my question. I'm wondering if I can disable the Intel graphics chip in Ubuntu like I can in Windows, which solves the problem. Also I'm wondering if there's an easy way to "start over" with graphics drivers in Ubuntu, since I seem to have installed too many things.

---

