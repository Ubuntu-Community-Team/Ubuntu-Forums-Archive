---
title: "HP Envy and Switchable Graphics (6850m)"
date: 2012-07-27
forum: Hardware
---

### Post by Pihpe on 2012-07-27
Hi!

So, I'm trying to get this combination to work. I'd love to use the discrete graphics (6850M) instead of the integrated GPU on my HP Envy 17-2100, but is it an impossible task? I'd be completely happy if I could just force my Ubuntu to use the 6850M only, wouldnt even need the possibility to switch it between the GPU's.

There is no way to switch to the DGPU from the bios as far as I know.

Any tricks or tips on how to get it working?

---

### Post by QIII on 2012-07-27
Pure ATI/ATI hybrid or Intel/ATI?  The latter is a can of worms.

If it's an ATI/ATI hybrid, do you have the proprietary fglrx driver installed?  (fglrx-updates is problematic for some people.)

If you do, did you run

```
sudo aticonfig --adapter=all --initial
```
?

---

### Post by Pihpe on 2012-07-27
> **QIII said:**
> Pure ATI/ATI hybrid or Intel/ATI?  The latter is a can of worms.

If it's an ATI/ATI hybrid, do you have the proprietary fglrx driver installed?  (fglrx-updates is problematic for some people.)

If you do, did you run

```
sudo aticonfig --adapter=all --initial
```
?

It's an Intel/Ati -hybrid, I guess that's why I'm so screwed with it. I tried catalyst 12.4 some time ago, and it could detect both GPU's but I never could get the DGPU to actually take over. I doubt the new 12.6's are any better in this aspect?

Edit: And if I try to install the proprietary fglrx driver from the "Restricted Drivers", it just fails.

---

### Post by QIII on 2012-07-27
Using the "Addition Drivers" graphical install does fail for some users.  Don't ask me why.  It seems to generally work from the command line (see the wiki in my signature and find "... alternate command line method ...")

When you had it installed, did Catalyst give you an option to switch and did you log out and log back in?  I've googled instances where people have claimed that this works, but they are always followed by a dozen comments that it didn't.

I got my daughter's ATI/ATI machine to work after quite a bit of frustration, but that was only one machine.

---

### Post by Pihpe on 2012-07-27
Tried both, installing the fglrx - driver from the command line (apt-get install fglrx), and also tried to install it by downloading the Catalyst 12.6 from AMD's website and building the packages from that. 

Both basically ended up the same, with the X giving the fallback 2D mode. The only difference was that with the Catalyst 12.6 install, it seemed to also hang up in that screen. =)

I wonder if it is even possible to get it to work with AMD/Intel -switchables?

---

### Post by wegah on 2012-09-15
No. From now. It's impossible to use the discrete card in our envy second generation.

Here you get more infos.
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

The good news is that with quantal and PRIME. Everything is working for now. At last something.

Besides HPship just stoped to give support for this lines. stoped new drivers. Cripletd our bios. turning our HM67 chipset a piece of money waste.

still have a chance of in future the card work.

HP. Never more.

---

