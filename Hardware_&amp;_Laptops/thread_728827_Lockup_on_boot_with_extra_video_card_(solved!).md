---
title: "Lockup on boot with extra video card (solved!)"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by peshwali on 2008-03-19
I had a problem and searched and search and finally found a solution, so I thought I would post this answer in its own thread, especially since it seems to be a relatively common issue in my forum searches.

The problem was this:
[LIST=1]
[*]I have an integrated video card that works fine with Ubuntu
[*]I added an external video card (Nvidia in my case but according to the posts in my search ATI seems to also have similar problems).  I have seen the problem with AGP and PCI cards.
[*]Once I disabled the internal card in the BIOS, Ubuntu would lock up on boot. Both with the standard boot and with the recovery option from GRUB.
[*]I tried Nvidia drivers, dpkg-reconfigure xserver-xorg, and any other solution commonly recommended.  I even tried a completely new installation in which I disabled the internal video before installation.  I then installed Gutsy with the alternate CD, which installed great but then had the same boot problems.
[*]As a note, my particular BIOS does not seem to disable the internal card, but rather makes the AGP priority (though I am not positive of the accuracy of that)
[*]Finally I found the below post in a 2007 post (referenced at the bottom)
[*]It worked for me on 2 Ubuntu installs (same hardware, but different hard drives) and it also worked for the person that I replied to in my post.
[*]As a note, I cannot say it will not cause other problems, but it definitely solved my specific issue.
[/LIST]:)
My post below:

> I think I found a solution and it seems to work for me.  The solution is for a ASRock motherboard (which I have), but it may work with others.  This was in a post a year ago:

> **todoporron said:**
> Hi 

About a year ago, I had the same problem with an Asrock board with embeded graphics and my Nvidia card.

The solution:

Edit your /etc/modprobe.d/blacklist file:

```
sudo gedit /etc/modprobe.d/blacklist
```

and add the following line:
```
blacklist intel_agp
```

After that, you have to install your Nvidia drivers if you have not done it yet. 

On your BIOS setup, disable your onboard graphics and enable your Nvidia card. This should solve the problem .

So what I did:

1. enabled and used internal MB video card to get to ubuntu
2. followed instructions above
3. shutdown and restarted computer, but now I disabled internal video in BIOS (as mentioned above)
4. booted into Ubuntu, but there was no gui, so I did ctrl-alt-f1 to get to terminal
5. did the following from the command prompt (choosing Nvidia or nv as graphics card and did other necessary steps, which should be explained elsewhere):
```
sudo dpkg-reconfigure xserver-xorg
```
6. Rebooted system
7. Went to work setting up video as desired (i.e. envy, nvidia, ubuntu's nvidia driver, etc.)

I did this in my new setup and in my old setup and both work now!!

For your reference, here is the post in context:
[http://ubuntuforums.org/showpost.php?p=2392604&postcount=2]("http://ubuntuforums.org/showpost.php?p=2392604&postcount=2")

---

