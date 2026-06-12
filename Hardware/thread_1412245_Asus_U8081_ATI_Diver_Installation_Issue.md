---
title: "Asus U80/81 ATI Diver Installation Issue"
date: 2010-02-21
forum: Hardware
---

### Post by ladgrove on 2010-02-21
Hello lads & ladettes,

just thought I'd post something up here to say I have an Asus 80/81 Notebook(For the purposes of this post, they're the same model), which runs an ATI Mobility Radeon HD 4750 Graphics Card.

I follow the usual prompts on the ATI website & downloaded me the latest version of the ATI auto installer, which runs & tells me the driver installed correctly, however, under System->Hardware Drivers, no ATI proprietary driver is displayed, nor can I run desktop effects etc.

It's been a little while since I've used Ubuntu & I've barely touched 9.10, so consider me a noob here. I've noticed that xorg.conf isn't the same either... not sure I like this new update method, seems to take away a bit of the flexibility at the expense of security, but that's another issue :p

Anyway, there is not much info about this particular laptop model on the web, so I'm wondering if someone can help me out, I get the feeling this should work, and have seen 2 reports online of people running Compiz with this model, but with no instructions of how to correctly get the ATI drivers running. 

I'll post all the relevant/necessary output of files as needed, if you could kindly give the commands needed to generate this output, that'd be awesome :)

Cheers,
Josh.

---

### Post by Vakman on 2010-02-21
What is the output of:
```
glxinfo | grep direct
```
Next, I have not heard of this "auto-installer". What is this?
Did you have to select your card model? Did you choose 4700 series or 4000 mobility series. This card is different so there may be problems. Either way, let us see what that outputs. If it reads "Yes" then that is a good sign :)

---

### Post by ladgrove on 2010-02-21
Thanks for the uber-quick reply Thisislaw.

**Some more info:**

Running Ubuntu Karmic 9.10 64-Bit
2.6.31-16-generic
Grub2 with Win7 dual-boot

The output of glxinfo | grep direct is:

```

```

Doesn't output anything?!

Also, yes, by 'Auto-Installer' I mean that I went to the ATI/AMD website & selected the 4700 model driver, then, in sudo, ran the 

```
sudo sh./ ati-driver-installer-10-2-x86.x86_64.run
```

I will give the 4000 a try & see what happens.

Cheers,
Josh

---

