---
title: "stop Battery Charge at less than 100%"
date: 2009-12-01
forum: Hardware
---

### Post by ikacer on 2009-12-01
Keeping a battery fully charged all the time is really bad for it. So I'm wondering if there is a way to tell my laptop to do something like this:

-stop charging when >= 90%
-start charging when < 84%

Any suggestions?

---

### Post by Native Dialect on 2009-12-01
If your battery is Li-Ion, then generally speaking, you should be fine. Li-Ion batteries do not suffer from the memory effect like nickel cadmium batteries do. Alternatively, you can remove your battery and run strictly from AC power if you know that you are going to leave your laptop plugged in for extended periods of time.

---

### Post by ikacer on 2009-12-01
While it is true that Lithium batteries are memory free, that has nothing to do with storage capacity loss from keeping it charged all the time. Keeping it fully charged still kills the battery. Isn't there some power manager settings for this, or some other program that has this I can use instead of gnome-power-manager?

It just occurred to me that maybe I can do this in the BIOS. I'm going to look for that now. I'll update this post on what I find.

Edit: ok, I just checked, and I can't do this through the BIOS.

---

### Post by bademeister on 2009-12-02
Dear ikacer,

I too am looking for something like this. I think it would really be nice if Ubuntu had something like "advanced powenmanagement for laptops".

In the meantime, if you are lucky enough to own a thinkpad you may want to check this site: [http://www.thinkwiki.org/wiki/Tp_smapi#Battery_charge_control_features]("http://www.thinkwiki.org/wiki/Tp_smapi#Battery_charge_control_features")
which apparently has some hacks which allow you to do just that. If you are unlucky (I am on a macbook pro now...), then you can stick around with me to hope that somebody who knows something about this comes along ...

cheers
Paul

---

### Post by ikacer on 2009-12-02
bademeister, you are awesome. I have a thinkpad, so the tp_smapi kernel module you linked to works for me :)

Still, this seems like a pretty basic feature, and I'm really surprised Ubuntu doesn't have better support for it. I found a Ubuntu brainstorm post on this:
[http://brainstorm.ubuntu.com/idea/22336/]("http://brainstorm.ubuntu.com/idea/22336/")

---

### Post by bademeister on 2009-12-02
Hey,

good for you ;) Also thanks for pointing out the brainstorm idea, i voted for it.

Yeah, the whole power management stuff is really pretty low level right now. I am also looking at how to reduce power consumption and am amazed by the amount of hacking that is still required.... even though most things seem to be similar on a lot of laptops, most everyone likes write their own script. There is some good stuff coming with the laptop-mode-tools but not a lot on the forums... I think instead of focusing so much on boot time (which is a good thing too, but first things first), the ubuntu team should do something in the power management field ;) 

Wouldn't it be great if you could donate towards a specific cause in open source? I would put down $50 for somebody to work on this power management stuff and integrate everything with gnome-power-manager. 

cheers
Paul

---

